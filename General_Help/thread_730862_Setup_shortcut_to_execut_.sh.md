---
title: "Setup shortcut to execut .sh"
date: 2008-03-21
forum: General Help
---

### Post by the_nite_owl on 2008-03-21
I just installed Aventail for Linux in Gutsy.
How can I setup a shortcut on my desktop to launch the startctui.sh file so I do not have to open up a terminal window and do it manually every time?

Thanks.

---

### Post by cmnorton on 2008-03-21
Right-click your mouse on a blank area of your desktop and select Create Launcher. Then you've got to play around with it from there as to what this program does and whether or not it's going to run in graphical or xterm mode.

Also, I'm assuming Aventail chmod'd this shell script with executable bit turned on, and as which user does this shell script need to run?

---

### Post by the_nite_owl on 2008-03-21
> **cmnorton said:**
> Right-click your mouse on a blank area of your desktop and select Create Launcher. Then you've got to play around with it from there as to what this program does and whether or not it's going to run in graphical or xterm mode.

Also, I'm assuming Aventail chmod'd this shell script with executable bit turned on, and as which user does this shell script need to run?

I was playing around with Create Launcher and was not getting anywhere.
Would I have to include a command like /bin/bash to tell it what to execute the .sh file with?
I tried a bunch of variations that did not work.

I think you hit the issue though, the file may not be set to run by anyone.  The installer placed a shortcut to the .sh file in the /usr/bin folder so it could be launched from anywhere but it may not have changed rights for executing the file.
So far I have always launched it using sudo /bin/bash startctui.sh

I am somewhat of a newbie and not real familiar with all of the shell commands yet.
Would I have to change the rights of the shortcut in /usr/bash or the file wherever it resides, or both?
And what parameters would I use with the chmod command to set it up for?

Thanks for the info.

---

### Post by Triggerhapp on 2008-03-21
in terminal ```
sudo chmod a+x thefileyouwant
```
This means that it will be allowed to run as a program, then, make the launcher run it (Just add the whole path/filename.sh to command) this should do it.

---

### Post by the_nite_owl on 2008-03-21
> **Triggerhapp said:**
> in terminal ```
sudo chmod a+x thefileyouwant
```
This means that it will be allowed to run as a program, then, make the launcher run it (Just add the whole path/filename.sh to command) this should do it.

That did it.
I had to use a command line of:  /bin/bash /usr/local/Aventail/startctui.sh

What is up with the script processor?  Why do I need to specify what to execute with each time, shouldnt it default to one already on the system?  Or does something else need configuring to get that to work?

I know that when I was trying to install Aventail the script processor it defaults to using was not working and I found a post saying to use /bin/bash instead and that allowed it to run.
It just seems to me that a script file should already be setup with a script processor.
I'm still fairly new at Linux though so I may be missing something.

I was running 64bit Feisty LAMP server for a long while but had too many problems making non 64bit apps work and when I tried installing the 32bit SSL support so Aventail could run it broke my system and I decided to give up 64bit.
Now I have to go through all of the Apache, MySQL and Samba setup again which is depressing but I did it once so....

Thanks for the help.  I had been wondering how to go about this for a while.

---

### Post by Triggerhapp on 2008-03-21
oh, you didnt tell the file how to run...
on the first line add ```
#!/bin/sh
``` That tells the computer what script language it is
If you write a perl script use ```
#!/usr/bin/perl
``` so on so forth.

If you tell it how this script runs, you wont need the "/bin/sh" in front of the command

---

