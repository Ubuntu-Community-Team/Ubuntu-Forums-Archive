---
title: "VirtualBox: how to duplicate machines?"
date: 2007-09-17
forum: General Help
---

### Post by megamania on 2007-09-17
Thanks to the ubuntu wiki and to the forums, in less than 3 hours I installed VirtualBox for the first time and managed to sort out all problems so far.

Now that the fresh install of Win Xp is up and running, I'd like to create a copy of it, in order to be able to recover my disasters by simply going back to the previous machine.

So, what should I do? Should I just copy the virtual drive and rename it, or is there a possibility to duplicate an existing machine? The latter would obviously be a much better option, because it would also save the settings.

---

### Post by sumguy231 on 2007-09-17
If you just want to be able to recover it in case you screw up, you can take a "snapshot" of it which you can revert to whenever you want. You can do that with Machine -> Take Snapshot.

---

### Post by megamania on 2007-09-17
I can clone the virtual disk using
```

VBoxManage clonevdi [source] [dest]

```
but this only copies the disk, not the settings. After that, I have to manually create a new machine and apply all settings (o.s. type, memory, sound, etc.) to it.

---

### Post by dustigroove on 2007-09-17
[FONT=Arial][SIZE=2][COLOR=Black]The snapshots function in VB will let you easily jump back to a defined state in your VM. Having a full backup of the vdi on a separate drive is suggested as well in case something unexpected happens (say, if your drive takes a dump).
[/COLOR][/SIZE][/FONT]

---

### Post by dustigroove on 2007-09-17
> **megamania said:**
> I can clone the virtual disk using VBoxManage clonevdi [source] [dest] but this only copies the disk, not the settings. After that, I have to manually create a new machine and apply all settings (o.s. type, memory, sound, etc.) to it.

Also backup the machines folder related to the particular VM you want to backup. It should be located in /home/username/.VirtualBox/Machines/.

.

---

### Post by bodhi.zazen on 2007-09-17
Best clone the disk. Snapshots are nice, but they can become corrupt.

The settings should be easily recreated ...

---

### Post by bioburg on 2008-04-26
I think I'm interested in the same aproach, since I have a clean XP install  with all settings (Vbox additions, resolution, direct X, a few files, updater off etc...) installed and I want to make 4 exact copies of it with a new name. So instead of installing Xp 4x more (and configuring my preferences) I'd like to use VBoxManage clonevdi. The manual is giving me a run around but not a how to...(what to type in the terminal screen)

SO if I sum up the added notions from above.

> **megamania said:**
> I can clone the virtual disk using
```

VBoxManage clonevdi [source] [dest]

```
but this only copies the disk, not the settings. After that, I have to manually create a new machine and apply all settings (o.s. type, memory, sound, etc.) to it.

> **dustigroove said:**
> Also backup the machines folder related to the particular VM you want to backup. It should be located in /home/username/.VirtualBox/Machines/.

.

I'm not very familiar with the code lines in Ubuntu since I only use it for a moth orso. But can I just copy the:
/home/username/.VirtualBox/Machines/example

to 

/home/username/.VirtualBox/Machines/example2
/home/username/.VirtualBox/Machines/example3
/home/username/.VirtualBox/Machines/example4
/home/username/.VirtualBox/Machines/example5

???

I noticed that the Snapshot has a very specific name so I don't think this will work ^^

If the (in my above mentioned) approach won't work can anyone give an example which code I have to type in the terminal screen to use VBoxManage clonevdi to create 4 extra copies of the same snapshot I'm having now?

---

### Post by dmjones500 on 2008-05-15
The manual suggests you don't manually copy in this manner, as it doesn't give a new unique identifier number to the copy.

You need to run:

```
cd /home/username/.VirtualBox/Machines/
vboxmanage clonevdi example.dvi example2.dvi
vboxmanage clonevdi example.dvi example3.dvi
vboxmanage clonevdi example.dvi example4.dvi
```

Then, I'm afraid you'll have to jump through the hoops and create a new VM, select the new .vdi file you created to act as the hard disk, and do the other settings...

Rather unexpectedly, the new copied drives don't magically appear in the drive list.  You have to choose "Add..." and select the .vdi files manually.

---

