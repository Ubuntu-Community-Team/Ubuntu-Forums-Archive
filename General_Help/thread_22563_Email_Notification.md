---
title: "Email Notification"
date: 2005-03-28
forum: General Help
---

### Post by Psquared on 2005-03-28
This thread has already been started several times, and I apologize for starting it again, but I could not find the answer.

I am using Warty and I want a notification window to open up when I receive new email. I am using Evolution. I prefer it because of the calendaring, but I can switch to a different program if need be.

In one of the threads it said something about a program called "mail-notification" that was available from the repos, but I have all the sources enabled (I think) and I can't find the program.

I did find something called "coolmail" which is supposed to act as a notification program, but I can only start it in a terminal. I did a search and there is no other information available.

I either need to: find "mail-notification" or figure out how to setup/configure "coolmail."

Any help would be appreciated.

---

### Post by PMO6022 on 2005-03-28
You can get mail notification here: [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

You do have to compile it yourself, but I got it running with my gmail account without too much trouble.  Make sure you read the README and INSTALL files after unpacking the tarball.

---

### Post by bored2k on 2005-03-28
[QUOTE=PMO6022]You can get mail notification here: [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

You do have to compile it yourself, but I got it running with my gmail account without too much trouble.  Make sure you read the README and INSTALL files after unpacking the tarball.[/QUOTE]
 >  apt-cache search mail-notification
mail-notification - Mail notification in system tray


[http://higgs.djpig.de/ubuntu/www/hoary/gnome/mail-notification](http://higgs.djpig.de/ubuntu/www/hoary/gnome/mail-notification)

No compiling needed ;) .

---

### Post by Psquared on 2005-03-28
> **bored2k][http://higgs.djpig.de/ubuntu/www/hoary/gnome/mail-notification](http://higgs.djpig.de/ubuntu/www/hoary/gnome/mail-notification)

No compiling needed  said:**
> 

Hey would you post your sources.list file? When I run the cache search I get nothing.

Here's mine:

[quote]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 
#deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/ 
#deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/ 


---

### Post by Psquared on 2005-03-28
bored2k,

I am using Warty not Hoary. The link above for the pre-compiled version is for Hoary.

---

### Post by bored2k on 2005-03-28
[QUOTE=Psquared]bored2k,

I am using Warty not Hoary. The link above for the pre-compiled version is for Hoary.[/QUOTE]
 Just noticed. My bad :-S

[http://www.macewan.org/index.php?m=20050215](http://www.macewan.org/index.php?m=20050215)
There is a how to in there [2nd post at the time I checked] .

---

### Post by Psquared on 2005-03-28
[QUOTE=bored2k]Just noticed. My bad :-S

[http://www.macewan.org/index.php?m=20050215](http://www.macewan.org/index.php?m=20050215)
There is a how to in there [2nd post at the time I checked] .[/QUOTE]

No problem --- and thanks for the link. I had a bunch of dependencies to install, but it finally went through. It looks like I will have to log out and back in to see the menu item.

---

### Post by Psquared on 2005-03-28
Still no menu item for mail-notification. When I start the program in a terminal using Mail-notification I get an error saying:

>  Bonobo could not locate the GNOME_MailNotification_Automation.server file. Please check your Mail Notification installation.

There were no errors during installation. (At least none that I saw after I installed the dependencies.) Any ideas????  :-k

---

