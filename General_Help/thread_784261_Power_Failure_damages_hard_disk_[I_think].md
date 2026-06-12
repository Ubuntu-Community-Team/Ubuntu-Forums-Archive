---
title: "Power Failure damages hard disk [I think]"
date: 2008-05-06
forum: General Help
---

### Post by Agentmilo on 2008-05-06
I have a Toshiba 120GB external USB hard disk. Recently I was using it on my dad's laptop, when suddenly the power went off. I was copying some files from the laptop to the usb hdd when it happened. The power went off just at the right moment :P. I was using Ubuntu 5.04 at the time.

Now the external drive works, but only in that specific version of Ubuntu; Yes, thats right, NO other OS. When I connect in Windows XP the system tray shows the external hdd icon, but nothing comes up. 

Also in Ubuntu, I can't write anything into the hdd. Only copy from it. When I do try to write, it says access denied.

When checking the properties, it says I'm not the owner of the drive. And all the options are grayed out.

What could be the problem? Why so suddenly can't I write into my own drive? The drive is around 8 months old. Also, please tell me how do I log into the Root user; when I do try to log into it via the Login window, it says the system administrator is not allowed to log in through here. 

Thanks in advance,
Milad

-You guys have quite a great community over here. Keep it up.

---

### Post by prshah on 2008-05-06
> **Agentmilo said:**
> 
Now the external drive works, but only in that specific version of Ubuntu; Yes, thats right, NO other OS. 

I'd suggest unmounting the drive and fsck'ing it (if ext2/3 based) or chkdsk'ing it (if it is NTFS/FAT32 based).

You can't log in as root user. If you need root access, place a "sudo" in front of whichever command you want to issue.

You can access a root terminal with the command ```
sudo -s
```, but this is risky and not generally recommended.

---

### Post by Agentmilo on 2008-05-06
When I click on unmount, I get an error "Cannot remove directory".

I had formatted it in Windows using FAT32 mode. Can you tell me exactly how I do chkdsk? I'm new to Ubuntu.

I appreciate your help, Thanks.

---

### Post by prshah on 2008-05-06
> **Agentmilo said:**
> 
I had formatted it in Windows using FAT32 mode. Can you tell me exactly how I do chkdsk? I'm new to Ubuntu.


If you can get in recognized in Windows, the command is (Start->Run) then ```
cmd.exe
chkdsk/f x:
``` where x: is your drive letter in windows. I suggest you try this first.

If (as you say) it's not working in windows, Applications-Accessories-Terminal, then ```
sudo umount /dev/xxx
sudo fsck -a /dev/xxx1
```

Where /dev/xxx is the device for the external drive, and xxx1 is the device+partion_number for the fat32 partition. (Eg: /dev/sdd1).

If you have doubts about the device address (/dev/xxx), then plug in the HDD and give the output of ```
dmesg | tail
sudo fdisk -l
mount
df

```

---

### Post by Agentmilo on 2008-05-07
Thanks, I will try it.

---

