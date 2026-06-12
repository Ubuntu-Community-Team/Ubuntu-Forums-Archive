---
title: "Upgrading python"
date: 2007-04-07
forum: General Help
---

### Post by metroknight on 2007-04-07
I'm now running Ubuntu 6.10/WinXP dual boot and I have python and wxpython installed. I need to find out how to upgrade both of them. I've been looking and reading the forums but I don't understand the instructions that well. I think I upgraded the wxpython but not python. If I did that, Do I need to unistall both and reinstall them?

---

### Post by ssavelan on 2007-04-07
> **metroknight said:**
> I'm now running Ubuntu 6.10/WinXP dual boot and I have python and wxpython installed. I need to find out how to upgrade both of them. I've been looking and reading the forums but I don't understand the instructions that well. I think I upgraded the wxpython but not python. If I did that, Do I need to unistall both and reinstall them?

Have tried apt?

sudo -s -H
apt-get update
apt-get upgrade


You could also upgrade your repos to feisty and run the above often,

---

### Post by metroknight on 2007-04-08
I'll try that as soon as I get a chance. How do you upgrade the repos?

---

### Post by ssavelan on 2007-04-08
> **metroknight said:**
> I'll try that as soon as I get a chance. How do you upgrade the repos?

you may want to backup the sources.list... but I don't see much point

sudo gedit /etc/apt/sources.list

replace everything in the file with:

## Feisty Fawn - Officials Repos

## Base
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted

## Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted

## Security
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main multiverse restricted

## Proposed
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted

---

### Post by metroknight on 2007-04-08
I'm probably going to wipe and reload the system since I screwed up other stuff also. I might also download and try the Feisty version also.

---

### Post by ssavelan on 2007-04-08
> **metroknight said:**
> I'm probably going to wipe and reload the system since I screwed up other stuff also. I might also download and try the Feisty version also.

I recommend setting up at least two Ubuntu partitions so you can really experiment.  If you crash one you can move all files onto the other and reinstall the dead one.  I did a few times over a couple of weeks and I learned a lot.  I can now set-up everything i want very quickly.

Keep the faith, you'll get it.  It's always nice to start from a fresh install.  The official release of Feisty is only 11 days away!  You might install a version of Feisty and an Edgy.  I do recommend going x86 generic even if you have a 64-bit proc.  Many things are harder to get working on the 64-bit.

You can check out SAGE (from washington.edu)

[http://modular.math.washington.edu/sage/]("http://modular.math.washington.edu/sage/")

It is a great collection of python modules that is packaged into a sweet math programs.

you can ./sage filename.py

and use a lot of the higher level functions that 

python filename.py 

wouldn't nec. give you.

It has great interactive command line stuff....

anyhoo.......

---

### Post by metroknight on 2007-04-08
Thanks for all the info. I just reinstalled my 6.06 and I'm in the process of updating it. It will take me a while but I will have it set back up to the way I liked it. If I can get acouple programs to run in Ubuntu then I will ditch my dual boot for straight ubuntu.

---

### Post by ssavelan on 2007-04-08
> **metroknight said:**
> Thanks for all the info. I just reinstalled my 6.06 and I'm in the process of updating it. It will take me a while but I will have it set back up to the way I liked it. If I can get acouple programs to run in Ubuntu then I will ditch my dual boot for straight ubuntu.

I have been running Feisty for a couple of weeks and I think that it is superb, btw.

What other programs are you trying to get running?

---

### Post by metroknight on 2007-04-08
I'm a RPGer and use Openrpg (a virtual pen and paper table setup) to game with. The latest version of it is dependent on python2.5 and wxpython 2.8.3 to run.

I also use PrintMaster for my sons schoolwork but as long as I have a good photo editor or graphics program to work with, I can skipp that program.

I think those are the main ones off the top of my head.

---

### Post by ssavelan on 2007-04-09
> **metroknight said:**
> I'm a RPGer and use Openrpg (a virtual pen and paper table setup) to game with. The latest version of it is dependent on python2.5 and wxpython 2.8.3 to run.


Well, you are going to be in luck.  You should definitely upgrade to Feisty repos... I think that my python was 2.3 or 2.4 when I was in Edgy.  Now:

bio@bio:~$ python
Python 2.5.1c1 (release25-maint, Apr  6 2007, 22:02:36) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

They have been sending a bunch of updates for Python recently.  A lot of Python (most?) is coded from within GNU/Linux.  The openrpg thing should be very well supported for ubuntu I would imagine.  Python is awesome!

Plus+  Audio/video/picture/media apps are getting better and better.  I think some great stuff is coming out.

[URL="http://ubuntuforums.org/showthread.php?t=293798&highlight=jahshaka+edgy"]

the problem might be that there are so many good open source alternatives.....
http://ubuntuforums.org/showthread.php?t=293798&highlight=jahshaka+edgy[/URL]

---

### Post by metroknight on 2007-04-09
I'll download 7.04 when it is released as stable. It should be just what I need to kick the windows habit.

---

### Post by ssavelan on 2007-04-09
> **metroknight said:**
> I'll download 7.04 when it is released as stable. It should be just what I need to kick the windows habit.

Just upgrade your repos now.  The servers are really fast b4 the storm.

---

### Post by metroknight on 2007-04-14
Well I just upgraded to 7.04 and so far so good. I screwed up my display as usual but I got some help and fixed it. Now to start testing things out and see what is broken or not.

---

### Post by ssavelan on 2007-04-14
to check your python version, you can just run:

python

in the terminal.  I usually have a couple of versions installed.  I'm not sure that it will default to the most updated.  If you have trouble, it may help to remove the earlier versions of python; i'm not sure.  Let me know how it turns out.

sos

---

### Post by metroknight on 2007-04-14
> **ssavelan said:**
> to check your python version, you can just run:

python

in the terminal.  I usually have a couple of versions installed.  I'm not sure that it will default to the most updated.  If you have trouble, it may help to remove the earlier versions of python; i'm not sure.  Let me know how it turns out.

sos

I have 2.5 listed and is the default. I got the wxpython to update to the latest but I'm having problems with getting a python program running. I posted the problem at the gaming site but maybe you might be able to shed some light on it also.

My other site post :

I have python 2.5 and wxpython 2.8.3 installed. I've downloaded the zipped version of openrpg 1.7.2. I extracted all the folders into an openrpg1 folder in my home folder.

This is the system info :

OpenRPG System Info 04-14-07
OpenRPG Version: 1.7.2
OpenRPG Build: 070226-00
Python: 2.5.1c1 (release25-maint, Apr 12 2007, 21:00:25)
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)]
wxPython Version: 2.8.3.0
Platform: Linux-2.6.20-15-386-i686-with-debian-4.0

Every time I tried double clicking on the start.py, it brings up an error about openrpg not being able to find critical files and asks for me to find the openrpg1 directory. It opens up a search window. When I go to the openrpg1 folder in my home folder and click on ok it does nothing. I double-click on the start.py again thinking that it might have fixed it and it goes through the process again.

What am I doing wrong?

---

### Post by ssavelan on 2007-04-14
run start.py in the terminal by navigating to the directory it is in:

cd /where/the/file/is/

Then run the script with python:

python start.py

You may get error messages, but they will be a lot more helpful than what you get by double clicking.  You may have some unmet dependencies or something.  You may have to run with an arguement like

python start.py install

you can look at the file in a text editor... may be some documentation in there:

gedit start.py

Get used to the terminal.  I recommend throw-back florescent green on black.

---

### Post by metroknight on 2007-04-14
I will try that later since it is family time now. Thanks for you help.

---

### Post by metroknight on 2007-04-14
> **ssavelan said:**
> run start.py in the terminal by navigating to the directory it is in:

cd /where/the/file/is/

Then run the script with python:

python start.py

You may get error messages, but they will be a lot more helpful than what you get by double clicking.  You may have some unmet dependencies or something.  You may have to run with an arguement like

python start.py install

you can look at the file in a text editor... may be some documentation in there:

gedit start.py

Get used to the terminal.  I recommend throw-back florescent green on black.

Thank you, between you advice and one of the programmers of openrpg, I got it working. This makes a big step towards leaving microsoft permently.

Again thank you all for the help you gave.

---

