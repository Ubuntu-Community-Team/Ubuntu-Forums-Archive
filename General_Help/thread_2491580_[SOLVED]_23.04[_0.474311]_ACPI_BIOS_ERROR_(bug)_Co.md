---
title: "[SOLVED] 23.04[ 0.474311] ACPI BIOS ERROR (bug): Could not resolve symbol [\]"
date: 2023-10-13
forum: General Help
---

### Post by blancobronco on 2023-10-13
[COLOR=#000000][FONT=Helvetica]I don't know what happened but after my OS went to sleep from a period of inactivity, I went to login in the usual way and the screen went blank. So I had to hard reboot the system and now I'm getting these messages.

I did an online search and tried all manners of corrections.

I'm not a programmer so I literally need a 

1 - do this
then
2 - do that 

set of instructions please and thank you for all suggestions:



[ 0.474311] ACPI BIOS ERROR (bug): Could not resolve symbol [\_SB.PC00.TXHC.R HUB.SS01], AE_NOT_FOUND (20221020/dswload2-162)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][     0.474330] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20221020/ps object-220)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][     0.474338] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PC00.TXHC.RHUB.SS02], AE_NOT_FOUND (20221020/dswload2-162)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][     0.474343] ACPI Error: AE_NOT-FOUND, During name lookup/catalog (20221020/ps object-220)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]/dev/ncme0n1p2: clean, 289008/31195136 files, 119143737/124751104 blocks[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][    2.818252] iwlwifi: No config found for PCI dev 54f)/0244, rev=0x370, rfid=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][    3.488093] Bluetooth: hci0: Failed to load Intel firmware file intel/ibt-0040-1050.sfi (-2)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][    3.488525] Bluetooth: hci0: Failed to read MSFT supported features (-56)[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-10-13
From your description, it was fine, then went to sleep, and on wakeup, the screen was blank.

You said you "rebooted"...

What does it do if you completely shutdown... Then boot cold?

---

### Post by blancobronco on 2023-10-13
Yes, the screen went black, no key that I pressed did anything, so I did a hard reboot; turned power off/on...when it loads
it ends up on a screen with the text I put in the original.

I have already backed up my files by accessing the hard drive from a boot disk.

I've tried everything else, even re-installing 23.04 but it says I have no hard drive space left...I know I do.

I'm lost

---

### Post by MAFoElffen on 2023-10-13
Being "out of space" could be your whole problem... Or it could be a corrupted filesystem, where it just thinks it's out of space.

Could you please post the results of these, this time using "Advanced Reply", press the "#" Icon in the Extended Tool Bar, which will insert CODE Tags, the pate the ouput within those Code Tags.
```

lsblk -e7 -o name,label,size,fstype,fsuse%,mountpoint

```
Mount the partitions of your install system from inside nautilus... by going to Other > the double click on the filesystems... Then in udisk (Disks) write down how they are mounted, then from a terminal, replace where I say <place_holder> with that path. Repeat for each partition that is mounted. It will most likely be /media/your_username/a_device_name/something/...
```

du <place_holder> -h 2>/dev/null | grep '^\s*[0-9\.]\+G'

```

---

### Post by blancobronco on 2023-10-13
I'm afraid I don't really understand what you are asking me to do, honestly.

So I cannot get into the OS, I just have the screen with those codes in the original post. How do I do any of the above from that screen?

Also, I tried hitting {delete} when the ubuntu logo came on as instructed on the screen, and I got a lot of code that spilt down the page. The only thing that stands out is this

[FAILED] Failed to start gdm.service -GNOME Display Manager, Aww 'systemctl status gdm.service' for details.

---

### Post by blancobronco on 2023-10-13
So I think I found a way to do at least a few of the things you asked by entering those commands on CNTRL-ALT-F2 terminal option

for the first command and I apologize because I cannot cut and paste as I'm typing it out character by character on another computer

```
name     label      size     fstype    fsuse%    mountpoint
          nvme0n1     476.9G
          nvme0n1p1         1G     VFAT       1%  /boot/efi
          nvme0n1p2  475.9G       ext 4      95%
```

---

### Post by MAFoElffen on 2023-10-14
You can do those commands from booting from an Installer LiveCD. Sorry, I thought you had one.

It looks like your hard disk it full (95%). 

Would need output from the second command to see where your space is being used.

---

### Post by blancobronco on 2023-10-14
Ok I will try with liveCD (USB).

I can reassure you that the hard drive is not full, and if it is, I have no idea how it became so.

I will put the second commands in now, if I have read them right...we'll see :)

---

### Post by blancobronco on 2023-10-14
[IMG]https://i.ibb.co/hmK2F9R/Screenshot-from-2023-10-14-05-48-24.png[/IMG]

First partition response 1.1GB:


```
bash: /dev/nvme0n1p1: Permission denied

```


Second partition response (the big one 511GB)

```
bash: /dev/nvme0n1p2: Permission denied

```


I should also mention that they say they are not mounted?


Third partition 1.5mb

```
bash: /dev/nvme0n1: Permission denied
```

---

### Post by blancobronco on 2023-10-14
> **blancobronco said:**
> Ok I will try with liveCD (USB).

I can reassure you that the hard drive is not full, and if it is, I have no idea how it became so.

I will put the second commands in now, if I have read them right...we'll see :)


So I went looking around and here's what I found as potential problem. In my video section I had something like 458GB of files :confused:

Then I remembered last week I installed Kazam to capture some screen recordings. It didn't seem to be working, I couldn't stop the video and then Kazam shut down for some reason. It must have been recording in the background and so I wasn't aware. Some of those files are huge. I have deleted them now, and will attempt to log back into the main installation again and let you know what happens.

---

### Post by MAFoElffen on 2023-10-14
Wow. LOL. Yes, "that" would do it. 

Since you deleted those and freed that space back up... It "should" start now.

Let me know how that goes for you.

---

### Post by blancobronco on 2023-10-14
Well I guess I can't be completely assured that one thing is not the problem because that turned out to be it. After deleting those files through the LiveCD login, I could login again normally. 

Who knew?  Well I guess you did. Thank you for your help!

Much appreciated.

Any ideas why permission was denied on the second command for the drives?
and one last request...
Any recommendations for a better screen capture program now? :)

---

### Post by MAFoElffen on 2023-10-14
Always happy to help. and happier when things work out well. LOL

Please select the "Thread Tools" link at the upper right to mark your thread as solved. That way other users can find what worked for you to solved their similar problems.

---

### Post by blancobronco on 2023-10-14
Will do. I put it in the title as well. But any idea why the permissions weren't allowing us to see the contents of the drives? I'm thinking maybe I should solve that now just in case I need to look in the future again?

---

### Post by MAFoElffen on 2023-10-16
Do this as a test from a LiveUSB
```

sudo mount -t vfat /dev/nvme0n1p1 /mnt
ls /mnt
sudo umount /mnt
sudo mount -t ext4 /dev/nvme0n1p2 /mnt
ls /mnt
sudo umount /mnt

```

---

