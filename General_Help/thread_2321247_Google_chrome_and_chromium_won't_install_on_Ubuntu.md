---
title: "Google chrome and chromium won't install on Ubuntu 16.04"
date: 2016-04-21
forum: General Help
---

### Post by JCAPER on 2016-04-21
Just did a clean install of Ubuntu 16.04 and started installing my main applications. However, it seems that both Chrome and Chromium won't install.

I downloaded the .deb version of chrome and tried to install it normally (double click), but Ubuntu software didn't install it. After that, I tried to use the command line "sudo dpkg -i google*", and it failed again. According to the error, it seems it needs a package called "libappindicator1". I googled that package but didn't find any way to install it.

I also tried to install Chromium from Ubuntu Software, but just like Chrome, it also fails to install. Any solutions to this problem?

---

### Post by RobGoss on 2016-04-21
I'm running 16.04 and was able to install using the Software center, 

I had to click on the install tab about twice but finally it was able to install successful

The 32-bit Google Chrome is no loner support for Ubunt Linux

---

### Post by deadflowr on 2016-04-21
Try:
```
sudo apt-get install -f
```

---

### Post by JCAPER on 2016-04-21
Noice, deadflowr solution worked perfectly! :D

Thank you both for your time, you're awesome!

---

### Post by hunterkasy on 2016-04-21
I try to install google chrome from a deb file, and it won't install, using the ubuntu software

---

### Post by VE6EFR on 2016-04-21
> **hunterkasy said:**
> I try to install google chrome from a deb file, and it won't install, using the ubuntu software

It's not installing for me either. Maybe there is an issue with the file that will be addressed in a day or so.

Update - I was able to get Chrome to install using the command line - [COLOR=#111111][FONT=Consolas]sudo dpkg -i google-chrome-stable_current_amd64.deb[/FONT][/COLOR]

---

### Post by RobGoss on 2016-04-22
> **JCAPER said:**
> Noice, deadflowr solution worked perfectly! :D

Thank you both for your time, you're awesome!



Glad you for the fix for it, Would you mind marking this thread as Solved you can use the Thread Tool tab at the top of this post

---

### Post by Paper Pusher on 2017-01-18
I have tried the previous suggestions; and nothing has worked.  More ideas?

---

