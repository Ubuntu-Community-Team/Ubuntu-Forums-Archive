---
title: "grub, new XP install, no grub"
date: 2007-10-22
forum: General Help
---

### Post by pha3r0 on 2007-10-22
I installed xp again for my wife (against my wishes) and now i am having trouble getting grub to boot either. currently the PC is botting and saying NTLDR missing (so what imo, i just need to get my linux partition back booting really.) I tried following instructions in a few threads i found, [Recover GRUB after XP install]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), and some others but im obviously missing something.

Following is my drive info from fdisk:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35518   285298303+  83  Linux
/dev/sda2           35519       48266   102398310    7  HPFS/NTFS
/dev/sda3           48267       48641     3012187+   5  Extended
/dev/sda5           48267       48641     3012156   82  Linux swap / Solaris


I set /dev/sda1 as boot which allowed me to get back in with my live CD and choosing "boot first hard drive"

setting it to anything else wont boot (missing NTLDR etc.)

I dont know where to go next or what info might be needed so if you need anything else just ask, and as usual thanks in advance.

P.S. worst case I will merge the partitions back together tell my wife I stopped using windows for a reason and if she want's it she can do it herself.

---

### Post by p_quarles on 2007-10-22
Did the directions in that link not work, or do you think you could benefit from some help understanding them? 

If it's the latter, I'm happy to try to help. If it just didn't work at all, though, I would suspect that some data got corrupted during the partitioning process, and you might be looking at a full reinstallation. 

Some ideas to consider:
1) Installing Windows first will make things go much easier (simply because Linux plays nicer with other OSes). You already have the partitions, so this would be pretty straightforward.

2) You might look at running Windows inside Virtualbox. That way you could install Ubuntu on the entire disk, and then whenever anyone wanted to use Windows they could simply load up the virtual machine. This has the added advantage of being more secure than a normal Windows installation, particularly if the users aren't very security-conscious.

---

### Post by pha3r0 on 2007-10-22
It's not a corrupt partition, I am writing this from my Ubuntu instalation now. and unfortunately using VMware is not an acceptable solution for her windows needs, although im sure if i was a guru i could make something work with wine or something, its just not the way to go right now.

As it stands I can boot and reboot using my live CD as i described above and i am fine with that but i would like to at least get back to having it boot on its own and preferably get windows running on its partition. 

Now windows does run but since this is my work computer and i took a lot of time transferring all of my work to a linux environment, finally, I'm not going to forsake that and go back to that damned OS just to please my wifes gaming fancies. After all i spent a lot of my childhood tinkering with early redhat and slackware distro's and now that I am doing web design I am really greatful to have powerful tools that i can use running on a very friendly system.

As far as the option of letting go and re-installing the entire system windows first, well I have everything backed up and burned a CD just now just in case you think that would be much easier then tracking down my trouble, and I am okay with that answer... Hell the time i spent today on this already i could have gone that route i think.

---

### Post by p_quarles on 2007-10-22
For gaming, you're correct: dual-booting is the best option. It is possible to get a number of games working either in Wine or Cedega, but if you have a Windows license then it's just more trouble than it's worth.

I really do think that the instructions you linked to should work unless there's a problem either with Windows or with Ubuntu on the disk. The entire filesystem doesn't need to be corrupt for something the boot directory to be messed up. So, yeah, reinstalling is probably the most straightforward way to fix this. If you haven't already, though, I'd give the Super GRUB Disk mentioned in your link a try first.

---

### Post by CouchMaster on 2007-10-22
You might try opening a terminal as root and typing
grub
root (hd0,0)
setup (hd1)
quit
Now I'm guessing here because you have windows on the 2nd. partition instead of the 1st., and I'm assuming that windows tried to take back the mbr on the 2nd partition.  Remember that Linux counts from zero so zero is actually the 1st partition etc.
If that doesn't work you can experiment and use a live CD to change grub if you can no longer boot the HD normally.

---

### Post by pha3r0 on 2007-10-22
I will try super grub now. (i checked that off before since i was running on the live CD and couldn't burn anything, if that fixes it ill feel bad for asking) and if that does not help I will try what couchmaster suggests, although they are quite similar to what i have already done i will just try again

---

### Post by pha3r0 on 2007-10-23
Problem solved... I used the Super GRUB bootdisk to automatically restore the MBR. While it was not as straight forward as it could be I am greatful yet again for those behind it, and for p_quarles pointing me back to it...

...Now to go install that damned WoW, god if i could DL a fully patched install now that would rock

Thank you again p_quarles, you saved me a lot of time.

---

