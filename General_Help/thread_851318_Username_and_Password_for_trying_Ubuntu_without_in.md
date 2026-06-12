---
title: "Username and Password for trying Ubuntu without installing"
date: 2008-07-06
forum: General Help
---

### Post by jbenuntu on 2008-07-06
Hello,
I just wanted to try out Ubuntu on my computer without installing it first. I am running Windows XP and have the CD ISO image on a CD. The ISO was verified on download via winMD5Sum and on burning via Ubuntu start-up screen. I am trying to do the Ubuntu option "Try Ubuntu without making any changes to your computer" when I boot-up my computer, with the Ubuntu ISO CD in the CD drive. Ubuntu loads, then it asks me for my Username and Password; but I did not install Ubuntu so there are none of these. How do I get past this to try Ubuntu ? Thanks.:confused:

---

### Post by sdennie on 2008-07-06
This is usually a symptom of the disk having burned incorrectly.  The LiveCD shouldn't ask for a password.  I would try burning the disk at a lower speed and seeing if that helps.

---

### Post by jbenuntu on 2008-07-06
Hello. I burnt the disc using InfraRecorder as per Ubuntu documentation site: 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

using the following settings from the box below (write speed of 1x), but still recieve same prompt screen for user name and password...?

---

### Post by nikgare on 2008-07-06
What is the name of the ISO file you burned?

---

### Post by jbenuntu on 2008-07-06
ubuntu-8.04.1-desktop-i386.iso

this is why i use windows. why is it IMPOSSIBLE to EVER install ANY type of Linux/unix system?
Installs attempted:
FreeBSD
Linux RedHat
Linux Fedora
Ubuntu
OpenSUSE
Installs Successful:
NONE
Computers Lost:
3
Linux/Unix = a waste of time.

---

### Post by cprofitt on 2008-07-06
Odd.

I never get prompted for a login when I use the 'try' option. While learning Linux may be difficult it is not impossible and with help from the fantastic community here it will be much easier.

---

### Post by billgoldberg on 2008-07-06
> **jbenuntu said:**
> ubuntu-8.04.1-desktop-i386.iso

this is why i use windows. why is it IMPOSSIBLE to EVER install ANY type of Linux/unix system?

Since you are on a windows pc, you can install Ubuntu using Wubi.

This will install Ubuntu like any other application in Windows.

So if you don't like it, go to add/remove and remove it.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

That will avoid the "username" and "password" issue you seem to be having.

---

### Post by Elfy on 2008-07-06
>  why is it IMPOSSIBLE to EVER install ANY type of Linux/unix system?Obviously it's not but you are having some problems :)

Try to use ubuntu as the username with no password.

But as others have said it is usually indicative of something wrong with the download or burn.

---

### Post by Gunman1982 on 2008-07-06
Do you get a graphical login or just a black and white screen where it prompts for a username?

---

### Post by Rainstride on 2008-07-06
TRY username ubuntu and password ubuntu. thats what they are in the try mode.

---

### Post by jbenuntu on 2008-07-06
> **billgoldberg said:**
> Since you are on a windows pc, you can install Ubuntu using Wubi.

This will install Ubuntu like any other application in Windows.

So if you don't like it, go to add/remove and remove it.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

That will avoid the "username" and "password" issue you seem to be having.

--------------------------------------
No it did not avoid the "username" and "password" issue. The same prompt comes up. I set the password to "password", and left the default username as "owner". It still will NOT LOGON. I tryed to log on using this Wubi, and it keeps kicking me back to the log on screen. Ubuntu refuses to load on my machine like EVER OTHER LINUX SYSTEM EVER.

---

### Post by jbenuntu on 2008-07-06
> **forestpixie said:**
> Obviously it's not but you are having some problems :)

Try to use ubuntu as the username with no password.

But as others have said it is usually indicative of something wrong with the download or burn.

-------------------------------------------------------------
This does not work.

---

### Post by 64dragon on 2008-07-06
do you have any other burning programs? i've used nero and never had a problem burning a linux distro at full speed and i've tried suse gnome and kde, ubuntu, kubuntu, mandriva and knoppix

---

### Post by athaki on 2008-07-06
Check the md5sum of your .iso file.  The following link is to a website with a free md5 sum checker. 

[http://www.brandonstaggs.com/filecheckmd5/](http://www.brandonstaggs.com/filecheckmd5/)

The result should read c69e34e92d5402d1b87e6babc739f774  
for ubuntu-8.04.1-desktop-i386.iso

---

### Post by jbenuntu on 2008-07-06
> **athaki said:**
> Check the md5sum of your .iso file.  The following link is to a website with a free md5 sum checker. 

[http://www.brandonstaggs.com/filecheckmd5/](http://www.brandonstaggs.com/filecheckmd5/)

The result should read c69e34e92d5402d1b87e6babc739f774  
for ubuntu-8.04.1-desktop-i386.iso

MD5Sum checks out both with the result you posted and the sum from the Ubuntu site.

---

### Post by jbenuntu on 2008-07-06
NOTE*********************************************
If your getting this same problem give up. There is no way around this. NONE of these solutions worked. Your wasting your time and Ubuntu will not install. I've wasted two days on this and lost 5 CD's, 1 DVD and had my system crash 2 times. DO NOT TRY UBUNTU. IT IS IMPOSSIBLE TO INSTALL.

---

### Post by cprofitt on 2008-07-06
> **jbenuntu said:**
> NOTE*********************************************
If your getting this same problem give up. There is no way around this. NONE of these solutions worked. Your wasting your time and Ubuntu will not install. I've wasted two days on this and lost 5 CD's, 1 DVD and had my system crash 2 times. DO NOT TRY UBUNTU. IT IS IMPOSSIBLE TO INSTALL.


Wow.

I just am not sure what error you are getting...

I do not know why you are getting prompted for a username/password for the liveCD... I have both the 32bit and 64bit versions of 7.10 and 8.04 and none of them prompt me for a username and password for the liveCD.

If you really think the CD burning is an issue try this -- [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

It is a burner from an actual MS employee who works on Windows and I have used it several times to burn various iso files to CD.

For the record I also need to point out to other people who stumble on this thread that the OP has not, despite later claims, installed Ubuntu. He is trying to use the liveCD and having an issue with a username and password being needed (despite this not being the experience for 99.999% of other users). **An install would prompt you for a username and password during the install.**

While it is not impossible that there is an issue with this would be an extremely rare problem.

To the OP -- we can try to help you, but getting frustrated will not help.

Perhaps try 'root' with no password.

---

### Post by nikgare on 2008-07-07
Can you tell us the specs of your computer, what options you give the liveCD at the boot promt, where you got the liveCD iso from, was it via the Ubuntu.com website, or a third party?
After googling, the username should be "ubuntu" and the password is nothing, but I belive that doesn't work for you.

---

### Post by jbenuntu on 2008-07-26
still unable to log on........I have ordered and recieved the Ubuntu disk: Ubuntu 8.04 LTS Desktop Edition. I STILL get the username and password screen and i STILL cannot log on. WTF.

system: Microsoft Windows XP
	Home Edition
	Version 2002
	Service Pack 2
eMachines
T6212
AMD Athlon(tm)64 Processor
3200+
1.99 GHz, 384 MB of Ram


username,password combos tried:
<none><none>
ubuntu<none>
root<none>
ubuntu,password
root,root
username,password

---

### Post by Shazaam on 2008-07-26
You could also install vmware or virtualbox on XP to try Ubuntu/linux as a virtual machine.....
[http://www.vmware.com/download/](http://www.vmware.com/download/)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by jkay on 2008-07-26
If you want to rule out bad burning order one.  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Says that it only takes 6-10 weeks, lol.

---

### Post by oceala on 2008-12-25
I just bought the Mirus Educational, Intel Powered Classmate PC Designed for Kids, Edubuntu Edition. When I turned it on it goes to the edubuntu screen and asks for a username and password. What username/password do I put in? This is the first time turning on this computer. I've searched online and have used many different suggestions but none have worked so far. Any assistance would be appreciated. Thanks.

---

### Post by whiteman on 2010-03-18
Recently I screwed up my sources.list..trying to get Boxee to work properly. I guess thats how it all started. Now when I do update..I dont get the Upgrade option. So I ordered a 9.10 disk. I wanted to see how it looked so I tried a trial look-see. Then I get a login screen? I never got this with Jaunty. It just went automatically. I didnt burn incorrectly etc..its a "factory disk". It came from the "home office" whatever that is.haha. WHat is the default username/password? I heard that oem was username but I tried using my own info but it didnt work. Ideas?

---

### Post by whiteman on 2010-03-18
> **jkay said:**
> If you want to rule out bad burning order one.  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Says that it only takes 6-10 weeks, lol.

I did. Thats the one that prompts for username/password! I am talking about Koala. Jaunty worked fine.

---

### Post by lgkwUNIX on 2010-08-31
i face this trouble to... but with ubuntu 10.4...
before require for login and pass has pop up INSTALLER FAILURE. 
the installer encountered an uncoverable error. A desktop session will now be run so that you may investigate.

---

### Post by rockager on 2010-09-01
if your md5 checksum was correct it means that there is some problem with the the image burner you use.
try running the ubuntu image file (.iso) on virtualbox
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
give the virtual machine 1gb ram (if you have 2gb)
if it is lessser than that try giving as much as possible (but leave some for the host os)
if it works then there is some problem with your image burner
if it does not than i am out of ideas.

---

### Post by niteshifter on 2010-09-01
Hi,

Should the OP still be interested:

Highlighted in red is his problem:
> system: Microsoft Windows XP
Home Edition
Version 2002
Service Pack 2
eMachines
T6212
AMD Athlon(tm)64 Processor
3200+
1.99 GHz, [COLOR="Red"]384 MB of Ram[/COLOR]

as per the system requirements page [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Not obvious at all when one starts with ubuntu.com, I had to google it.

OP: you may have success with Xubuntu instead.

---

### Post by graphius on 2011-01-20
Just to close this thread if anyone is having this problem.
short version:
[INDENT]use username: root
before you enter a password, change the desktop to desktop (safe mode)
leave the password blank[/INDENT]

this gets you to a command prompt. maybe this will help developers fix this bug...

I wanted to resize a partition on my NAS, so I just needed to get into gparted. I booted from a USB stick created from Startup Disk Creator on my desktop. (Ubuntu 10.10)

system info:
Intel Celeron 2.8
1.5 GB RAM

PS I have installed Ubuntu on a lot of computers over the years. This is the first time I remember getting a username/password prompt. It was also the first time I used a USB stick instead of a CD. :confused:

---

### Post by graphius on 2011-01-20
double post....

---

### Post by graphius on 2011-01-20
Either I have a bad connection today, or the forum servers are tired...

---

### Post by Nonayo on 2012-01-14
[FONT="Arial"]I'am not sure if my problem was the same as the OP but I tried Ubuntu on a new blank hard drive from a CD, and it loaded fine.  Then I wanted to shutdown the computer and chose 'suspend' instead of shutdown, to come back at it later.  When I turned it back on, there was a window on the empty desktop picture asking for a username and password. I had access only to the top right icons, but selecting shutdown would not work. Not being able to logon I ended up here, and as Forestpiskie suggested:

username: ubuntu  
password: blank 

and it loaded perfectly. Thanks![/FONT]

---

### Post by oldos2er on 2012-01-14
Closed, necromancy.

---

