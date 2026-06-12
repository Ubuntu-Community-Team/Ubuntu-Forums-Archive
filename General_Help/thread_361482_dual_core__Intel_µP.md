---
title: "dual core  Intel µP?"
date: 2007-02-14
forum: General Help
---

### Post by gillmre on 2007-02-14
Do i need a special version of 6.06 or 6.10 for a dual core  Intel µP?   Disk boots.   I can do mem test and check sum.   Install starts but after the music i get a blank screen then soon after there is no more CD ativity. Both disk load on P3 computer ok.

---

### Post by dannyboy79 on 2007-02-14
it's a graphic issue. you need to pass special vga options to the boot line prior to booting. it depends what kind of video card you have but this worked for an ati vid card owner:

Well, I finally got Ubuntu running, here's how:

1. Download the Alternate CD, install Ubuntu.
2. The system will reboot, start in rescue mode (or the safe mode). You should have a console. Type:

Quote:
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx  

This will install ATI drivers which, it seems, we're not installed "by default". At that moment, you got a fully running Ubuntu  Enjoy.

or try to add this to the boot line before booting: live vga=771 or maybe just vga=771.

so what you'll need to do is when the first menu comes up about booting first hard disk or testing cd, or testing memory, chose whatever option there is so you can add options to the boot line. then you'll see something like this: /vmlinuz-2.6.15-26-686 root=/dev/hdc2 ro quiet splash
what you want to do is simply add what I said on the end so it would be
/vmlinuz-2.6.15-26-686 root=/dev/hdc2 ro quiet splash live vga=771 

or without the live. that's it, hopefully if you don't want to downlaod and install using the alternate install cd, then you can try these things. just so you know, even if you go the alt install route and you have  a nvidia card, and you get a black screen after booting back up after the install, then follow the steps above that the ati user used booting into recovery mode but use gogle to find out what you need to do to install and enable the nvidia drivers.

---

### Post by gillmre on 2007-02-14
dammyboy79:

I would like to use 6.10 BUT which alternate do i down load?

Is vga=771 the same for all ATI cards?   I hace a dual DVI FireMV 2200 ATI.

Thanks,
&#402;g

---

### Post by dannyboy79 on 2007-02-15
**WOW, I didn't think that when I started writing this that it would be this long! Make sure you read thru this entire post prior to doing anything. **

you would download the alternate install cd for 6.10. as far as the vga boot option, I don't know but you aren't gonna blow anything up by trying it. good luck. I have put a link to the alternate install cd, but you don't have do this if the vga boot option works, so try that first. as the live cd is starting, it'll bring you to the screen where it asks you what you want to do, you'll want to chose the option that allows you to modify the boot options, and add what I suggested above, if it doesn't work 1 way, try it again the other way before you move on to the next solution of using the alternate install cd. all the alt. install cd is, is a text version of the install, that's why you'll be able to do it, becuase it doesn't require graphics BUT as soon as the install is done and you reboot, you'll need to boot into recovery mode and do what I suggested. just a word of advice, ATI drivers are not the easiest to get working, I see many people very upset about how hard it is to get their ati cards to work with 3d acceleration and sometimes just even getting any graphics. don't give up to soon and make sure you read as many guides on installing drivers for your card as possible and now that you have informed me of your card, I searched and found a few links to help you install the drivers that support your card.

according to this link, support for your card was DROPPED from the driver in version 8.29.6 BUT you can use a legacy driver which is 8.28.8
[http://www.rage3d.com/board/showthread.php?t=33868060](http://www.rage3d.com/board/showthread.php?t=33868060)

this is a link that will help ya, apparently there is a guy named KanoTheMaster that created a script that can patch old drivers on the fly and detects that your card is a legacy r200 one and selects 8.28.8 and newer cards get 8.29.6. he states, For Ubuntu support remove restricted modules package first but I don't beelive that the restricted modules packages is installed by default but you will want to make sure prior to runnign the script, you can do this by typing  sudo aptitude search restricted*, but before that, type uname -r at the command line to find out what kernel you're using, then when the search results come up, you'll see a letter in the very beginning of each line, if it has an i, than that means it's installed and you'll want to remove it first by doing sudo aptitude remove linux-restricted-modules-2.6.15-26-386 (or whatver your kernel is). This is only if you want to use the script that I have linked to.
thread is here that talks about script
[http://www.rage3d.com/board/showthread.php?t=33868060](http://www.rage3d.com/board/showthread.php?t=33868060)
this is the actual script, you would download it, you could use wget, if you try wget and it says no command, than simply do sudo aptitude install wget, then you can use it by typing, wget [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh) and it'll only download it to the current dir you're in. then you run it by typing sudo sh install-fglrx-debian.sh or sudo ./install-fglrx-debian.sh at the command line, keeping in mind that you need to be in the dir that you downloaded it to.
[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

OR, here is a link to help you install without using a script.
[http://customisinglife.wordpress.com/2006/11/08/installing-ati-drivers-on-edgy/](http://customisinglife.wordpress.com/2006/11/08/installing-ati-drivers-on-edgy/)

ubuntu-6.10-alternate-i386.htm

this will download the iso from a ftp site but I would suggest using bit-torrent, it's way faster. and you can learn about it here. [https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)
and then you would get the torrent file for 6.10 alternate cd from here: [http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)
and it's called ubuntu-6.10-alternate-i386.iso.torrent

all the links I provided are for the 386 version, so if you have a power pc or an amd64 you need to download those respectfully.

---

