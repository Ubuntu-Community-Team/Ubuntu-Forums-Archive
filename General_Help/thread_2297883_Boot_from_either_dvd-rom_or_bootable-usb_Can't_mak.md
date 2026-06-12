---
title: "Boot from either dvd-rom or bootable-usb: Can't make it!!! Please help me out... ;("
date: 2015-10-07
forum: General Help
---

### Post by webwiller on 2015-10-07
**_This is my last thought but I think this is what I could have to solve things....which keyboard key you press at boot to get recovery choice, memtest and stuff screen???? Please.....and ty in adv!!! ;)_**


Hi there,
I'm baby-linux so please, treat me like if I was (which I am) :D .

Joking aside...

When I'm nervous messing up with PC and Oses does relax me and calm me down.
The other day was one of those days.




My Pc config before my messing up was:

1SSD 256mb With Win10
1HDD Sata 1Tb partitioned, 500mb for D:\ and same dor E:\

I downloaded ubuntu 14.04 LTS and with live CD & GParted I created a partition in C:\ (the SSD disk) and mounted wint into: /win

Fine.

Don't know what I did (when I mess up first I do, then I think. Inverted=perverted I know...

I lost my win partition And now noway I can get into windows10.

But the real main problem (I thought I could solve this....MAY-BE) but I needed to boot into live cd or bootUSB again. NOWAY.  i tried to play round with BIOS but nothing to do. It wont boot, And I get a S.M.A.R.T. Issue on the 1TB HDD. Anyway those are formatted and empty. 

Who can hel me boot into my bootable USB pen drive?

---

### Post by webwiller on 2015-10-07
What I would luke to do with my PC is:

First back to its hardware config which is: 1*256mb SSD + 1TBHDD partitioned into 1*500mb+1*500mb for data and data important backups.

Now what I'd like:

First want to recover my /win partition and, if possible, I'd like it to be shown as a HDD partition and NOT as a standard Directory.
Then I want my ubuntu partition in the 256mbSSD of kinda 27gb+3gb swap
Then I want my 2 partitions D&E to look like HDD partition and NOT Directories and want the mounted obv so that both Uby&Win can share them as good friends. Or I could also format E:/ with ext4 for Ubuntu data and leave D as it is (ntfs) for win. But for few reason I'd prefer both partitions to be ntfs and shared by the 2 OSes.

Gparted can hel me with the partition table (and I need help to make Gparted make a logic, ordinated, beatiful partition table. Dont mind backing up, messing all round I just want it to be my baby in the end and love it for the rest of my life... ;(
But how can I tel Mr.Ubuntu "Hey look, I'd like this partition to be shown as a HDD and not mounted as a Directory!" Would he understand me?! Guess not...

But I know that with your help guys we can make a really good job!

Many thanks in advance...and sorry for being so silly but today is the 4th day I get mad with this...and this is my reaction instead of swearing and shouting....

---

### Post by yancek on 2015-10-07
> 1HDD Sata 1Tb partitioned, 500mb for D:\ and same dor E:\

What are you doing with the other 999GB on that drive?  Did you actually mean 500GB not MB?

> 
I downloaded ubuntu 14.04 LTS and with live CD & GParted I created a  partition in C:\ (the SSD disk) and mounted wint into: /win

I have no idea what that means or why you would do it?  Do you mean you re-sized (shrunk) the C partition with your already installed windows to make room for Ubuntu? 

> if possible, I'd like it to be shown as a HDD partition and NOT as a standard Directory.

From Linux, partitions are accessible from mount points which are directories.  If you want it to be able to accesss other partitions by going to Computer or My Computer as in windows, you'll have to use windows.

To install Ubuntu you will have to format the partition with a Linux filesystem, ext4 being the default.  If you want to share data between windows and Linux you will need to use ntfs or vfat as a default windows system is totally incapable of recognizing the filesystem or reading or writing to it.  I think it would be a good idea to familiarize yourself with Linux drive/partition naming conventions which you can get from the page at the link below under Disk Management and Partitioning.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Reading your first post, I'm not really sure what you did.  If you wanted to shrink the windows partition to create unallocated space on which to put Ubuntu, you should have done that from windows.  GParted can modify partitions obviously but you are better off using windows software to change windows partitions and you usually need to run chkdsk from windows after doing any changes

I would suggest you boot the Ubuntu medium and post the output of:  sudo fdisk -l(Lower Case Letter L in the comnand).

---

### Post by buzzingrobot on 2015-10-07
> **webwiller said:**
> 


I downloaded ubuntu 14.04 LTS and with live CD & GParted I created a partition in C:\ (the SSD disk) and mounted wint into: /win 

I think you're saying your downloaded an Ubuntu install image, burned it to DVD, and successfully booted it?  Then, you used GParted.

However, you can't create a partition in "C:".  More accurately, "C:" lives on a partition. What you can do, though, is reduce the size of the partition that C: lives on, or simply delete that entire partition (and C: along with it).

> Who can hel me boot into my bootable USB pen drive?

Scroll down the page here and you'll find some instructions: [URL="http://www.ubuntu.com/download/desktop"]http://www.ubuntu.com/download/desktop.


[/URL]

---

