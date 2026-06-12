---
title: "unable to use su"
date: 2007-07-24
forum: General Help
---

### Post by clinto on 2007-07-24
I'm trying to run a script that installs xdvdshrink but it requires that it has root privileges. Does "su" not work in Ubuntu, or do you have to add your account to the sudoers list to be able to use it? I want to add the su command into the install.sh script. Otherwise, I don't know how else to run it.

---

### Post by needtolookatascreenshot on 2007-07-24
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by kerry_s on 2007-07-24
sudo su

---

### Post by upthelum on 2007-07-24
Try sudo -i which will then ask for your root password.

---

### Post by clinto on 2007-07-24
> **needtolookatascreenshot said:**
> No, su doesn't work out of the box and you shouldn't enable it.

Why not simply use sudo?

because, I would have to write sudo in everywhere it was needed, and I'm not sure where it would be needed. I don't totally understand script, since it seems to use different commands. I thought at first that it just used normal commands in a sequential order. I have some basic programming skills(VERY basic... as in... Q... and HTML), I under how tags work, like the if and fi, but there are a few different other tags I don't understand. It would take me forever trying to figure out where sudo goes before each line it needed it.

sudo su and sudo -i. Thanks guys. I'll try those.

---

### Post by clinto on 2007-07-24
Okay, apparently, that isn't going to work. It asks me for my password and then gives me the prompt. I have to figure out a way to start the script in a shell that already has root privileges. Is there a way I can open the script using command line with sudo? I'm not sure that would work anyways. Maybe I have to sign on in recovery mode?

Here's the code(I hope I'm not infringing by posting this, if I am, tell me a soon as possible and I'll delete it):

```

#!/bin/bash

clear
echo "DVDShrink installer v1.1"

# run this script as root

if [ $UID -ne 0 ]
then
   echo
   echo "You have to be root to run this installer."
   echo
   read
   exit
fi

function testistring {
   INP=`echo $1 | tr 'a-z' 'A-Z'`
   TST=`echo $2 | tr 'a-z' 'A-Z'`
   VAR=${INP%%$TST*}
   if [ "$VAR" = "$INP" ]; then echo 0; else echo 1; fi 
}

echo
echo "Checking for dependencies"
BAD=0
which tccat > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   Transcode not installed or utilities not executable"; ((BAD++)); fi
which mplex > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   MJpegtools not installed or utilities not executable"; ((BAD++)); fi
which subtitle2pgm > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   SubtitleRipper not installed or utilities not executable"; ((BAD++)); fi
which mkisofs > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   Mkisofs not installed or utilities not executable"; ((BAD++)); fi
which dvdauthor > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   Dvdauthor not installed or utilities not executable"; ((BAD++)); fi
which growisofs > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   DVD+RW-tools not installed or utilities not executable"; ((BAD++)); fi
which gocr > /dev/null 2>&1
if [ $? -ne 0 ]; then echo "   GOcr is not installed or utilities not executable"; ((BAD++)); fi

if [ $BAD -gt 0 ]; then
   echo
   echo "   One or more of the utilities that DVDShrink requires are not installed or"
   echo -n "   are not executable. Continue the installation? (y/n)   "
   read YN
   if [ -z $YN ]; then exit; fi
   if [ `testistring $YN 'n'` -eq 1 ]; then exit; fi 
fi

echo
echo "Installing DVDShrink..."   
echo "--------------------------------------------"

echo
echo "Removing old version from /usr/local/bin if it exists"
for FILE in dvdsfunctions dvdshrink copydvd xdvdshrink.pl; do
   if [ -f /usr/local/bin/$FILE ]; then
      rm -f /usr/local/bin/$FILE
   fi
done

echo
echo "Creating application directories if needed"
for DIR in doc applications; do
   if [ ! -d /usr/share/$DIR/dvdshrink ]; then
      mkdir -p /usr/share/$DIR/dvdshrink
   fi
done

echo
echo "Installing files"
cp usr/bin/* /usr/bin
cp -R usr/share/* /usr/share

echo
echo "Removing rc files if they exist"
for DIR in `ls /home`; do
   if [ -f /home/$DIR/.dvdshrinkrc ]; then
      echo "   Found rc file in /home/$DIR... removing"
      rm -f /home/$DIR/.dvdshrinkrc
   fi
done

echo
echo -n "Checking for perl-gtk2   "
VAR=`find /usr -name Gtk2.pm 2> /dev/null`
if [ -z $VAR ]; then
   echo "Not found!"
   echo "   perl-gtk2 not found..."
   echo "   If you want the graphical 'front-end' to the scripts you'll need"
   echo "   to install perl-gtk2."
   echo
else
   echo "Found!"
fi

echo
echo "DVDShrink must be reconfigured the next time it's run"
echo


```

---

### Post by kuja on 2007-07-24
Why not run the script itself with sudo -- ie: sudo ./somescript.sh

---

### Post by clinto on 2007-07-24
> **kuja said:**
> Why not run the script itself with sudo -- ie: sudo ./somescript.sh
That's what I was looking for. I wasn't sure how to run a script from command line. However, when I tried this, it just sat back at prompt doing nothing. :/

```

bott@bott-desk:~$ cd dvdshrink/
bott@bott-desk:~/dvdshrink$ ls
install.sh  install.sh~  usr
bott@bott-desk:~/dvdshrink$ sudo ./install.sh 
Password:
root@bott-desk:/home/bott/dvdshrink# 

```

Does no one know how to run a script using a shell? For there being 800 some people on at one time, it sure seems hard to get different input here. I know a lot of people have the "go google it yourself" attitude toward such inquiries, but I'm just trying to figure this out as quickly as possible. I have about 5 different things going on at the same time. I have a test coming up at the end of the month that I need to study for. I need to rip these dvds so I can get them back to... *ahem* my shelf. I've been pulling my hair out for months trying to figure out how to backup dvds using linux. I use dvdshrink, dvdfab, and deepburner for windows and they work great. I just can't figure out why any application I use under linux will NOT work properly.

---

### Post by doodaa on 2007-07-24
sudo -s option work?

---

### Post by Nekiruhs on 2007-07-24
Do this. ```
echo "alias su='sudo -s'" >> ~/.bashrc
``` Log out and log in. Su now works.

---

### Post by Mr. C. on 2007-07-24
Please stop the rant and self-pity, and focus on helping us help you.

The stock Ubuntu system makes creating a root shell unavailable by default.  It really doesn't matter, because you are provided with a more accountability friendly, and configurable alternative sudo.  Here are some commands, and explanations as to their function:
```

sudo -s                         # creates a root shell
sudo ./install.sh               # will fail if install.sh is not executable
sudo /full/path/to/install.sh   # will fail if install.sh is not executable
sudo bash ./install.sh          # will work regardless of install.sh execute perms

```

Your command and output example you show would have cleared the screen, or posted an error "sudo: ./install.sh: command not found".  Therefore, we can infer that the script "install.sh" that you posted is different than the one actually run via your "sudo ./install.sh" command.  The backup file install.sh~ supports the theory that you have modified the install.sh file.

Get in the habit of reading the man pages for command line commands!

```
man sudo
```

MrC

---

### Post by clinto on 2007-07-24
> **Nekiruhs said:**
> Do this. ```
echo "alias su='sudo -s'" >> ~/.bashrc
``` Log out and log in. Su now works.

You'd meant to use this in a terminal shell and not incorporate it into the script right? That writes what is in the parenthesis into the .bashrc file. I don't really understand what the .bashrc file is for, but I can figure that one out on my own. I just would like a general explanation of what I have done actually does.

*edit*
Ooooh, I see. That's interesting. I still don't understand what sudo -s does though. Couldn't I just write sudo -s into the script then, instead of writing it to my .bashrc file?

*edit*
Wow, that's weird. It will let me use su in command line, but when I write it into the script, it asks me for my password, then it gives me an authentication failure.

```

DVDShrink installer v1.1
Password: 
su: Authentication failure
Sorry.

You have to be root to run this installer.

```

@Mr. C
Sorry, I didn't see you there. Thank you, that clears up A LOT. I'd read the man page, I do any time I don't understand something, but very often I don't understand what the man page is saying. They seem to be written in a way that most only understand if they already have a good understanding of what is being discussed. It's very technical and I haven't learned enough to understand exactly what is being stated in the man pages. But you've translated it for me very well.

If what you say is true, I don't understand why sudo ./install.sh didn't work. I was in the correct directory and the file *is* executable. I'll try the sudo bash.

(sorry if I was ranting. I've been posting here for some time and it seems that more often than not I get only a couple posts from people who really don't know what they're talking about. I try to figure things out on my own as much as I can before going insane... most of the time)

---

### Post by clinto on 2007-07-24
I think it worked.

```

bott@bott-desk:~$ cd dvdshrink/
bott@bott-desk:~/dvdshrink$ ls
install.sh  install.sh~  usr
bott@bott-desk:~/dvdshrink$ sudo bash ./install.sh

DVDShrink installer v1.1


Checking for dependencies
   MJpegtools not installed or utilities not executable

   One or more of the utilities that DVDShrink requires are not installed or
   are not executable. Continue the installation? (y/n)   

```

Thanks again guys. I really appreciate the help. I'll help others once I've gained enough wisdom on such things.

---

### Post by Mr. C. on 2007-07-24
It sounds like you've got things working.

In the future, for better help, show your data, instead of interpreting it. Show how you know the file is executable, for example:

```
ls -l install.sh
pwd
```

Specific data leads to specific diagnosis; speculation leads to poor guesses and inaccurate diagnosis.

MrC

---

### Post by clinto on 2007-07-24
It's tough starting at the bottom. I didn't even know the ls -l command. I've been wanting to get the comptia linux+ certificate by next year, but I have a LONG way to go. Thanks again. I'd be pretty lost without people like you. I know it can be quite nauseating, being depended upon by newbz.

---

### Post by Mr. C. on 2007-07-24
Understood, but you're on your way.  Start with some basics... review the coursework and try some of the homework and labs:

[http://cis68a.mikecappella.com](http://cis68a.mikecappella.com) 

When you are ready, move to

[http://cis68c1.mikecappella.com](http://cis68c1.mikecappella.com)
[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)
[http://cis68c2.mikecappella.com](http://cis68c2.mikecappella.com)

MrC

---

