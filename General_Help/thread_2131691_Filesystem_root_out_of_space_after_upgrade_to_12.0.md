---
title: "Filesystem root out of space after upgrade to 12.04"
date: 2013-04-02
forum: General Help
---

### Post by arno77 on 2013-04-02
I have successfully upgraded to 12.04 but now receive warning messages that the root is running out of space, having left only some 270MB. I am surprised about that message becasue I have allocated almost 12GB to root. Further, the Disk Usage Analyzer (see screenshot) indeed says that 100% of / are used whereas GParted (see other screenshot) says that there are >3GB unused space (of a total of >11GB). The Disk Usage Analyzer also says that 91% of my /home are used whereas GParted  shows 105GB unused space (of a total of 180GB).

What do I miss? Does anybody have a similar problem? Can anybody help?

---

### Post by Bashing-om on 2013-04-02
arno77; Hi !

Drop down to a lower level for a closer inspection. What do the terminal commands:
```
sudo du -h /root
du -h /boot
df -i
``` show for file system and inode usage ?[INDENT=2]
that should tell the tale

[/INDENT]

---

### Post by grahammechanical on 2013-04-02
I think that you will find that Disk Usage Analyser shows / folder to have 100% usage for everybody. It just does that. It does on my system using 13.04 and if I was to boot into 12.04 or 12.10 on my machine it will say the same even though the partitions are different sizes.

Also I think that you are missing (to use your words) the fact that Disk Usage Analyser is measuring the /home folder under / folder and not the usage on your /home partition. I know that you have just upgraded to 12.04 but I can tell you that Disk Usage Analyser in 13.04 lets us select which partition to analyse. And it shows the correct usage for mounted partitions.

But nontheless, you are getting a warning message. Ubuntu likes to run with spare capacity. I think that whatever is sending out that warning message is including set aside spare capacity. The upgrade process should have removed the old kernels from whatever you upgraded from. Old kernels can pile up and take some space. But not in this case I think. When was the last time you emptied the Rubbish bin?

Regards.

---

### Post by CatKiller on 2013-04-02
I concur that you're reading the baobab output wrong. Also, 12 GiB isn't that much these days. You have a bunch of free space in your /home partition though, so you can use GParted to shrink that partition and expand your / partition. 25 GiB would probably be fine, but 50 might be better. You can't fiddle with / on a running system, though, so you'll need to use either the Ubuntu cd or a GParted cd to do the operation. You'll also probably need to turn off swap.

EDIT: @grahammechanical Upgrading the OS doesn't remove old kernels in case the installation process goes pear-shaped. That needs to be done manually once you've verified that the new system is working.

---

### Post by Paqman on 2013-04-02
+1 for dumping all the old kernels, they're about 100MB each. Also if you've just done an upgrade you may well have a ton of packages sitting in your APT cache. Try running:
```

sudo apt-get clean

```

---

### Post by arno77 on 2013-04-03
> **Bashing-om said:**
> arno77; Hi !

Drop down to a lower level for a closer inspection. What do the terminal commands:
```
sudo du -h /root
du -h /boot
df -i
``` show for file system and inode usage ?[INDENT=2]
that should tell the tale

[/INDENT]

hi Bahing-om thanks for your reply! here the outputs produced by the commands

arno@tantalus-laptop:~$ sudo du -h /root
[sudo] password for arno: 
796K	/root/.synaptic/log
4.0K	/root/.synaptic/tmp
812K	/root/.synaptic
4.0K	/root/.wapi
24K	/root/.local/share/webkit/icondatabase
28K	/root/.local/share/webkit
76K	/root/.local/share/gvfs-metadata
112K	/root/.local/share
116K	/root/.local
4.0K	/root/.aptitude
4.6M	/root/.rpmdb
4.0K	/root/.gconfd
4.0K	/root/.gnome2/accels
12K	/root/.gnome2
4.0K	/root/.pulse
4.0K	/root/.debtags
4.0K	/root/.gnome2_private
4.0K	/root/.gconf
4.0K	/root/.config/ibus/bus
8.0K	/root/.config/ibus
4.0K	/root/.config/ubuntu-tweak/temp
8.0K	/root/.config/ubuntu-tweak
8.0K	/root/.config/gtk-2.0
4.0K	/root/.config/enchant
32K	/root/.config
8.0K	/root/.dbus/session-bus
12K	/root/.dbus
4.0K	/root/.gvfs
4.0K	/root/.cache/dconf
8.0K	/root/.cache
5.6M	/root

arno@tantalus-laptop:~$ du -h /boot
16K	/boot/grub/locale
4.3M	/boot/grub
48M	/boot

arno@tantalus-laptop:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda5        732960 274438   458522   38% /
udev             205424    576   204848    1% /dev
tmpfs            210520    535   209985    1% /run
none             210520      4   210516    1% /run/lock
none             210520      6   210514    1% /run/shm
/dev/sda6      11845632  98564 11747068    1% /home

---

### Post by arno77 on 2013-04-03
Thanks! 

As far as I can see from checking synapic package manager  the old kernels have been removed. So that shouldn't cause the problem. But I haven't emptied the Rubbish bin for a while. Will do that and see if it helps.

Thansk also for clarifying what Disk Usage Analyser shows. Did indeed nto get that.

---

### Post by arno77 on 2013-04-03
> **CatKiller said:**
> I concur that you're reading the baobab output wrong. Also, 12 GiB isn't that much these days. You have a bunch of free space in your /home partition though, so you can use GParted to shrink that partition and expand your / partition. 25 GiB would probably be fine, but 50 might be better. You can't fiddle with / on a running system, though, so you'll need to use either the Ubuntu cd or a GParted cd to do the operation. You'll also probably need to turn off swap.

EDIT: @grahammechanical Upgrading the OS doesn't remove old kernels in case the installation process goes pear-shaped. That needs to be done manually once you've verified that the new system is working.

Thanks for your reply, but what do you mean with "baobab"?

Its right 12GB is't that much but still there are 3GB left and the warning message says that only a few (hundred) MBs are left. Where does this difference come from. I know that I could increase the space of the / partition but would prefer another solution before fiddling aoround with partitions. Also hadn't any problem before the upgrade.

---

### Post by arno77 on 2013-04-03
> **Paqman said:**
> +1 for dumping all the old kernels, they're about 100MB each. Also if you've just done an upgrade you may well have a ton of packages sitting in your APT cache. Try running:
```

sudo apt-get clean

```

hi and thanks for the tip.

I've run "clean". We'll see if it helps.

---

### Post by CatKiller on 2013-04-03
> **arno77 said:**
> Thanks for your reply, but what do you mean with "baobab"?


It's the tool that's displayed as Disk Usage Analyser.

---

### Post by arno77 on 2013-04-09
Hi all. Thanks for all suggestions.

I did empty my trash bin and also ran "sudo apt-get clean" with the result that I didn't receive warning messages for 3. But since yesterday they pop up again.

Does anybody have more ideas what I could do? Any help is very much appreciated.

---

### Post by arno77 on 2013-04-09
hi Bahing-om. Could you help me in reading the output. What do I learn from it? Thanks.

> **arno77 said:**
> hi Bahing-om thanks for your reply! here the outputs produced by the commands

arno@tantalus-laptop:~$ sudo du -h /root
[sudo] password for arno: 
796K	/root/.synaptic/log
4.0K	/root/.synaptic/tmp
812K	/root/.synaptic
4.0K	/root/.wapi
24K	/root/.local/share/webkit/icondatabase
28K	/root/.local/share/webkit
76K	/root/.local/share/gvfs-metadata
112K	/root/.local/share
116K	/root/.local
4.0K	/root/.aptitude
4.6M	/root/.rpmdb
4.0K	/root/.gconfd
4.0K	/root/.gnome2/accels
12K	/root/.gnome2
4.0K	/root/.pulse
4.0K	/root/.debtags
4.0K	/root/.gnome2_private
4.0K	/root/.gconf
4.0K	/root/.config/ibus/bus
8.0K	/root/.config/ibus
4.0K	/root/.config/ubuntu-tweak/temp
8.0K	/root/.config/ubuntu-tweak
8.0K	/root/.config/gtk-2.0
4.0K	/root/.config/enchant
32K	/root/.config
8.0K	/root/.dbus/session-bus
12K	/root/.dbus
4.0K	/root/.gvfs
4.0K	/root/.cache/dconf
8.0K	/root/.cache
5.6M	/root

arno@tantalus-laptop:~$ du -h /boot
16K	/boot/grub/locale
4.3M	/boot/grub
48M	/boot

arno@tantalus-laptop:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda5        732960 274438   458522   38% /
udev             205424    576   204848    1% /dev
tmpfs            210520    535   209985    1% /run
none             210520      4   210516    1% /run/lock
none             210520      6   210514    1% /run/shm
/dev/sda6      11845632  98564 11747068    1% /home

---

### Post by Bashing-om on 2013-04-09
arno77; Hey

All we are doing is looking at the Disk Usage. I see nothing in these outputs to indicate a problem where we are looking.
How big are these "directories" as well as how many;
"df -i" -> if we are running out of "inode" assigments
For info on "du" see:
```
man du
```
In situations such as this there exist at least 3 primary causes;
1. /boot is to capacity due to the presence of older unused kernels;
2. /home is at capacity due to many applications installed OR the trash not dumped;
3. /root is at capacity due to /var/log filled up from a run-a-way logging of an errant condition in the operating system.

So let's look at the system as a whole to get an idea as to what is going on:
```
df -h
```
and to move things along, let's look at "/var/log" ;
```
du -h /var/log | sort -nr | less
``` sorts large directories first and pipes(|) to "less" for pagination (q to quit)[INDENT=3]
so a tale is told
[/INDENT]

---

