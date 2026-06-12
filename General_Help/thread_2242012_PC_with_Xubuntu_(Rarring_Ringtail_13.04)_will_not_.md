---
title: "PC with Xubuntu (Rarring Ringtail 13.04) will not start [video linked]"
date: 2014-08-30
forum: General Help
---

### Post by queazy03 on 2014-08-30
Hi,

  My brother's PC won't start and I don't know what to do.  

  Here is a video link showing what happens at "[http://youtu.be/xeijG1WGMdk](http://youtu.be/xeijG1WGMdk)".   I built this PC which runs a Xubuntu operating system, version 13.04  Rarring Ringtail if I remember right.  The hardware part list that the  PC is made from is here at "[http://pcpartpicker.com/parts/partlist/](http://pcpartpicker.com/parts/partlist/)", but note that the graphics card is "[www.asus.com/Graphics_Cards/EAH4350_SILENTDI512MD2LP/]("http://www.asus.com/Graphics_Cards/EAH4350_SILENTDI512MD2LP/")".


  The words that pop up on the screen before it goes completely blank are
  [HR][/HR]  Starting Network Connection Manager
Starting Crash Report Submission Daemon
Starting amac(h)romistic crom
Stopping amac(h)romistic crom
Checking Battery state...
Stopping System V runlevel compatability
Starting
  [HR][/HR]  and on the far right it says "OK" to all of them on the same line.


  What can I do to make the computer run properly?  Thank you

---

### Post by sudodus on 2014-08-30
- How new is the computer?

- Did it work with Xubuntu before?

I ask because you use Xubuntu Raring 13.04. It has passed end of life, and the repositories are no longer maintained. Please try a current version, start with Xubuntu 14.04.1 LTS with long time support until April 2017. See also these links.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL][Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

There may be issues with the Radeon card, and you may be able to solve them with the [boot option]("https://help.ubuntu.com/community/BootOptions") **nomodeset** or some other boot option, and a proprietary driver.

Depending on the age of the hardware, an Ubuntu flavour based on 12.04 LTS or 14.04 LTS might work better.

- 12.04 LTS (Xubuntu end of life April 2015, but there are alternatives that promise support until April 2017) - for older hardware
- 14.04 LTS (Xubuntu end of life April 2017, and there are alternatives that promise support until April 2019) - for newer hardware

---

### Post by queazy03 on 2014-08-30
> **sudodus said:**
> - How new is the computer?

- Did it work with Xubuntu before?

I ask because you use Xubuntu Raring 13.04. It has passed end of life, and the repositories are no longer maintained. Please try a current version, start with Xubuntu 14.04.1 LTS with long time support until April 2017. See also these links.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL][Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

There may be issues with the Radeon card, and you may be able to solve them with the [boot option]("https://help.ubuntu.com/community/BootOptions") **nomodeset** or some other boot option, and a proprietary driver.

Depending on the age of the hardware, an Ubuntu flavour based on 12.04 LTS or 14.04 LTS might work better.

- 12.04 LTS (Xubuntu end of life April 2015, but there are alternatives that promise support until April 2017) - for older hardware
- 14.04 LTS (Xubuntu end of life April 2017, and there are alternatives that promise support until April 2019) - for newer hardware

Hi,

The computer has been working wonderfully since it was originally installed with Xubuntu Rarring Ringtail in roughly June of 2013.  The graphics card was installed a few months after that, with no issue.  y brother has been using the computer a lot and has a tons of personal files there on the hard drive.  I don't mind installing an upgraded version of Xubuntu, but what I do NOT want to happen is to lose all the many many personal files my brother has on the hard drive.   

There were no changes to either software or hardware anytime recently, in fact I chose a Xubutu OS so that it would be hassle free and my brother would not be able to change the software without knowing it (by say accidentally getting malware).  

How do you recommend I proceed, while making sure that these personal files will remain accessible?  Thank you.

---

### Post by QIII on 2014-08-30
Hello!

Whatever you do, ***back up*** all of your brother's important files.  There is no guarantee that anything will preserve them no matter what you do.  Errors can and will happen.  Remember the words of Robert Burns in *To a mouse ...*:  

"The best-laid schemes o' mice an' men 
Gang aft agley,"   

Does this machine have a separate /home partition?

Just to be sure, did I mention to ***back up*** all of your brother's important files? ;)

---

### Post by queazy03 on 2014-08-31
Hi

I haven't been able to even get to login / desktop the way the machine is now.  How can I go about backing up the files?  Thank you.

---

### Post by sudodus on 2014-08-31
***Boot a live system from a CD/DVD/USB drive***, for example an Ubuntu live CD, Knoppix, Clonezilla ... and either

1. Simply copy your brother's important files to an external disk or to some cloud service like google drive or dropbox

2. Run a special backup program. See this link [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

3. Make a cloned copy or image of the whole system (for example with Clonezilla).

The first option is easiest, and probably enough, if your brother can tell you which files to copy, or from which directories to copy files.

---

### Post by queazy03 on 2014-09-02
Hi, 

I used Linux Mint to back up files, but for some reason some files were "locked" and I couldn't back them up.  What can I do about that?

I could't figure out those links at all, I'm sorry.  I didn't know what to do.  I mean, I can't even run the computer to install that software.  So what I did do was make this old boot-up CD that had something called "Linux Mint" on it, that I had used to try to recover files from a dying hard drive a year ago.  Using this boot CD, you can run a temporary OS based off of whatever Linux Mint is, to move programs around.  With that, I was able to backup files onto an external hard drive I had.  The external hard drive I use has 1 terabyte of free space, and my bro's hard drive had 500g of total space, most of which was used.  The thing was, I tried to back up all 500gigs and only ended up backing up 200gig, because some files were "locked".  How can I back up these "locked" files?  Thank you.

---

### Post by queazy03 on 2014-09-03
Ok, here are some screenshots of what I mean. 


  [http://imgur.com/AxvOVM3](http://imgur.com/AxvOVM3)


  When I use that bootup CD that creates a temporary OS based off of  LinuxMint, I get a "locked" symbol over some folders and I get denied  permission to copy files.  In the end I thought I had backed up  everything, but when I double checked, I had only backed up 40% of all  files because the rest were denied in the same fashion as in this screen  shot.  Help!  What can I do to back up all the files?  Thank you.

---

### Post by sudodus on 2014-09-03
I'm not sure why and how those folders and files are locked. Maybe it is a 'permissions' issue. In that case you can do the backup with superuser privileges (gksudo for GUI application programs).

It is risky with sudo, because you can easily destroy important files without intention, but if you are careful it should be OK. So try like this.

I think Xubuntu has the file browser Thunar, so in a terminal window run this command:

```
gksudo thunar &
```

---

