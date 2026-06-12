---
title: "Really need some help..."
date: 2008-02-01
forum: General Help
---

### Post by aero528 on 2008-02-01
Ok, i am a noob at using Linux, so excuse my ignorance with some things.  I am running Kubuntu 7.10.  I have been having some varies problems, but some iv fixed from searching and some i think i'v just made worse.  Heres my main problem.  I was trying to install wine, but i think i added the repository wrong.  My source.list file in my /etc/apt folder looks like this....

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
[http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

The last line is whats giving me the problem.  Whenever I open adept manager I log in, and then it gives me this error....

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

If I try to run apt-get update in the terminal I get this error...

E: Type 'http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list' is not known on line 45 in source list /etc/apt/sources.list

Any ideas on what I can do?  If you guys think you need any other things to help figure it out, tell me, i'll do my best.  Is there any way I can just revert to total defaults and start over?  Thanks in advance for any and all help, and sorry i'm such a noob!  I love kubuntu,  but this is getting way out of my leage.  Also, is there any place I can get a crash coarse on using ubuntu?  I'v done some computer programing so I can get around in the console ok, but I still have trouble.  Again, thanks!

---

### Post by Rocket2DMn on 2008-02-01
Delete the line you currently have for wine, then follow the short directions on this page from wine - [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
The command "sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list" is run in terminal.
Don't forget to run update afterward (before upgrading/installing anything)
```
sudo apt-get update
```

---

### Post by aero528 on 2008-02-01
Ok, I go into the source.list file and I try to delete the line, but when I try to go and save it, it gives me this error....

The document could not be saved, as it was not possible to write to file:///etc/apt/sources.list.
Check that you have write access to this file or that enough disk space is available.

I know I have more than enough space in the partition(about 120GB).  The first thing I tried to do when installing wine, was to follow those exact instructions, but they didn't work for me.  Everything went fine, but the program just didn't install for some reason.  I updated before and after I tried to install it.  Thanks for the really quick reply.

---

### Post by Rocket2DMn on 2008-02-01
This file has to be edited with root permissions.  I thought you knew this because it looked like you had edited the file already, that's my bad assumption, sorry.
In Kubuntu* (not Ubuntu with GNOME, hehe)
```
kdesu kate /etc/apt/sources.list
```

---

### Post by aero528 on 2008-02-01
Thats not a problem...like I said, I really don't know what i'm doing, but thanks for the help!  If I run the code you gave me, I get this error....

The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found

If I run just sudo gedit /etc/apt/sources.list(because i'v seen everything else run with just sudo.....I really dont know).  If I try to run sudo apt-get install gksu, I get the same error telling me this...

E: Type 'http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Any ideas about that?  Like I said, i'm sorry i'm so new at this, but I guess you have to start somewhere...

---

### Post by Rocket2DMn on 2008-02-01
Yeah I noticed youre using KDE, check my fixed post.

---

### Post by aero528 on 2008-02-01
Gotcha, ok, well now it gives me this error when I run that code...

X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I have honestly no clue whats going on...

---

### Post by Lord Illidan on 2008-02-01
Is it an error or a warning? Does kate still come up, or does the whole thing crash with those words?

---

### Post by aero528 on 2008-02-01
Kate does not come up, but the terminal doesn't crash.  It just gives me that message and does nothing else.

---

### Post by Lord Illidan on 2008-02-01
Try using sudo instead :

sudo kate /etc/apt/sources.list

Also, you're not using 7.10. Those entries in your sources.list indicate feisty, not gutsy.

---

### Post by aero528 on 2008-02-01
Using sudo worked, I got the line deleted.  You guys are amazing.  I got wine installed.  Your right, i'm running 7.04, Feisty.  That would be good to know.  I thought I downloaded 7.1, but I guess not.  Thanks a ton guys!

---

