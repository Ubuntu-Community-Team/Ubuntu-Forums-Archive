---
title: "Linux Response Very Slow"
date: 2008-01-17
forum: General Help
---

### Post by techgy on 2008-01-17
I'm new to this forum and VERY new to Linux itself. 
All of my experience has been on Windows machines, so please forgive my ignorance.

I recently installed v7 of the Linux Desktop to a P4 Machine w/256 meg RAM and a 40 Gig drive. CPU is 2 gig Hz.  I realize that the RAM needs to be increased however;

When I click on any item on the desktop it takes several seconds before ANYTHING happens. Desktop response is very slow - even for this machine, which ran quite well on a Win XP OS.   

Before I put money into increasing the RAM, I was wondering if I missed something during the install. 
If anyone has any recommendations as to where I might look I'd appreciate suggestions. 

My goal in working with the LINUX OS is to become somewhat familiar with it. I don't have anything specific that I'm trying to accomplish other than just experimentation.  

From what I've been told Linux is supposed to be much better than Windows, but I wonder if I have to sacrifice speed for being better??

Suggestions welcome. 

Thanks

Techgy

---

### Post by Lord Illidan on 2008-01-17
First check if there's anything clogging up the Ram. Use System -> Administration -> System Monitor.

Ubuntu is a modern desktop, over 7 years older than XP, so expect some higher memory requirements. However, you can get over this by using Xubuntu, or another distribution altogether. I recommend Zenwalk (although it is harder than Ubuntu).

---

### Post by AaronMiller on 2008-01-17
Yeah I have the same issue all the time. Firefox takes forever to load up it seems and the interface just seems sluggish and chunky if that makes any sense. It shouldnt be ram since the memory usage is ~200mbs with 1GB of ram on the system.

---

### Post by Whiffle on 2008-01-17
Sounds to me like a hard drive issue.  Try opening up a terminal and running:

sudo hdparm -tT /path/to/your/harddrive*


* usually something like /dev/sda

---

### Post by Jerry N on 2008-01-17
> **techgy said:**
>   

From what I've been told Linux is supposed to be much better than Windows, but I wonder if I have to sacrifice speed for being better??


I will likely be flamed for saying this here but don't believe everything you are told about Linux being "much better than Windows" or any other such comparison.  It is like saying that a Prius is "much better" than a Taurus or that a PS3 is "much better" than an Xbox.  (In truth, I don't know crap about either PS3 or Xbox).  Like beauty, "better" tends to be in the eye of the beholder.  For me, the only things better about Linux at this point in time are its cost and (probably temporary) lack of susceptibility to viruses and worms.  I certainly have not found it to be faster than a properly tuned XP system but I will continue to evaluate various Linux distros as future alternatives to Windows Vista and/or its successors.  

I find Ubuntu and LinuxMint to be *_much better _* than the other distros I have installed and tested but then I admit to be as *full of it* as anyone else :twisted:  

Jerry

---

### Post by Jerry N on 2008-01-17
An additional note to my previous comments:  I just installed PCLinuxOS and for the short time I played with it I found it to be the very most sluggish Linux distribution I have tried.  Others have found it to work better for them than Ubuntu.  Go figure!

Jerry

---

### Post by DrMega on 2008-01-17
Ubuntu 7.10 (Gutsy) is a bit slow on lower spec machines. 6.10 (Edgy) and 6.06 (Dapper) will run on just about anything. I think it is since Compiz/Fusion was integrated into Gnome (for us Ubuntu users that happened in 7.10 if I'm not mistaken).

That said, my main machine only has 512MB RAM, a 1.8GHz Duron, a mediocre graphics card (well old actually, nVidia N6200) and it is fine, so more memory might do the trick.

If you can't be bothered to wait until you've had chance to add more RAM, try installing the Xubuntu Desktop (in synaptic) and trying that. There is less eye candy but it is much less resource hungry and you can run all the same apps. Also you can keep the default Gnome desktop around so you can easily switch back if you want to.

---

### Post by techgy on 2008-01-17
Thanks to all the replies. I'll read over what has been said and see what I can do.
I do have one question though. A couple suggestions were made to try "xbuntu". 
Pardon a stupid question but what is it? Is this a smaller edition of the full version?

Do I have to remove the full version to install Xbuntu?

---

### Post by lswest on 2008-01-17
xubuntu is another version of ubuntu which uses the xfce window manager, instead of GNOME, and can be downloaded from [here]("http://www.xubuntu.com/") and yes, to install it you need to remove Ubuntu, or you can alternatively just download and install xubuntu-desktop using apt-get/synaptic in the already install ubuntu on your computer.

---

### Post by Christmas on 2008-01-17
Xubuntu is a distribution which uses XFCE instead of GNOME as a window manager. It's usually faster and uses less memory (from what I've heard, I've never tried it). You can install it on a clean partition or just install the XFCE packages alongside your GNOME installation.

However I'd strongly recommend you to try Kubuntu, which uses KDE as a desktop environment. For me KDE was always faster and might be easier for a beginner. Also, if I recall correctly (I might be wrong), Beryl is disabled in Kubuntu.

---

### Post by DrMega on 2008-01-17
> **lswest said:**
> xubuntu is another version of ubuntu which uses the xfce window manager, instead of GNOME, and can be downloaded from [here]("http://www.xubuntu.com/") and yes, to install it you need to remove Ubuntu, or you can alternatively just download and install xubuntu-desktop using apt-get/synaptic in the already install ubuntu on your computer.

No, no, no.

You don't need to uninstall Ubuntu, or create a new partition or anything like that. You can do this:

1. In Ubuntu you go to System->Administration->Synaptic Package Manager.
2. Find 'Xubuntu Desktop' and install it.
3. Go to log off, and choose Switch Session (or hit CTRL+ALT+Backspace)
4. At the login screen, choose Change Session - At the resulting dialog, chose Xfce
5. You will be asked if you want to use it just for now, or make it default, that's up to you.
6. Log in as normal

Then hey presto, Xubuntu.

That way you have all the same apps and data that you had in Ubuntu. Why? Because you are in the same OS, you just switched the desktop environment.

---

### Post by techgy on 2008-01-17
The xbuntu desktop is not listed among the choices in the package manager.

---

### Post by lswest on 2008-01-18
the package name is, i believe, "xubuntu-desktop" and should be in the package manager.  Make sure you have you software repositories enabled (edit-->repositories, i think [never really use synaptic]) and deselect the CD if it's selected, and select universe/multiverse (not needed for the xubuntu package, but useful nonetheless^^) and then try searching for it again.

---

### Post by zetetic on 2008-01-18
> **techgy said:**
> Thanks to all the replies. I'll read over what has been said and see what I can do.
I do have one question though. A couple suggestions were made to try "xbuntu". 
Pardon a stupid question but what is it? Is this a smaller edition of the full version?

Do I have to remove the full version to install Xbuntu?

Why are you making questions about this kind of subjects, when you can easily learn anything you want about them just by going to Ubuntu site or googling??? Like writing this on a Google search: "What is xubuntu".

Don't you know how to read  or how to use google?

Did you at least bored to search this forum about xubuntu, before asking this kind of question here???

---

### Post by DrMega on 2008-01-18
> **zetetic said:**
> Why are you making questions about this kind of subjects, when you can easily learn anything you want about them just by going to Ubuntu site or googling??? Like writing this on a Google search: "What is xubuntu".

Don't you know how to read  or how to use google?

Did you at least bored to search this forum about xubuntu, before asking this kind of question here???

Is there any need for this kind of attitude. A guy asked a legitimate question, even if it has been asked before there is no need to insult him/her. If you asked a question would you like to see a response like this?

---

### Post by dan0z on 2008-01-18
Just thought that i may add, I have to disagree about ubuntu being slow on lower spec machines, I am currently running ubuntu v7 on two PIII 733Mhz with 256mb RAM on-board graphics, and both machines run fine a little slow but very useable, in my oppinion if i had XP on these machines the speed would be terrable.

Dan

---

### Post by ugm6hr on 2008-01-18
XFCE / Xubuntu is a reasonable option (I started on Xubuntu 7.04 myself).

Before you do that though, why not just try turning Compiz off in (Gnome aka standard) Ubuntu.

System-> Preferences-> Appearance
*Visual Effects* tab
Select *None*

Also, you can disable unnecessary processes at Startup:

System-> Preferences-> Sessions
*Startup programs* tab
Untick the following (unless you specifically need them):
Restricted Drivers Manager
Print Queue Applet
Bluetooth Manager
Evolution Alarm Notifier
If you don't have wifi - you don't need Network Manager either.

Then try rebooting, and see if things are any better.

If not, you can get big speed increases with XFCE (xubuntu-desktop) or other lighter Window Mangers.

---

### Post by Christmas on 2008-01-18
These two links should be of help too:

On how to install XFCE (the desktop environment used by Xubuntu):
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

On low-specs systems (though yours is not that low...):
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

