---
title: "How to launch Python scripts at boot?"
date: 2008-02-15
forum: General Help
---

### Post by Donshyoku on 2008-02-15
I have a problem, and proposition too!  I have been working on making an SVN installation guide for Elisa Media Center. I have the program and all of its dependencies and plugins installed now, but crash during launch. 

The problem is that I need to launch multiple Python scripts to run in the background before the program will start.  I have 5 scripts that have to run before I can launch the actual application. And some depend on others... I need a way to create a button or script that will then "cd" and launch each python script in order.  I need them all running before I can get it working right and experience the latest!

Not only is this for my new media center, but I also am making a Blogger page for the issue since I know a lot of people (and many on the Elisa forums) looking for an easy way to get this moving on their system as the SVN version is a huge update.

Help me get it running and I'll quote you in the Blogger HOWTO and give some nice links for your blog/homepage/whatever. Promotion is always good, I need the app,and getting Linux/SVN working is all about community.  

Please help!

---

### Post by SpaceTeddy on 2008-02-16
can't you just put the scripts in */etc/rc.local*, which is exactly for the purpose of running user programms at boot time ?

if you have more complicated scripts, i'd suggest you write yourself a little batchfile which exectues everything in order, and then put the call to that file into */etc/rc.local*

**example how one could do it:**
create a directory /etc/boot (must be root for this)
create a file named runPython in that directory with the content
> cd /absolute/path/to/my/scripts 
./run-first-script.py
./run-second-script.py

make the file exectuable with > chmod +x /etc/boot/runPython
last, add the following line to */etc/rc.local*
> /etc/boot/runPython

that should execute about anything at boot time... while runPython can call any script it wants...

This is an ugly hack, but it works.. as far as i know :)

---

### Post by Donshyoku on 2008-02-16
I'll give it a shot here in a bit.  Sounds good in theory to me at least.  I am working now to nail down the order in which scripts to place.  Some depend on others while some aren't dependent.  It's such a headache of trial and error!

Here's a more simple question.  Can I create a custom launcher with multiple commands?  I need a button I can create for each script, but I need to be able to "cd" and "python script.py" each one and Gnome isn't accepting "&&" as an excuse for that.

---

### Post by SpaceTeddy on 2008-02-16
buttons.... yes, you'll need to create a script for each button though. same as before, just put the scripts in your homedir, make them exectuable and then tell a button to launch them

a better way (i think) is if you setup aliases in your .bashrc and do the trial and errors in the command shell. edit your .bashrc for examples... 
NOTE: you need to close and open the terminal to make the changed in the .bashrc to take effect. or you simply run "bash" in your terminal...

ok, gotta hurry (sorry for the short answer)

---

