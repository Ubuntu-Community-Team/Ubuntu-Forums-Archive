---
title: "Ubuntu 7.10 - Display in and out, error message"
date: 2008-03-11
forum: General Help
---

### Post by Firehalk on 2008-03-11
Hey guys,

I'm new on Ubuntu (and Linux also), but I really got interested on it after trying Ubuntu 6.06. I love it. But because of some new stuff and facilities of 7.10, I decided to try it, in order to install later.

Well, I'm not trying to install still, just use Live CD to test.

My problem (and I saw some other info on forums too, that didn't work my case) is that my display go nuts and I cant go into Ubuntu. 

I can barely see the Ubuntu's cursor on screen, then the screen goes black, go back to the cursor again, do it many times, until I get the message:

**"The display server has been shut down about 6 times in the last 90 seconds[...]"**

I've tried to open **xorg.conf** and change to "vesa" the Device sector, but its already Vesa there.

So I tried something else: be patient :P Helped a little, since I got into Ubuntu (after 3min without doing nothing, the CD reads again and i got into). But then it showed my Videocard wasn't detected... So I went through the list of drivers it shows, and found "Unichrome" (mine is **VIA/S3G Unichrome Pro IGP**). After I selected it... boom... went back to the previous screen, the one with that message I quoted above.

Any ideas? My VGA isnt compatible? Wont work with Ubuntu? :confused:

Appreciate any information!

I'm really in the mood to use it.

---

### Post by wblancqu on 2008-03-11
Try installing Ubuntu using The "alternate" installation CD (text-based). After installation, start a console (Ctrl-Alt-F1, Ctrl-Alt-F2...). Then follow this:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Grtz

---

### Post by prshah on 2008-03-11
Maybe too high a resolution (Not able to allocate enough videoram?)

You should really change to the correct driver rather than the Generic VESA.. to change run the command "sudo dpkg-reconfigure xserver-xorg" or follow [http://ubuntuforums.org/showthread.php?t=76037](http://ubuntuforums.org/showthread.php?t=76037)

that said..

A post of your /etc/X11/xorg.conf would be helpful... or just edit it using "sudo gedit /etc/X11/xorg.conf" and find a line starting with "Modes" and followed by a number of resolutions, eg "800x600" "1024x768" etc etc and leave only one mode. eg "1024x768". Also reduce the DefaultDepth to 16 from 24/32.

Try it with the above changes, and if it works, you can gradually step up the resolution till you are comfortable, or the problem recurs. 

Cheers,
PRShah

---

### Post by Firehalk on 2008-03-11
Thanks for replies but didn't work.

Just to make easy stuff: I didn't change nothing at all. Resolution is the same as default (1024), as the xorg.conf file is the default too (I don't have how to copy it, because i'm using Live CD and my problem is that I can't go into Ubuntu. If I could copy the file, there would not exist this topic for sure :().

The only tries I've did were those I told.

Also, tried now to install openchrome drivers as suggested. Can't do it. Even following the tutorial from that website ([https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)) don't work here. I always receive:

**Couldn't find package xserver-xorg-video-openchrome** 

Even after enabling those stuff the website says to (Universe and Multiverse repositories, etc).

Download the alternate version isn't good deal for me, because I don't want to install it. I want test a lot first through live cd, to install later.

I tried to use **sudo dpkg-reconfigure xserver-xorg** but thats way too damn complicated to me... I don't have any idea of many stuff it asks for. :(

---

### Post by wblancqu on 2008-03-11
for the xserver-xorg-video-openchrome package, you must enable the Universe Repository. To do this, alter file /etc/apt/sources.list, and make it look like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free
```

You might want to replace the "us" in several URL's to your country code (e.g. be for Belgium). This code comes from [http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")

After that, perform these commands:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Then try reinstalling the package, should work now.

Good luck!!!

---

### Post by Firehalk on 2008-03-12
wblancqu, thanks for trying to help me, but it still don`t work :(

I have follow everything u said me to do. It installed a bunch of updates and stuff (5mb download, with a lot of stuff. Something like 20 stuff installed through it).

Then I tried again to install that package (the drivers) but still, all commands I type I receive: **Couldn't find package**

I tried the manual install and the more automatic one too. Both give me that message when I type the commands they say there.

Btw, since I`m not able to run 7.10, i tried 6.06 here. I can access well the OS (it loads), so im trying it here now. I replace **gutsy **for **dapper** and the country letters for my country (br) in order to test. 

Downloaded everything too, but still the packages won`t install. Same error saying that couldn`t find package.

On gutsy i couldn`t try it anymore, because i only have terminal, and type all that on terminal is impossible. Too much stuff.

Any other ideas?

---

### Post by wblancqu on 2008-03-12
Any luck with the "Manual installation" part of [https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")?

Make sure you also follow the "Before you start" to make sure universe is enabled.

---

### Post by Firehalk on 2008-03-12
Tes. I tried that. Followed all instructions.

Still, i receive the same as always:

**Couldn't find package <name_of_package>**

It never finds the packages for me to get :(

I tried Ubuntu 8.04 Alpha 6 here, but still I can't run Ubuntu. On 8 it gives me a lot more of errors. I will wait for final release of it.

Why I always receive "can't find package"? Isn't because it's not more on servers?

---

### Post by haxx on 2008-03-12
ive read in a few spots that 7.10 is basicaly a flop distro unless ur on dell modern machines (not shure if the writters of the articles actualy know what there talkin about ) since i read these articles though i have given up on 7.10 (kubu-Xu-and ubu) i went back to 7.04 and did a complete update (not distro ) and left out the new kernel packs in the update for a second run at updates after the initial one.

ALL MY PROBS ARE SOLVED 

i have my 19"w lcd runing - eve online - compiz cube all working like a charm and none of the annoying 5minute boot times that i saw from each 7.10 release.

and BTW the live disk doesnt realy allow u to change as much as an installed copy does


PS can u post your hardware list (atleast as complete as possible) as u never know there may simply be problems with support

PSS as for packages its likely u dont have the respositories setup correctly to hit the source lists out there available (or internet connection(likely u already have that though))

---

### Post by Firehalk on 2008-03-12
Thanks for replying.

Hmm 7.04 is the only version I didn't try yet (of the most new ones). Even 8.04 a6 didn't work fine here. Gave me lots of **hdc:ide_intr** errors (but this another problem).

Well, i know there will be lack of stuff while using Live CD. But I saw people going through same problem when installing it, so I guess If I try to install, that problem will remain.

_My system specs are:_

> Proc: Intel® Core&#8482;2 Duo 1.8GHz
Memory: 1GB DDR2-533
Mobo: VIA P4M800 PRO
Video: VIA/S3G Unichrome PRO IGP
Monitor: Samsung SyncMaster 796MB 17'
HD: Samsung 74GB
DVD-RW: Samsung Writemaster

---

