FROM ubuntu:14.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update

# ghc-7.8.4
RUN apt-get install -y wget atool build-essential
WORKDIR /root
RUN wget https://www.haskell.org/ghc/dist/7.8.4/ghc-7.8.4-x86_64-unknown-linux-deb7.tar.bz2
RUN aunpack ghc*
WORKDIR /root/ghc-7.8.4
RUN ./configure
RUN make install

# current cabal
RUN apt-get install -y cabal-install zlib1g-dev
WORKDIR /root
RUN cabal update
RUN cabal install cabal-install
ENV PATH /root/.cabal/bin:${PATH}
RUN apt-get remove -y cabal-install

# happy and alex
RUN apt-get install -y alex
RUN cabal install happy
RUN rm /root/.ghc -rf
