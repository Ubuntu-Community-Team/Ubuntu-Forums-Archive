---
title: "AVG Anti-Virus by Grisoft  &quot;Help For users&quot;"
date: 2008-06-11
forum: General Help
---

### Post by TrackTrack on 2008-06-11
AVG Anti-Virus by Grisoft  you can get the program here,
[http://free.grisoft.com/ww.download?prd=afl]("http://free.grisoft.com/ww.download?prd=afl")

How To update, 

Simply GO To Applications Accessories Terminal "NEW"

Type Commands. 

su
/opt/grisoft/avg7/bin/avgupdate -o 3 -m

-------------------This should start the update,------------------------- 
(-o 3 -m) "-o" is update from online   3 - recommended update 
-m, --complete     only complete updating files
-------------------------------------------------------------------------
As user root
Althou there is an easy way to do this you can simply go to your Applications & you should see AVG For Linux Workstation,
With Ubuntu some time's this may not work and you need to use su command,

Why su?
Well i've been look'ing around and it's to keep the Ubuntu OS safe, from user's modify-ing File's that there is no need to modify,

Say like Windows in your C:/ (dir) if you modify the shell/ "Only The Looks Of Windows" i will not go into the file (dir) 
"This is just a basic what & How"
So back to what i was say'ing if you were to modify this in any way you could get the blue sreen of death,

Thou you can modify alot with Ubuntu and nothing goes wrong why they keep it safe and smart, i see some that say they don't get this and what not with "PLZ HELP!" who can for get "OMG I NEED HELP" 
yes you do, go learn to read, and see how easy it is just don't give up,

> or you can also /opt/grisoft/avg7/bin/avgupdate To see the list

-------------------------------------------------------------------------------------------------------------
oh and if you wish to Modify your Root Folders "Party" As i call it, The easy way i have your new Friend,
---------------------------------Simply----------------------------------------------------------------------
Applications Accessories New Terminal
Type Commands.
> su
it will ask for your user pass just Enter your pass once you have done that Enter this
> gksudo nautilus 
That's it you can go out and party, as i call it,

hmmm you can't sign into su?
simply type 
> sudo
it will ask for your user pass,Just Enter your "Log IN" PassWord and there you go,
you can use command su

---

### Post by aysiu on 2008-06-11
*su* won't do anything in a default Ubuntu installation, because root logins are disabled. The command would be ```
sudo /opt/grisoft/avg7/bin/avgupdate -o 3 -m
```

---

### Post by bufsabre666 on 2008-06-11
or you can get the avast linux version, which has deb&rpm installers, install it, run 'gksudo avast-gui' or equivalent, and you can update and run scans and everything from that.avg really lost its way along time ago and when i left windows for good ive never bothered with them, ive always loved avast though, never let me down

---

### Post by TrackTrack on 2008-06-12
> **aysiu said:**
> *su* won't do anything in a default Ubuntu installation, because root logins are disabled. The command would be ```
/opt/grisoft/avg7/bin/avgupdate -o 3 -m
```

That's ture but i alway's run commands in su ----------------------------
 
But yes you don't have to be in su, :) 
i hate to say when i'am wrong but yeah rahrahrah i'am wrong on this one,

---

### Post by K.Mandla on 2008-06-12
Moved to General Help.

---

