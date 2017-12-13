FROM amazonlinux:latest
COPY virtualhost.conf /etc/nginx/conf.d/virtualhost.conf
RUN yum update -y
RUN yum install -y git bzip2 gcc openssl-devel readline-devel zlib-devel nginx mysql-devel
RUN mkdir ~/.rbenv
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv
RUN mkdir ~/.rbenv/plugins ~/.rbenv/plugins/ruby-build
RUN git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
RUN echo "NETWORKING=yes" >/etc/sysconfig/network
RUN cd ~/.rbenv/plugins/ruby-build && ./install.sh && \
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile && \
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile && \
source ~/.bash_profile && \
rbenv install 2.3.5 && rbenv global 2.3.5
RUN source ~/.bash_profile && gem install rails --no-ri --no-rdoc && gem install bundler && gem install mysql2
RUN /etc/init.d/nginx start
RUN echo "clear" > /usr/local/bin/c
RUN echo "ls" > /usr/local/bin/l
RUN echo "ls -al" > /usr/local/bin/ll
RUN echo "pwd" > /usr/local/bin/p
RUN chmod 755 /usr/local/bin/c /usr/local/bin/ll /usr/local/bin/l /usr/local/bin/p

