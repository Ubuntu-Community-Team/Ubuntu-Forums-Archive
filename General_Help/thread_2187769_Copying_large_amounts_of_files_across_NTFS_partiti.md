---
title: "Copying large amounts of files across NTFS partitions may cause system 'lockup'"
date: 2013-11-13
forum: General Help
---

### Post by syntaxerror74 on 2013-11-13
Well, even though I feel that this cannot be a Lubuntu-only problem, I've tagged it as such for the time being.

This problem will occur on my Lubuntu Saucy box when copying files - especially from one NTFS-formatted partition to another - via **console commands as well as a GUI based file-manager** (PcManFM, Nautilus, Dolphin...).
It has even proved to be a reason for power-cycling the system, read the following ...

---------------------------------------------------------------------------------------------------
...**test case**...

- Have a real HUGE amount of files ready, e. g. one whole 50 GB partition with preferably lots of small files
(a full-blown, Windows 7 system partition with a huge registry and lots of stuff installed would be ideal)

- Copy everything from A to B and wait.

On my PC, the following will occur very frequently after about 80% is copied:

- *(When using GUI-based file manager)* Dialog window will freeze at where it currently is
- CPU load will go up to 100% and stay there
- Sound playing (even a simple 'mplayer' in console) will stop ABRUPTLY
- After about 2 minutes, you will get a kernel message that *mount.ntfs* has not responded for 120 seconds.
- You cannot even login as root (!) on the emergency consoles anymore (e. g. CTRL-ALT-F2) since it doesn't even make it to the 'Password:' prompt
- Alt-PrtSc-K does not work either [1] **edit: solved: see footnote**
---------------------------------------------------------------------------------------------------

Does this sound familiar to anybody? No? 

Lastly, let me tell you that the standard answer in this case "your cabling is faulty", "some of your HDDs needs to be replaced" does *NOT* apply. I got sick and tired of the problem and did my "partition copy" task by firing up an old 6.X Knoppix CD, and yes, it worked flawlessly. A second one had 130 GB to be copied later, and still no problems.
So this issue must have been introduced only **recently**...

----
*footnote*:
[SIZE=1][1] Gee, turned out "emergency keys" **Alt-PrtSc-K** (and friends) were disabled in Lubuntu, and so was the whole keyboard control of the "Magic Keys"!! My, my...
"Fix": (was 176). **True root shell required. **Does not work by 'sudoing'.
```
# echo 180 > /proc/sys/kernel/sysrq
```
When counting the LSB as Bit 0, it turned out that Bit 2 was not set. Original bitmask was $B0, but it must be $B0 *OR* $4, which is $B4 (180).
Wonder whoever got the idiotic idea of disabling this??
If you want to get this change permanent: the value is stored in */etc/sysctl.d/10-magic-sysrq.conf*
I've instantly made that change, since I'm sure I will at least be more able to intervene next time it locks up. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG][/SIZE]

---

### Post by sudodus on 2013-11-13
It might be a memory handling problem, maybe due to ***zRAM***.

You can disable it, and try again to copy some huge amounts of data.

Renaming [FONT=courier new]**/etc/init/zram-config.conf**[/FONT] to [FONT=courier new]**/etc/init/zram-config.donotstart**[/FONT] and ***reboot*** should work to disable zRAM.

---

### Post by syntaxerror74 on 2013-11-13
Thanks for the reply. 
But wait...isn't zRAM "just" a kind of swapping mechanism?

What about just doing a simple
```
# swapoff /dev/zram0
```
instead ?

---

### Post by sudodus on 2013-11-14
Yes, you can try that if you wish. It should work as a temporary tweak.

Or (/dev/zram* if you have more than one processor and hence several zram devices)

```
sudo swapoff /dev/zram*
sudo rmmod zram

```
to shut it off completely.

---

