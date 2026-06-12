---
title: "mplayer doesn install in Hoary"
date: 2005-04-05
forum: General Help
---

### Post by Teleyinex on 2005-04-05
I have found that today its impossible to install mplayer via marillat, 'cause we have libfontconfig1 with version: 2.2.3-4ubuntu7 and mplayer requires >= 2.3.0 so we CANT install it. 

There are another problems with other packects as libvorbisa0.

Some one knows more?

---

### Post by brickbat on 2005-04-05
hi,

I installed mplayer but vouldn't get it working.   There is an mplayer-custom in one of the repositories and it installed it successfully.  When I tried to run it however, it just crashed.

ciao
bb

---

### Post by mtron on 2005-04-05
In my subjective opinion (plz correct me) i get better mplayer preformance when I build it from the tar.gz file. Try using the following script (taken from an earlier post on this forum). It will inshalla compile & install the packages, codecs and the latest mplayer (MPlayer-1.0pre6a) with the default blue skin on hoary

1. fist check that your sources.list is up-to-date
[INDENT]run from a terminal window
**$ sudo gedit /etc/apt/sources.list**
Check that you have the following resp.:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./

now reload your package list 
**$ sudo apt-get update**
[/INDENT]

2. now type in the terminal window
[INDENT]**$ gedit mplayer.sh**

Copy the following code in the file and save it 

# start script mplayer install
sudo mkdir mplyr
cd mplyr
# get & install Ubuntu packages
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y libdvdcss2
# get mplayer program
wget http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre6a.tar.bz2
# get codecs
wget http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20050216.tar.bz2
#
# get fonts
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2
#
# get skin
wget http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2
#
tar -xjf MPlayer-1.0pre6a.tar.bz2
cd MPlayer-1.0pre6a
./configure --enable-gui
make
make install
#
cd ..
tar -xjf essential-20050216.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20050216/* /usr/local/lib/codecs/
#
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
#
tar -xjf Blue-1.4.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
#
cp -r Blue/* /usr/local/share/mplayer/Skin/default/
#
cp MPlayer-1.0pre6a/etc/* /usr/local/etc/mplayer/
#
cd ..
# start gmplayer program
gmplayer
#
exit
# end script mplayer install

save the file and close gedit[/INDENT]

3. to start the script type:
[INDENT]**$ sudo ./mplayer.sh**
at the end the mplayer gui should pop up. if yes, close mplayer if no, post the error plz.[/INDENT]

4. to delete the temporary folder "mplyr" that was created by the script in your home directory, [INDENT]you need to change the ownership. to do this type:
**$ sudo chown -R your_username_here mplyr**

now you can delete the folder in nautilus. to run mplayer create a launcher with the Command "gmplayer"[/INDENT]

Hope this helps sb. Cheers 
Michael

---

### Post by Teleyinex on 2005-04-05
Thanks for the script, cause you have showed me the dev packages of Xorg for compile mplayer with xv support. 

I prefer too to use a compiled version of mplayer. But my friends uses the mplayer from marillat, and what I want was to give it a try. Now is perfectly clear: compile ALWAYS mplayer, cause the mplayer from marillat has lots of dependencies.

Thanks for all.

---

