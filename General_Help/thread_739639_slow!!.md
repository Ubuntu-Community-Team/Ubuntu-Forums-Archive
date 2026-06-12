---
title: "slow!!"
date: 2008-03-29
forum: General Help
---

### Post by T2manner on 2008-03-29
idk whats wrong.
my ubuntu is always slow.
it's not super slow, but it's slow enough to make me want to switch over to windows.
idk why either.
i even reinstalled it and it's still slow.

---

### Post by scragar on 2008-03-29
firstly I would check your ram usage, ubuntu uses your free ram to improve performance, and if it runs out it resorts to using swap(on your HD), which is MUCH slower, and could account for it's slower speed.
```
free
```will give you the needed information, alternativly you could run ```
system-monitor
```to see whats running, and how much CPU usage and RAM it's using, although I wouldn't close anything without checking what it does first.

---

### Post by T2manner on 2008-03-30
tyler@tyler:~$ free
             total       used       free     shared    buffers     cached
Mem:       1034608     632292     402316          0      64296     243276
-/+ buffers/cache:     324720     709888
Swap:      1253028          0    1253028
tyler@tyler:~$ system-monitor
bash: system-monitor: command not found
tyler@tyler:~$ 

this is just with firefox open
i usually have pidgin open too

---

### Post by kellemes on 2008-03-30
```
top
```
can give an idea of what stuff is running and making your system slow..

Also, have you installed a driver for your videocard? Tell us about it.
And are you using compiz and other resource hungry toys?

You haven't even told us what hardware you have..

---

### Post by diablo75 on 2008-03-30
There is no actual "system-monitor".  The command you want is "gnome-system-monitor"

Use this to view your currently running processes.  Does anything seem to stick out as using a lot of your processor?

---

### Post by T2manner on 2008-03-30
well i'll have to get back to this later bcs my internet stopped working on ubuntu :[
i'm having so  many problems on there it's driving me crazy

---

### Post by Taino on 2008-03-30
> **T2manner said:**
> tyler@tyler:~$ free
             total       used       free     shared    buffers     cached
Mem:       1034608     632292     402316          0      64296     243276
-/+ buffers/cache:     324720     709888
Swap:      1253028          0    1253028
tyler@tyler:~$ system-monitor
bash: system-monitor: command not found
tyler@tyler:~$ 

this is just with firefox open
i usually have pidgin open too

hmm... has it always been slow? does it boot slow? or just get slow "after" firefox is open or just "after both" firefox and pidgin are open?

```

       total          used          free
Mem:  = [COLOR="Blue"]1034608[/COLOR]    [COLOR="Red"]632292[/COLOR]     402316

       total          used          free
Swap: = [COLOR="Blue"]1253028[/COLOR]          [COLOR="Red"]0[/COLOR]          1253028

```

could run "memtest" to make sure your physical ram isnt buggy or failing, ram can go partially bad and cause odd things to happen.. weird.. your swap isnt even in use, comp shouldnt be slowin up.

curious, how is your harddrive set up?

```

sudo fdisk -l

```

---

### Post by lilalmond on 2008-03-30
Hi

My laptop is also slow...
The output of the command "free" is 
```
              total       used       free     shared    buffers     cached
Mem:        482812     470320      12492          0      10428     150472
-/+ buffers/cache:     309420     173392
Swap:      1253028     127564    1125464 
```

The output of the command "sudo fdisk -l" is
```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94869486

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3492    28049458+  83  Linux
/dev/hda2            3493        3648     1253070    5  Extended
/dev/hda5            3493        3648     1253038+  82  Linux swap / Solaris 
```


I have an ATI Radeon and i run ubuntu gutsy
I also have compiz fusion and awn up and running

I posted another thread about some problem i had installing drivers for ATI Radeon and it  screwed up my laptop...
[http://ubuntuforums.org/showthread.php?t=738442](http://ubuntuforums.org/showthread.php?t=738442)

Anyway any help would be great.
Thx

---

### Post by T2manner on 2008-03-30
i don't want to get on ubuntu atm.
for some unknown reason my wireless adapter stopped working.
i was trying to fix it and it just stopped working. :\
so i'm not on ubuntu.
i might reinstall it, idk what to do

---

### Post by T2manner on 2008-03-30
okay
and it's always been a little slow.
but it gets bad when i have pidgin and firefox up.
firefox grays out alott
i hate it

the memtest woudln't work. it needed the program memtester and when i tried to install it it said it was missing.
heres 
sudo fdisk -ltyler@tyler:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcde9cde9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10336    78140128+   7  HPFS/NTFS
tyler@tyler:~$

---

### Post by scragar on 2008-03-30
greying out is a compiz effect used on busy windows, disable that right away if you have it running:
System > preferences > appearance
then the visual effects tab.

I would really recomend running top or gnome-system-monitor (thanks diablo75 for spotting that), and see what's using your CPU power most, said application is proberly causing your slow speed.

---

### Post by diablo75 on 2008-03-30
You might try loging into a fail-safe gnome session to see if that helps.

From the login screen, click the options menu upon, and select the session option.  Change to the failsafe gnome, login, tell it "Just this once" and check it out.

---

