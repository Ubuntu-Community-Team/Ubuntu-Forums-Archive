---
title: "Adding Javascript to MediaTomb on Ubuntu 14.04 Error"
date: 2014-06-11
forum: General Help
---

### Post by archangel714 on 2014-06-11
I am attempting to rebuild the  MediaTomb version 0.12.1-5ubuntu2 with javascript added in. However I am  getting a “dpkg-source: error: aborting due to unexpected upstream  changes, see /tmp/mediatomb_0.12.1-5ubuntu2.diff.GbqfBo”
dpkg-buildpackage: error: dpkg-source -b mediatomb-0.12.1 gave error exit status 2
 
my build process is as follows...
1.) sudo mkdir ~/temp_files/
2.) cd ~/temp_files/
3.) sudo apt-get build-dep mediatomb
4.) sudo apt-get source mediatomb
5.) sudo nano mediatomb-0.12.1/debian/rules
6.) change --disable-libjs to --enable-libjs
7.) Save and exit nano
8.) sudo wget [http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs2d_1.9.1.16-20_amd64.deb](http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs2d_1.9.1.16-20_amd64.deb)
9.) sudo wget [http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs-dev_1.9.1.16-20_amd64.deb](http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs-dev_1.9.1.16-20_amd64.deb)
10.) sudo dpkg -i libmozjs2d_1.9.1.16-20_amd64.deb
11.) sudo dpkg -i libmozjs-dev_1.9.1.16-20_amd64.deb
12.) cd mediatomb-0.12.1/
13.) sudo ./configure
14.) sudo su
15.) sudo dpkg-buildpackage -us -uc

 
That when the error above appears. I am still somewhat new to  Unbuntu/Linux and am not sure what is going on. Thought it might be  because I never updated the changelog (which I did not have to do on a  previous build for an earlier Ubuntu). Sadly updating the changelog does  not seem to remove the errors.

 
The /tmp/mediatomb_0.12.1-5ubuntu2.diff.GbqfBo is confusing to me.  The top area looks like the same change log located in the changelog for  mediatomb.

 
Thanks in advance for any help!

---

### Post by cariboo on 2014-06-12
Moved to General Help, as you'll probably get more help here.

---

### Post by pmas001 on 2014-11-20
Hello
I'm aa newbie with ubuntu, and hope I'm following the rules.
I hope this helps. I was in the same boat as you. Just came across this post ([http://richardappleby.wordpress.com/2012/05/31/mediatomb-on-ubuntu-12-04/](http://richardappleby.wordpress.com/2012/05/31/mediatomb-on-ubuntu-12-04/)). This issue is addressed near the bottom of the comments section (2014). basically swap out the new mediatomb-0.12.1/src/scripting directory with that from mediatomb_0.12.1.orig.tar.gz and retry the compile.

Oh, also the compile command is different, but I'm too newb to understand it :)

seems to have worked for me...
good luck!

---

