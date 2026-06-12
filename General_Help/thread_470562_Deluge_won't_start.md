---
title: "Deluge won't start"
date: 2007-06-11
forum: General Help
---

### Post by guitarmaniac on 2007-06-11
For some reason deluge won't start for me any more. Haven't used it in a while so not sure what's causing it (probably firestarter as I installed that last week).
Here's what the terminal gives me:
```
luke@ubuntu:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Torrent Size 363835185.0
Available Space 30759542784
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)
luke@ubuntu:~$ 
```

---

### Post by moore.bryan on 2007-06-11
[I]have you tried reinstalling?
```
sudo aptitude reinstall deluge
```
[/I]

---

### Post by madmetal on 2007-06-11
> **moore.bryan said:**
> [I]have you tried reinstalling?
```
sudo aptitude reinstall deluge
```
[/I]

it wont help..
its a known deluge bug..
try to delete
~/.config/deluge/persistent.state file
and then open deluge again.. ;)

---

### Post by guitarmaniac on 2007-06-11
> **madmetal said:**
> it wont help..
its a known deluge bug..
try to delete
~/.config/deluge/persistent.state file
and then open deluge again.. ;)

thanks man, that did it, have some popcorn :popcorn:

---

### Post by madmetal on 2007-06-11
> **guitarmaniac said:**
> thanks man, that did it, have some popcorn :popcorn:

thanks , i will take :popcorn: when come to sidney ;)

---

### Post by Purple Grant on 2007-06-13
> **madmetal said:**
> it wont help..
its a known deluge bug..
try to delete
~/.config/deluge/persistent.state file
and then open deluge again.. ;)

Thanks, I had the same problem and that sorted it right out. ::D

Could someone explain why?

---

### Post by madmetal on 2007-06-15
> **Purple Grant said:**
> Thanks, I had the same problem and that sorted it right out. ::D

Could someone explain why?

i think Zach (the developer) can explain so i will ask him ;)

---

### Post by zachtib on 2007-06-16
> **madmetal said:**
> i think Zach (the developer) can explain so i will ask him ;)

if something in the settings becomes corrupted, sometimes deluge can fail to start, as you saw here.  we're trying to improve the situation, and it's much improved in the new 0.5.1.1 release.

---

### Post by Blofeld on 2007-06-18
The fix worked for me as well, thanks, geeks!
:KS

---

### Post by honeydew on 2007-06-18
this is not a good fix.  This is the second time I had many active torrents and loss them with this fix.  I installed the newer version do we think it will be safe to close the program with active torrents?

---

### Post by crabhunt on 2007-11-01
> **honeydew said:**
> this is not a good fix.  This is the second time I had many active torrents and loss them with this fix.  I installed the newer version do we think it will be safe to close the program with active torrents?

Inside the .config/deluge/torrentfiles directory all the torrents are still there, so once u delete the persistent.state file, you will see all your active torrents gone, but then you open all the torrent files from deluge again from the directory I mentioned above and save the downloading into the same directory where your active downloads were downloading in, this way it will recover all the downloads,... you will not loose anything..

---

### Post by honeydew on 2007-11-06
however if you have a ratio scheme (upload:leech) 2:1  and you have 50+ torrents it kinda botches things when you have to go re-seed everything, I just like keeping a good ratio, I like to keep my torrents in a revolving door patern.. new ones come in.. other ones stop seeding when they reach the appropriate ratio.  

either way.. Im still using deluge.. grabbed the newest version a few days ago.. keep up the good work.

---

### Post by gordonh on 2007-11-06
> **zachtib said:**
> if something in the settings becomes corrupted, sometimes deluge can fail to start, as you saw here.  we're trying to improve the situation, and it's much improved in the new 0.5.1.1 release.

I'd used aptitude to "completely remove" deluge when I had this problem, and then couldn't find it to reinstall.

I've removed the persistant.state file and downloaded from the site linked above and reinstalled.

current problem.  I can't find the program to execute.

It's not under appliations, typing deluge-torrent in terminal does nothing and right-clicking a torrent file doesn't give deluge as an option to open with.

Help please.

correction it's on the right click menu, but when I use that a message shows opening ... which disappears (as it did before deleting the persistant state file

---

### Post by honeydew on 2007-11-06
hrmm... my exe is located here... 

/usr/bin/deluge

if its not installed maybe try downloading the debian package of the website..  and running dpkg -i  .. if you get any errors be sure to post the output.

---

### Post by gordonh on 2007-11-07
/usr/bin/deluge

OK.  that's the same for me.  what next

---

### Post by gordonh on 2007-11-08
nudge

---

