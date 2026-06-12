---
title: "Unable to Restore Grub Loader of Dual-booted Laptop w/ Ubuntu 16.04 &amp; Win 10"
date: 2018-05-12
forum: General Help
---

### Post by moxie99 on 2018-05-12
[COLOR=#000000][FONT=times\ new\ roman]Have  an Acer Aspire V3-571 64-bit laptop dual-booted with Windows 10 Home  Edition and Ubuntu 16.04.3 LTS. Previous large Windows updates did not  mess with grub loader, but the April 2018 Win 10 update killed the grub  loader. Error message (quotation marks mine):
[/FONT][/COLOR]
[COLOR=#000000][FONT=times\ new\ roman]" error: no such partition.
[/FONT][/COLOR]
[COLOR=#000000][FONT=times\ new\ roman]   Entering rescue mode...
[/FONT][/COLOR]
[COLOR=#000000][FONT=times\ new\ roman]   grub rescue>_ "
[/FONT][/COLOR]
[COLOR=#000000][FONT=times\ new\ roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times\ new\ roman]The screenshots below were obtained via the Ubuntu 16.04 iso DVD which I used to access my laptop via the optical drive. 

[/FONT][/COLOR]
[COLOR=#000000][FONT=times\ new\ roman]Tried to solve on my own. Have read various posts & tried several proposed solutions (kept only sketchy notes), but thus far, have been unable to restore grub. Would like to ask for your help. Please advise. Thanks in advance.

[/FONT][/COLOR]

---

### Post by oldfred on 2018-05-12
All the way back to Windows 7, Windows has a bug (they may call it a feature) that rewrites partition table on upgrades or major changes. And then they forget to write the Linux logical partition back into the partition table. Data is still there, if you have not otherwise done anything.
Some just restore partition to partition table and it boots, others have to also totally reinstall grub.

Use testdisk or parted rescue to find & restore missing partition.
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
        [https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue) 
    
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
        [https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

---

### Post by dragonfly41 on 2018-05-12
Note that two of above links with shortened url ... are broken .. 404 error.

---

### Post by oldfred on 2018-05-12
Thanks dragonfly41, fixed the shortened URLs. 
Not sure how I got those, as I know the forum shortens them, and try to only copy from source not from a post.

---

### Post by moxie99 on 2018-05-30
Am replying to my original post, with the following update. In spite of attempts to restore grub loader, I have been unable to. My makeshift solution is to boot Ubuntu with an Ubuntu iso & select "Try Ubuntu." I can get into Windows 10 by using the Super Grub2 iso CD. I am temporarily giving up on the restoration of the grub loader. Am unsure if this fix qualifies as a solution, for the purpose of signing off on this thread.  Unhappily, this fix is the best I can do for now. Thanks again.

---

### Post by oldfred on 2018-05-30
Did you try restoring the partition to the partition table with testdisk or parted rescue?
You cannot fix grub unless you do that.

And if you do not fix grub, you still can reinstall a Windows boot loader to boot Windows directly. Best to use your Windows repair disk or installer, if it has the repair console.

---

