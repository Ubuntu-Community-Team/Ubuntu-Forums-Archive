---
title: "Boot up trouble"
date: 2019-06-10
forum: General Help
---

### Post by Langstracht on 2019-06-10
This morning I was faced with "grub -rescue"

I followed the instructions at [https://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition](https://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition) (even though I had not deleted a partition!)

All was well until 

```
insmod normal
```

which helpfully informed me:

' ... normal mode' not found.

So much for that.

I then created a boot-repair-disk ... which the computer won't, or can't, read.

Then on to a bootable USB stick.  Which, happily the computer did accept and boot up.

Alas it does not give access to any of the files on the system.

I need access to these if only to immediately copy to an ext HD.

Can anyone help me accomplish that.

TIA

Allan

---

### Post by TheFu on 2019-06-10
Use the boot-repair stuff. Boot into that disk, flash drive, doesn't matter.  Center-bottom of the page, click the "gather info" button (or whatever it is called).  Post the URL that it generates back here.

There just isn't enough facts yet to help. Sorry.

---

### Post by Langstracht on 2019-06-10
Thanks for replying.

Alas, as I said, the computer refuses to open the recovery disk.

As for the USB stick, it does boot up.  But the page that opens only has two icons, "Install Ubuntu" and "Examples".  

No sign of any information gatherer there.  Or anywhere else I can find.

Allan

---

### Post by Rubi1200 on 2019-06-10
What version Ubuntu do you have installed and what version is on the USB?

---

### Post by Langstracht on 2019-06-10
Thanks to you also for replying.

14.04 is on the computer.

16.04 is on the USB.  Couldn't find anything older  ...

---

### Post by TheFu on 2019-06-10
> **Langstracht said:**
> Thanks for replying.

Alas, as I said, the computer refuses to open the recovery disk.

As for the USB stick, it does boot up.  But the page that opens only has two icons, "Install Ubuntu" and "Examples".  

No sign of any information gatherer there.  Or anywhere else I can find.

Allan

Sorry, I read it to mean that the optical media didn't work, but you were able to put boot-repair onto the flash storage.

Boot-repair pulls lots and lots of information using commands include in that distro and posts that data to an anonymous URL.

BTW, support for 14.04 ended a few months ago.

---

### Post by Langstracht on 2019-06-10
So, I'm not sure what I should (you would have me) do in this situation ...

---

### Post by TheFu on 2019-06-10
Put [boot-repair ISO]("https://help.ubuntu.com/community/Boot-Repair") onto some flash storage, boot from that, click the "gather info", post the URL back here.
Do not run any "repair", just gather the information. Repairs can break things at this point.

Or, if you just want to get the data off the system, you can use a normal desktop ISO for Ubuntu, boot into that (DVD, CD, Flash, SDHC, whatever ....), choose "Try Ubuntu" and copy all the data off as you like.  
In this temporary environment, you can install packages ... like boot-repair or LVM or encryption tools to gain access to storage. Because it is temporary, anything installed will be gone at reboot.  I find the 16.04 [Ubuntu-Mate distro]("http://cdimage.ubuntu.com/ubuntu-mate/releases/") to be a nice trade-off between light-GUI and enough convenient packages available. Any recent desktop Ubuntu should be fine - xubuntu, lubuntu, ... whatever.  They all should have a "try ubuntu" option at boot.  Normally, I use a nearby mirror  of the distro from the local University to make the download faster.  Moving data 25 miles is easier than moving it 5000 miles.

Make the bootable media using any of the normal ISO writing methods.  mkusb,  dd, ddrescue, unetbootin, rufus, yumi, any tool that works is fine.  I use ddrescue.
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0) has more details. There are instructions for Windows and OSX too. Links to those are on that webpage.  I have never followed those instructions.

---

### Post by Langstracht on 2019-06-10
Sorry I guess I didn't explain this too well.

The USB results in a page with just "install Ubuntu" and "Examples" icons - no icon at the bottom of the page (or anywhere else that I can see) to collect anything.

And, the boot up does not result in access to "my HD" - it seems because it doesn't get mounted.  Consequently I am not able to copy any data.  

Oh that I were!

---

### Post by westie457 on 2019-06-10
Hi, it looks to me that you have the Server ISO which does not have a Graphical interface.

You need a Desktop ISO on a USB stick. You can get one for 16.04 from here. [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

When you have that boot from it to TRY mode, connect to the internet and get Boot Repair from here using the 2nd option. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

As others have suggested do not try any repairs, just click on the button to 'Create a Boot Report', this will generate a link you can post here.

The report will give us enough information to suggest some fixes.

The Boot Repair ISO has not been updated in a while.

---

### Post by &amp;wP*!) on 2019-06-10
Grub can read ISO images from harddisk, and boot them. Thus no need for USB stick or whatever to install or start a Linux distro for debugging. You can save the ISO image of any of such Linux distro into a partition Grub can read and add an entry for this ISO. An example Grub menu entry you can add into your **/boot/grub/grub.cfg**:
```
menuentry "Some Ubuntu ISO" {
        set isofile="/<directory>/Ubuntu.iso"
        loopback loop (hd0,5)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
        initrd (loop)/casper/initrd
}
```
The menu entry above assumes that your ISO is located in /dev/sda5 ( hd0,5 ). You can change this according to your wishes.

The example is from [here]("https://help.ubuntu.com/community/Grub2/ISOBoot").

With loopback loop command above, you can even look inside of an ISO interactively in Grub interactive prompt.

---

### Post by Langstracht on 2019-06-10
The ISO I downloaded was from [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads).  

I went the CLI route with Disk Repair and got this:

[http://paste.ubuntu.com/p/5YrM6dxrms/](http://paste.ubuntu.com/p/5YrM6dxrms/)

url.

VERY much looking forward to this remedying the issue.

Thanks & best

Allan

---

### Post by oldfred on 2019-06-10
You are showing Mint in sda1 and unknown in sda6.
Was sda6 your missing install?

It is not even showing as ext4 which you probably have to fix first.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    
You may be able to use Disks or command  line to set partition as ext4, you do not want to format it as that will erase it.

sudo fdisk /dev/sda
Command (m for help): t
Partition number (1-5): 1
Hex code (type L to list codes): 83
Command (m for help): w

Use m command as I now see man fdisk has w as wipe but using fdisk and w command still shows w as write. May depend on whether old fdisk or newer fdisk (with gpt support).

---

### Post by Langstracht on 2019-06-11
Thanks for your response.

Alas most of this is way beyond my ken ...

Sorry but I didn't know that I had a missing install.  Install of what?  And how would I have known?

I think you want me to issue the following commands:

1 ```
sudo parted -l
```

but I don't know what I am going to do with the output

2. ```
]sudo e2fsck -C0 -p -f -v /dev/sdb1[/CODE

or?

3. [CODE]sudo e2fsck -f -y -v /dev/sdb1 
```

If this IS a choice, does it matter what I choose?  And (alas) again, what is the result?  Output?  The fix(es) is made?  ...

Finally for

```

sudo fdisk /dev/sda
Command (m for help): t
Partition number (1-5): 1
Hex code (type L to list codes): 83
Command (m for help): w
```

I guess I know what to do with "sudo .." but not with the following four lines.  Are they responses?  Options?  ...?

I think you are offering these as ways to (potentially) get a working computer.

Actually, I would be happy if I could just get access to the HD and copy the files.

Apologies for my noob-ness and thanks again.

Allan

---

### Post by TheFu on 2019-06-11
If you are a noob, stick with the normal, desktop, downloads. Most of the issues seem self-inflicted because you happen to choose a non-GUI ISO when there are 8 GUI ISO installs which would have let you "Try Ubuntu" and been done getting data.

You can get the data using a non-GUI install, but when you are new and not good at knowing the processes to make partitions available, it is very hard on our end to help.

IMHO, **the alternate installer is to be avoided unless you are an expert.**  It is designed for special situations, usually due to hardware problems.  Even the "Server" installer has a recovery mode that will automatically access prior storage and let you run shell commands to copy off files/directories and do lots of storage management things.  I'm a server guy, but I use the **Ubuntu-Mate ISO** file when I need to rescue a system that is having boot issues.  See the link above, already provided.  Is there a reason you are avoiding that solution?

---

### Post by Langstracht on 2019-06-11
I didn't intentionally choose a non GUI install.  And if the "url above' (of which there are many) you are referring to is [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads) then, as I said, that is where I downloaded the file from.

If that isn't the url that you are referring to, perhaps you could identify the one in question.

And perhaps you would also be kind enough to share with me (another?) url, of the 8 that you referred to, where I could download a GUI install and hopefully deal with this problem.

TIA

---

### Post by oldfred on 2019-06-11
This is the standard desktop installer.
       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Each of the commands I posted were examples, but you have to use your partition that has issues.

From Boot-Repair report, this says sda6 has issues, and you only show Mint or did you only have Mint installed, Mint is not Ubuntu? See line 36 in report.
```


[COLOR=#ff0000]sda6[/COLOR]: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
```
 
I changed this example to 6 for your partition to then have a known type:

sudo fdisk /dev/sda
Command (m for help): t
Partition number (1-6): [COLOR=#ff0000]6[/COLOR]
Hex code (type L to list codes): 83
Command (m for help): w

Then you may need repairs:
sudo e2fsck -C0 -p -f -v /dev/[COLOR=#ff0000]sda6[/COLOR]
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/[COLOR=#ff0000]sda6[/COLOR]

If it does not then boot, run Boot-Repair again.
If still the 14.04 install which is now obsolete, Boot-Repair may not be able to fix it as repository is closed. LTS versions like 14.04 have 5 years of life and need to be updated before they expire.

---

### Post by Langstracht on 2019-06-12
Sorry I had another emergency I had to deal with.

Finally ran fdisk, ending up with:

Re-reading the partition table failed.: Device or resource busy.

Followed by:

The kernel still uses the old table. The new table will be used at the next re-boot  or after you run partprobe(8) or kpartx(8).

Perhaps this is the expected result and I should just re-boot and see what happens.  Or perhaps evidence of another problem.  Or perhaps I should be running partprobe or kpartx ...

Thought it best to err on the side of caution and hope for further guidance.

All of that said, if I did run Mint on the machine ... and I suppose I must have ... it was years ago and it (the machine) ran fine up until this week making me wonder if Mint is part of the problem.

Anyway I hope you have the patience to continue your much appreciated hand holding.

Allan

---

### Post by rbmorse on 2019-06-12
I think I know the answer to this question, but I have to ask it anyway:  Do you have a good, recent backup of your personal data?   If you do, life gets much simpler.

---

### Post by Langstracht on 2019-06-12
Not sure what you mean by "personal data" but I have a back up of supposedly "everything" from about 3 weeks ago.

Unfortunately, VERY unfortunately, there's been a whole lot of activity since then.  That I am REALLY loathe to lose.  Don't care too much about the machine but I need to keep the files.

---

### Post by Langstracht on 2019-06-12
A couple of thoughts/questions:

1.  What would happen if I installed (or tried to) Ubuntu from the bootable USB?  Would it fail?  If not, and it did install, would it erase everything on the HD.  Indeed, would it do that anyway if it failed?

2.  An earlier post to this thread suggested that had I used a GUI boot up on the USB I would have been able to access the HD without any problems.  Is that true?  And, if so, can someone please give me a URL where I can locate this GUI file.

TIA

---

### Post by oldfred on 2019-06-12
Because of the errors as shown by Boot-repair report nothing will show files.
You have to at least run the fixes suggested above.
Normally the file browser, or folder icon will open any partition and let you browse for files.

If fixes do not work then major repair tools like testdisk or photorec may be required, if worth the effort. 
I used photorec and it took overnight to scan drive & write all found files to another hard drive. But I had old backup, and same files saved many times. Photorec found all the old (deleted) copies so I had many versions of same file. Photorec does not recover full filename either, so you have to work with extensions only & rename yourself.

---

### Post by Langstracht on 2019-06-12
I'll be happy to (try to) run the fixes suggested ... but first I think I need to deal with the (error?) messages:

"Re-reading the partition table failed.: Device or resource busy."

Followed by:

"The kernel still uses the old table. The new table will be used at the next re-boot or after you run partprobe(8) or kpartx(8)"

thrown up by the original "fdisk".

But how?

Thanks as always.

---

### Post by oldfred on 2019-06-12
First run the fixes in post #17, that may solve it.

---

### Post by Langstracht on 2019-06-13
So I ran the first CLI with the following result:

e2fsck: Bad magic number in super-block while trying to open /dev/sda6

/dev/sda6/: The superblock could not be read or does not describe a valid ext2/ext3/ext4 file system  If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else) then the superblock is corrupt, and you might try running e2fsck with an alernative super block:

      e2fsck -b 8193 <device>

or

     e2fsck -b 32768 <device>

thinking it might be helpful I ran another boot-repair status - paste.ubuntu.com/p/3H8M4YTDNr/

Look forward to your response.

Allan

---

### Post by oldfred on 2019-06-13
In #15 I said you probably have to reset sda6 to ext4.
You need to run the fdisk commands to set type 83 first.

Boot-Repair report still shows sda6 as unknown. Line 39.

---

### Post by Langstracht on 2019-06-13
You probably won't be surprised to learn that I'm confused again.

I'd be happy to reset sda6 to ext4, but I have no idea how to do that.

Is this:

```
sudo mkfs.ext4 /dev/sda6
```

how I do that?
.
Did I not run run the fdisk commands to set type 83 first.  Except I guess it didn't work ...

You'll recall I got the (error?) messages:


Re-reading the partition table failed.: Device or resource busy.

Followed by:

The kernel still uses the old table. The new table will be used at the next re-boot or after you run partprobe(8) or kpartx(8).

So maybe re-booting will instigate the "new" table?

---

### Post by oldfred on 2019-06-13
Use fdisk to set type to 83
If then still not seen
run the mkfs.ext4 command 
Only run on your sda6 partition.

---

### Post by Langstracht on 2019-06-13
O.k. so I ran fdisk again.  And, perhaps not surprisingly, got the same messages as the first time.

Seen?  How would I know?

How should  I proceed?

---

### Post by oldfred on 2019-06-13
And then you ran the mkfs command & rebooted?

---

### Post by Langstracht on 2019-06-13
No, I did not.

But I have now and gotten this latest (error?) message:

sudo: unable to execute /sbin/mkfs.ext4: Input/output error
Hangup0

Sigh!!!!

---

### Post by Langstracht on 2019-06-15
Well, I guess that's it for receiving any help.

Disappointing ... but perhaps understandable.

So, thanks for the support you did give.

---

### Post by oldfred on 2019-06-15
Does fdisk not let you set type to 83?
Post the exact commands you ran.

---

### Post by Langstracht on 2019-06-15
Thanks for coming back.

This time it claims it did change it to 83.

---

### Post by oldfred on 2019-06-15
And then post exact commands from mkfs command.
sudo mkfs.ext4 /dev/sda6

---

### Post by Langstracht on 2019-06-15
I don't believe this - but sudo apt-get install says it can't locate the makefs package.  And I can't find it "manually"

---

### Post by Langstracht on 2019-06-15
I did some trawling around the 'net and noticed some sources seem to think mkfs instead or makefs.

So I've given mkfs a try ... and it seems to have worked.

sda6 is now shown by Disks to be Ext4.  But unmounted.

So!  What's next?

---

### Post by Langstracht on 2019-06-15
Having now gone through remedial reading 101, I see that using mkfs was what you said in the 1st place!  

Sorry about that.

---

### Post by oldfred on 2019-06-15
Can you now mount it and see files?
And now fsck may work if you cannot see files, yet.

Or at least will testdisk work to see files? (from your other thread's suggestions?)

---

### Post by Langstracht on 2019-06-15
To do that I would use

```
mount -t ext4 /dev/sda6  /mnt/
```

Is that correct?

Then I sh/could see the files by using "Files"?

---

### Post by oldfred on 2019-06-15
If you mount in /mnt you have to drill down to / & back up to /mnt.

---

### Post by Langstracht on 2019-06-16
I went ahead "anyway".

mount needed a sudo but that's o.k.

And yes, according to Disks, the drive is now mounted.

Thinking "copy the files", I tried Files anyway.  And it gave me no file access.

:Alas, here we go again:

```
sudo apt install testdisk
```

was unable to locate the package.

And, just to add to my frustration, Files reports "mnt" is empty.Even though Disks says it's "Mounted at /mnt".

I take if you mean to use either:

```
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck

or

sudo e2fsck -f -y -v /dev/sdb1 
```

Yes?  Or perhaps both?  In that order?

---

### Post by VMC on 2019-06-16
> **pencuse said:**
> Grub can read ISO images from harddisk, and boot them. Thus no need for USB stick or whatever to install or start a Linux distro for debugging. You can save the ISO image of any of such Linux distro into a partition Grub can read and add an entry for this ISO. An example Grub menu entry you can add into your **/boot/grub/grub.cfg**:
```
menuentry "Some Ubuntu ISO" {
        set isofile="/<directory>/Ubuntu.iso"
        loopback loop (hd0,5)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
        initrd (loop)/casper/initrd
}
```
The menu entry above assumes that your ISO is located in /dev/sda5 ( hd0,5 ). You can change this according to your wishes.

The example is from [here]("https://help.ubuntu.com/community/Grub2/ISOBoot").

With loopback loop command above, you can even look inside of an ISO interactively in Grub interactive prompt.
This doesn't work with Secure Boot. See [this]("https://askubuntu.com/questions/642653/loopback-module-for-grub-with-secure-boot").

---

### Post by oldfred on 2019-06-16
My original post was an example that used sdb1 and said to use all your ext4 partitions.
Your partition that seems like it should be ext4 was sda6, so you have to run fsck on sda6. 

Most suggest a general fsck command, but if it starts asking for y or yes and you have many files pressing y can be a pain. The two commands are one that will not ask for y and another that then automatically says yes.

---

### Post by Langstracht on 2019-06-16
To pencuse.

Sorry but  I am just a bit confused.  This thread started with me complaining that booting up always, and only, had me receiving a "GRUB RESCUE" response.  So I don't believe I can "Grub" anything.

As for the ISO file, I don't believe I have an ISO on the problem HD.  And I have to wonder why you think I do.

What I do have is about 250,000 files on the drive that Disk Usage and Properties tell me about with, as yet, no way to access them.

To oldfred

Thanks for the feedback.  You didn't seem to choose between the two commands.  And I'm not able to.  So I'll give the first one a whirl and see what gives.

Not sure what it might give me but I'll report whatever I can find.

---

### Post by oldfred on 2019-06-16
These are two different fsck command as they use different parameters over the generic fsck.
See
man fsck

Then you may need repairs:
sudo e2fsck -C0 -p -f -v /dev/[COLOR=#ff0000]sda6[/COLOR]
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/[COLOR=#ff0000]sda6[/COLOR]

---

### Post by Langstracht on 2019-06-16
Well so much for that.

I've run both commands - both with the same result:

"/dev/sda6 is mounted.
e2fsck: Cannot continue, aborting."

Alas, so, the beat goes on ...

---

### Post by oldfred on 2019-06-16
You have to unmount sda6 to run fsck.

---

### Post by Langstracht on 2019-06-17
I suppose you would have expected me to have more trouble.  And, unfortunately, you'd have been right!

Attempt to unmount results in:

"Command 'unmount' not found, did you mean:

command 'unmount' from deb mount

Try: sudo apy install <deb name>

I'd be happy to, if I knew what "<deb name>" was ...

---

### Post by Langstracht on 2019-06-17
Remedial typing needed too.

sudo apt install, NOT sudo apy install

---

### Post by Dennis N on 2019-06-17
> Attempt to unmount results in: "Command 'unmount' not found...

'unmount' is not the command, it should be 'umount'. An easy mistake to make.

Mount filesystem on sda1 at /mnt/tmp and then unmount:
```
sudo mount /dev/sda1 /mnt/tmp
sudo umount /mnt/tmp
```

---

### Post by Langstracht on 2019-06-17
Thank you for that.

And indeed, umount unmounted the drive.

I ran the suggested fsck command which appeared to have no problems.

Thinking it was the "right" thing to do, I then tried to (re)mount /dev/sda6, only to be told:

"mount: /dev/sda6: can't find in etc/fstab" 

Because that ain't where it is. (have to say it's a bit of a p,o. that umount finds it fine and mount doesn't.)

In any event, as this painful saga continues, how do I identify whatever so that mount WILL find it.  Disks (still) shows the Device to be /dev/sda6!

---

### Post by oldfred on 2019-06-17
Are you using live installer?
Then it would not be in fstab to remount.
You probably mounted using file browser at /media/$USER/UUID or label if labeled.

You either have to have a mount point to mount to, or one of a few defaults.

---

### Post by Langstracht on 2019-06-17
My access, such as it is, to the computer is with USB 18.04.  And I think that means I'm using a live installer.

I did not 'manually' mount anything.  So, 18.04 did it by itself?

The only info Disks offers is that the devices are dev/sda1 and dev/sda6 with different UUIDs - what ever that implies.

I think you are saying that I need to mount to the UUID?  Can you give me a command line that would accomplish that.  

Thanks, so much, yet again.

---

### Post by oldfred on 2019-06-17
You can go into Disks and mount it like you did before?

       Is drive now sda or sdb, you need to use correct drive. To see partitions:
sudo parted -l
If sdb6 otherwise change to sda6
sudo mount /dev/sdb6 /mnt 

the /mnt will only be one mount.
If you want to mount others you have to create mount points. You can use any name/label that you like, but must be consistent and case makes a difference in Linux. One is not one as capital letter is different.
sudo mkdir /mnt/one
sudo mkdir /mnt/two

sudo mount /dev/sdb1 /mnt/one
sudo mount /dev/sdb6 /mnt/two

---

### Post by Langstracht on 2019-06-18
I still don't see any way to mount in Disks.  And I really don't think I did that "before".

In any event, on to the latest problem.

Running ```
parted -l
``` reports the following:

"Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes"

And helpfully goes on to offer me the choice of Ignoring or Cancelling ...

Meantime this drive we've been chasing would still appear to be sda6.

---

### Post by oldfred on 2019-06-18
That warning is usually from your live installer. You can ignore it.

---

### Post by Langstracht on 2019-06-18
thank you.

So I ignored it. 

And then back to the same old problem with ```
sudo mount /dev/sda6/mnt
```, 
"mount: /dev/sda6/mnt: can't find in /etc/fstab"

---

### Post by oldfred on 2019-06-18
Spaces are very important in Linux. Adding a space where not required or not having a space where required can change a command or make it invalid.

You used.
sudo mount /dev/sda6/mnt
But it should be this with a space between the device /dev/xxx and the mount point /mnt(in this case).
sudo mount /dev/sda6 /mnt

---

### Post by Langstracht on 2019-06-18
A "space" on my monitor is very small.  Add to that ageing eyes and well ...

So that dealt with.  Disks reports that sda6 is not mounted at /mnt!

Now what?

---

### Post by Langstracht on 2019-06-18
So much for my typing. NOW not NOT!!!

---

### Post by VMC on 2019-06-18
What's the output of : ```
lsblk -f
```.

---

### Post by Langstracht on 2019-06-18
A whole lot more than I would be able to type accurately.

What specifically are you looking for?

---

### Post by oldfred on 2019-06-18
You copy & paste from terminal to here.
And if longer output & to preserve formatting, you use code tags.

       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by Langstracht on 2019-06-18
I think maybe you are thinking that I am accessing this thread from the inoperative machine.

I am not - I am on another.

The defective has USB usage and connection issues but, if it's that important, I'll try to work around it somehow ...

---

### Post by Langstracht on 2019-06-18
```
NAME FSTYPE LABEL                UUID                                 MOUNTPOINT
loop0
     squash                                                           /rofs
loop1
     squash                                                           /snap/core
loop2
     squash                                                           /snap/gtk-
loop3
     squash                                                           /snap/gnom
loop4
     squash                                                           /snap/gnom
loop5
     squash                                                           /snap/gnom
loop6
     squash                                                           /snap/gnom
loop7
     squash                                                           /snap/gnom
sda                                                                   
&#9500;&#9472;sda1
&#9474;    ext4                        2ad1aa98-3c60-415f-8482-85b797e0ff91 /media/ubu
&#9500;&#9472;sda2
&#9474;                                                                     
&#9500;&#9472;sda5
&#9474;    swap                        a01d95e6-ca63-4617-aebb-59c70fd79a03 [SWAP]
&#9492;&#9472;sda6
     ext4                        0da9069a-66b1-41c4-937e-b5581637972c /mnt
sdb  iso966 Ubuntu 18.04.2 LTS amd64
&#9474;                                2019-02-10-00-27-34-00               /cdrom
&#9500;&#9472;sdb1
&#9474;    iso966 Ubuntu 18.04.2 LTS amd64
&#9474;                                2019-02-10-00-27-34-00               
&#9492;&#9472;sdb2
     vfat   Ubuntu 18.04.2 LTS amd64
                                 5655-3E5A                            
sr0
```

---

### Post by oldfred on 2019-06-18
Seems to correctly show sda6 as ext4, mounted at /mnt

Have you now tried the fsck commands on sda6?
Or run Boot-repair?

---

### Post by Langstracht on 2019-06-18
I take it you mean:

```
   sudo e2fsck -C0 -p -f -v /dev/sdb1


   sudo e2fsck -f -y -v /dev/sdb1
```

I have, many times before, but I can do so again.

Likewise with boot-repair.

With the first:

"/dev/sda6 is mounted.
e2fsck: Cannot continue, aborting"

As before, unless I am mistaken.

boot-repair is "not found" as a command.  And I am unable to find it.

---

### Post by oldfred on 2019-06-18
Each time you reboot a live installer, you have to reinstall Boot-Repair by adding its ppa & updating system. Details on commands to copy into terminal.
        [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  
    
You have to unmount as said before if you want to run fsck.
Or can you now see your files in /mnt?

---

### Post by Langstracht on 2019-06-19
Just wanted to say thanks to everyone who has contributed to this thread - ESPECIALLY oldfred for his patience, generosity and knowledge.

That being said,  I am done.

It's been a week and a half trying to rectify this situation and, while it may not be true, I think I am no closer to a solution and I have been repeating the same commands over and over.  

So the laptop is now toast ... and I'm on to something new.

But thanks again.

---

