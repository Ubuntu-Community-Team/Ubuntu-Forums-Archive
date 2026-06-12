---
title: "Kubuntu 13.04: Impossible access"
date: 2013-06-21
forum: General Help
---

### Post by nemrod57 on 2013-06-21
Hello, after several posts since yesterday in several forums without any responses, I try here with the hope of a solution:
After updating kubuntu 12.10==> 13.04, I have problem of **White screen**! 
Impossible to access something. Impossible to do something. Trying to reboot, and with grub unsuccessfully repair damaged pckg, impossible to access to the previous version 12.04, 12.10, 11.04, 11.10. I did not overcome the problem. Does it exist commands line ?
I suspect the nvidia driver loading, sometimes the mouse seems to be freeze. With the live cd, I can access kubuntu 13.04 without problem.
I use kubuntu since 2008, I use to upgrade it after each new  distribution, this is the first time I see a such mess. What should I do  ? **Any Commands line** ?
Have you a solution please ?

Regards.

---

### Post by dino99 on 2013-06-21
i know its disturbing, but that issue is well known, and its posted everywhere with the solution (only need to search a bit):

[http://ubuntuforums.org/showthread.php?t=2088736&page=2&p=12598892#post12598892](http://ubuntuforums.org/showthread.php?t=2088736&page=2&p=12598892#post12598892)

---

### Post by nemrod57 on 2013-06-21
Thx for your quick response, however I cannot access to any menu, any menu, I have a white screen **without possibility** to use a such menu like 
> 
*gnome-tweak-tool-->Desktop-->Have file manager handle the desktop-->off*

Moreover I installed **Kubuntu**, not ubuntu.
How could I access into the Operating System ? Did you mean with live CD ?

---

### Post by xc3RnbFO8P on 2013-06-21
If you use Live CD,
try to rename /your home folder/.kde  to .kde bak
and restart

if it don't  works change it back.

---

### Post by uRock on 2013-06-21
Moved to General Help

---

### Post by nemrod57 on 2013-06-23
After doing [FONT=arial black]**ctrl+alt+F1**[/FONT] and [FONT=arial black]**startX**[/FONT] I could finally access to my kubuntu environnement. First fundamental step. 
However the problem still persist. I have several messages relating problem as for example Authorisation Failed-Failed to obtain authentification -. When I tried update, by using "**sudo apt-get update && sudo apt-get upgrade **" with console, the system told me that It stays nearly 1 Gb, in fact I doubt the system is still stable. The Muon software manager shows a problem see attachment
Can someone help me please.


PS:do not take it as an attack, however, You _**should understand**_ that we are not all, a system specialist, even less unix specialists. I agree with you, linux users nowadays should have the minimum unix knowledges in Unix Environnement. As Iam working unix environnement such solaris with Oracle Database, I know of course the only basic unix commands, **but not enough for system**. Ubuntu should become the main Operating System in the world, in order to democratize it, you will have to understand that, most of the people **does not understand what Unix is**, and expect the same support as Windows. I understand it is a great challenge, but it is worth, in order to delete Microsoft, Apple presence, or any commercial O/S.

[IMG]http://imageshack.us/a/img547/4342/9m6t.jpg[/IMG]

---

### Post by xc3RnbFO8P on 2013-06-23
Try sudo startx

---

### Post by nemrod57 on 2013-06-23
Thx for your response.
it did not run.
In fact my simple question is:
Does it exist a simple way to repair this -probable- damaged package with cd or dvd ? Why did I download, an upgrade my softs as I already have a dvd with me ? I have many networks problem, because I will have to pass by this **** old fashionned dsl connexiions, -waiting the optic fiber-. I have already several times tried to upgrade from a version to another with Internet, each times, it fails, du this fithy dsl.
I bought a dvd-inside a newspaper- in order to avoid downloading something.
Regards.

---

### Post by xc3RnbFO8P on 2013-06-23
Did you mean that 
ctrl+alt+F1 and sudo startX 
dont work?

---

### Post by nemrod57 on 2013-06-23
> **Ringi said:**
> Did you mean that 
ctrl+alt+F1 and sudo startX 
dont work?

_**No!**_.
I mean, repair failing system by a dvd. I tried to boot, with grub, it offers you a possibility to repair damaged packages, but it did not help me.
For example if I recall, windows XP offered you the possibilty to repair the system by insering cd/DVD. I think it must be the same with Kubuntu, but I don't know how to do. Moreover, I don't know untill now, if it is not a problem with KDE itself.
The problem, I can access Ubuntu/Kubuntu with LiveCD, but with my system, it seems that there are damaged pckgs, detering to install the good Nvidia driver, and updating softwares.

---

### Post by xc3RnbFO8P on 2013-06-23
> **nemrod57 said:**
> _**No!**_.
I mean, repair failing system by a dvd. I tried to boot, with grub, it offers you a possibility to repair damaged packages, but it did not help me.
For example if I recall, windows XP offered you the possibilty to repair the system by insering cd/DVD. I think it must be the same with Kubuntu, but I don't know how to do. Moreover, I don't know untill now, if it is not a problem with KDE itself.
The problem, I can access Ubuntu/Kubuntu with LiveCD, but with my system, it seems that there are damaged pckgs, detering to install the good Nvidia driver, and updating softwares.

I never tried it, so I don't know,

I use Recovery option and choose network and then "Drop to root shell prompt"

---

### Post by nemrod57 on 2013-06-23
Could you detail 
> 
*Drop to root shell prompt*

As Iam not Unix specialist, could you please give us the commands line script you would use.

---

### Post by xc3RnbFO8P on 2013-06-23
Switch the computer on, hold down the shift key until the boot menu appears. In the grub menu, choose for the &#8220;recovery mode&#8221; option.

[IMG]http://itsfoss.com/wp-content/uploads/2012/07/Ubuntu-Grub-Recover-Password.jpg[/IMG]

You can also try repair broken package.

---

### Post by nemrod57 on 2013-06-24
I tried unsuccessfully. I don't know what to do once inside Drop to root shell prompt. Do you know any website ?
It is strange that it is impossible to repair an O/S just with DVD, very strange. I bought a DVD containing Ubuntu, Kubuntu, etc...but the system asked me to update via network, and Internet.
Let's hope that we could upgrade, or repair damaged packages by DVD.

---

### Post by xc3RnbFO8P on 2013-06-24
In Recovery window:
enable network
then
Drop to root shell
then 
startx

---

### Post by nemrod57 on 2013-06-24
It did not run.

---

### Post by xc3RnbFO8P on 2013-06-24
Did you tried: 
Repair broken package
and 
Run in failsave graphic mode

---

### Post by nemrod57 on 2013-06-24
> **Ringi said:**
> Did you tried: 
Repair broken package
and 
Run in failsave graphic mode

I've done ***Repair broken package***, I left the dvd, however, with no results. Nevertheless, without being in ***Drop to root shell*** mode. 
Iam going to try it next, I will say you about results.
In ***Drop to root shell*** mode, I launched startx, there were no result, I could not see any interface.
However, as I post everywhere I can since wednesday -as the desperate situation asks me- this post could be an answer but I don't know how he does
**[http://www.kubuntuforums.net/showthread.php?62595-Upgrade-from-12-04-to-13-04&p=330428#post330428](http://www.kubuntuforums.net/showthread.php?62595-Upgrade-from-12-04-to-13-04&p=330428#post330428)**
Teunis seems to say that _[SIZE=3][FONT=arial black][COLOR=#FF0000]**there would be  -I say would be, Iam not sure-a possibilty to upgrade, repair by CD**[/COLOR][/FONT][/SIZE]_ since 12.04. If this is the case it would be usefull for every users like us, interresting by kubuntu.
Iam waiting for his response, you are aware about the result too.

Regards.

---

### Post by steeldriver on 2013-06-24
I haven't followed this whole thread, however it seems to me you have 2 options

1. you could *try* to update and repair from the DVD either using apt-cdrom or by editing your sources.list manually, however if you can only boot to the recovery shell and are not EXTREMELY familiar with the command line this is likely to be painful and frustrating

2. you could use the DVD in 'live' mode to back up all of your important data to an external drive and then use it again to do a clean install of 13.04

---

### Post by nemrod57 on 2013-06-24
> **steeldriver said:**
> .... use it again _**to do a clean**_ install of 13.04
What did you mean by clean ? A complete erase of the previous install ? If this is the case, Ubuntu team has many works to do, because since to 1998-2008, period where I used Windows, I've formated only two times.
This is this cumbersome procedure that obliged me to migrate toward linux.
I hope, I won't have to do another format.

---

### Post by xc3RnbFO8P on 2013-06-24
Dont give up jet now try:
enable network
then
Drop to root shell
then 
**dpkg --configure -a**
followed by
**apt-get -f install**
if all goes well then
**apt-get update && apt-get upgrade**

---

### Post by nemrod57 on 2013-06-24
Notice that, I passed to another step, from impossible access O/S, now I have access through these following commands ***ctrl+alt+f1***, and  ***startx***.
Now my problem is I still have the white screen 
 and when I try to upload i have these following messages :

[IMG]http://imageshack.us/a/img850/9973/5tej.jpg[/IMG]


[IMG]http://imageshack.us/a/img826/9896/rudc.jpg[/IMG]



[IMG]http://imageshack.us/a/img547/4342/9m6t.jpg[/IMG]



After doing apt-get install -f command,  gives the following result
> 
sudo apt-get install -f
[sudo] password for zebulon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apport-hooks-medibuntu evolution-couchdb-backend g++-4.6 gir1.2-gtk-2.0 indicator-messages kdegraphics-mobipocket
  launchpad-integration libattica0.3 libbabl-0.0-0 libbasicplayer-java libberkeleydb-perl libboost-date-time1.46.1
  libboost-filesystem1.46.1 libboost-iostreams1.46.1 libboost-program-options1.46.1 libboost-system1.46.1
  libboost-thread1.46.1 libcamel-1.2-29 libcdt4 libcelt0-0 libcmis-0.2-0 libcommons-el-java libconfig-tiny-perl
  libcouchdb-glib-1.0-2 libcrypt-twofish-perl libdatetime-format-mail-perl libdatetime-format-w3cdtf-perl libdconf0
  libdesktopcouch-glib-1.0-2 libdiscid0 libdrm-nouveau1a libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10 libedata-book-1.2-11
  libedata-cal-1.2-13 libedataserver-1.2-15 libexiv2-11 libexpect-perl libfile-find-rule-perl libgdata1.9-cil libgdu0
  libgegl-0.0-0 libgnomekbd7 libgraph4 libgvc5 libhtml-strip-perl libimobiledevice2 libio-stty-perl libjasper-java
  libjetty-java libjflac-java libjlayer-java libjmac-java libjorbis-java libjson-glib-1.0-0 libjspeex-java libkexiv2-10
  libkimproxy4 libkjdsp-java libktorrent3 libkwineffects1abi3 libkwinglutils1 libkworkspace4abi1
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libmagickcore4 libmagickcore4-extra libmagickwand4
  libmath-round-perl libmp3spi-java libmusicbrainz3-6 libnepomukdatamanagement4 libnepomuksync4 libnumber-compare-perl
  libopenspc0 libpathplan4 libservlet2.4-java libslf4j-java libsox1b libstdc++6-4.6-dev libtaglib2.0-cil libtext-glob-perl
  libtorrent-rasterbar6 libtritonus-java libtritonus-jni libuniversal-require-perl libvorbisspi-java libwww-curl-perl
  libx264-120 libxfce4util4 libxml-rss-libxml-perl libyajl1 python-farstream python-gpgme python-ubuntuone-control-panel
  python-xmpp transcode-utils ttf-sil-gentium-basic ubuntuone-control-panel ubuntuone-control-panel-qt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 330 not upgraded.


---

### Post by nemrod57 on 2013-06-24
After ***enabling network***
and switching to
***Drop to root shell***
  typing
**dpkg --configure -a**
followed by
**apt-get -f install**
if all goes well then
**apt-get update && apt-get upgrade**

does not give me results.
In fact, Iam writing you from Kubuntu, but without possibility to update, upgrade softwares.

---

### Post by xc3RnbFO8P on 2013-06-24
ctrl+alt+f1 and now you need to login
username 
password

---

### Post by nemrod57 on 2013-06-25
Maybe my poor english level, detered me to say important things.
Indeed since I did ctrl+alt+f1 and l typed my username and passord I could access to the O/S for friday. In fact the title of the topic is not appropriate, the great challenge since friday is to remove the white screen, and how I can to update the O/S.

---

### Post by xc3RnbFO8P on 2013-06-25
> I did ctrl+alt+f1 and l typed my username and passord
I asked just to be sure.

Does Muon Software Manager ask for a password

sudo apt-get install polkit-kde-1

---

### Post by nemrod57 on 2013-06-25
> **Ringi said:**
> I asked just to be sure.
Does Muon Software Manager ask for a password

Yes of course

> 
sudo apt-get install polkit-kde-1

As Iam at work now, I will test as soon as possible, I will lea a feedback

---

### Post by nemrod57 on 2013-06-25
After doing 
> **Ringi said:**
> 
[FONT=arial black]**[COLOR=#FF0000]sudo apt-get install polkit-kde-1[/COLOR]**[/FONT]


The result :

> 
**sudo apt-get install polkit-kde-1**
[sudo] password for zebulon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
polkit-kde-1 is already the newest version.
The following packages were automatically installed and are no longer required:
  apport-hooks-medibuntu evolution-couchdb-backend g++-4.6 gir1.2-gtk-2.0 indicator-messages kdegraphics-mobipocket
  launchpad-integration libattica0.3 libbabl-0.0-0 libbasicplayer-java libberkeleydb-perl libboost-date-time1.46.1
  libboost-filesystem1.46.1 libboost-iostreams1.46.1 libboost-program-options1.46.1 libboost-system1.46.1
  libboost-thread1.46.1 libcamel-1.2-29 libcdt4 libcelt0-0 libcmis-0.2-0 libcommons-el-java libconfig-tiny-perl
  libcouchdb-glib-1.0-2 libcrypt-twofish-perl libdatetime-format-mail-perl libdatetime-format-w3cdtf-perl libdconf0
  libdesktopcouch-glib-1.0-2 libdiscid0 libdrm-nouveau1a libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10 libedata-book-1.2-11
  libedata-cal-1.2-13 libedataserver-1.2-15 libexiv2-11 libexpect-perl libfile-find-rule-perl libgdata1.9-cil libgdu0
  libgegl-0.0-0 libgnomekbd7 libgraph4 libgvc5 libhtml-strip-perl libimobiledevice2 libio-stty-perl libjasper-java
  libjetty-java libjflac-java libjlayer-java libjmac-java libjorbis-java libjson-glib-1.0-0 libjspeex-java libkexiv2-10
  libkimproxy4 libkjdsp-java libktorrent3 libkwineffects1abi3 libkwinglutils1 libkworkspace4abi1
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libmagickcore4 libmagickcore4-extra libmagickwand4
  libmath-round-perl libmp3spi-java libmusicbrainz3-6 libnepomukdatamanagement4 libnepomuksync4 libnumber-compare-perl
  libopenspc0 libpathplan4 libservlet2.4-java libslf4j-java libsox1b libstdc++6-4.6-dev libtaglib2.0-cil libtext-glob-perl
  libtorrent-rasterbar6 libtritonus-java libtritonus-jni libuniversal-require-perl libvorbisspi-java libwww-curl-perl
  libx264-120 libxfce4util4 libxml-rss-libxml-perl libyajl1 python-farstream python-gpgme python-ubuntuone-control-panel
  python-xmpp transcode-utils ttf-sil-gentium-basic ubuntuone-control-panel ubuntuone-control-panel-qt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, _**0 to remove and 330 not upgraded**_.


Moreover what shoud I do with this following message ?
[IMG]http://imageshack.us/a/img15/5915/19m8.jpg[/IMG]

I think this is one of the problem, but Iam afraid to click on the bad button.

---

### Post by xc3RnbFO8P on 2013-06-25
I think it is best use livedisk to back things up and make a fresh install.
You don't need to format the hdd it is ready.

---

### Post by deri on 2013-06-25
That error message you see about audio hardwares, just press no. I get that sometimes. I think it's somekind of bug in the kubuntu. That's not something very dangerous at all.

---

### Post by nemrod57 on 2013-06-26
Thank you very much to all for your help, it was very helpfull.
Thank you all guys.

---

### Post by nemrod57 on 2013-06-29
Hello, 
Feedbacks from the install. All is OK. Thx for all.
You can close the subject and set it as solved. The only critics that I have concerning this wonderfull Ubuntu Operting System, we cannot upgrade a previous install with CD/DVD.
What a pity.
More than never, I will stay on Kubuntu, and my next shopping is Ubuntu SmartTV, and SmartPhone.

PS : I had also a decisive help from this 
**[http://www.kubuntuforums.net/showthread.php?62595-Upgrade-from-12-04-to-13-04/page2](http://www.kubuntuforums.net/showthread.php?62595-Upgrade-from-12-04-to-13-04/page2)**


Regards.

---

