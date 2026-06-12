---
title: "Can't Read Superblock"
date: 2019-05-13
forum: General Help
---

### Post by electrosteam on 2019-05-13
Lubuntu 18.04.2 32 bit 4.18.0-18-generic desktop.

My laptop power supply failed and the replacement is a tower.
Laptop critical data had been backed up but interested in transferring all the data to the tower. 

Used a USB Adapter cable to connect the laptop hard drive to a Windows 10 machine and transferred the data to a USB flashdrive

When I connect to my Linux machine and attempt to view I get an error message:

Error mounting /dev/sdb1 at /media/john/......: can't read superblock on /dev/sdb1.

Although I now have the data, I am a keen linux learner, but need some encouragement on just how to solve the problem.
I have seen 'fsck -y /dev.sdb1' suggested but entering 'man fsck' does not show an option '-y'.

Is the '-y' safe ?
Any other suggestions ?
John.

---

### Post by Rubi1200 on 2019-05-13
Hi,

check here for what the -y option does [https://linux.die.net/man/8/fsck](https://linux.die.net/man/8/fsck)

Scroll down [https://prnt.sc/nnwki7](https://prnt.sc/nnwki7)

Basically, -y tells fsck to attempt to fix any problems it finds.

A safer option is to just run fsck first to determine what problems, if any, are there.

So, for example:

```
fsck /dev/sdb1
```

If it returns an error code or specifies problems it found then you can try the -y option.

In any event, if you are concerned about data integrity first run fsck as in my example and if in doubt about the results post back here so we can advise.

Hope this helps.

---

### Post by electrosteam on 2019-05-13
Thanks for taking the interest, tried the command suggested:

```

john@Lionel:~$ sudo fsck /dev/sdb1
[sudo] password for john: 
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sdb1: recovering journal
fsck.ext4: Unknown code ____ 251 while recovering journal of /dev/sdb1
fsck.ext4: unable to set superblock flags on /dev/sdb1

/dev/sdb1: ********** WARNING: Filesystem still has errors **********


```

John.

Subseqently:
Tried the '-y' parameter, it got rid of the '__251' but still shows the 'WARNING'.

---

### Post by Rubi1200 on 2019-05-13
Are you able to access and backup all your important data?

If yes, please do so and then boot the computer with a liveCD/USB and run this command on the unmounted file system:

```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```

---

### Post by electrosteam on 2019-05-13
Used my Lubuntu install disc:
```

lubuntu@lubuntu:/$ sudo e2fsck -C0 -p -f -v /dev/sdb1
/dev/sdb1: recovering journal
e2fsck: Unknown code ____ 251 while recovering journal of /dev/sdb1
e2fsck: unable to set superblock flags on /dev/sdb1


/dev/sdb1: ********** WARNING: Filesystem still has errors **********

```

One issue now is my Thunderbird client has been stripped of all its contacts !
I will investigate that separately and raise a new thread if necessary.
John.

---

### Post by Rubi1200 on 2019-05-13
I was concerned it would not work (not sure what the Thunderbird issue is all about).

So, the next step is to try and replace the bad superblock with a good one. If this does not work, then you may have to accept that the drive is failing and needs to be replaced but let's first try this.

Again, from the live install disk in Try mode run these commands:

```
sudo dumpe2fs /dev/sdb1 | grep -i backup
```

What this should return is a number or numbers of good superblocks.

Note the numbers carefully and then run this command:

```
sudo fsck -b 32768 /dev/sdb1
```

The number 32768 is just an example, your superblocks may be numbered differently.

You may also need to try more than one superblock if the first one does not work.

If running with the -b option works you should be okay (fingers crossed).

---

### Post by electrosteam on 2019-05-14
Rubi1200,
thanks for taking the time and support:
```

ubuntu@lubuntu:~$ sudo dumpe2fs /dev/sdb1 | grep -i backup
dumpe2fs 1.44.1 (24-Mar-2018)
dumpe2fs: Input/output error while trying to open /dev/sdb1

```

Took over 8 minutes to make the error response.
John

---

### Post by Rubi1200 on 2019-05-14
Okay, if you are on the liveCD/USB open GParted and if you have a swap partition make sure it is off; right-click >> swapoff

Then try this command:

```
sudo mke2fs -n /dev/sdb1
```

It should show you a list of superblocks.

If yes, then try this again:

```
sudo e2fsck -b 32768 /dev/sdb1
```

Change block number as relevant.

Reboot.

If the problem is fixed, great.

If not, you will have to repeat the above steps using another superblock until there are no more errors.

---

### Post by electrosteam on 2019-05-14
On normal boot:
Used Synaptic to install GParted, just opened it to see interactive window, closed.

On live CD:
On the terminal: dmesg, lshw show presence of sdb and identify brand and size.

On live CD GUI:
gparted came up without installing, launched.

Pop-up window:
[ Error fsyncing/closing /dev/sdb1: Remote I/O error ]
Selection buttons [Retry] and [Ignore] tried several times.
A slightly different message showed several times.

Multiple cancel attempts eventually got to a clean display of sda details.

Did not attempt any actions.

John.

---

### Post by Rubi1200 on 2019-05-14
Can you post the output of this please:

```
sudo fdisk -l
```

---

### Post by electrosteam on 2019-05-14
As requested:

```

john@Lionel:~$ sudo fdisk -l
[sudo] password for john: 
Disk /dev/sda: 74.5 GiB, 80030957056 bytes, 156310463 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7c890617

Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1  *     2048 156309503 156307456 74.5G 83 Linux


```

Waited over 10 minutes, the activity LED on the USB adapter plug on the hard drive was on steady, gave up and closed.
John

---

### Post by Rubi1200 on 2019-05-14
Just to recap:

if you are on the Linux machine you are unable to connect to sdb but if you use a live medium it can, just about, recognize it?

Did you try the two commands from post #8 while on the live medium?

If none of that works, not sure what to tell you.

Seems the drive has probably failed and there is not much we can do.

I will keep looking for options but not sure what else to try at this time.

---

### Post by electrosteam on 2019-05-14
Rubi1200,
Yes, when on Live CD, dmesg and lshw both give a very brief acknowledgement that sdb is present.

Commands suggested in Post #8 were entered on the Live CD.
Not sure what you meant by the [swapoff] suggestion but, AFAIK, my system was built without a dedicated swap partition.

Heard a lot about GParted so, when you suggested it, I first used Synaptic to install on the normal boot GUI, and gave it a brief view only.
Then when on the Live CD, GParted was available without having to install it.
 
I have opened a new thread on the issue of empty Thunderbird Address Book, and added Sent Folder missing and Mozilla bookmarks missing.

Thanks for the help, not the end of the world.
John

---

### Post by Rubi1200 on 2019-05-14
Well, we tried :-)

Best of luck with everything.

---

