---
title: "Install Kompozer or Blue Griffon web editors"
date: 2016-07-19
forum: General Help
---

### Post by yoramdavid on 2016-07-19
Hello,

I have been using Komposer web editor for many years, until my last system which was Linux Mint Cinnamon 17.
But now I cannot install it, I followed those threads with no luck:
- [http://askubuntu.com/questions/767028/install-kompozer-on-ubuntu-16-04]("http://askubuntu.com/questions/767028/install-kompozer-on-ubuntu-16-04")
- [https://ubuntu-mate.community/t/kompozer-in-ubuntu-mate-16/6302/2]("https://ubuntu-mate.community/t/kompozer-in-ubuntu-mate-16/6302/2")

I then read that Blue Griffon was a better package and also tried to install it without luck, following this thread:
- [https://forums.linuxmint.com/viewtopic.php?t=70689]("https://forums.linuxmint.com/viewtopic.php?t=70689")
I dound no executale file inside the opt folder, I then downloaded it from here: [http://www.bluegriffon.org/#download]("http://www.bluegriffon.org/#download") and installed it but all I get is an icon on the menu called Blue Griffon with an interrogation mark.

Can any one help?

---

### Post by DogMatix on 2016-07-19
I would recommend you give 'Bluefish Editor' a look over. I think it will accomplish everything you require and is available in the Ubuntu Software Centre.

---

### Post by &amp;KyT$0P# on 2016-07-19
I use BlueGriffon every once in a while and I can't even follow that Linux Mint thread.  All you need to do is just extract the BlueGriffon .tar.bz2 and run the bluegriffon executable from the place you extracted it.

If you need it more accessible, like in your desktop's menus, here's my .desktop file for BlueGriffon 1.7.2:
```
[Desktop Entry]
Encoding=UTF-8
Name=BlueGriffon
Exec=/home/user/bluegriffon/bluegriffon
Icon=/home/user/bluegriffon/chrome/icons/default/default48.png
Categories=Development
Version=1.0
StartupNotify=true
Type=Application
Terminal=0

```
(Obviously, you would replace /home/user/bluegriffon with the full path to where you chose to put BlueGriffon's installation directory.)

I don't use Mate, so not sure if they do this differently, but at least for the desktops I've used it should work to simply save that as "bluegriffon.desktop" in ~/.local/share/applications (or, if you make it system-wide install, /usr/share/applications).

Hope this helps :)


(On a related note, I've been wanting to set up the new 2.1.1 version of BlueGriffon for myself for a while now, but haven't got around to it... 8-[  so if you're using BlueGriffon 2.1.1, the .desktop file might not be quite right.  I don't know.)

---

### Post by oui on 2016-07-20
Hi David,
Simply install Seamonkey, an other (a bit different version) of kompoZer is included (CTRL 4 after starting Seamonkey); I use both Seamonkey as kompoZer and bluefish (but it is absolutely NOT the same and NOT comparable as bluefish doesn't show the page WYSYG. But Seamonkey as well as the old, not any more developed stand alone kompoZer create both relatively complex code, often an orgy of code (like Word or Office!). I use kompoZer to create url's (html files only with the url in the manner of Microsoft favorites) and to archive news paper article, text only part. So is the use of Seamonkey welcome (an other possible combination for that job would be the old kompoZer, it continues to start very well, plus Xombrero browser). Html development do I in bluefish as nothing changes your code in it!

to install the old stand alone kompoZer, you can use old Ubuntu packages (existing for both 32 or 64 bit). for 64 bit I did use

kompozer_0.8-b3.dfsg.1-0.1ubuntu2_amd64.deb
kompozer-data_0.8~b3.dfsg.1-0.1_all.deb
libidl0_0.8.14-0.4+b1_amd64.deb
libnspr4_4.10.7-1+deb8u1_amd64.deb
libnspr4-0d_4.10.7-1+deb8u1_amd64.deb
libnss3_3.17.2-1.1+deb8u2_amd64.deb
libnss3-1d_3.17.2-1.1+deb8u2_amd64.deb

I assume it will continue to work in the actual 16.04.

good luck

---

### Post by yoramdavid on 2016-07-20
> **DogMatix said:**
> I would recommend you give 'Bluefish Editor' a look over. I think it will accomplish everything you require and is available in the Ubuntu Software Centre.

Hi DogMatix, the reason I like Kompozer or Blue Griffon is that they are "YGWYS".
Thanks

---

### Post by yoramdavid on 2016-07-20
> **halogen2 said:**
> I use BlueGriffon every once in a while and I can't even follow that Linux Mint thread.  All you need to do is just extract the BlueGriffon .tar.bz2 and run the bluegriffon executable from the place you extracted it.

If you need it more accessible, like in your desktop's menus, here's my .desktop file for BlueGriffon 1.7.2:
```
[Desktop Entry]
Encoding=UTF-8
Name=BlueGriffon
Exec=/home/user/bluegriffon/bluegriffon
Icon=/home/user/bluegriffon/chrome/icons/default/default48.png
Categories=Development
Version=1.0
StartupNotify=true
Type=Application
Terminal=0

```
(Obviously, you would replace /home/user/bluegriffon with the full path to where you chose to put BlueGriffon's installation directory.)

I don't use Mate, so not sure if they do this differently, but at least for the desktops I've used it should work to simply save that as "bluegriffon.desktop" in ~/.local/share/applications (or, if you make it system-wide install, /usr/share/applications).

Hope this helps :)


(On a related note, I've been wanting to set up the new 2.1.1 version of BlueGriffon for myself for a while now, but haven't got around to it... 8-[  so if you're using BlueGriffon 2.1.1, the .desktop file might not be quite right.  I don't know.)

Hi halogen2,
I had done that before and it did not work, double clicking on the file called "bluegriffon" would do nothing nor the shortcut created in the menu.
I did it again and now it works, it takes quite a long time to open but it does and there is an working icon on the menu as well.
Thank you.

---

### Post by &amp;KyT$0P# on 2016-07-20
You're welcome!  :KS

---

### Post by yoramdavid on 2016-07-20
> **oui said:**
> Hi David,
Simply install Seamonkey, an other (a bit different version) of kompoZer is included (CTRL 4 after starting Seamonkey); I use both Seamonkey as kompoZer and bluefish (but it is absolutely NOT the same and NOT comparable as bluefish doesn't show the page WYSYG. But Seamonkey as well as the old, not any more developed stand alone kompoZer create both relatively complex code, often an orgy of code (like Word or Office!). I use kompoZer to create url's (html files only with the url in the manner of Microsoft favorites) and to archive news paper article, text only part. So is the use of Seamonkey welcome (an other possible combination for that job would be the old kompoZer, it continues to start very well, plus Xombrero browser). Html development do I in bluefish as nothing changes your code in it!

to install the old stand alone kompoZer, you can use old Ubuntu packages (existing for both 32 or 64 bit). for 64 bit I did use

kompozer_0.8-b3.dfsg.1-0.1ubuntu2_amd64.deb
kompozer-data_0.8~b3.dfsg.1-0.1_all.deb
libidl0_0.8.14-0.4+b1_amd64.deb
libnspr4_4.10.7-1+deb8u1_amd64.deb
libnspr4-0d_4.10.7-1+deb8u1_amd64.deb
libnss3_3.17.2-1.1+deb8u2_amd64.deb
libnss3-1d_3.17.2-1.1+deb8u2_amd64.deb

I assume it will continue to work in the actual 16.04.

good luck

Hi oui,
I tried to install seamonkey from the repositories but it is not there. I then downloaded it from [here]("https://launchpad.net/ubuntu/+source/seamonkey/2.0.11+build1+nobinonly-0ubuntu0.10.04.1") and unpacked the files but could not figure out what to do to install it.

I then downloaded all the files you mentioned to install kompozer and it worked but now synaptic says I have three broken packages:
libidl-2-0
libidl-2-0:i386
libnss3-nssdb

> libidl-2-0: Depends: libc6 (>= 2.14) mas 2.23-0ubuntu3 está instalado
            Depends: libglib2.0-0 (>= 2.16.0) mas 2.48.1-1~ubuntu16.04.1 está instalado
            Depends: cpp:any mas é um pacote virtual
libidl-2-0:i386: Depends: libc6 (>= 2.7) mas 2.23-0ubuntu3 está instalado
                 Depends: libglib2.0-0 (>= 2.16.0) mas 2.48.1-1~ubuntu16.04.1 está instalado
                 Depends: cpp:any mas é um pacote virtual
libnss3-nssdb: Depends: libnss3 (= 2:3.23-0ubuntu0.16.04.1) mas 2:3.17.2-1.1+deb8u2 está instalado

If I choose to fix broken packages it removes kompozer.
If I do not, it does not let me install anything else.
Any idea how to get around that?
Thank you.

---

### Post by yoramdavid on 2016-07-31
I could not keep Kompozer, any idea how to install it without corrupting the packages?

---

