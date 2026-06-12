---
title: "Ubuntu/Windows MBR issues"
date: 2008-04-11
forum: General Help
---

### Post by noxinvictus on 2008-04-11
Hello everyone, I've been using Ubuntu for just over a year now and have always went through these forums whenever experiencing any technical difficulties and always with success.  However, despite the number of threads I have read regarding my present dilemma, none appear to fit the ticket.   Here's a summary leading up to my present standings...

1.  Ubuntu Gutsy as exclusive partion/OS.
2.  Decided to install WinXP to run a few apps that Wine doesn't (yet) support well
3.  Partitioned some space... installed XP... success
4.  Windows snagged the MBR (imagine that), thus making Grub disappear... 
5.  Fixed MBR using guide ala [HERE]("http://ubuntuforums.org/showthread.php?t=224351")... success

And now... I do not have any option to boot XP.  It appears that most of the questions regarding this topic supposes that one installed Windows first (typically the case) and then later added Ubuntu.  I wish it were as easy because my first installation of a Linux distro was with Windows first... 

So how would one go about booting back into Windows or, all the better, given the dual-boot option to go with either OS?  Gparted recognizes the NTFS partition aside the others, but Start-Up Manager only shows the ext3 ones and thus will only give me the option to boot from one of the three Ubuntu interfaces.  Here is what fdisk shows:

```


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1757    14113071   83  Linux
/dev/sda2   *        1758        4678    23462932+   7  HPFS/NTFS
/dev/sda3            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris


```

Any advice as to who I may obtain the option to boot into Windows (without having to rewrite MBRs to go back into Ubuntu, repeat, ad nauseum)?  Thanks.

---

### Post by LaRoza on 2008-04-11
Just add Windows to grub.

Run:

```

gksudo gedit /boot/grub/menu.lst

```

Add this to the bottom. (You can make the title anything you want)


> 
title           Windows XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1



---

### Post by noxinvictus on 2008-04-11
Quick response, easy and effective edit.  Thanks a ton!

---

