---
title: "Linux as Small Office Server"
date: 2007-09-09
forum: General Help
---

### Post by bumcheekcity on 2007-09-09
I want to set up a Linux Server for a small office of 15 PCs. We ideally want to move everyone we can off Windows, save for a few select people. We're a small website building office, so only our Graphic Designer, Receptionist/Accountant, Tech Support and Boss need Windows, the rest of us programmers can use Linux. And it's cheaper :D

I've set up a Linux server using the Webmin package in my house, and I must say, it's the best piece of software I've ever found. I've managed to get it as a firewall (completely secure) and distributing Internet through my home network. However, the Office Server will need more than this. It's going to need:

- Firewall/Internet Routing
- Fileserver
- SAMBA domain that Windows and Linux clients can logon to. 
- CVS Server
- Apache Webserver (actually, probably more than one of these).

And, we only want ONE set of usernames and passwords for CVS, SAMBA, etc. So, it might be a pretty big task, but is it going to be easy enough to do, bearing in mind that I couldn't get the blasted SAMBA domain working at home yet?

On another note, who knows how to get a Samba domain working? I keep getting "Access is Denied" errors when I connect to the domain in Windows XP, using the correct username and password, with a machine account for the computer name.

---

### Post by HermanAB on 2007-09-09
Setting up Samba as a domain controller is a bit of a black art.  You'll have to do some reading on the Samba web site.

I am doing the reverse: Using Linux machines with a Windows based domain controller and it is a immensely difficult to get that to work.  See this guide for some ideas, it is not what you want to do, but it will give you some clues and tell you where the common pitfalls are: [http://www.aeronetworks.ca/LinuxActiveDirectory.html](http://www.aeronetworks.ca/LinuxActiveDirectory.html)

Also see this guide for general Samba debugging tips: [http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

Cheers,

H.

---

### Post by Ubuntu Warrior on 2007-10-19
> **bumcheekcity said:**
> I want to set up a Linux Server for a small office of 15 PCs. We ideally want to move everyone we can off Windows, save for a few select people. We're a small website building office, so only our Graphic Designer, Receptionist/Accountant, Tech Support and Boss need Windows, the rest of us programmers can use Linux. And it's cheaper :D

I've set up a Linux server using the Webmin package in my house, and I must say, it's the best piece of software I've ever found. I've managed to get it as a firewall (completely secure) and distributing Internet through my home network. However, the Office Server will need more than this. It's going to need:

[I][COLOR="DarkOrange"]I fully agree with you, Linux is a truly remarkable gift to the world of computer users (and hackers :) ). We have migrated away from a Microsoft Active Directory domain to a Ubuntu Linux SAMBA/OpenLDAP network. We currently run all our networking services, file- and print-sharing, LDAP directory services, DHCP, DNS, auth, etc., off Ubuntu Linux servers with huge success. We currently have about 150 users in the business of which around 40 are installed with Ubuntu Feisty software. The workstations have allowed us to reduce os, office and antivirus client licenses and are extremely stable and fast. (We are currently looking at Gutsy but have some initial problems getting Gutsy to auth against our Samba/OpenLDAP network with is hosted off Feisty servers).

A piece of advice - under NO circumstances use Windows to host your network as you will still need to license Linux clients accessing MS network resources. Linux is totally capable of fully replacing a Windows 2k/2003/AD solution and runs a lot smoother. If you still need to run some Windows clients so be it (we do) but try your utmost to manage these down as far as possible.[/COLOR][/I]

- Firewall/Internet Routing
- Fileserver
- SAMBA domain that Windows and Linux clients can logon to. 
- CVS Server
- Apache Webserver (actually, probably more than one of these).

And, we only want ONE set of usernames and passwords for CVS, SAMBA, etc. So, it might be a pretty big task, but is it going to be easy enough to do, bearing in mind that I couldn't get the blasted SAMBA domain working at home yet?

*[COLOR="DarkOrange"]I don't want to mislead you, you are going to have to learn a lot and it will be a lot of work getting your new Linux network operational but the rewards are well worth the effort. You definitely need to go for OpenLDAP integrated with Samba (smb-ldap) for a single-sign-on-type solution.[/COLOR]*

On another note, who knows how to get a Samba domain working? I keep getting "Access is Denied" errors when I connect to the domain in Windows XP, using the correct username and password, with a machine account for the computer name.

*[COLOR="DarkOrange"]Lots of guidance is available for setting up Samba with OpenLDAP (search for smb-ldap) and this info will be essential in the project. Good luck![/COLOR]*

---

### Post by dayvy on 2007-10-19
I know it's not ubuntu but you might want to have a look at this. It's based on CentOS and I believe it will do all that you want without too much hassle.

[http://www.smeserver.org/](http://www.smeserver.org/)

I didn't see mention of a cvs server in the documentation but a quick search on their forums shows that people were able to get that up an running without too much trouble.

---

### Post by disasm on 2007-10-19
depending on your need for security for authentication between windows clients and samba server, if you trust your connection between the two to transmit plain text passwords, samba can use pam to authenticate.

Sam

---

### Post by meharts on 2007-10-19
Hi to everyone, sorry to but in on this thread but could do with some help. I posted the following today but haven't had a reply. [http://ubuntuforums.org/showthread.php?t=580089](http://ubuntuforums.org/showthread.php?t=580089)

My question is this. I can by pass my router for installing and updating my software, but I still have the problem of getting access to my distro. I tried installing webmin from the command line but no dice. There appears to be something wrong with the package!! The only other option is a .tgz file and then how can one get that onto the computer without a desktop friendly gui?

I am also a great believer in webmin but can't figure out how to get it onto my computer without installing ubuntu-desktop.

I would also like to keep my distro light. Once you have installed ubuntu-desktop it isn't easy getting rid of all the unwanted packages later.
Once again, I do apologize for butting in but wondered if you webmin guys have any solutions?

meharts

---

### Post by disasm on 2007-10-19
> **meharts said:**
> Hi to everyone, sorry to but in on this thread but could do with some help. I posted the following today but haven't had a reply. [http://ubuntuforums.org/showthread.php?t=580089](http://ubuntuforums.org/showthread.php?t=580089)

My question is this. I can by pass my router for installing and updating my software, but I still have the problem of getting access to my distro. I tried installing webmin from the command line but no dice. There appears to be something wrong with the package!! The only other option is a .tgz file and then how can one get that onto the computer without a desktop friendly gui?

I am also a great believer in webmin but can't figure out how to get it onto my computer without installing ubuntu-desktop.

I would also like to keep my distro light. Once you have installed ubuntu-desktop it isn't easy getting rid of all the unwanted packages later.
Once again, I do apologize for butting in but wondered if you webmin guys have any solutions?

meharts

Figure out what's wrong with the package. If you think removing unwanted debs is bad, try removing code you compile from scratch (unless you change the prefix, to a directory that contains no other apps. Then you just rm the directory).

Sam

---

### Post by dayvy on 2007-10-19
I haven't tried this version in gutsy but give it a go:

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb)

This will download the package.

Go to the directory where you downloaded this and type: dpkg -i webmin_1.370_all.deb

That should install it or will at least tell you what dependencies are missing.

---

### Post by meharts on 2007-10-19
OK thanks for the heads up guys!!

meharts

---

### Post by meharts on 2007-10-19
Well, I have tried your info dayvy and it worked a treat. First I did a re-install and then I changed to root and ran #wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb)

The install went all right but webmin was missing 5 dependencies, so I typed them up and tried apt to install the first one on the list. It wouldn't install due to the other 4 dependencies. I then ran #apt-get -f install and that took care of the 5 missing dependencies and continued to configure webin DONE!!

Thanks again for your help.:)

meharts

---

### Post by dayvy on 2007-10-19
Glad it worked for you.

---

### Post by Wiebelhaus on 2007-10-19
two months ago one of the techs in the shop I work in setup the same size office he sold them a high end server with windows server 2003 , this tech knows what he's doing no question , but he's been out there at the very least once a week poking server 2003 , he's worked with server 2003 extensively in the past but is starting to finally realize it's a piece of crap , but it's to far gone to recommend a linux distro as the guy vehemently hates anything linux , So instead of starting an arguement , I'll just sit back and watch him suffer and know If I was in the same situaton , my setup would be working without issues.

---

