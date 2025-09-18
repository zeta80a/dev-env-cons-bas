# CentOS7のベースイメージを取得
FROM centos:7

# vault.centos.org を使うように yum repo を修正
RUN sed -i 's|mirrorlist=|#mirrorlist=|g' /etc/yum.repos.d/CentOS-*.repo && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*.repo

# ぱっけ更新
RUN yum update -y && yum clean all
    
# yumでepel-releaseとnginxをインストール
RUN yum -y install epel-release && \
    yum -y install nginx && \
    yum clean all

# ホスト側のindex.htmlをコピー
COPY index.html /usr/share/nginx/html

# コンテナ起動時に実行するコマンド
ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]