---
title: "Help transferring files"
date: 2015-05-30
forum: General Help
---

### Post by ty_me_up on 2015-05-30
Hello,

First off, if you respond please put everything in layman's terms as I am not savvy with some computer areas. I am in desperate need of help and have searched so many ancient threads to no avail. 

My Macbook crashed awhile back and instead of spending an insane amount of money to get the files off of it I thought I would try my hand with Ubuntu. No need to post an opinion on whether or not this is a good idea, I simply have no other choice. So as I said, I would like to get my files off of my Mac side to an external hard drive using Ubuntu. I have installed Ubuntu onto a different flash drive and have tried booting up my computer to access the Mac files through it; however, I am not able to see the local drive for my Mac side under devices. I'm hoping someone can be kind enough to walk me through this with as much description as possible. Also I CAN NOT risk losing these mac files as it is several years of data, so if there is any way to get them onto an external hard drive I would be forever grateful! Please help if you can.

---

### Post by monkeybrain20122 on 2015-05-30
[http://ubuntuforums.org/showthread.php?t=1939428](http://ubuntuforums.org/showthread.php?t=1939428)

---

### Post by HermanAB on 2015-05-30
You can google for "linux mount mac hfs" to get slew of howto guides.

---

### Post by ty_me_up on 2015-05-30
> **monkeybrain20122 said:**
> [http://ubuntuforums.org/showthread.php?t=1939428](http://ubuntuforums.org/showthread.php?t=1939428)

I tried the first code prompt but I have no clue what the codes displayed mean and which device is which...


> **HermanAB said:**
> You can google for "linux mount mac hfs" to get slew of howto guides.

I have spent the last few days searching online and haven't found anything.  The things I have found that are somewhat relevant are years old and are still confusing because I don't know code.  If one of you could explain a bit more, that would be a huge help :/

---

### Post by coffeecat on 2015-05-30
I'll see if I can help. Getting files off a Mac-formatted HFS+ drive is quite possible but permissions and ownerships on files can trip you up. First thing. What is the formatting of the external hard drive you want to copy to? Is it NTFS? If that doesn't mean anything to you, did you format it in a Windows machine, in a Mac machine or did you buy it already formatted? If already formatted, was it pre-formatted for an Apple machine or a Windows machine? The question is important because to do this exercise elegantly it's better if the external HD is formatted NTFS - a Microsoft filesystem. NTFS can be written to from Ubuntu and it is has the advantage of side-stepping all the permissions and ownership problems. 

You can use a FAT32 formatted external hard-drive instead, but this has the disadvantage of a 4GB filesize limit, which means that large video files - for example - won't be copied.

Once you've confirmed what sort of external hard drive you have, I'll talk you through a GUI way of doing this by drag and drop rather than using terminal commands.

---

### Post by ty_me_up on 2015-05-30
> **coffeecat said:**
> I'll see if I can help. Getting files off a Mac-formatted HFS+ drive is quite possible but permissions and ownerships on files can trip you up. First thing. What is the formatting of the external hard drive you want to copy to? Is it NTFS? If that doesn't mean anything to you, did you format it in a Windows machine, in a Mac machine or did you buy it already formatted? If already formatted, was it pre-formatted for an Apple machine or a Windows machine? The question is important because to do this exercise elegantly it's better if the external HD is formatted NTFS - a Microsoft filesystem. NTFS can be written to from Ubuntu and it is has the advantage of side-stepping all the permissions and ownership problems. 

You can use a FAT32 formatted external hard-drive instead, but this has the disadvantage of a 4GB filesize limit, which means that large video files - for example - won't be copied.

Once you've confirmed what sort of external hard drive you have, I'll talk you through a GUI way of doing this by drag and drop rather than using terminal commands.

Thanks for the reply!  The external HD is formatted for a Mac, I did this before getting Ubuntu.

---

### Post by coffeecat on 2015-05-30
> **ty_me_up said:**
> Thanks for the reply!  The external HD is formatted for a Mac, I did this before getting Ubuntu.

Then we need to stop at this point and think this through. The Apple HFS+ filesystem is really only of use in the Apple world. Ubuntu can read from it but not write to the journalled version. Even reading from HFS+ presents challenges because of the aforementioned permissions and ownership isues. Which is why I will give you a GUI workaround for this when the time comes.

But back to the external HD you are intending to write to. Do you ever intend to use that external HD with a Mac? If not, then I suggest you reformat it. Which leads us to what filesystem you use. I note that you seem to be intending to use Ubuntu as a temporary measure. Do you have access to a Windows machine, or do you use Windows at all regularly? Or do you intend to convert to Ubuntu? Or possibly use a mixture of Ubuntu and Windows, or Ubuntu and MacOS or some other combination?

**Edit:** a subsidiary question, which may be important depending on how we proceed. When you say you installed Ubuntu to a flash drive, do you mean that you prepared a live USB which boots up to a live session, or did you do a "proper" installation which included creating an account with a username and password of your own choice?

---

### Post by ty_me_up on 2015-05-30
> **coffeecat said:**
> ABOVE POST


As for Ubuntu, I have a bootable version on the USB, it is not actually installed on my laptop.  Also I only intend to use Ubuntu as a temporary way to get my Mac files to an external HD.  Also, the Ubuntu flash drive is a different on from the external I want to transfer my files to.

That being said I would like to be able to access my files from my Mac again, say after reformatting my laptop to its original and using the external HD to transfer the files back.  

The only Windows computer I have available is my brother Mac with Windows Bootcamp.  If that would be useful at all.  I do not, however, have any way of connecting the 2 computers with one of those single cords.

---

### Post by Morbius1 on 2015-05-30
> My Macbook crashed awhile back 
Crashed as in it won't boot. Or crashed as in it won't let you login.

The reason I asked is because of this:
> The only Windows computer I have available is my brother Mac with Windows Bootcamp.

One mac can be booted into Target Disk Mode while it's connected to another mac via firewire or thunderbolt. When you do that the "brother mac" will see the other mac on it's desktop as an external disk drive.

I have only done this once - I repeat I have only done this once - just to see if it works so I would suggest you follow Apple's instructions rather than rely on my memory:
[Transfer files between two computers using target disk mode]("https://support.apple.com/kb/PH19021?locale=en_US")

Or ask about it in the Apple forum.

---

### Post by ty_me_up on 2015-05-30
> **Morbius1 said:**
> Crashed as in it won't boot. Or crashed as in it won't let you login.

The reason I asked is because of this:

One mac can be booted into Target Disk Mode while it's connected to another mac via firewire or thunderbolt. When you do that the "brother mac" will see the other mac on it's desktop as an external disk drive.

I have only done this once - I repeat I have only done this once - just to see if it works so I would suggest you follow Apple's instructions rather than rely on my memory:
[Transfer files between two computers using target disk mode]("https://support.apple.com/kb/PH19021?locale=en_US")

Or ask about it in the Apple forum.

I meant my Mac won't boot up.  It goes to the Apple logo and the loading bar underneath that never finishes.  I'm trying to use Ubuntu as that is the only way I have seen online other than spending the money to take it into a shop.

As for hooking up my Mac to the other Mac, like I said I don't have the FireWire cords nor do I have the money for one right now.  So Ubuntu is my only option.

---

### Post by coffeecat on 2015-05-30
> **ty_me_up said:**
> As for Ubuntu, I have a bootable version on the USB, it is not actually installed on my laptop.  

Which doesn't really answer my question. It's a bit moot now in the context of what you have said subsequently, but what I was trying to get from you was whether you simply burnt the ISO to the USB stick or whether you did a proper installation of Ubuntu. There are some practical implications which would affect the advice given.

> **ty_me_up said:**
> Also I only intend to use Ubuntu as a temporary way to get my Mac files to an external HD.

This is a very fundamental point. I'll infer from this that you need the files on the Mac-formatted drive so that you can use them with another Apple machine in the future. It is possible to do this in Ubuntu but, quite frankly, I'm not prepared to walk a newcomer to Linux through the arcane steps needed to do this which, in essence, would be:

1 - Reformat the external drive with the unformatted version of HFS+ using Ubuntu, or your brother's Mac. 

2 - Use a terminal to invoke root privileges to copy all the necessary files, whilst preserving their permissions and ownership. That would be fairly easy if I was standing in the same room as you - a nightmare to get all the necessary information when you're trying to help someone in a forum. 

When I offered a GUI method earlier, I was making the mistaken assumption that the destination hard drive wasn't, or didn't have to be, formatted with an Apple filesystem.

Now, from your first post:

> **ty_me_up said:**
> however, I am not able to see the local drive for my Mac side under devices.

That worries me somewhat. If you can't see the internal drive partition, that might mean that the hard drive is failing, or has failed. We haven't really established why MacOS is not booting, and a failing HD is a possibility.

This is how you find your internal drive/partition. In the Ubuntu desktop, near the top of the dock on the left, there is an icon that looks like a filing cabinet. Click on that to open the file manager. In the left pane, possibly under the trash icon depending on the actual release of Ubuntu that you are using, will be a list of detected devices and partitions. If your MacOS partition has been detected, it will be listed either as "XX GB Filesystem" (or similar) if the partition has no label, or the partition label if it has. Simply click on that line, the partition will be mounted and you will see the folder structure in the main pane. You will see them as they actually are, not as you have been used to seeing them in MacOS, which gives a simplified impression of the file structure to the user. You will find your personal files in the User (Users?) folder.

> **ty_me_up said:**
> As for hooking up my Mac to the other Mac, like I said I don't have the FireWire cords nor do I have the money for one right now. So Ubuntu is my only option. So Ubuntu is my only option.

Well, I don't know. Bearing in mind what I said above, using Ubuntu to try to copy your files to a Mac-formatted HD may not be easy or even feasible. I'm not trying to be difficult, but operating systems are designed to work best with their own native filesystems, that's even before you run into all the permissions and file ownership issues I've already mentioned.

---

### Post by ty_me_up on 2015-05-30
Well from what you have said it seems like this is going to be too difficult for a walk through.  Because I can't see my Mac under "devices" I'm assuming there isn't any easy way to locate it, like you said.  As for the reason my Mac won't boot up, I have no clue.  I have been on multiple Apple forums and called their service department many times.  This was my last resort to not have to pay kids of money for a repair.  Thanks for trying.

---

### Post by coffeecat on 2015-05-30
One last thing. It might be possible to obtain some sort of clue as to what might be happening to your internal hard drive from Ubuntu. In the following I'm assuming that you are using Ubuntu 14.04, 14.10 or 15.04. You never actually said which release of Ubuntu you are using.

From the Ubuntu desktop open a terminal with ctrl-alt-t. Run this command:

```
sudo fdisk -lu
```

Copy and paste the output into your post. Keyboard shortcuts are different in the terminal. Highlight the output with the mouse/trackpad, right-click -> Copy. You can then paste the output into your post with the usual ctrl-v shortcut - or right-click in the editor -> Paste.

Next thing is you can check the SMART status of the internal drive. Click on the topmost icon in the dock and type "disks" into the dash. Open the Disks utility. The interface has detail differences between the different Ubuntu releases, but you should be able to see all detected devices in the left pane. Do you see the internal HD? If you do, highlight it and look for SMART on the right somewhere. In my Ubuntu 15.04 it is hidden in the dropdown menu accessible from the icon that looks like three horizontal lines. In earlier versions of Ubuntu, the interface was more user friendly (blame the gnome devs for making it obscure) and a SMART option was more obvious. Check the SMART data and run the self-test. This tells you about the health of the drive.

---

