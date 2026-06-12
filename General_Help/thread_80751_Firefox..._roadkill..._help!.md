---
title: "Firefox... roadkill... help!"
date: 2005-10-22
forum: General Help
---

### Post by MasterXandrex on 2005-10-22
I tried updating firefox using the howto to go from the installed version to the new beta in the tips and tricks section. I now get an error stating...

Cannot launch icon

Details: Failed to execute child process "firefox" (No such file or directory)

whenever I click the launcher... someone please help me fix it... even if I just have to restore the old one... please!

---

### Post by rsankuratri on 2005-10-22
Can you right click on the Firefox icon and see the properties on the basic tab?  See that the command that the script being invoked is right

Also on a terminal type the text given below and hit enter

==========
which firefox
========

---

### Post by MasterXandrex on 2005-10-22
It seems to be right, additionally if I just type firefox in the terminal I get the command not found error.

---

### Post by rsankuratri on 2005-10-22
What is the output of the terminal when you type "which firefox"?

---

### Post by MasterXandrex on 2005-10-22
I get nothing, just a new prompt

---

### Post by rsankuratri on 2005-10-22
Do you know the folder that it was installed in?  Usually it would be /usr/lib/mozilla-firefox

If that is right then have you tried creating a new desktop launcher for that?

If not first search for files and folders in the / folder that match firefox

---

### Post by MasterXandrex on 2005-10-22
I can run firefox if I type

cd /usr/lib/mozilla-firefox
./firefox

thank you for that, but how do I get it to be a normal shell command (I would like to know this for future reference as well)?

---

### Post by rsankuratri on 2005-10-22
Hang on I will tell you how o create a short cut...:)

---

### Post by rsankuratri on 2005-10-22
Click on Applications --> System Tools --> Applications Menu Editor
Select the Internet in the Browser pane (Left side)
If you already have Firefox there.  Right click on the Firefox item in the Right hand side pane and select properties.
Hit the browse button and then navigate to the firefox shell script and close everything.  You should be able to start browsing from the short cut

---

### Post by MasterXandrex on 2005-10-22
No, I made a new launcher icon that works... I want to be able to launch it from shell just using the command "firefox"

---

### Post by phup on 2005-10-22
something like

sudo ln -s /usr/lib/mozilla-firefox/firefox /usr/bin/firefox

should create a link in the /usr/bin to the version in the mozilla-firefox folder

---

### Post by MasterXandrex on 2005-10-22
thanks... that did it

---

### Post by rsankuratri on 2005-10-22
Create a sym link as below
=================
ln -s /usr/lib/firefox /usr/lib/mozilla-firefox/firefox
==================

That sould do it.  

Also put a "%u" after firefox
==============
firefox %u
==============
Hope that helps.  I am a newbee too.  Don't give up;)

---

