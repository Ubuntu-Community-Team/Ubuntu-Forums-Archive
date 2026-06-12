---
title: "Mounting volume in GRUB"
date: 2023-03-22
forum: General Help
---

### Post by Mark Phelps on 2023-03-22
I'm using Ubuntu 22.04.1 and have a 40_custom file containing a list of boot stanzas, one for each ISO file I want to use.

While it works fine, the ISOs are stored in the Ubuntu filesystem in an isos folder.

I have added another distro to the drive and moved these ISOs to a separate partition.

I can access that partition inside Ubuntu because I added the partition to the FSTAB file.

But, when I boot into GRUB, it does not know about that partition because it is not mounted.

So, is there any way, like maybe in the Header file, to add a mount command to GRUB so it sees that directory?

---

### Post by MAFoElffen on 2023-03-22
You point the 40_custom loopback file pointers to that drive and new partition...

RE: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[quote="Ubuntu Wiki"]
loopback:

    The loopback line must reflect the actual location of the ISO file. In the example, the ISO file is stored in the user's Downloads folder. X is the drive number, starting with 0; Y is the partition number, starting with 1. sda5 would be designated as (hd0,5); sdb1 would be (hd1,1).
    
Other Location Examples:
        (hd0,5)/boot/$isofile    Located in the system's normal /boot partition on sda5
        (hd0,6)/$isofile            Located in a separate boot partition on sda6
        (hd0,7)/username/Downloads/$isofile    Located in a separate home partition on sda7
        (hd1,2)/iso/$isofile      Located in the /iso folder of the sdb2 data partition
[/quote]

---

### Post by Mark Phelps on 2023-03-23
Thanks for the quick reply and links ...

I read through the page and looked at the samples. and fhen booted into GRUB and then, into its command line.  

When I list the devices, there are four -- sda through sdd. Of these, sda is a Windows drive, sdb is the Linux drive.  On sdb, the ISOs partition is #6.  So, that would mean that the command format should be (hd1,6).  

I did several ls commands using that and confirmed that command sees the ISOs partition and the contents of the iso-files directory in that partition.  So, I modified the GRUB stanzas to use the hd1,6 entry.

But when I boot the GRUB menu and select that stanza, it fails repeatedly with an error message about NTFS errors encountered while mounting sda4 -- which is a partition on the first Windows drive!

So, when I point GRUB to hd1,6, why is it trying to mount hd0,4?  There are no entries in the GRUB stanzas for hd0 -- those are all Windows partitions.

I read through the examples again and again, and from what I can tell, to load the six partition on the second drive, I should use hd1,6 -- which is what I am doing.

As a test, I changed that to hd0,6 -- but that did not work (of course).

So, now what?

---

### Post by yancek on 2023-03-24
>   it fails repeatedly with an error message about NTFS errors encountered while mounting sda4 

Could you try this again and get the exact error to post?  If I understand correctly, you are booting from Grub on an installed Ubuntu system and trying to boot an iso file on (hd1,6).  Do you have an entry in the Ubuntu /etc/fstab for the windows partition?  If so, comment it out by placing a # at the beginning of its line. The link below to the Grub Manual shows a list of commands available.  Note that mount is not there.  You are getting that error from Ubuntu.  If that doesn't resolve the problem, I have no other suggestions.  Good luck.


[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

---

### Post by tea for one on 2023-03-24
Are you able to isolate, de-activate or physically remove your disks?

Leave attached your Ubuntu OS disk which contains partition 6.
The only accessible disk should then be sda.
The target [COLOR="#0000FF"]loopback loop (hd0,6)$isofile[/COLOR] should be fine.

---

### Post by oldfred on 2023-03-24
Are the ISO in a folder in hd1,6?

I always forget to update grub when updating or changing ISO. So I created one permanent boot stanza in grub's 40_custom to configfile to a text file in my ISO folder. 

Entry in grub that I never change, note that it is second drive and folder /ISO, I use labels to find it:

 ```
menuentry 'Live ISOs in data drive' {
search --set=root --label data --hint hd1,gpt4
configfile /ISO/livecdimage.cfg
} 

```

Then /ISO/livecdimage.cfg is similar to 40_custom with boot stanza. 

```
menuentry "Kubuntu 22.04 Jammy amd64 loopback.cfg" {
      iso_path=/ISO/jammy-desktop-amd64.iso
      export iso_path
      loopback loop $iso_path
      set root=(loop)
      configfile /boot/grub/loopback.cfg
    }

```

But if I plug a flash drive in & reboot it often is hd0, so when trying to boot ISO I have to manually edit drive from hd1 to hd2,
Or if booting directly from my sdb drive that drive becomes hd0, so default entries need to be different to boot same ISOs.

---

### Post by Mark Phelps on 2023-03-24
Thanks for the additional replies ...

My responses:

The  error is what I posted -- GRUB is failing on an MFT error when trying to force a mount of the NTFS partition #4 on drive zero -- when the GRUB stanza is telling it to mount partition #6 on drive one.

There are no Windows partition or drive entries in my FSTAB file, only entries for Linux partitions.

The drives are not easily removed as they are NVMe sticks attached to the motherboard with heatsinks on top of them.

Yes, the ISOs are all in the same iso-files folder on partition #6 on the Linux drive. When I boot into the command line in GRUB and do ls commands, they see the partition and ISO files without problems.

I will try the liveimage.cfg approach and see what happens.

---

### Post by Mark Phelps on 2023-03-24
@oldfred:

Many thanks for the details -- but I am confused by part of what you wrote.

In the 40_custom entry, it points to a config file livecdimage.cfg

But in that file, it points to another config file loopback.cfg

In looked into my /boot/grub folder and there is a grub.cfg file there but no loopback.cfg file there, so is this something I have to create?

---

### Post by oldfred on 2023-03-24
Oh,
That was one of my experiments. I normally just boot grub.cfg but notices the loopback file and tried it. 
With the loopback entry I got the install menu, where with grub, it just boots into live mode & I can install from that.

```
menuentry "Kubuntu 23.04 Lunar Daily Live ISO" {
    set isofile="/ISO/lunar-desktop-amd64.iso"
    loopback loop (hd1,5)$isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram noeject
        initrd (loop)/casper/initrd
}

```

I do show both grub & loopback in /grub in the ISO. Either should work if you want grub menu.
Above entry just boots directly.

---

### Post by MAFoElffen on 2023-03-24
In your post(s) you referred to sda, sda, etc... Which is triggered after the Kernel boots, and assigns sda to what is the first booted drive. Just as Windows assigns drive C: to what it booted as.

You need to go to Grub command line from the Grub2 menu, and investigate how Grub2 see's the drives (That is what I do). Grub usually follows what the BIOS recognizes as the drive order... which can be a different order than both Windows and Linux OS'es see them.

At the Grub prompt
```

grub > ls (hd<Tab>

```
Then when you see the usual suspects... Follow the bread crumbs.
```

grub > ls (hd0,gpt1)/

```
And follow the bread crumbs until you find your ISO files.

---

### Post by Mark Phelps on 2023-03-24
@oldfred: Thanks for the changes -- I will try those.

@MAFoElffen -- as mentioned, I booted into the GRUB command line, did a bunch of ls commands and confirmed they pointed to the ISO files. That's where I got the (hd1,6) that I put into the GRUB stanzas.

---

### Post by MAFoElffen on 2023-03-24
I don't see where you posted the contents of your 40_custom file...

oldfred has posted examples... But I do not see what 'you' are doing.

Maybe if we saw that, something might pop out from other's perspectives being able to see that(?). Just reaching for more info to try to help you...

---

### Post by Mark Phelps on 2023-03-24
OK, here is the entry I added to the 40_custom file:

> 
menuentry "Live ISOs in ISOs directory" {
search --set=root --label data --hint hd1,gpt6
configfile /iso-files/livecdimage.cfg
}


Here is the contents of the livecdimage.cfg file:
> 
#!/bin/sh

menuentry "ISO Clonezilla live from miso-files" {
set isofile1="/iso-files/clonezilla-live.iso"
loopback loop (hd1,6)$isofile1
linux (loop)/live/vmlinuz boot=live union=overlay username=user config components noswap nolocales edd=on nomodeset nodmraid ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" keyboard-layouts= ocs_live_batch=\"no\" locales= vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile1
initrd (loop)/live/initrd.img
}

menuentry "ISO Rescuezilla live from iso-files" {
set isofile4="/iso-files/rescuezilla-live.iso"
loopback loop (hd1,6)$isofile4
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile4 quiet noeject toram splash
initrd (loop)/casper/initrd.lz
}                


When I select the Live ISOs entry in the GRUB menu, the screen clears, the following message is displayed:

Press any key to continue ...

I press any key or wait a few seconds, and the GRUB menu reappears.

Nothing else happens.

When I do "ls (hd1,6)/iso-files/" in GRUB command prompt, I get the list of files in that folder.

---

### Post by oldfred on 2023-03-24
My ISO folder is in a data partition, so labeled.
So my find the drive is really by label.

> [FONT=monospace][COLOR=#000000]     FSTYPE   SIZE FSUSED   LABEL  PARTLABEL [/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]sda6   ext4   302.7G 117.8G data   data  

 [/COLOR][/FONT]

Notes not updates as from another install. Filename is livecdimage.cfg
```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd1,3)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
```

---

### Post by Mark Phelps on 2023-03-25
OK ... missed that.  Thought "data" was the type of partition.

I will change the label and see what happens.

---

### Post by Mark Phelps on 2023-03-25
@oldfred:

That made all the difference!!  I changed the "label" -- and now it works!!

Thanks so much for the code.

---

### Post by oldfred on 2023-03-25
Glad you got it working.
Sometimes we assume that something is obvious when the first time is is not so clear.

---

