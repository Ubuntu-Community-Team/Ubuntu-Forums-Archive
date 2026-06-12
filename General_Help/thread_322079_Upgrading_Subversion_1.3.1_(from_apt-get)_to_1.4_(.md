---
title: "Upgrading Subversion 1.3.1 (from apt-get) to 1.4 (from source)?"
date: 2006-12-19
forum: General Help
---

### Post by dudinatrix on 2006-12-19
I have Subversion 1.3 installed using the Ubuntu repositories (Dapper Drake). Works great, been using it for months. I now need to upgrade to 1.4, but the repositories only have 1.3. 

How do I go about upgrading to 1.4 from source? Is that going to cause any problems in the future when the repository version is updated, or will it just "know" that I upgraded manually?

Any specific help would be appreciated.. I'm not used to installing/upgrading from source, so any guidance would help! :)

---

### Post by pay on 2006-12-19
Firstly install the needed files```
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep subversion

```Then download the source and extract it```
wget http://subversion.tigris.org/downloads/subversion-1.4.2.tar.bz2
tar jxvf subversion-1.4.2.tar.bz2
cd subversion-1.4.2
./configure
make
sudo checkinstall make install
sudo dpkg -i subversion*.deb
```Theres alot more information about the ./configure process and adding support for certian libraries in the tar ball with the file INSTALL. Checkinstall makes a debian file, so apt will know about it and if there is a newer version it will update it for you. This is the ./configure script that I used```
./configure --prefix=/usr --host=x86_64-pc-linux-gnu --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --with-apr=/usr --with-apr-util=/usr --without-apxs --enable-javahl --without-jikes --with-jdk=/opt/blackdown-jdk-1.4.2.03 --with-swig --with-neon=/usr --with-berkeley-db --with-zlib --with-python --enable-nls --with-apr=/usr --with-apr-util=/usr --disable-experimental-libtool --disable-mod-activation --libdir=/usr/lib64 --build=x86_64-pc-linux-gnu
```

---

### Post by dudinatrix on 2006-12-20
Thanks a ton for your detailed reply! It all looks great, except that last ./configure bit looks pretty overwhelming to me; do I need to copy paste that, or can/should just do "./configure" with no parameters?

Also, what exactly does this do?:
```
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep subversion
```I never used "aptitude" before, is that the same as apt-get? By the way, this is on a server with no GUI (so thanks for the command line instructions)!

And finally, I assume this will keep all of my existing subversion configuration in tact?

Thanks again!!

---

### Post by pay on 2006-12-20
./configure will more than likely figure out it all for you, but if something goes wrong then you will need to configure it by hand like I did. aptitude is similar to apt-get, yet I believe it handles dependencies better. apt-get build-dep <package> downloads all the required files for compiling  <package>. I think that it will keep your configuration in tact, but I can't be sure so you might want to wait for someone else to back that up. But it will remove the old 1.3.* version.

---

