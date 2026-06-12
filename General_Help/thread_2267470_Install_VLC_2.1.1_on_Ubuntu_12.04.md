---
title: "Install VLC 2.1.1 on Ubuntu 12.04"
date: 2015-03-01
forum: General Help
---

### Post by nathandetroit on 2015-03-01
These instructions are for compiling and installing VLC 2.1.1 on Ubuntu 12.04

If you are coming here because you found out that this no longer works:

          sudo add-apt-repository ppa:djcj/vlc-stable

and this doesn’t work:

          sudo add-apt-repository ppa:videolan/stable-daily

then you have come to the right place. Unfortunately djcj is no longer maintaining the ppa, so this is no longer an option for Ubuntu 12.04.  As an alternative, it is possible to compile the source code for VLC and install it into Ubuntu 12.04. While this is a somewhat more involved and time consuming procedure, it is really not all that difficult. Simply follow the instructions below and you should be good to go.

Note: I did this for VLC 2.1.1, but it should also work for some later versions of VLC (although probably not the most recent versions, at least with respect to Ubuntu 12.04). I did this because I wanted to use VLC Mobile Remote on Android, and this requires VLC 2.1 or later. I’m using some old desktop hardware in relation to this, and the old hardware will not run any Ubuntu version later than 12.04. Before starting I recommend removing any VLC related PPAs, and completely uninstall (purge) VLC if you have already installed an older version.

To download and compile VLC:

Get the source code from the Videolan FTP site:

      Open a terminal
      cd to the directory you want to download to

              wget -c download.videolan.org/pub/videolan/vlc/2.1.1/vlc-2.1.1.tar.xz
      
      extract the source code from the tar file

              tar -xJvf vlc-2.1.1.tar.xz

      cd to the vlc-2.1.1 directory

             cd vlc-2.1.1

      Issue the following commands to compile the source code and install VLC (this will proabably take about 30 minutes, depending upon your hardware):

            sudo apt-get build-dep vlc
            ./configure
            make
            sudo make install

Here are all of the commands in order (after you have opened a terminal and issued a cd command to move to your chosen download directory):

              wget -c download.videolan.org/pub/videolan/vlc/2.1.1/vlc-2.1.1.tar.xz
              tar -xJvf vlc-2.1.1.tar.xz
             cd vlc-2.1.1
            sudo apt-get build-dep vlc
            ./configure
            make
            sudo make install

After the install you will need to logout and log back in  again (or possibly reboot) in order for the VLC app to show up in your list of applications.

---

### Post by brickz2 on 2015-09-23
Hi, nathandetroit:
 I succeed as your instruction. But when i move the vlc folder to another path, i failed to run the ./configure or make command. The error is as below:
 "src/vlc-2.1.1/autotools/missing: line 81: aclocal-1.14: command not found"
 Can you kindly tell me how to fix this error? Thx.

---

