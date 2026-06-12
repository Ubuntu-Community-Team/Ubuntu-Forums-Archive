---
title: "PySDM package removed. Alternative?"
date: 2012-10-26
forum: General Help
---

### Post by SpeedoJoe on 2012-10-26
I used to install PySDM on Lubuntu 12.04 but today I have noticed that the package is no longer available in 12.10.

Does anyone know why it has been removed and/or if there is an alternative way of installing it excluding downloading a .deb manually?

---

### Post by coffeecat on 2012-10-26
Pysdm has been unmaintained since it was first developed in 2005 and often caused problems. The appearance of its [webpage]("http://pysdm.sourceforge.net/") reveals how neglected it is. As far as I remember it didn't support UUIDs in /etc/fstab nor the ext4 filesystem. I for one am giving hearty thanks that it has been removed from the repositories at last - there will be fewer people with damaged systems seeking help here now.

You don't need it. Automounting of partitions and devices from the file manager should cope with most of your needs. If you require partitions or devices to be mounted on boot, then there is no substitute for editing /etc/fstab manually.

---

### Post by techvish81 on 2012-10-26
actually there is a substitute,  it is " mount manager" and it is available in the repos.:-)

---

### Post by coffeecat on 2012-10-26
> **techvish81 said:**
> actually there is a substitute,  it is " mount manager" and it is available in the repos.:-)

Also a dead, unmaintained app. As is ntfs-config before someone else suggests this. I repeat:** If you require partitions or devices to be mounted on boot, then there is no substitute for editing /etc/fstab manually. ** It would be good if there was a reliable GUI app for this, but I know of none that I would let anywhere near my systems.

---

### Post by damo65 on 2012-10-28
> **coffeecat said:**
> Also a dead, unmaintained app. As is ntfs-config before someone else suggests this. I repeat:** If you require partitions or devices to be mounted on boot, then there is no substitute for editing /etc/fstab manually. ** It would be good if there was a reliable GUI app for this, but I know of none that I would let anywhere near my systems.

pysdm worked perfectly for me for years, in the absence of actually just automounting secondary (etc) hdd's on a system when installing the OS. The only thing I need this for is so my mp3 players can remember what and where my music is. I'm pretty sure that early Ubuntu versions (8.xx, maybe 9.xx) actually did auto mount all hdd's when doing the install. In other words, fstab didn't need to be manually altered after the event. I would like to see this fixed, please.  

I'm currently using arios automount, which does the job well enough, although I do need to remember to not have any external usb drives attached when I boot as it seems to mount those first.

---

### Post by techvish81 on 2012-10-28
> **damo65 said:**
> pysdm worked perfectly for me for years, in the absence of actually just automounting secondary (etc) hdd's on a system when installing the OS. The only thing I need this for is so my mp3 players can remember what and where my music is. I'm pretty sure that early Ubuntu versions (8.xx, maybe 9.xx) actually did auto mount all hdd's when doing the install. In other words, fstab didn't need to be manually altered after the event. I would like to see this fixed, please.  

I'm currently using arios automount, which does the job well enough, although I do need to remember to not have any external usb drives attached when I boot as it seems to mount those first.


i would also like to see it fixed,  i don't understand the logic behind not auto-mounting connected drives, ( they are connected,  so the user wants to use them, ) 

usb drives are auto-mounted without anything to be done manually.  i don't think it is hard to edit fstab.  but not intuitive for beginners and not matching the user friendly centric concept of ubuntu.

---

### Post by Mykro on 2012-11-05
I too would like to see a modern PySDM alternative.  I had my mounts set up perfectly, but forgot that /etc/fstab would be blown away by the 12.10 upgrade.  The automounting works well enough for one account, this is true, but if a second account logs on they are unable to access the drives as they have been mounted to /media/Mykro/drive1.  A shared hard drive of photos etc is a common scenario and it would be nice for people to be able to set this up graphically or have it "Just Work".

---

### Post by coffeecat on 2012-11-05
When using the term "automounting", we need to be clear whether we are talking about the automounting that occurs when you plug in a USB drive or click on a partition listed in the left pane of the file browser - this is the functionality built into Ubuntu/Kubuntu/Xubuntu. Or whether we are talking about setting up a custom mount line in /etc/fstab. Hence some comments:

> **Mykro said:**
> I had my mounts set up perfectly, but forgot that /etc/fstab would be blown away by the 12.10 upgrade.

An upgrade does **not** blow away /etc/fstab. If you had a working /etc/fstab in 12.04 it will work when you upgrade to 12.10 - it worked for me. So long as you are mounting the same partition with the same UUID and you have the same mountpoint that is referred to in /etc/fstab, it will work. If you have a problem with /etc/fstab following the upgrade, I suggest you look for a reason elsewhere. This is nothing to do with the new mountpoints - /media/username/ - that you see in 12.10 with udisks2.

> **Mykro said:**
> The automounting works well enough for one account, this is true, but if a second account logs on they are unable to access the drives as they have been mounted to /media/Mykro/drive1.  A shared hard drive of photos etc is a common scenario and it would be nice for people to be able to set this up graphically or have it "Just Work".

If by "automounting" you mean the automounting done by udisks2 when you plug an external drive in, or click on a partition in the file browser, then that is by design. If you want a partition mounted so that different accounts can use it, then create an entry in /etc/fstab. Which, by the way, was not broken by your upgrade.

> **techvish81 said:**
> i would also like to see it fixed,  i don't understand the logic behind not auto-mounting connected drives, ( they are connected,  so the user wants to use them, ) 

usb drives are auto-mounted without anything to be done manually.  i don't think it is hard to edit fstab.  but not intuitive for beginners and not matching the user friendly centric concept of ubuntu.

I don't follow your reasoning. If you plug in a USB drive, it is automounted. Easy. If you have an internal partition not yet mounted, you simply click on it in the left pane of the file browser, and it is automounted. Easy. The reasons for needing custom mounting in /etc/fstab are infrequent. I agree that hand-editing /etc/fstab is not intuitive, but that is out of Ubuntu's control. It needs a committed developer upstream to create an app, and be prepared to commit to maintaining it.  

If you mean that you would like to see Windows type behaviour, in that other internal partitions are immediately available from the file browser, then there are good reasons why I don't want all my partitions mounted automatically every time I boot up. However, as far as the user is concerned, it is **easier** in Ubuntu than in Windows. In Windows, open Explorer and you have to double-click on drive G: (say) to open it. In Ubuntu, open Nautilus (or Dolphin or Thunar for Kubuntu or Xubuntu) and single-click on the partition you want to browse. It is automounted and the file system appears in the main pane. Windows = **double**-click. Ubuntu = **single**-click. Much easier! :wink:

> **damo65 said:**
> pysdm worked perfectly for me for years, in the absence of actually just automounting secondary (etc) hdd's on a system when installing the OS.

You were lucky.

> **damo65 said:**
> The only thing I need this for is so my mp3 players can remember what and where my music is. I'm pretty sure that early Ubuntu versions (8.xx, maybe 9.xx) actually did auto mount all hdd's when doing the install.

Not so. Perhaps you used the "advanced" option with the installer and designated certain partitions for mounting, in which case the installer would have created custom /etc/fstab entries. In fact automounting - in the sense of USB drives being automounted or partitions when clicked on from Nautilus/Dolphin/Thunar - is far better than it was a few years ago.

> **damo65 said:**
>  In other words, fstab didn't need to be manually altered after the event. I would like to see this fixed, please.

Who are you asking? This is a forum.

> **damo65 said:**
> I'm currently using arios automount, which does the job well enough, although I do need to remember to not have any external usb drives attached when I boot as it seems to mount those first.

It seems to me that you are making life difficult for yourself. By your own admission, arios is interfering with the perfectly functional automounting functionality built in to Ubuntu. Arios does not create /etc/fstab entries, so it is not a substitute for pysdm. 

Let me be clear. I wish there was a reliable GUI app for creating /etc/fstab entries, but I do not know of one that I would let anywhere near my systems. Pysdm and ntfs-config are sad examples of good ideas where it seems that the initial interest of the developer has waned, leaving the app to neglect and bit-rot.

---

### Post by techvish81 on 2012-11-05
> **coffeecat said:**
> 


I don't follow your reasoning. If you plug in a USB drive, it is automounted. Easy. If you have an internal partition not yet mounted, you simply click on it in the left pane of the file browser, and it is automounted. Easy. The reasons for needing custom mounting in /etc/fstab are infrequent. I agree that hand-editing /etc/fstab is not intuitive, but that is out of Ubuntu's control. It needs a committed developer upstream to create an app, and be prepared to commit to maintaining it.  

If you mean that you would like to see Windows type behaviour, in that other internal partitions are immediately available from the file browser, then there are good reasons why I don't want all my partitions mounted automatically every time I boot up. However, as far as the user is concerned, it is **easier** in Ubuntu than in Windows. In Windows, open Explorer and you have to double-click on drive G: (say) to open it. In Ubuntu, open Nautilus (or Dolphin or Thunar for Kubuntu or Xubuntu) and single-click on the partition you want to browse. It is automounted and the file system appears in the main pane. Windows = **double**-click. Ubuntu = **single**-click. 

very informative post, thank you.  but to clarify i must say, i am not at all comparing it with windows. i just wish ubuntu to be much more user friendly  .  you are right that it is much easier in ubuntu, but i use several symlinks and therefore i need  a partition to be auto mounted at boot,  for symlinks to work.  if there is a option somewhere in the 'disks' or settings,  it would be much more user friendly. or if there is an app for that. that's all i want to say,  

there may be some reasons for not auto mounting at boot by default, i am sorry for not considering them.

---

### Post by azariah001 on 2013-06-14
Hi guys I know this thread is getting a little old but..... I went searching around and..... guess what Ubuntu's developers (core developers mind you not likely the wider community) have built in a GUI utility in Ubuntu 13.04 Raring. :D It's called "Disks" and you can change most of the options available in fstab without fiddling with the command line. :)

Just select the partition you want to change select the gears for options and uncheck the auto settings. That's pretty much it as the defaults that are pre-set after you uncheck, auto include, :P mount on startup. :) Check the article here [http://www.liberiangeek.net/2013/05/mounting-external-storage-devices-in-ubuntu-13-04-raring-ringtail-is-a-lot-easier-with-disks-tool/](http://www.liberiangeek.net/2013/05/mounting-external-storage-devices-in-ubuntu-13-04-raring-ringtail-is-a-lot-easier-with-disks-tool/) for more info.

---

### Post by Morbius1 on 2013-06-14
Assuming they can find anyone to take it on it will take a few professional developers a year or so to clean up the code in Disks so that it doesn't produce so many errors. Want an alternative to PySDM? _Templates_.

Here are the templates:
```
UUID=DA9056C19056A3B3 /media/WinX ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
UUID=C4DB-C1B0 /media/WinY vfat defaults,utf8,umask=000,uid=1000 0 2
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

```
Use the following to find the correct UUID:
```
sudo blkid -c /dev/null
```
Create your own mount points and you are good to go.

The best tool to make that all happen: gedit

---

