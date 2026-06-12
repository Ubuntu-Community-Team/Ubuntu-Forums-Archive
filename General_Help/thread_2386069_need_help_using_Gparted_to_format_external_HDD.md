---
title: "need help using Gparted to format external HDD"
date: 2018-02-28
forum: General Help
---

### Post by Buntu Bunny on 2018-02-28
Situation is that my hard drive died. I have been able to load a Xubuntu 16.04 live session into RAM, so I have access to Gparted. I have a new hard drive in an external enclosure and want to format it. Gparted recognizes it and the first step should be to unmount it, but when I right click on the bar I only see "mount" in the menu. However, it and all other options (including "format") are grayed out.

Following the directions in [Ubuntu Documentation here]("https://help.ubuntu.com/community/InstallingANewHardDrive"), I'm told 

> 1) Right-click on the white bar and choose "New."

2) For "New Size" the number should be the maximum allowable, to fill the entire disk. 

Note: my bar is gray, not white. When I right click it and select "new" it says 

> No partition table found on device /dev/sda. 
A partition table is required before partitions can be added.
To create a new partition table choose the menu item:
Device --> Create Partition Table.

I do that and am given a warning that all data will be erased. New partition table type is msdos, but "apply" doesn't change anything. I'm still in the same boat.

Obviously I'm stumped or I wouldn't be here. What am I doing wrong?

---

### Post by oldfred on 2018-02-28
You say in RAM, but is it from Live installer. Or are you unmounting that.

Do you really want MBR/msdos? If UEFI system you want gpt, and even if older BIOS system you can use gpt if you also add a bios_grub partition. Only if also installing Windows in BIOS boot mode would you still want the 35 year old MBR/msdos partitioning.

If drive is over 2TiB you have to use gpt.

And some external caddies do not recognize large drives or have other issues.

---

### Post by sudodus on 2018-02-28
It seems to me that you are doing things correctly.

How do you 'apply' - do you click on the tick icon?

Could it be that the external box is not compatible with either the HDD or the computer's USB system (hardwarewise or softwarewise)?  Can you try with the HDD connected internally?

It might work better without 'toram'.

---

### Post by Buntu Bunny on 2018-03-02
My apologies for not responding sooner. I thought I had subscribed to this thread through email but received no notifications of replies. Came by to check!

> **oldfred said:**
> You say in RAM, but is it from Live installer. Or are you unmounting that.

Old Fred my machine no longer recognizes my internal hard drive, but I am able to load Xubuntu 16.04 from a live DVD. I just can't save anything. No, I am not unmounting anything. 

> Do you really want MBR/msdos? If UEFI system you want gpt, and even if older BIOS system you can use gpt if you also add a bios_grub partition. Only if also installing Windows in BIOS boot mode would you still want the 35 year old MBR/msdos partitioning.

msdos is the only option Gparted offers me. 

> If drive is over 2TiB you have to use gpt.

And some external caddies do not recognize large drives or have other issues.

1 TiB. It was an inexpensive caddy but it's supposed to work with up to 1 TiB!

I also tried this with Lubuntu 17.10 on my laptop. The problem was the same so maybe it is the caddy. OTOH, I've been searching around for this problem and find others have had it as well. But the solutions don't fit for me. 

> **sudodus said:**
> It seems to me that you are doing things correctly.

How do you 'apply' - do you click on the tick icon?

Sudodus, "apply" is greyed out as well. 

> Could it be that the external box is not compatible with either the HDD or the computer's USB system (hardwarewise or softwarewise)?  Can you try with the HDD connected internally?  It might work better without 'toram'.

Well, since both you and Old Fred suggest it, it seems possible that it's the caddy. I haven't tried the HDD internally, but certainly will to see what happens.

I also have Gnome Disks on Lubuntu 17.10 and it recognizes the HDD plugged in externally. I haven't tried to do anything with that yet, however.

Thank you both for the replies!

---

### Post by sudodus on 2018-03-03
> **Buntu Bunny said:**
> Well, since both you and Old Fred suggest it, it seems possible that it's the caddy. I haven't tried the HDD internally, but certainly will to see what happens.


Let us know what happens, when you try the HDD internally :-)

---

