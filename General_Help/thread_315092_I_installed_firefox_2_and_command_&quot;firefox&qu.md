---
title: "I installed firefox 2 and command &quot;firefox&quot; no longer exists [Resolved for now]"
date: 2006-12-08
forum: General Help
---

### Post by Matt Heath on 2006-12-08
Hi, I'm new at this; sorry if I have the wrong place.

Last night I installed Firefox 2 manually on the Dapper release. I ran "firefox" in the terminal and it started upo fine. Having shut down and restarted my computer, now when I type "firefox"  I get an error message "command not found". When I click the button in the "Applications" menu for firefox I get:
"Could not launch menu item

Details: Failed to execute child process "firefox" (No such file or directory)".

On the other hand, if I do "System>Help>Online Documentaion" it opens up firefox 2 to get it. 

Can anyone help?

---

### Post by earobinson on 2006-12-08
try mozilla-firefox if that dont work try  apropos firefox

---

### Post by aysiu on 2006-12-08
Can you explain what steps you took to "install Firefox manually"?

---

### Post by Matt Heath on 2006-12-08
I get this: 
matt@matt-heath:/$ mozilla-firefox

run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin.


matt@matt-heath:/$ apropos firefox
firefox (1)          - a Web browser for X11 derived from the Mozilla browser
mozilla-firefox (1)  - a Web browser for X11 derived from the Mozilla browser

---

### Post by Matt Heath on 2006-12-08
I downloaded the binary from the mozilla website then follwed some instruction fron a forum (I think here somewhere): The commands I typed were (if i have the right bit of past typing)

matt@matt-heath:/$ cd ~./.mozilla/firefox/*.default 
matt@matt-heath:/$ mkdir ~/Desktop/ffsettings 
matt@matt-heath:/$ cp bookmarks.html cert8.db cookies.tst formhistory.dat hostperm.1 key3.db signons.txt history.dat mimeTypes.rdf ~/Desktop/ffsettings
matt@matt-heath:/$ sudo tar xzvf firefox-2.0.tar.gz -C /opt 
matt@matt-heath:/$ cd tmp 
matt@matt-heath:/$ sudo tar xzvf firefox-2.0.tar.gz -C /opt
matt@matt-heath:/$ sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins  
matt@matt-heath:/$ sudo rm /usr/lib/firefox/plugins/libtotem_mozilla.* 
matt@matt-heath:/$ rm firefox-2.0.tar.gz 
matt@matt-heath:/$ cd 
matt@matt-heath:/$ mv ~/.mozilla/firefox ~/.mozilla/firefox1.x.ubuntu 
matt@matt-heath:/$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
matt@matt-heath:/$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox 
matt@matt-heath:/$ sudo dpkg-divert --divert /usr/bin/mozilla-firefox --rename /usr/bin/mozilla-firefox
matt@matt-heath:/$ sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox


And the ran "firefox" which worked

---

### Post by aysiu on 2006-12-08
[quote=Matt Heath]And the ran "firefox" which worked[/quote] So your problem is now solved?

---

### Post by Matt Heath on 2006-12-08
> **aysiu said:**
> So your problem is now solved?
O NO, sorry.

YESTERDAY it worked. Today it doesn't.

---

### Post by aysiu on 2006-12-08
Maybe the symlink is broken for whatever reason?

Can you try this? ```
cd /opt/firefox
./firefox
``` If that works, we'll work on fixing the symlink.

---

### Post by knight17 on 2006-12-08
Try to re-install it.

---

### Post by aysiu on 2006-12-08
> **knight17 said:**
> Try to re-install it.
That's another approach. If you do decide to follow this route, I'd recommend using the Firefox installation script--it'll save you cutting and pasting that many commands!

Here's the script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Matt Heath on 2006-12-08
> **aysiu said:**
> That's another approach. If you do decide to follow this route, I'd recommend using the Firefox installation script--it'll save you cutting and pasting that many commands!

Here's the script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
Hmmm... I tried to do this, and got "...Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
The following packages have been kept back:
  libruby1.8
The following packages will be upgraded:
  firefox
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.Need to get 0B/7932kB of archives. After unpacking 86.0kB will be used.Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 103953 files and directories currently installed.)Preparing to replace firefox 1.5.dfsg+1.5.0.3-0ubuntu3 (using .../firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mozilla-firefox', which is the diverted version of `/usr/bin/mozilla-firefox'
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.debE: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of firefox-gnome-support: firefox-gnome-support depends on firefox (= 1.5.dfsg+1.5.0.8-0ubuntu0.6.06); however:
  Version of firefox on system is 1.5.dfsg+1.5.0.3-0ubuntu3.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on firefox-gnome-support; however:
  Package firefox-gnome-support is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-gnome-support
 ubuntu-desktop
Previous command did not complete successfully. Exiting."

:( Any more suggestions (I'm very grateful for you all trying btw)

---

### Post by Matt Heath on 2006-12-08
> **aysiu said:**
> Maybe the symlink is broken for whatever reason?

Can you try this? ```
cd /opt/firefox
./firefox
``` If that works, we'll work on fixing the symlink.
This gives:

matt@matt-heath:~/Desktop$ cd /opt/firefox
matt@matt-heath:/opt/firefox$ /firefox
bash: /firefox: No such file or directory

---

### Post by aysiu on 2006-12-08
There's a period before the flash on that last command. Instead of ```
/firefox
``` it should be ```
./firefox
```

---

### Post by Matt Heath on 2006-12-08
> **Matt Heath said:**
> This gives:

matt@matt-heath:~/Desktop$ cd /opt/firefox
matt@matt-heath:/opt/firefox$ /firefox
bash: /firefox: No such file or directory

I WAS WRONG; it's this. I left out the "." when I tried it before.
"matt@matt-heath:/opt/firefox$ ./firefox" DOES make firefox start?

Can anyone tell me how to fix this? 

Is it a separate problem that it won't re-install?

---

### Post by Matt Heath on 2006-12-08
> **aysiu said:**
> There's a period before the flash on that last command. Instead of ```
/firefox
``` it should be ```
./firefox
``` Yes, sorry, had you already posted this? 
This works; it starts it up ok.

---

### Post by aysiu on 2006-12-08
If that's the case, I think you can just paste these commands in again (yes, I realize you did this originally, but something seems to have undone them at some point) to make it all work again: ```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

---

### Post by Matt Heath on 2006-12-08
> **aysiu said:**
> If that's the case, I think you can just paste these commands in again (yes, I realize you did this originally, but something seems to have undone them at some point) to make it all work again: ```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
``` wooyay! that seems to work. thank you

I'll just restart and check it doesn't break again

---

### Post by aysiu on 2006-12-08
Something weird is going on, though--like those errors you encountered when you tried to run the script: ```
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb (--unpack):
trying to overwrite `/usr/bin/mozilla-firefox', which is the diverted version of `/usr/bin/mozilla-firefox'
Errors were encountered while processing:
/var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.debE: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of firefox-gnome-support: firefox-gnome-support depends on firefox (= 1.5.dfsg+1.5.0.8-0ubuntu0.6.06); however:
Version of firefox on system is 1.5.dfsg+1.5.0.3-0ubuntu3.
``` Well, I hope everything sticks for you.

---

### Post by Matt Heath on 2006-12-08
Well, it's started back up working ok :). Thanks, you've been great.

If the problem is something deeper I guess I'll be back.

---

### Post by Matt Heath on 2006-12-08
> **aysiu said:**
> Something weird is going on, though--like those errors you encountered when you tried to run the script: ```
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb (--unpack):
trying to overwrite `/usr/bin/mozilla-firefox', which is the diverted version of `/usr/bin/mozilla-firefox'
Errors were encountered while processing:
/var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.debE: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of firefox-gnome-support: firefox-gnome-support depends on firefox (= 1.5.dfsg+1.5.0.8-0ubuntu0.6.06); however:
Version of firefox on system is 1.5.dfsg+1.5.0.3-0ubuntu3.
``` Well, I hope everything sticks for you.
Could "Something weird" may be that somehow my computer thinks it's running Firefox 1.5. Synaptic lists "1.5dfsg.." as the name of the installed version and the latest version of Firefox and when I tried marking it and upgrading it broke in the same way again. Also I clicked to ionstall upgrades first thing when I switched on, so that may have been what broke it. 
Also, Synaptic says there is a broken package when I sign in and doesn't seem to think that there is when I run the broken filter.

---

### Post by aysiu on 2006-12-08
Hm. I don't know. What happens when you try to run this command? ```
sudo apt-get -f install
```

---

### Post by Matt Heath on 2006-12-08
I get:


matt@matt-heath:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts libthai0
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/7932kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103953 files and directories currently installed.)
Preparing to replace firefox 1.5.dfsg+1.5.0.3-0ubuntu3 (using .../firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mozilla-firefox', which is the diverted version of `/usr/bin/mozilla-firefox'
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


And it breaks in the same way again.

I probably have to go and sleep now (it's 0230 here), but any advice will be VERY much appreciated in the morning.

---

### Post by aysiu on 2006-12-08
[This thread](http://ubuntuforums.org/showthread.php?t=306480) may help.

---

### Post by Matt Heath on 2006-12-09
> **aysiu said:**
> [This thread](http://ubuntuforums.org/showthread.php?t=306480) may help.

Hmm nothing there seemed to work. I have posted a reply there saying I have a similar problem.

---

### Post by Matt Heath on 2006-12-09
I think I have it fixed. I ran the un-install script next to the one you suggested then reinstalled and it seems fine.

---

