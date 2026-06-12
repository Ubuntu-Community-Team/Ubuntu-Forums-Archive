---
title: "Can't add software?!?!"
date: 2008-06-24
forum: General Help
---

### Post by Lmnlme on 2008-06-24
OK, I can't get any new software (ie dependencies for gnupg2.0.9, etc) because of some crap.  I installed KDE4.0 and Xfce to try them out (using apt-get) and then removed them in a similar manner.  I don't know if something got left behind, or if I tried to remove something twice, or what, but it seems like my software registry (if ubuntu has such a thing) is out-a-whack.  BTW if you couldn't tell, im n00bish to linux (4 yrs on mac, 1 week on ubuntu).

ANYWAY, heres the code - this command was recommended by ubuntu's updater as a fix to my problem:

lmnlme@lmnlme:~$ sudo apt-get install -f
[sudo] password for lmnlme: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 python-pylibacl libgbf-1-common devhelp-common latex-xft-fonts
  libmysqlclient15off vcdimager libgbf-1-1 libjack0 libapr1 libiso9660-5
  libgdl-gnome-1-0 openvpn-blacklist network-manager-pptp pptp-linux procmail
  libgdl-1-common libgladeui-1-7 network-manager-openvpn pinentry-curses
  gtk2-engines-qtcurve libiptcdata0 libdevhelp-1-0 liba52-0.7.4 anjuta-common
  ocrad libwildmidi0 vpnc libdvdread3 libcdaudio1 network-manager-vpnc
  libsidplay1 zoo mpg123 libsoundtouch1c2 libid3tag0 pmount libgmyth0
  resolvconf openvpn libvcdinfo0 mysql-common libgdl-1-0 python-pyxattr
  libmpeg2-4 libmms0 wdiff libfaad0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 27 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140384 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
lmnlme@lmnlme:~$ 


What to do, what to do???

---

### Post by Lmnlme on 2008-06-24
zomg ok, I tried something....no idea yet if it was good or bad.  I saw in the code I posted (^^) that a command was recomended (apt-get autoremove) so I did.  I did $sudo apt-get autoremove kio-umountwrapper

This is what it did:

lmnlme@lmnlme:~$ sudo apt-get autoremove kio-umountwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 python-pylibacl libgbf-1-common devhelp-common latex-xft-fonts
  libmysqlclient15off vcdimager libgbf-1-1 libjack0 libapr1 libiso9660-5
  libgdl-gnome-1-0 openvpn-blacklist network-manager-pptp pptp-linux procmail
  libgdl-1-common libgladeui-1-7 network-manager-openvpn pinentry-curses
  gtk2-engines-qtcurve libiptcdata0 libdevhelp-1-0 liba52-0.7.4 anjuta-common
  ocrad libwildmidi0 vpnc libdvdread3 libcdaudio1 network-manager-vpnc
  libsidplay1 zoo mpg123 libsoundtouch1c2 libid3tag0 pmount libgmyth0
  resolvconf openvpn libvcdinfo0 mysql-common libgdl-1-0 python-pyxattr
  libmpeg2-4 libmms0 wdiff libfaad0
The following packages will be REMOVED:
  anjuta-common devhelp-common gtk2-engines-qtcurve kio-umountwrapper
  latex-xft-fonts liba52-0.7.4 libapr1 libcdaudio1 libdevhelp-1-0 libdvdread3
  libfaad0 libfreebob0 libgbf-1-1 libgbf-1-common libgdl-1-0 libgdl-1-common
  libgdl-gnome-1-0 libgladeui-1-7 libgmyth0 libid3tag0 libiptcdata0
  libiso9660-5 libjack0 libmms0 libmpeg2-4 libmysqlclient15off libsidplay1
  libsoundtouch1c2 libvcdinfo0 libwildmidi0 mpg123 mysql-common
  network-manager-openvpn network-manager-pptp network-manager-vpnc ocrad
  openvpn openvpn-blacklist pinentry-curses pmount pptp-linux procmail
  python-pylibacl python-pyxattr resolvconf vcdimager vpnc wdiff zoo
0 upgraded, 0 newly installed, 49 to remove and 27 not upgraded.
1 not fully installed or removed.
After this operation, 48.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140384 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Removing anjuta-common ...
Removing libdevhelp-1-0 ...
Removing devhelp-common ...
Removing gtk2-engines-qtcurve ...
Removing latex-xft-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/latex-xft-fonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing liba52-0.7.4 ...
Removing libapr1 ...
Removing libcdaudio1 ...
Removing libdvdread3 ...
Removing libfaad0 ...
Removing libjack0 ...
Removing libfreebob0 ...
Removing libgbf-1-1 ...
Removing libgbf-1-common ...
Removing libgdl-gnome-1-0 ...
Removing libgdl-1-0 ...
Removing libgdl-1-common ...
Removing libgladeui-1-7 ...
Removing libgmyth0 ...
Removing libid3tag0 ...
Removing libiptcdata0 ...
Removing vcdimager ...
Removing libvcdinfo0 ...
Removing libiso9660-5 ...
Removing libmms0 ...
Removing libmpeg2-4 ...
Removing libmysqlclient15off ...
Removing libsidplay1 ...
Removing libsoundtouch1c2 ...
Removing libwildmidi0 ...
Removing mpg123 ...
Removing mysql-common ...
Removing network-manager-openvpn ...
Removing network-manager-pptp ...
Removing network-manager-vpnc ...
Removing ocrad ...
Removing openvpn ...
 * Stopping virtual private network daemon.                              [ OK ] 
Removing openvpn-blacklist ...
Removing pinentry-curses ...
Removing pmount ...
Removing pptp-linux ...
Removing procmail ...
Removing python-pylibacl ...
Removing python-pyxattr ...
Removing resolvconf ...
Removing vpnc ...
Removing wdiff ...
Removing zoo ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
lmnlme@lmnlme:~$ 


so I deleted a bunch of stuff, and still got the same ****ing error!

RATS!!!  and FOOBAR!!!
:(

---

### Post by wormser on 2008-06-24
Try doing this.

```
sudo apt-get autoremove
```
```
sudo apt-get install -f
```
```
sudo apt-get update
```

---

### Post by Lmnlme on 2008-06-24
I tried the apt-get install -f first - that what started this nonsense.

when I tried [$sudo apt-get autoremove] I get this:



lmnlme@lmnlme:~$ sudo apt-get autoremove
[sudo] password for lmnlme: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 27 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 138511 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
lmnlme@lmnlme:~$ 


I assume this is bad...

---

### Post by Lmnlme on 2008-06-24
btw I click on the red down arrow for update DLs and it says:

Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
A previous upgrade which didn't complete
Problems with some of the installed software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu
  [ Partial Upgrade ]   [ Close ]

I click Close and I get:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

oh noes.  This is when I first tried [install -f]

just so you know.

---

### Post by wormser on 2008-06-24
> **Lmnlme said:**
> I tried the apt-get install -f first - that what started this nonsense.

FYI, you should always put the commands in the order somebody gives them.  In this case it really did not matter.  Try this one.

```
sudo dpkg --purge kio-umountwrapper
```

```
sudo apt-get update
```

---

### Post by Lmnlme on 2008-06-24
I assume it is meant in order its given, but the OS gave me [install -f] before I even posted, I guess I just provided information out of order :(

anyway, when I do purge, I get:

lmnlme@lmnlme:~$ sudo dpkg --purge kio-umountwrapper
[sudo] password for lmnlme: 
(Reading database ... 138511 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
lmnlme@lmnlme:~$ 

sorry if my code is spamming these posts :(

---

### Post by wormser on 2008-06-24
> **Lmnlme said:**
> sorry if my code is spamming these posts :(

The details are great.  I just hate the post that go on with useless information.  Sticking to the commands you run and the errors is all you need.  Try this one.

```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by Lmnlme on 2008-06-24
ok, interesting and different, but somehow I feel no progress...

no errors on the first command, but on the second [sudo apt-get update] I get a bunch of hits and then

Fetched 192B in 1s (144B/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

...is this bad too?  it only seems funny, because when I run update, it tells me to update... weird.  Well, thanks for the help so far, I'm off to bed for the night - birds are chirping and the sun's coming in the windows ;)

---

### Post by wormser on 2008-06-24
That error is telling you to add the key for the repository.  Directions are [here]("http://winehq.org/site/download-deb").  Is the other error gone?

---

### Post by Lmnlme on 2008-06-24
terminal freezes (I can Ctl-C out) when I do [sudo apt-key ad - ]

when I Ctl-C, I get: 

gpg: Interrupt caught ... exiting

anyway, I'll let it run for a while -maybe it'll catch up to itself...

---

### Post by wormser on 2008-06-24
Did you do the whole command?

```
*wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```*

---

### Post by Lmnlme on 2008-06-24
I did not know it was all one command ;) I did it now, and it said [OK] hehe.

Software index is still broken according to the updater, though - I'll try the rest of the wine thing, but I think I will end up re-installing ubuntu anyway (I just got my Mac OS dvds in the mail today, so I'm gonna try and dual boot).

I'll try the rest of those commands first, so that way at least we can call it resolved ;)

---

### Post by Lmnlme on 2008-06-24
i finished the wine directions, and all went well.  (including the apt-get update) but when I went back and tried autoremove, or install -f, I get that same kio-umountwrapper error.  I tried the --purge again, and got the same:

dpkg: error processing kio-umountwrapper (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper


oh well, I'm gonna go ahead and reformat to install Mac OSX.  Hopefully I can swipe bootcamp from my wife and it will work on my 10.4 (bootcamp is for 10.5) if I can, then I'll dual boot that way - hate to change the topic of this thread, but does anyone know how to dual boot using linux as a base instead of mac w/boot camp?  ie is there a Linux equivalent to apple's boot camp?

---

### Post by saitoh on 2008-06-24
you shouldn't be using apt-get, instead use aptitude as it will keep track of dependencies and remove unused files/libs. However don't mix aptitude and apt-get. 

Next time use the following to install:

sudo aptitude install desktop kde

---

