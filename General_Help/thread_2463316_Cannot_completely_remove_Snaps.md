---
title: "Cannot completely remove Snaps"
date: 2021-06-08
forum: General Help
---

### Post by dddman on 2021-06-08
```
/dev/loop0        101376   101376         0 100% /snap/core/11081
/dev/loop1         32896    32896         0 100% /snap/snapd/11841
/dev/loop2         32896    32896         0 100% /snap/snapd/12057
/dev/loop3        101632   101632         0 100% /snap/core/11167
/dev/sda1         523248        4    523244   1% /boot/efi
tmpfs             402964      336    402628   1% /run/user/1000
ubu@ubu:~$ snap remove snapd
error: cannot remove "snapd": snap "snapd" is not removable: remove all other snaps first
ubu@ubu:~$ snap remove core
error: cannot remove "core": snap "core" is not removable: snap is used by the model
ubu@ubu:~$ sudo rm snapd
[sudo] password for ubu: 
rm: cannot remove 'snapd': No such file or directory
ubu@ubu:~$ sudo rm snap
rm: cannot remove 'snap': No such file or director
```

I cannot remove the final 4 /dev/loop

---

### Post by TheFu on 2021-06-08
Some DEs have snap dependencies.  But in general, you can

```
snap list
sudo snap remove {list of snap names}
sudo apt remove --purge snapd
```
And that will remove the snaps and all ability for them to be loaded, unless you take a manual step to re-install snapd.

---

### Post by ajgreeny on 2021-06-08
If you want remove all the snaps in your system, and that is entirely up to you, you first need to find what snaps are actually installed with command ```
snap list
``` Then, one by one to avoid possible removal problems, use command ```
sudo snap remove *snapname*
```copying the name from that list
Once they have all been removed you can then run ```
sudo apt purge snapd
``` to remove snapd.

I did this back in July 2020 on my installation of Xubuntu 20.04, not because of any major problems with the snaps installed, but more because I wanted to test the feasibility of doing so.  
All went well without any problems and I replaced the chromium snap that I had installed using apt, not realising at the time that it would really pull in the snap version, with a version from a development ppa at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev?field.series_filter=focal](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev?field.series_filter=focal).

---

### Post by dddman on 2021-06-08
Hello people

@ajgreeny
That worked, all loops are now gone.  Thanks

And no I'm not giving up on snaps: I wanted to see if removing all snaps would speed up my system.  I had 6 snap packages installed and have read this can slow down your system.  I am not having a performance issue, just wanted to be sure.  For my system I see no change in performance.  Running 4 core/4G ram.

Earlier I reduced my snaps to just one package (firefox).  Firefox took 150M of space and snaps took 350M.  So to install the first snaps package takes quite a bit of space.

Solved

Thanks for the replys

---

### Post by Dennis N on 2021-06-08
When you remove a snap package, you also automatically create a snapshot of all data created for that snap package so that you can restore the snap later with **snap restore**. I don't know if all those snapshots are removed when you purge snapd, but I would check and see. Let us know.

---

### Post by dddman on 2021-06-08
Thanks Dennis, I'll do a file system search if ever I do this again.  Right now I'm already rebuilding and installed snapd (140M), this did not create any /dev/loops.  Next I'll install snap package firefox.  Thats really the only snap package I need to run.  I run snaps FF and FFesrPPA.  Others will get added if necessary.

edit
I changed my mind, just going to run FFesr, no snaps installed at this time.  See how long that last :)

---

### Post by TheFu on 2021-06-08
~/snap/ in your HOME is where personal snap data seems to go.  It would not be cleaned up when a snap is removed or purged.

---

### Post by dddman on 2021-06-08
Yep, deleted the Snaps home folder.  I did a file system search and received a massive amount of non snap hits (like snapshot).  I skimmed through them and looks like purge did a good job.  Also hit it with Bleachbit which has autoremove and autoclean.  Think that does it

---

