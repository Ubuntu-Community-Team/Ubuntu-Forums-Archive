---
title: "apt-get dist-upgrade removes /usr/local/bin &amp; resets update-alternatives"
date: 2014-03-25
forum: General Help
---

### Post by oxsyn on 2014-03-25
On ubuntu 14.04 I'm compiling a custom vim binary using the process detailed here: [https://gist.github.com/nfarrar/9745304](https://gist.github.com/nfarrar/9745304).  In summary, I install it to /usr/local/bin and register it using update-alternatives, without removing the existing vi & vim packages.
When I run sudo apt-get -y update &7 sudo apt-get -y upgrade && sudo apt-get -y dist upgrade the binaries are removed from /usr/local/bin and deregistered from the alternatives configuration.

Is this the way it is supposed to function? And if so, I assume there's something I should be doing to prevent this from happening. Any suggestions?

> [SIZE=2]# install build dependencies for vim:
sudo apt-get -y build-dep vim

# install some additional, necessary tools:
sudo apt-get -y install checkinstall mercurial python-dev python3.3-dev

# clone the latest version of vim source:
sudo hg clone [https://vim.googlecode.com/hg/](https://vim.googlecode.com/hg/) /usr/local/src/vim

# change to src directory
pushd /usr/local/src/vim

# build our makefile (install to /usr/local):
sudo ./configure \
    --prefix=/usr/local \
    --enable-gui=no \
    --with-features=huge \
    --with-x \
    --enable-cscope \
    --enable-perlinterp \
    --enable-luainterp \
    --enable-rubyinterp \
    --enable-pythoninterp \
    --with-python-config-dir=$(python2.7-config --configdir)

## python3 support (not currently working)
#  --enable-python3interp \
#  --with-python3-config-dir=$(python3.3-config --configdir)
# 
# with gui support
#  --enable-gui=auto \
#  --enable-gtk2-check \
#  --enable-gnome-check
#
# for additional configuration options use ./configure --help

# build vim, specify the runtimedir
sudo make VIMRUNTIMEDIR=/usr/share/vim/vim74

# install vim using checkinstall (debian)
sudo checkinstall

# return to previous directory
popd

# install /usr/local/bin/vim as alternative for vi, vim, and editor
sudo update-alternatives --install "/usr/bin/vim" "vim" "/usr/local/bin/vim" 1
sudo update-alternatives --install "/usr/bin/vi" "vi" "/usr/local/bin/vim" 1
sudo update-alternatives --install "/usr/bin/editor" "editor" "/usr/local/bin/vim" 1

# set /usr/local/bin/vim as default for vi, vim and editor
sudo update-alternatives --set vim "/usr/local/bin/vim"
sudo update-alternatives --set vi "/usr/local/bin/vim"
sudo update-alternatives --set editor "/usr/local/bin/vim[/SIZE]

Edit: Copied in build process.

---

### Post by monkeybrain20122 on 2014-03-25
In order to avoid that you should have named the package something else like vim-git instead of vim during checkinstall and then run update-alternatives, that way it wouldn't be removed at update. It is obvious if you take a look at synaptic, there is always only one entry for package foo no matter where you install it. When update apt-get checks the package's name and version and decides whether to replace it or not, doesn't matter where you install it. You probably don't notice this if you manage your packages by just copy and pasting commands (one reason I am a big proponent of the gui for new users, at least you can intuit your way rather than copying and pasting gibberish as if they are magical mantras) 

Also, I think in order to update-alternatives you also need to set one for the system one. Basically update alternatives creates a symlink which you can switch on the fly to decide which version to use, e.g the symlink /usr/local/bin/vim may point to /usr/bin/vim or /usr/local/bin/vim-git when you configure it, so you need to have entries for both.

BTW, I think using the option -y (yes to all) in upgrade and install is a very bad idea as it doesn't give you a chance to abort it if it wants to remove something else or shows other anomalies. It takes you a few seconds to type 'y' when prompted after reading the outputs but can save you from lots of potential troubles.

---

### Post by oxsyn on 2014-03-26
> **monkeybrain20122 said:**
> In order to avoid that you should have named the package something else like vim-git instead of vim during checkinstall and then run update-alternatives, that way it wouldn't be removed at update. It is obvious if you take a look at synaptic, there is always only one entry for package foo no matter where you install it. When update apt-get checks the package's name and version and decides whether to replace it or not, doesn't matter where you install it. You probably don't notice this if you manage your packages by just copy and pasting commands (one reason I am a big proponent of the gui for new users, at least you can intuit your way rather than copying and pasting gibberish as if they are magical mantras) 

Also, I think in order to update-alternatives you also need to set one for the system one. Basically update alternatives creates a symlink which you can switch on the fly to decide which version to use, e.g the symlink /usr/local/bin/vim may point to /usr/bin/vim or /usr/local/bin/vim-git when you configure it, so you need to have entries for both.

BTW, I think using the option -y (yes to all) in upgrade and install is a very bad idea as it doesn't give you a chance to abort it if it wants to remove something else or shows other anomalies. It takes you a few seconds to type 'y' when prompted after reading the outputs but can save you from lots of potential troubles.

Thank you. :) That explains what I was missing. I'm using the name vim-local for the package instead - prior to this I had never used checkinstall. I understand your concern about the -y flag with apt in the script - in this case I'm using this to install a custom compiled version of vim on new systems with a repeatable process on virtual machines that have a saved state that can be rolled back to (if necessary) so I think it's O.K. :) Now I just have to figure out how to get the python3 support working. Thanks again!

[https://github.com/nfarrar/dotfiles-bin/blob/master/bin/install/tools/vim.sh](https://github.com/nfarrar/dotfiles-bin/blob/master/bin/install/tools/vim.sh)
> #!/usr/bin/env bash


echo 'comiling vim from source ...'


VIM_SRC_URL='https://vim.googlecode.com/hg/'
VIM_SRC_DIR='/usr/local/src/vim'
VIM_BIN_DIR='/usr/local'
VIM_RUNTIME_DIR='/usr/share/vim/vim74'


# install build dependencies for vim:
sudo apt-get -y build-dep vim


# install some additional, necessary tools:
sudo apt-get -y install checkinstall mercurial python-dev python3.3-dev


# if src doesn't already exist, clone - otherwise update
if [ -d $VIM_SRC_DIR ]; then
    sudo hg clone $VIM_SRC_URL $VIM_SRC_DIR
else
    pushd $VIM_SRC_DIR && hg pull && popd
fi


# change to src directory
pushd $VIM_SRC_DIR


# build our makefile (install to /usr/local):
sudo ./configure \
    --prefix=/usr/local \
    --enable-gui=no \
    --with-features=huge \
    --with-x \
    --enable-cscope \
    --enable-perlinterp \
    --enable-luainterp \
    --enable-rubyinterp \
    --enable-pythoninterp \
    --with-python-config-dir=$(python2.7-config --configdir)


## python3 support (not currently working)
#  --enable-python3interp \
#  --with-python3-config-dir=$(python3.3-config --configdir)
#
# with gui support
#  --enable-gui=auto \
#  --enable-gtk2-check \
#  --enable-gnome-check
#
# for additional configuration options use ./configure --help


# build vim, specify the runtimedir
sudo make VIMRUNTIMEDIR=$VIM_RUNTIME_DIR


# install vim using checkinstall (debian)
sudo checkinstall \
    --pkgname=vim-local \
    --pkggroup=vim \
    --pkgsource=/usr/local/src/vim \
    --default


# return to previous directory
popd


# install /usr/local/bin/vim as alternative for vi, vim, and editor
sudo update-alternatives --install "/usr/bin/vim" "vim" "/usr/local/bin/vim" 1
sudo update-alternatives --install "/usr/bin/vi" "vi" "/usr/local/bin/vim" 1
sudo update-alternatives --install "/usr/bin/editor" "editor" "/usr/local/bin/vim" 1


# set /usr/local/bin/vim as default for vi, vim and editor
sudo update-alternatives --set vim "/usr/local/bin/vim"
sudo update-alternatives --set vi "/usr/local/bin/vim"
sudo update-alternatives --set editor "/usr/local/bin/vim"

---

