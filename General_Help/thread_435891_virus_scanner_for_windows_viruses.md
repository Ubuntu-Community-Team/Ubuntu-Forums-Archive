---
title: "virus scanner for windows viruses?"
date: 2007-05-07
forum: General Help
---

### Post by Fittersman on 2007-05-07
is there any virus scanner that works on ubuntu that will scan your files for a windows virus?

i like to download on ubuntu, but sometimes i need to transfer my files over to windows and i dont want any viruses on it, so i was just wondering if i could scan before i transfer.

---

### Post by Wiebelhaus on 2007-05-07
Install [F-Prot]("http://ubuntuforums.org/showthread.php?t=88357&highlight=install+f-prot")

Or 

 
ClamAV & Firestarter Can be installed via [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation")

I personally like f-prot allot.

AVG for linux is crappy.

---

### Post by Fittersman on 2007-05-07
ive got another question for you, i hear that AVG (for windows) is free, but when i downloaded the installer it asks for a code (product key type deal, dont remember what they called it though) 

so, is it free, or do i need to buy it?

---

### Post by the lemming on 2007-05-07
> **Fittersman said:**
> ive got another question for you, i hear that AVG (for windows) is free, but when i downloaded the installer it asks for a code (product key type deal, dont remember what they called it though) 

so, is it free, or do i need to buy it?

It's completely free.  Just a registration process, that is all.

I used it for quite a while but I now prefer Avast.  That is also free but it speaks to you when it has downloaded updates.

---

### Post by Fittersman on 2007-05-07
so, how do i get that code then? it wont install without it...

and avast eh? ill google that one, never heard of it before

---

### Post by Fittersman on 2007-05-07
well, avast looks pretty good, ill give that a shot later then, thanks :D

---

### Post by Wiebelhaus on 2007-05-07
> **Fittersman said:**
> so, how do i get that code then? it wont install without it...

and avast eh? ill google that one, never heard of it before

watch the version you install , the free one is burried a bit on the grisoft site.
[http://www.filehippo.com/download_avg_antivirus/](http://www.filehippo.com/download_avg_antivirus/)

---

### Post by Fittersman on 2007-05-07
```
cleippi@FamilyComputer:~/Desktop$ sudo dpkg -i  fp-linux-ws.deb
(Reading database ... 101664 files and directories currently installed.)
Preparing to replace fp-linux-ws 4.6.8 (using fp-linux-ws.deb) ...
Unpacking replacement fp-linux-ws ...
Setting up fp-linux-ws (4.6.8) ...
***************************************
* F-Prot Antivirus Updater            *
***************************************

There's a new version of:
"Document/Office/Macro viruses" signatures on the web.
Starting to download...
Starting to download...
Download completed.

There's a new version of:
"Application/Script viruses and Trojans" signatures on the web.
Starting to download...
Starting to download...
Download completed.

The downloaded version of fp-sign.zip has a different checksum than
the one advertised by the update server.
Fatal error. Exiting...
dpkg: error processing fp-linux-ws (--install):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 fp-linux-ws

```

how do i fix that?

---

### Post by Lucifiel on 2007-05-07
Does F-prot support scanning of Thunderbird emails?

---

### Post by Wiebelhaus on 2007-05-07
> **Lucifiel said:**
> Does F-prot support scanning of Thunderbird emails?

yes ma'am.

---

### Post by Wiebelhaus on 2007-05-07
> **Fittersman said:**
> ```
cleippi@FamilyComputer:~/Desktop$ sudo dpkg -i  fp-linux-ws.deb
(Reading database ... 101664 files and directories currently installed.)
Preparing to replace fp-linux-ws 4.6.8 (using fp-linux-ws.deb) ...
Unpacking replacement fp-linux-ws ...
Setting up fp-linux-ws (4.6.8) ...
***************************************
* F-Prot Antivirus Updater            *
***************************************

There's a new version of:
"Document/Office/Macro viruses" signatures on the web.
Starting to download...
Starting to download...
Download completed.

There's a new version of:
"Application/Script viruses and Trojans" signatures on the web.
Starting to download...
Starting to download...
Download completed.

The downloaded version of fp-sign.zip has a different checksum than
the one advertised by the update server.
Fatal error. Exiting...
dpkg: error processing fp-linux-ws (--install):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 fp-linux-ws

```

how do i fix that?

"The downloaded version of fp-sign.zip has a different checksum than
the one advertised by the update server."

sounds like a version check failure , may want to try and download the newest version from [F-prot directly]("http://www.f-prot.com/download/home_user/download_fplinux.html").

---

### Post by Fittersman on 2007-05-07
why would it automatically download the wrong version (of the virus definitions i think)?

if you mean to download the f-prot again, that is the site i got it from already

unless i misunderstood you

---

### Post by Lucifiel on 2007-05-07
> **sx66gns said:**
> yes ma'am.


Thank you! :) I hope it has a GUI frontend. 

Btw, your avatar looks cool. Where'd you get it from? :) 

And how'd you know I was female? O_o;;

---

### Post by Wiebelhaus on 2007-05-07
> **Lucifiel said:**
> Thank you! :) I hope it has a GUI frontend. 

Btw, your avatar looks cool. Where'd you get it from? :) 

And how'd you know I was female? O_o;;

It does

not sure , I picked it up somewhere , it is however related to Blizzard entertainment.

It's my "man-sense"

---

### Post by Wiebelhaus on 2007-05-07
> **Fittersman said:**
> why would it automatically download the wrong version (of the virus definitions i think)?

if you mean to download the f-prot again, that is the site i got it from already

unless i misunderstood you

I was thinking possibly that you had downloaded an older version and it was getting an error when the version did not check out with the server , let me look into it.

---

### Post by Fittersman on 2007-05-07
> **Lucifiel said:**
> 
And how'd you know I was female? O_o;;

what guy would have a chick in their avatar? (well unless it was a hot babe or something, but not a drawing like that one)

---

### Post by Lucifiel on 2007-05-07
> **sx66gns said:**
> It does

not sure , I picked it up somewhere , it is however related to Blizzard entertainment.

It's my "man-sense"

Cool, thank you! Man-sense, huh? :) 

Btw, I was not able to install it from the repositories in Synaptic. So, I downloaded the .deb file from the official site. However, when I tried to install the .deb file, I got some Error: "Cannot install libnet-perl". 

Okay, I'm going to install libnet-perl now but do you have any idea what that does? 'Cos it looks like a lot of files are going to be affected and I'd like some warning if things are going to go haywire.

---

### Post by Lucifiel on 2007-05-07
> **Fittersman said:**
> what guy would have a chick in their avatar? (well unless it was a hot babe or something, but not a drawing like that one)

*shrugs* Not all men are like that. But whatever.

---

### Post by Wiebelhaus on 2007-05-07
> **Lucifiel said:**
> Cool, thank you! Man-sense, huh? :) 

Btw, I was not able to install it from the repositories in Synaptic. So, I downloaded the .deb file from the official site. However, when I tried to install the .deb file, I got some Error: "Cannot install libnet-perl". 

Okay, I'm going to install libnet-perl now but do you have any idea what that does? 'Cos it looks like a lot of files are going to be affected and I'd like some warning if things are going to go haywire.

follow the instruction in this[ thread]("http://ubuntuforums.org/showthread.php?t=88357&highlight=install+f-prot")

"sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential libwww-perl libgtk2.0-dev checkinstall"

this is a crucial command that has to be ran in the term.

Also

Found some of those avatars :)
[http://www.milkysavatars.net/war.shtml](http://www.milkysavatars.net/war.shtml)

---

### Post by Lucifiel on 2007-05-07
> **sx66gns said:**
> follow the instruction in this[ thread]("http://ubuntuforums.org/showthread.php?t=88357&highlight=install+f-prot")

"sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential libwww-perl libgtk2.0-dev checkinstall"

this is a crucial command that has to be ran in the term.

Also

Found some of those avatars :)
[http://www.milkysavatars.net/war.shtml](http://www.milkysavatars.net/war.shtml)

Thank you for the avatars. :) 

Big oopsie. I forgot I'd already installed the Fprot installer. No wonder why the first command wouldn't work... doh! :p 

Darn. Think the repository link is down:
$ : sudo aptitude update && sudo aptitude upgrade

dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up f-prot-installer (0.5.22) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

---

### Post by phillipchandler on 2007-06-26
Hi Everyone.

Im wanting to install F-Prot. I downloaded the deb file for ubuntu 7.04, went to install, it needed the dependency libnet-perl.
So I went to synaptic and clicked on libnet-perl, and to my amazement it wanted to uninstall what seems like a lot of my system files.
I currently have both GDM & KDM installed, and libnet-perl wanted to unistall these, plus evolution, acroread, and libnet-perl wanted to uninstall these, plus a load others. Any help on what I may have missed, or what I may be doing wrong ?

Thanks
Phillip

---

### Post by phillipchandler on 2007-06-26
Sorry ! I found the answer, and it seems to work.

ttps://bugs.launchpad.net/ubuntu/+source/perl/+bug/108137

Edit /var/lib/dpkg/status
Find section "Package: perl-modules", Line "Conflicts:".
Change "libnet-perl (<= 1:1.19-3)" to "libnet-perl (<= 1.19-3)"

Now you're able to install libnet-perl via "sudo apt-get install libnet-perl"

---

