---
title: "Copied Home/user directory from one 22.04 to another. Now Login Loops... How to fix?"
date: 2023-04-04
forum: General Help
---

### Post by 777funk on 2023-04-04
I had a corrupted file system on a new 22.04 install so I decided to create a backup of home/<user>. I then reinstalled (same computer) from a Live CD and pasted the original home/user to the new install. 

This seemed to work (as in it will boot), but now I have a login loop. 

I did this in hopes that it will be as if nothing ever happened and all programs and settings will be what they were before the corruption. I've never done this so I have no idea if it will work. Is this the case?

---

### Post by DuckHook on 2023-04-04
> **777funk said:**
> &#8230;in hopes that it will be as if nothing ever happened and all programs and settings will be what they were before the corruption. I've never done this so I have no idea if it will work. Is this the case?
In short, no.

A reinstall is basically concluding that you wish to start over. But dragging in the entirety of your old /home holder means that you wish to exactly recreate your old environment. These are opposing and contradictory objectives. If there was something wrong with that environment that caused you to reinstall in the first place, then dragging it back in will only recreate the initial problem.

Therefore, it is not surprising that your login is looping. The login process is user&#8209;specific. Each /home directory contains configuration files that tell the system how to set itself up and are tied to its specific user. You don't go into details about what you mean by "corrupted file system", but if that corruption was in your /home directory, then you see where the problem is when you just dragged everything back in.

In a reinstall, the proper way to restore data is to selectively restore only the real data, but not the configs. You want the new install configs to be active not your old, possibly corrupted ones. Most people store their data in the usual directories: documents, downloads, music, videos, etc and any further directories that you may have created. Restore only those and you should be able to log in.

Your old settings and programs will ***not*** be there, but that's the whole point of a reinstall: to start fresh from a known good state and not inherit any unknown problems. I find that it's not really that big a deal to recreate my old settings and reinstall my old programs, but that's because I always leave my base system in a state as close to default as possible.

---

### Post by Impavidus on 2023-04-04
What could have gone wrong is that your restored home directory isn't owned by you. Maybe it's owned by root, as you may have used the root user to restore it. Or maybe it's swapped with a different user. If there are two ordinary users on your system, but this time you created them in reverse order, their numeric userIDs got swapped and along with that file ownership. If you can access a root shell (try the option to boot in recovery mode in grub), you can check and fix ownership.

---

### Post by 777funk on 2023-04-04
Interesting and thank you for the replies! I believe the easiest course of action is to do a fresh install of OS and all my software (audio production so LOTS of configuration and installation of specific applications). 

BTW, the problem came in by using Timeshift. For some reason it hung and I had to reboot the system. When I rebooted, the FS was corrupted. I could access all the data via booting to a Live CD, so I was hoping to copy much of that and not have to start fresh (10 hours of installation and config), but maybe that's the best bet. This time I will copy the entire hard drive to a spare when I'm done setting up my system, just incase something goes wrong again. 

I will say that this drive had a few bad sectors before I started... maybe that's why Timeshift hung. I may never know. I like the idea of Timeshift, but I'm a little afraid now to try it again since my first experience didn't work out so well. I'll probably try it with the fresh install first (before I spend another 10 hours setting things up) just to make sure all is well.

---

### Post by DuckHook on 2023-04-04
Yup, yanking the plug in the middle of what is essentially a massive file I/O operation will definitely ruin your day.

Bad sectors are also bad news. If they are few, stable and not growing, then you can possibly get away with it, but in my experience, when my drives start generating bad sectors, I replace them. The cost of a new drive is nothing compared to the trouble they create if ignored.

If you are doing audio work that involves special audio servers like Jack and are reinstalling anyway, then consider installing Ubuntu Studio, which is optimized for audio.

Timeshift is useful, but it doesn't replace backups. Glad to know that you have those. Instead of (or in addition to) Timeshift, consider installing as LVM. You can then make snapshots and restore from them. This shares similarities to Timeshift, but is also more robust: since you have to do the snapshot offline, they are more dependable.

---

### Post by ne29914 on 2023-04-04
I already explained here why Timeshift gave you problems (post #3): [https://ubuntuforums.org/showthread.php?t=2485611](https://ubuntuforums.org/showthread.php?t=2485611)

---

### Post by DuckHook on 2023-04-04
I was unaware of this other thread.

The most cogent advice to OP is that given by [HermanAB in post #9]("https://ubuntuforums.org/showthread.php?t=2485611&p=14137461#post14137461"). It is succinct and well stated enough to warrant quoting:> **HermanAB said:**
> In my experience it is best to do development work in a VM, leaving the host alone.  Backing up a VM is easy- just make a zip archive of it.
This is a far better way to achieve your objective&#8230; VMs can be more easily snapshotted and restored. Easier even than Timeshift or LVM or ZFS snapshots. They can also be cloned and backed up more easily.

Yet another way would be containers, though I fear that this is getting too arcane.

If your audio tweaks are needed at the HW level, then VMs may not work. But if VMs do work, then use them. When other options are available, it is ***always*** best to leave the host alone.

---

### Post by #&amp;thj^% on 2023-04-04
> **DuckHook said:**
> Easier even than ZFS snapshots. They can also be cloned and backed up more easily.


DuckHook I promise I'm not singly picking on you in any form or fashion, but the above is subjective IMHO IE:
```
zsysctl list
ID                        ZSys  Last Used
--                        ----  ---------
rpool/ROOT/ubuntu_omvt40  true  current


me on Tue Apr 04 at 01:50 PM in ~ branch: (HEAD) 
>> zsysctl machine show omvt40
Name:           rpool/ROOT/ubuntu_omvt40
ZSys:           true
Last Used:      current
History:        
  - Name:       rpool/ROOT/ubuntu_omvt40@autozsys_htv9r5
    Created on: 2023-03-27 09:22:12
  - Name:       rpool/ROOT/ubuntu_omvt40@autozsys_ywlmbf
    Created on: 2023-03-27 09:21:07
  - Name:       rpool/ROOT/ubuntu_omvt40@autozsys_5gpq9d
    Created on: 2023-03-27 09:15:20
  - Name:       rpool/ROOT/ubuntu_9ld0zm
    Created on: 2023-03-27 08:56:06
  - Name:       rpool/ROOT/ubuntu_omvt40@autozsys_w3gb9k
    Created on: 2023-03-26 10:35:26
Users:
  - Name:    me
    History: 
     - rpool/USERDATA/me_a2rtj3@autozsys_d8tzn5 (2023-04-04 13:45:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_ews99s (2023-04-04 12:44:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_cnusld (2023-04-04 11:43:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_l0vdba (2023-04-04 10:42:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_da5lzx (2023-04-04 08:40:22)
     - rpool/USERDATA/me_a2rtj3@autozsys_lbl5c0 (2023-04-04 08:06:54)
     - rpool/USERDATA/me_a2rtj3@autozsys_ahp17x (2023-04-04 07:58:58)
     - rpool/USERDATA/me_a2rtj3@autozsys_dohrcr (2023-04-04 00:18:08)
     - rpool/USERDATA/me_a2rtj3@autozsys_21tgcd (2023-04-03 23:17:58)
     - rpool/USERDATA/me_a2rtj3@autozsys_bha8i4 (2023-04-03 22:16:57)
     - rpool/USERDATA/me_a2rtj3@autozsys_gqortb (2023-04-03 21:15:57)
     - rpool/USERDATA/me_a2rtj3@autozsys_xk8dvw (2023-04-03 20:14:57)
     - rpool/USERDATA/me_a2rtj3@autozsys_9yhbre (2023-04-03 19:14:48)
     - rpool/USERDATA/me_a2rtj3@autozsys_9qlvg9 (2023-04-03 19:00:31)
     - rpool/USERDATA/me_a2rtj3@autozsys_h7020p (2023-04-03 18:27:53)
     - rpool/USERDATA/me_a2rtj3@autozsys_q0fxz5 (2023-04-03 18:09:47)
     - rpool/USERDATA/me_a2rtj3@autozsys_u32mkx (2023-04-03 17:33:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_ij21ll (2023-04-03 16:32:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_vttbbu (2023-04-03 15:31:45)
     - rpool/USERDATA/me_a2rtj3@autozsys_u0yp90 (2023-04-03 14:54:41)
     - rpool/USERDATA/me_a2rtj3@autozsys_8anf7d (2023-04-03 13:54:36)
     - rpool/USERDATA/me_a2rtj3@autozsys_zwn4zm (2023-04-03 13:39:02)
     - rpool/USERDATA/me_a2rtj3@autozsys_y4vq9a (2023-04-03 12:47:53)
     - rpool/USERDATA/me_a2rtj3@autozsys_q7q3cr (2023-04-03 07:33:09)
     - rpool/USERDATA/me_a2rtj3@autozsys_27n1ej (2023-04-02 23:22:14)
     - rpool/USERDATA/me_a2rtj3@autozsys_r46pl2 (2023-04-02 15:15:14)
     - rpool/USERDATA/me_a2rtj3@autozsys_4pclck (2023-04-02 07:08:14)
     - rpool/USERDATA/me_a2rtj3@autozsys_wbdovl (2023-04-01 22:55:26)
     - rpool/USERDATA/me_a2rtj3@autozsys_7mgd7g (2023-03-31 15:01:10)
  - Name:    root
    History: 
     - rpool/USERDATA/root_a2rtj3@autozsys_htv9r5 (2023-03-27 09:22:13)
     - rpool/USERDATA/root_a2rtj3@autozsys_ywlmbf (2023-03-27 09:21:07)
     - rpool/USERDATA/root_a2rtj3@autozsys_5gpq9d (2023-03-27 09:15:20)
     - rpool/USERDATA/root_m0v3ok (2023-03-27 08:56:06)
     - rpool/USERDATA/root_a2rtj3@autozsys_w3gb9k (2023-03-26 10:35:26)


```
Took less than 40 seconds
But agreed that One should pick-up a stratagem that is within that users understanding, and can recall in the event of a major mis-hap

---

### Post by 777funk on 2023-04-04
> **ne29914 said:**
> I already explained here why Timeshift gave you problems (post #3): [https://ubuntuforums.org/showthread.php?t=2485611](https://ubuntuforums.org/showthread.php?t=2485611)

What you had posted may be an issue, but not in my case since I wasn't trying to restore at all. I was actually trying to create a snapshot. It wouldn't do anything other than go back to the start screen. I knew how to create a snapshot since I had 3 there already. It (Timeshift) was just acting up for some reason. So I figured, maybe it can't hold 3 snapshots and hit delete on one of them. At this point (deleting a snapshot), it froze and the computer became unusable. I shut it down since I didn't know what else to do. The computer then would not boot (even to the grub screen) and said there was corruption.

---

### Post by 777funk on 2023-04-04
> **DuckHook said:**
> I was unaware of this other thread.

The most cogent advice to OP is that given by [HermanAB in post #9]("https://ubuntuforums.org/showthread.php?t=2485611&p=14137461#post14137461"). It is succinct and well stated enough to warrant quoting:
This is a far better way to achieve your objective&#8230; VMs can be more easily snapshotted and restored. Easier even than Timeshift or LVM or ZFS snapshots. They can also be cloned and backed up more easily.

Yet another way would be containers, though I fear that this is getting too arcane.

If your audio tweaks are needed at the HW level, then VMs may not work. But if VMs do work, then use them. When other options are available, it is ***always*** best to leave the host alone.

Audio is pretty fussy (interfaces via USB and Firewire and latency). Imagine trying to play a piano that responded a second after you struck a note. I'm sure a musician could train their brain to latency compensate, but I find it's better off (and possible in my case) to just make sure latency is very low (11ms or less). 

So, at least in the past, this has meant no VMs (for actual use). For proof of concepts, I'm sure VMs could work, if it wasn't too much trouble to reach hardware via USB or Firewire. There comes a point where being a musician is hard enough and being an IT guy has to be secondary. Linux has come a long way in audio production from say 10 years ago. It's still harder today than just going with Win or Mac, but the end results can be better with Linux in my opinion. I can get great low latency performance with samplers and virtual instruments. There are no software "rentals", and I can get away with using an old laptop with obsolete hardware interfaces. 

I'm no pro, but to show the quality of what's available now, I think this thing (dexed VSTi) sounds at least as good as a hardware Yamaha DX7 (big bucks when new and probably still today):
[https://www.youtube.com/watch?v=UmaJ_biUuRE](https://www.youtube.com/watch?v=UmaJ_biUuRE)

---

### Post by DuckHook on 2023-04-04
> **1fallen said:**
> DuckHook I promise I'm not singly picking on you in any form or fashion, but the above is subjective IMHO
You need never be concerned about things like that.

I've been corrected on these forums so many times that I've lost count. Every time, I learn something new and appreciate the insights.

I also hope that no one on these forums is so thin&#8209;skinned as to take offence at being corrected.
> Took less than 40 seconds
But agreed that One should pick-up a stratagem that is within that users understanding, and can recall in the event of a major mis-hap
As it happens, I use ZFS on almost all of my installs and leverage its snapshot feature in exactly the way that you describe. My reference to VMs being easier is based on the fact that restoring a host snapshot will always be harder than restoring a VM/container, simply because a host system restore must be done offline whereas a VM/container restore is done from an already working host system.
> **777funk said:**
> What you had posted may be an issue, but not in my case since I wasn't trying to restore at all.
In your case, it is possible that bad sectors may be your bugbear. Since your install is so heavily customized, then the solutions are:

[LIST=1]
[*]Simplify your host by hiving all customizations off to a VM a la HermanAB's solution, or
[*]Buy a new disk that is reliable, or
[*]Both of the above
[/LIST]
> **777funk said:**
> Audio is pretty fussy (interfaces via USB and Firewire and latency). Imagine trying to play a piano that responded a second after you struck a note. I'm sure a musician could train their brain to latency compensate, but I find it's better off (and possible in my case) to just make sure latency is very low (11ms or less). 
Hence my suggestion to explore Ubuntu Studio which uses low&#8209;latency Jack.
> So, at least in the past, this has meant no VMs (for actual use). For proof of concepts, I'm sure VMs could work, if it wasn't too much trouble to reach hardware via USB or Firewire.
Here's where containers might work better. Since they are not abstracted several further layers away from the iron like VMs are, their latency is also much reduced. Some people get bare metal performance out of their containers.
> There comes a point where being a musician is hard enough and being an IT guy has to be secondary.
This would rule out LXD unless you really wanted to go down a rabbit hole. I've not tried to make LXD audio work with Jack either, so that is another impediment.
> Linux has come a long way in audio production from say 10 years ago. It's still harder today than just going with Win or Mac, but the end results can be better with Linux in my opinion. I can get great low latency performance with samplers and virtual instruments. There are no software "rentals", and I can get away with using an old laptop with obsolete hardware interfaces. 

I'm no pro, but to show the quality of what's available now, I think this thing (dexed VSTi) sounds at least as good as a hardware Yamaha DX7 (big bucks when new and probably still today):
[https://www.youtube.com/watch?v=UmaJ_biUuRE](https://www.youtube.com/watch?v=UmaJ_biUuRE)
You've given me new food for thought. I didn't know that Linux based autdio had come so far. It's good to see. I agree that in your case, bare metal customization is your best and most realistic option. This simplifies your choices: a new drive. If you don't need scads of storage, then a SSD might be the best option. Even less latency too.

Good Luck and Hppy Ubuntu&#8209;ing.

---

### Post by #&amp;thj^% on 2023-04-04
> **DuckHook said:**
> My reference to VMs being easier is based on the fact that restoring a host snapshot will always be harder than restoring a VM/container, simply because a host system restore must be done offline whereas a VM/container restore is done from an already working host system.

Understood, I should of pondered that thought a bit longer. :D

---

### Post by TheFu on 2023-04-04
Creating a ZIP archive of a VM single file is easy to understand, that's certain.
LVM snapshots are instantaneous to create, but harder to understand.  Also, having rolling LVM snapshots could be something useful, say one per day, provided enough storage exists to allow the system to keep working with so many frozen blocks on storage.  Taking snapshots with LVM doesn't move any data anywhere.  That's the 2nd step in a good backup process.  All of this can happen while the system is running, actively being used.  Similarly, restoring an LVM snapshot will nearly instantaneously return the disk to that point. No data is moved.  

That's in an ideal world. If the disk with LVM and the snapshots is corrupted, then some or all of that data in the snapshot could be useless.

Everything about LVM snapshots applies to ZFS and BTRFS snapshots too.  These all are "volume managers" and have snapshot capabilities that don't copy/move any data, they just freeze existing blocks of data at a known instant and prevent modification of those storage blocks.  Any changes to the files that are frozen, have to be written elsewhere.

Timeshift knows how to work with BTRFS and BTRFS snapshots.  Snapshots still need a backup tool (or **sudo cp -rp**) to copy the data from the snapshot to some other storage.

For VMs, there are many different storage backends.  Virtualbox uses VDI files, KVM/QEMU uses qcow2 files, but supports perhaps 20 other storage methods, including ZFS, LVM, and cluster file systems.  Regardless, qcow2 and VDI have an internal idea of "snapshot" that freezes the blocks and begins writing any new or updated files at the end.  This is very handy for testing software when we need to restart tests with exactly the same initial data and nothing else.  LVM and ZFS can be used in this way without using virtual machines.

But, it is still true that for normal people, copying an entire vdi or qcow2 file into a "bak" file will be much easier to understand.  OTOH, those copies will take minutes (or longer) and use 2x the storage for each copy.  Real snapshots, as provided by volume managers, don't take any added space.

---

