---
title: "Problem logging into Gnome session"
date: 2007-03-03
forum: General Help
---

### Post by VivaUbu on 2007-03-03
Please help, I do not know how to do much in the terminal window, just the basic stuff.

I have been happily using Ubuntu 6.06 for a few months on my Toshiba Satellite laptop (wireless with a Belkin USB wifi dongle, couldn't make a card work).and today, trying to login into my Gnome session it returned this error message:

[FONT="Courier New"][SIZE="2"]"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."[/SIZE]
[/FONT]

I am the "administrator", argh!  :-? . So I tried to login using my wife's account and the same thing happened.

I can launch Ubuntu in a command line no problem, in fact, I get the Ubuntu GUI screen and the message comes up in a GUI interface and all. The problem is that I don't know what to do once I am in the command line, like for example, where do I navigate to in order to start erasing files in case there is no more disk space or how to check for disk space or what else to do in order to keep working in Ubuntu. What I really don't want to do is to have to reinstall as if I was back in Microsoft world.

Thank you very much for any help I can get.

---

### Post by taurus on 2007-03-03
Can you post the output of this command from a prompt after you have logged into a console?  I think you are running out of disk space.

```
df  -h
```

---

### Post by VivaUbu on 2007-03-04
Thanks Taurus, this is the output for "df -h" :

Filesystem   Size   Used   Avail   Use%   Mounted_on
/dev/hda2     17G   16G        0   100%   /
varrun        248M    12K   248M      1%  /var/run
varlock       248M   4.0K   248M      1%  /var/lock
udev          248M   104K   248M      1%  /dev
devshm      248M        0   248M      0%  /dev/shm
lrm             248M    19M   230M      8%  /lib/modules/2.6.15-28-386/volatile

Sorry for the figures being bunched up, don't know how to make tables in this here message posting interface, but empty spaces separate columns. First line does say:

Avail 0
Use% 100%
Mounted on /

Thing is I know I have a whole bunch of Gigs in my Trash Bin I could immediately delete if only I could get to it.

---

### Post by taurus on 2007-03-04
> **VivaUbu said:**
> 
Thing is I know I have a whole bunch of Gigs in my Trash Bin I could immediately delete if only I could get to it.

Are they in your $HOME directory?  You can run this command to at least clean out your cache to give you some space.

```
sudo aptitude clean
```
Now, what's the output of this command then?

```
ls -la ~/.Trash
```

---

### Post by VivaUbu on 2007-03-04
Quote:
Are they in your $HOME directory? You can run this command to at least clean out your cache to give you some space.

Code:

sudo aptitude clean

---------------
:) 
Magic! It worked! I was able to login into Gnome and empty out my Trash Bin. Thank you, thank you, thank you.

:shock: 
All Hail Mighty Taurus!
Master of the Console!
Lord of the Command Line!

PS By the way, the"ls -la ~/.Trash" command returned "no such file or directory"

---

### Post by taurus on 2007-03-04
How about

```
du -h ~
```

---

### Post by VivaUbu on 2007-03-04
Wow! du-h returns a whole big list of files with their sizes. Now I see where the Trash Bin lives. At my Home as .Trash (no wonder I couldn't see it). So next time I just have to navigate there to empty. 

Your "aptitude clear" command did wonders though. 

And it will not happen again! I am leaving some empty disk from now on.

Many thanks again.

---

### Post by taurus on 2007-03-04
It's a good idea to run this command once in a while to check on the disk space.  ;) 

```
df -h
```

---

### Post by VivaUbu on 2007-03-06
Great. Now I have a collection of useful commands to try out from time to time.

Thanks so much for taking the time to help us solve problems.

All the best

---

