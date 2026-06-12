---
title: "Vista &amp; Ubuntu 12.10 Dual Boot: Minimal BASH-like line editing is supported"
date: 2013-01-02
forum: General Help
---

### Post by jpierretravels on 2013-01-02
Hello everyone,

I've looked through the forums for an answer to my question but have yet to find a solution. Here's the situation:

I have Windows Vista and Ubuntu 12.10 running on a Toshiba Satellite L300. The dual boot "system" (as far as I understand it) runs off of Windows' dual-boot program, not the Ubuntu dual-boot program; I have Ubuntu installed "inside" Windows, using Wubi.

Normally Ubuntu boots up just fine. The problem began earlier today after I shut down my computer, closing Windows and then rebooted it. When I tried to start up Ubuntu, I got the following message: 

[CENTER]**GNU GRUB Version 2.00-7 Ubuntu 11**[/CENTER]

[b]Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename
grub>[/B]
     
When I pressed TAB and the following information came up:
    
[B]Possible commands are; blocklist boot cat chainloader cmp color configfile debug displaymem embed find fstest geometry halt help hide impsprobe initrd install ioprobe kernel lock makeactive map md5crypt module modulenounzip pager partnew parttype password pause read reboot root rootnoverify savedefault serial setkey setup terminal terminfo testload testvbe unhide uppermem uuid vbeprobe
grub>[/B]

The full story is that I started my day in Ubuntu, logged off into Windows, logged into Windows, then downloaded a driver for a printer (HP LaserJet P1005; this guy, [*[COLOR="RoyalBlue"]here[/COLOR]*]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=bi-54963-6&cc=us&dlc=en&lc=en&os=2093&product=3435676&sw_lang=")). Then, after ensuring that the printer worked, I shut down Windows and attempted to boot up Ubuntu. It was at that point that the error(?) message came up. :/

I'm *really* worried -- I'm a university student and school starts in less than a week and despite the image that goes along with Ubuntu-users, I'm *not* very tech savvy at all!! I don't want to go back to using Vista (or Windows..) for school work.. it hasn't proven as stable or as trustworthy as Ubuntu (so far).

Thanks in advance for any help!

---

### Post by oldfred on 2013-01-02
Does Windows still boot ok?

Wubi depends on the Windows boot loader and the Windows NTFS files system as it really is just a large file inside the NTFS partition.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
    
I do not know wubi well. It could be corruption in the NTFS file system. 
Did Windows run chkdsk? 
Or corruption in the ext4(?) file system that wubi creates.

       Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

    
If you really like Ubuntu it may be time to upgrade to a fully partitioned install, so Ubuntu does not depend on Windows. :)
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by jpierretravels on 2013-01-02
Windows still boots fine. Luckily I've moved everything I do to cloud systems, so I don't depend necessarily need to depend on one OS or another.

Others have also already started recommending that I set up a partition for Ubuntu, as well. I tried this at first -- but like I said, I'm not very tech savvy.. and having a tight time-budget makes it harder for me to figure out.

Any recommended links on a simple explanation for those who need things explained in "simple English"? :)

I don't know what chkdsk is, but I'm guessing you're talking about the system checkup that occurs when you start up Windows after a hard shut-down. If that's what you mean, then yeah -- it checked it out and it was fine. 

I don't understand this line:
--> "*Or corruption in the ext4(?) file system that wubi creates.*", or what "*missing root.disk*" means : /

Sorry.. computers are a completely foreign language to me.. I'm just an average user : / Thanks for your help and suggestions :)

**_UPDATE:_** I just got a message in Windows stating that some files are corrupted and that I should restart Vista. I restarted Vista, and the chkdsk got stuck at 66%.

---

### Post by oldfred on 2013-01-02
Windows run chkdsk whenever you have file corruption on the Windows NTFS file system. Often caused by powerfailue or user shutdown system when running. But it can be just a bad block on hard drive. Chkdsk does not fix everything on one pass, so often you have to run it until you get no errors.

LInux equivalent is fsck or e2fsck to run repairs on a Linux formatted partition.

Wubi is just a large file in Windows. The file is root.disk and internally it is formatted as a Linux file system ext4.

---

### Post by jpierretravels on 2013-01-02
Ok,.. so how do I solve this problem? I mean, is there something that I can type as if it were a terminal? :confused:

Or would the answer be to uninstall Ubuntu entirely, and then re-install it in its' own partition?

---

### Post by oldfred on 2013-01-03
I believe the links I gave in post #2 had suggestions with screen shots on chkdsk or fsck. I do not know wubi well enough to suggest more.

---

