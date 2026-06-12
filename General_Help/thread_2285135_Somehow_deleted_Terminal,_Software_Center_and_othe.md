---
title: "Somehow deleted Terminal, Software Center and others"
date: 2015-07-03
forum: General Help
---

### Post by Xayide on 2015-07-03
My Ubuntu version is 14.04 LTS.
I was trying to install Python from the terminal, and I did as told here:
[http://askubuntu.com/questions/101591/how-do-i-install-python-2-7-2-on-ubuntu](http://askubuntu.com/questions/101591/how-do-i-install-python-2-7-2-on-ubuntu)

I know ubuntu comes with Python already installed but I wanted the Python command line to test some things.
The thing is that suddenly, from my leftmost menu bar, my Terminal Icon disappeared, as well as the Software Centre, Terminator, Reddit, Software Updates... This already happened once, and I don't know how I did it (maybe trying to install Python too or maybe just touching things i shouldn't). Last time I just shutdown my system and booted it up back, but when it booted nothing appeared: not the left menu bar, nor the uppermost menu either, nothing, just the desktop with a shortcut there.  This time I couldn't find my Terminal anywhere either, but I managed to open Xterm and perform:
$ sudo apt-get --purge gnome-terminal 
and then
$ sudo apt-get install gnome-terminal
as well as 
$ sudo apt-get install software-center
Now I have my Terminal and my software Center back, but I don't know if my system got corrupted or anything! Software Center is telling me to reboot the laptop, but I'm afraid of what it comes when it boots back! How can I know if the system got corrupted or something is failing?
Please help! I'm a total noob and I don't know what to do!
Thank you in advance!

---

### Post by v3.xx on 2015-07-03
Ubuntu 15.04; python version 2.7.9-1 is in the software center.  Why use an older version?  Did you have an existing python version already installed?

Consider using a testing platform instead of your production install.  A virtual machine (virtualbox) can be a big help.

Whats going to happen when you reboot?  Don't know.

[http://packages.ubuntu.com/vivid/python](http://packages.ubuntu.com/vivid/python)

---

### Post by ian-weisser on 2015-07-03
> **Xayide said:**
> My Ubuntu version is 14.04 LTS.
I was trying to install Python from the terminal, and I did as told here:
[http://askubuntu.com/questions/101591/how-do-i-install-python-2-7-2-on-ubuntu](http://askubuntu.com/questions/101591/how-do-i-install-python-2-7-2-on-ubuntu)

Oh, dear.
Don't do that. It breaks your system...as you have discovered.
Which of those three answers did you follow?


> **Xayide said:**
> I know ubuntu comes with Python already installed but I wanted the Python command line to test some things.

All versions of Python, including the *two* you already had installed on your Ubuntu system, include the 'Python command line' (also known as the *interpreter*).


> **Xayide said:**
> The thing is that suddenly, from my leftmost menu bar, my Terminal Icon disappeared, as well as the Software Centre, Terminator, Reddit, Software Updates... This already happened once, and I don't know how I did it (maybe trying to install Python too or maybe just touching things i shouldn't). 

That is expected behavior when you replace a version of Python that those parts of the system expect.


> **Xayide said:**
> Please help! I'm a total noob and I don't know what to do!

You have two options:
1) You can try to undo the damage - remove the older version of Python, and restore the version of Python your system needs to function properly. It's not difficult for an experienced user, but it does require a bit of terminal-fu, and can take a few hours (or days) if you need much online help with the process.
2) You can backup your data and reinstall. This is rather overkill for such a repair...but it will fix the problem, and takes only an hour or so.

Which option do you prefer?

---

### Post by Xayide on 2015-07-03
> **ian-weisser said:**
> Oh, dear.
Don't do that. It breaks your system...as you have discovered.
Which of those three answers did you follow? 

I followed the first answer, the one chosen as best.

> **ian-weisser said:**
> 

When from the Terminal I type 'python' am I accessing the Python Interpreter? 


[QUOTE=ian-weisser;13314643]
That is expected behavior when you replace a version of Python that those parts of the system expect.


Why does that happen? What has the menu and the graphical environment to do with python?


> **ian-weisser said:**
> 
You have two options:
1) You can try to undo the damage - remove the older version of Python, and restore the version of Python your system needs to function properly. It's not difficult for an experienced user, but it does require a bit of terminal-fu, and can take a few hours (or days) if you need much online help with the process.
2) You can backup your data and reinstall. This is rather overkill for such a repair...but it will fix the problem, and takes only an hour or so.

Which option do you prefer?

I didn't know how to remove the version I installed as i didin't know where it was saved and without access to the terminal it was harder for me. I already had a backup so reinstalling Ubuntu was pretty easy (overkill as you say, but I'm pretty much a noob and don't know troubleshooting techniques. 

I would really appreciate some tips to avoid doing these things again and/or some good tutorials that show me how linux works (I have a couple tutorials I'm currently reading to start understanding Linux, learning commands and files and stuff, but any help and explanation will be appreciated!

---

### Post by ian-weisser on 2015-07-03
> **Xayide said:**
> When from the Terminal I type 'python' am I accessing the Python Interpreter?

Exactly. Examples:
```
$ python             ## Runs the interactive Python 2.7 interpreter
$ python something   ## Runs the 'something' script using (non-interactive) Python 2.7
$ python3            ## Runs the interactive Python 3.4 interpreter
$ python3 something  ## Runs the 'something' script using (non-interactive) Python 3.4
```

Of course, previous versions of Ubuntu used Python 3.1 and 3.2, and future versions will use 3.5 and higher.


> **Xayide said:**
> What has the menu and the graphical environment to do with python?
Some elements may be written in Python, or may depend upon other software written in Python.

One example: Software Center depends upon a specific version of Python. When you replaced that version, you broke Software Center.



> **Xayide said:**
> I would really appreciate some tips to avoid doing these things again and/or some good tutorials that show me how linux works (I have a couple tutorials I'm currently reading to start understanding Linux, learning commands and files and stuff, but any help and explanation will be appreciated!

I'm glad you got your problem sorted one way or another.
The basic* concepts *of a Debian-based distribution like Ubuntu are pretty simple. In this case, the concept is "It's included in the default install already." Lots of cool things are.

That Askubuntu question is misleading. It explains how an expert could upgrade to the latest bleeding-edge release of Python before it gets packaged and added to the Ubuntu repositories. Handy for skilled and experienced early-adopters and testers and packagers; terrible for you.

---

### Post by Xayide on 2015-07-03
Thank you so much! This was so helpful! I'll try to download everything I can from the Software Center whenever possible and not mess that much with the terminal!

---

### Post by mc4man on 2015-07-03
You were following a 2+ yr. how-to, usually not a good idea when dealing with specific sources.
In this case if you followed the first post it would have been a checkinstall install, somewhat lucky as the package - "python" would be updated back to the current 14.04 version. 
you may have lost some additional things but they can be re-installed if you find something missing now that you are back to the 14.04 version of the python package

(the checkinstall package would have been python (2.7.5-1), trusty uses 2.7.5-5ubuntu3 which is what you probably now have.
you could ck. that with 
```
apt-cache policy python
```
A quick look suggests around 90 packages could have been affected, time will tell there. Maybe run this to ck on some - 
```
sudo apt-get install ubuntu-desktop
```

---

