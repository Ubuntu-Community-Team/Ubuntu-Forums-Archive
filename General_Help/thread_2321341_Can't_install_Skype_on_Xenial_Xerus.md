---
title: "Can't install Skype on Xenial Xerus"
date: 2016-04-22
forum: General Help
---

### Post by Laura_Nbl on 2016-04-22
Hi

I'm not really good at IT so please explain it like I'm 5.
Ok, so I downloaded The Skype deb.4.3.0.37 i386 package from the Skype webpage, and am able to open it with Ubuntu Software. But- when I click on 'Install' it acts as though it's installing for a second and then the install button become active again (if that makes sense).

So, I googled and found this site with instructions on how to install it via the terminal. But, every time I enter,
```
$ sudo dpkg --add-architecture i386
```

I get this reply 
```


bash: /$: No such file or directory


```

Any thoughts?

Oh, and Dropbox did the same thing, but I found a command that 'fixed it'.

---

### Post by mastablasta on 2016-04-22
shouldn't Skype be available in software center?

---

### Post by howefield on 2016-04-22
That does look like a valid command, can you copy/paste from the terminal back here to include the entire input and output.

---

### Post by Laura_Nbl on 2016-04-22
Here it is:```
 laura@Laura-Aspire-E5-511:~$ $ sudo dpkg --add-architecture i386
$: command not found
laura@Laura-Aspire-E5-511:~$ 

```

Also, no Skype is not available from Software.

---

### Post by sudodus on 2016-04-22
Please remove the $ character (it is the prompt, does not belong to the command line).

---

### Post by Laura_Nbl on 2016-04-22
I didn't add it. It's output.

---

### Post by Laura_Nbl on 2016-04-22
Oh, wait. I see what you mean.

---

### Post by sudodus on 2016-04-22
Please try the following command line, and post the output

```
sudo dpkg --add-architecture i386
```

---

### Post by Laura_Nbl on 2016-04-22
Ok, the first two steps of the tutorial worked, but then I wanted to do the third step and it says I need superuser privilege. 

```
laura@Laura-Aspire-E5-511:~$  sudo dpkg --add-architecture i386
[sudo] password for laura: 
laura@Laura-Aspire-E5-511:~$ sudo apt-get update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Get:2 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]
Hit:3 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:4 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Fetched 247 kB in 3s (66.4 kB/s)                   
Reading package lists... Done
laura@Laura-Aspire-E5-511:~$ dpkg -i skype-ubuntu-precise_4.3.0.37-1_i386.deb
dpkg: error: requested operation requires superuser privilege
```

---

### Post by howefield on 2016-04-22
> **Laura_Nbl said:**
> Here it is:```
 laura@Laura-Aspire-E5-511:~$ $ sudo dpkg --add-architecture i386
$: command not found
laura@Laura-Aspire-E5-511:~$ 

```

Also, no Skype is not available from Software.

Looks like you added a $ sign to precede the command as sudodus said, it should look like...

```
laura@Laura-Aspire-E5-511:~$ sudo dpkg --add-architecture i386
```

I haven't checked for 16.04 but skype should be available (certainly used to be) from the Software Centre but you'd need to enable the partners repository to see it.

---

### Post by sudodus on 2016-04-22
```
**sudo** dpkg -i skype-ubuntu-precise_4.3.0.37-1_i386.deb
```

---

### Post by Laura_Nbl on 2016-04-22
I did, still no Skype.

```
laura@Laura-Aspire-E5-511:~$ sudo dpkg -i skype-ubuntu-precise_4.3.0.37-1_i386.deb
dpkg: error processing archive skype-ubuntu-precise_4.3.0.37-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubuntu-precise_4.3.0.37-1_i386.deb
laura@Laura-Aspire-E5-511:~$ 
```

---

### Post by westie457 on 2016-04-22
```
 cd /path/to/deb    #real path to where the deb file is.
sudo dpkg -i name_of_file.deb
``` should sort it .
Post the output especially if any errors.

Thank you

---

### Post by Laura_Nbl on 2016-04-22
Errr, sorry, I don't quite understand. Like I said, I'm a noob. I tried this:

```
sudo dpkg -i386.deb /home/laura
[sudo] password for laura: 
dpkg: error: unknown option -u

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
laura@Laura-Aspire-E5-511:~$ 
```

but evidently I misunderstood.

---

### Post by howefield on 2016-04-22
Just for info, Skype is available to install from the Partner repository.

Open up the Software and Updates application, go to Other Software tab and check the Canonical Partners option, you'll be asked for your password and to update your sources. Then

```
sudo apt install skype
``` 

will install it.

---

### Post by sudodus on 2016-04-22
+1

Installing from the repositories is easier and you get automatic updates too :-)

---

### Post by Laura_Nbl on 2016-04-22
Huh, it doesn't appear in Software though. But it does work in terminal. Would that work or would I still have trouble installing it? Also, it says that it would use over 300mb of disk space, is that normal?

---

### Post by howefield on 2016-04-22
> **Laura_Nbl said:**
> Huh, it doesn't appear in Software though. But it does work in terminal. Would that work or would I still have trouble installing it? Also, it says that it would use over 300mb of disk space, is that normal?

I noticed it didn't show in the Ubuntu Software application but does install fine via the terminal. 
Yes it is normal to take that much space, in my installation here, it needs 83.4MB of downloads and will take 379MB of the disk, skype itself isn't taking that much disk space.. it is all the dependencies that it needs to run.

```
hugh@xenial:~$ sudo apt install skype
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 gstreamer1.0-plugins-base:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libbsd0:i386 libc6:i386 libcap2:i386 libcdparanoia0:i386 libcomerr2:i386 libcups2:i386 libdbus-1-3:i386
  libdbusmenu-qt2:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386
  libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgcc1:i386 libgcrypt20:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglib2.0-0:i386 libgmp10:i386 libgnutls30:i386 libgpg-error0:i386 libgssapi-krb5-2:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhogweed4:i386 libice6:i386 libicu55:i386
  libidn11:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386 libllvm3.8:i386
  liblzma5:i386 libmng2:i386 libmysqlclient20:i386 libnettle6:i386 libogg0:i386 libopus0:i386 liborc-0.4-0:i386
  libp11-kit0:i386 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libpulse0:i386 libqt4-dbus:i386
  libqt4-declarative:i386 libqt4-network:i386 libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386
  libqtwebkit4:i386 libsamplerate0:i386 libselinux1:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libsystemd0:i386 libtasn1-6:i386 libtheora0:i386
  libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386 libuuid1:i386 libvisual-0.4-0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxml2:i386 libxrender1:i386
  libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxt6:i386 libxv1:i386 libxxf86vm1:i386 mysql-common
  qt-at-spi:i386 skype-bin:i386 sni-qt:i386 zlib1g:i386
Suggested packages:
  gvfs:i386 nas:i386 glibc-doc:i386 locales:i386 rng-tools:i386 gnutls-bin:i386 krb5-doc:i386 krb5-user:i386
  libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386 jackd2:i386 opus-tools:i386
  libqt4-declarative-folderlistmodel:i386 libqt4-declarative-gestures:i386 libqt4-declarative-particles:i386
  libqt4-declarative-shaders:i386 qt4-qmlviewer:i386 libqt4-dev:i386 libthai0:i386 qt4-qtconfig:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed
  gcc-5-base:i386 gcc-6-base:i386 gstreamer1.0-plugins-base:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libbsd0:i386 libc6:i386 libcap2:i386 libcdparanoia0:i386 libcomerr2:i386 libcups2:i386 libdbus-1-3:i386
  libdbusmenu-qt2:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386
  libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgcc1:i386 libgcrypt20:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglib2.0-0:i386 libgmp10:i386 libgnutls30:i386 libgpg-error0:i386 libgssapi-krb5-2:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhogweed4:i386 libice6:i386 libicu55:i386
  libidn11:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386 libllvm3.8:i386
  liblzma5:i386 libmng2:i386 libmysqlclient20:i386 libnettle6:i386 libogg0:i386 libopus0:i386 liborc-0.4-0:i386
  libp11-kit0:i386 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libpulse0:i386 libqt4-dbus:i386
  libqt4-declarative:i386 libqt4-network:i386 libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386
  libqtwebkit4:i386 libsamplerate0:i386 libselinux1:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libsystemd0:i386 libtasn1-6:i386 libtheora0:i386
  libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386 libuuid1:i386 libvisual-0.4-0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxml2:i386 libxrender1:i386
  libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxt6:i386 libxv1:i386 libxxf86vm1:i386 mysql-common
  qt-at-spi:i386 skype skype-bin:i386 sni-qt:i386 zlib1g:i386
0 to upgrade, 130 to newly install, 0 to remove and 20 not to upgrade.
Need to get 83.4 MB of archives.
After this operation, 379 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

---

### Post by Laura_Nbl on 2016-04-22
Ok, problem solved. It actually was the Partner repository. Thanks for you replies!

---

