---
title: "Does journalctl -b tell me why the display is not loading on startup?"
date: 2022-03-22
forum: General Help
---

### Post by andrewcorser on 2022-03-22
[This is an attempt at resetting a [question]("https://ubuntuforums.org/showthread.php?t=2472059") that I asked well back in February, before WWIII started]

When powered up, my home server desktop pc loaded Ububtu  (20.04.3 LTS) and its pool of 4 zfs NAS drives...however the screen  display was blank but for a cursor. [following help from this forum] Ctrl-Alt-F4 (or ssh over the network from a Windows 10 laptop using wsl) got me a command line with the Ubuntu welcome messages. Files were still being rsync'ed from the Windows laptop to the  pool on the server (I think) by way of backup.

 
Since then I have tried a number of different things, including  changing the grub so that I can choose recovery mode, but nothing has  brought back the gui.  Booting from a usb stick DOES load the gui (so  the hardware is working), but then the zfs pool is not available (and I  am nervous about reinstalling Ubuntu, as there are several things which  my (linux-savvy) son had to do to make the whole home server system  work).


 Now when I boot the system from the hard disk, as well as the  gui/display not loading, the zfs pool is also not being mounted, so my  backup is no longer working.

 I was looking for a way I can see a record of Ubuntu's loading process so that  I can identify when and what is stopping the graphics interface from  working, and now why the zfs pool is not being mounted.

I have found the command 

journalctl -b

which, I think, IS a log of the startup process.  As you will no doubt know, this is  a very long file.

At line 2420, in yellow, it says 'fatal server error' on a line  /usr/lib/gdm3/gdm-x-session[1077]:      which looks like the display  system..?  (see link below for image of first lines of the journal, and the lines which seem to me to tell me where the display fails)

It says 'unable to load X server...(gdm-autologin-session): session closed for user andrew' and then 'GdmDisplay: Session never registered, failing'

[I]...[https://andrewcorser.com/NAS/journalctl-b.jpg](https://andrewcorser.com/NAS/journalctl-b.jpg)

[/I]Is this why the display is not loading at startup?  It says the issue is 'XKB: couldn't compile keymap...This could be missing or incorrect setup of xkeyboard-config...also check the logfile at "/home/andrew/.local/share/xorg/Xorg.0.log"'

Where is xkeyboard-config?  /home/andrew/.local/share/xorg/Xorg.0.log is empty.

Can anyone help, please?

---

### Post by #&amp;thj^% on 2022-03-22
My friend, I believe TheFu had mentioned in your last thread about the pitfalls using Experimental ZFS support.
I've been around Linux for 17 years or more now, and I would not use ZFS root, unless as a testing propose only. (Nothing production related) 
As it matures (bugs and new features) in age and usage, things will change.
Example: 
> For a mirror or raidz topology, /boot/grub is on a separate dataset. This was originally bpool/grub, then changed on 2020-05-30 to bpool/BOOT/ubuntu_UUID/grub to work-around zsys setting canmount=off which would result in /boot/grub not mounting. This work-around lead to issues with snapshot restores. The underlying zsys issue was fixed and backported to 20.04, so it is now back to being bpool/grub.
Things like the above can leave a system in utter chaos and broken.
So far from both your old thread and this thread there is nothing that jumps out at me, as far as a suggestion to help. :(
Maybe have a read here for more info:[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html)
And I wonder if you have ever run a ZFS scrub against it?
**_Please do not run one now though,as it could further the mess you have now. _**
**ZFS makes no allowances for administrator error. It assumes implicitly you know what you're doing at all times.**
I did see this though:
Key points to study?
```

[1033] pam_unix(gdm-autologin:session): session closed for user andrew
Unable to run X server
GDM Display: Session never registered, failing. 
```
LAST EDIT:Those points above, can also be related to disk space, "Unable to run X server" errors, GDM is failing to start or getting "session closed for user gdm" errors, it's worth checking that you have free disk space for GDM to start!

Sometimes, it's the simple things that are the hardest to find...

---

### Post by MAFoElffen on 2022-03-22
I was the one that was mainly helping you there in that last thread. There were many times when questions went unaswered, or a very long delay before you answered something. Even some information we asked for, you were wary about answering, and instead of posting result, you answered indirectly, as somewhat censored.

Honestly, I lost rack of it when there was one of those long delays... Until late last week, you sent me a PM asking me if the results of your boot-info report changed anything(???) But you never sent me, nor anyone else that I am aware of any link to see those results. Nor did you post a link to those results. So I let it go. You had told us (along the way) that you would get your son, who set it up to help you... That was what I assumed when the delay was very long.

I offered to post detailed instructions on how I mount ZFS filesystems from a LiveCD... Remember, I am the one who is helping to add that to 'boot-info' and 'boot-repair,' based on sharing on my experience, and contributing to. But at that time, it was not needed, as you had told us the you could boot, and use <Cntrl><Alt><F4> to access vtty4, with access to your ZFS pools... Then(now), you say you lost access to your pools.

The questions now would be: Where would you like to go from here? And if so, we need timely, accurate information to be able to help you. Are you open to helping us to be able to help you? We are not clairvoyant, nor can we read minds. If we ask a question or output from a command, it is without any intent, but to help you solve your problem.

To calm you down about posting information publicly... In my own Forum scripts, I mask sensitive data in reports that will be posted publicly... But those are IP addresses, serial numbers, MAC Addresses, etc. What you were touchy about, as I remember, had something to do with the PPA's, and the naming conventions contained in your system setup for pools and such(???). I don't consider those as sensitive data... And cannot imagine why someone would think that. But I am an IT Professional with more years of experience that I feel needs to be said, that deals with all types/forms of security, business trade secrets, embarrassing personal data and business niches, etc. So I am not saying that is not possible... But rather unexplained.

I'm not afraid of ZFS. I have worked with it as a Systems Administrator, and had to support it for about 2 decades. It has been in Production systems in UNIX (Sun Systems and Oracle Solaris) and now in BSD. BSD (OpenZFS) "is" trying to catch up with years of improvements and updates from ZFS Linux. Some people are just nervous about what they do not know. I can agree with that, in that respect that there are not a whole lot of people around these days (like me), that know much about ZFS, and think it is something "New" and/or mainstream, or not accepted. I don't claim to know everything. I've just been around for too many years, having to support things and have been exposed to a whole lot of things along the way. In some respects, it just makes me feel old.

---

### Post by andrewcorser on 2022-03-24
> **MAFoElffen said:**
> I was the one that was mainly helping you there in that last thread. 

There were many times when questions went unaswered, or a very long  delay before you answered something. Even some information we asked for,  you were wary about answering, and instead of posting result, you  answered indirectly, as somewhat censored.


Yes, MAFoElffen, thank you for your offers of help, and your advice: I have tried to respond as quickly as I could (bearing in mind that I am several hours out of sync with you, as I am in the UK, not the US) but, if you look back through the thread you will see how often I was only able to get through the first bit of your advice before I came upon something that stopped me going further - usually because, as I have said before, I am new to Ubuntu and Linux, and I needed help getting round the blockage.

To be clear, my first issue, and the one that is stopping me get anywhere near getting this machine to work again (and it has worked effectively for 9 months or more, so I don't believe the system design is flawed - the problem with the design is really my lack of Ubuntu-Linux knowledge, which is why I came to Ubuntu Forums) my main issue is that it will not boot into the graphics display.

Yes, it is very helpful that you explained to me how to use Alt-Ctrl-F4 to get to the command line (although I had already got to the command line over the network, as I had explained) but I need the system to boot into a graphics display: I am not an IT professional, and my knowledge of using the command line is not sufficient to run the system that way.

So I go back to my most recent question: [FONT=arial][SIZE=2]does journalctl -b tell me why the display is not loading on startup? The link to the bits of the journal that I think might be relevant is:[/SIZE][/FONT][SIZE=2][FONT=arial] [https://andrewcorser.com/NAS/journalctl-b.jpg](https://andrewcorser.com/NAS/journalctl-b.jpg)
[/FONT][/SIZE][FONT=arial][SIZE=2]
[/SIZE][/FONT]
[[[REgarding ZFS, as I have said before: I am committed to using zfs - and I am supremely confident that it will be possible to load the pool back up once I have got the graphics display back.  The link to the boot-info is [https://paste.ubuntu.com/p/dYVrnsvM2B/](https://paste.ubuntu.com/p/dYVrnsvM2B/)]]]

btw I am writing this at 11 am in the UK on Thursday 24th March 2022.

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> LAST EDIT:Those points above, can also be related to disk space, "Unable to run X server" errors, GDM is failing to start or getting "session closed for user gdm" errors, it's worth checking that you have free disk space for GDM to start!

Sometimes, it's the simple things that are the hardest to find...

The os is installed on a Seagate Baracuda 510M.2 MDME 250 Gb, so the space is there...how it is mounted/allocated etc, I do not know...

...does this from lsblk indicate anything?

nvme####     259:0    0 232.9G  0 disk
&#9500;&#9472;nvme###p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme###p2 259:2    0 232.4G  0 part /

---

### Post by MAFoElffen on 2022-03-24
Yes!!! Thank you for the link to those pictures of your journalctl snippets. Those were invaluable!

I know you can't cut and paste that into text from with how your system is booting... So let me point out "where" things seem to be going on to the others here...

In the state of his system, he cannot cut and paste output, as he has no graphics session, so he is showing the output with photos... In the second of his photos, at time stamp "MAR 20 14:03:37..." There is a dump of an error from his Xorg.0.log... where his x kepboard map had various problems.

Remember where I was looking for his Xorg.0.log in /var/log/, where in most of the Linux world, that file is located? His xorg log is located at "/home/andrew/.local/share/xorg/Xorg.0.log".

That is the file I need to see... Somehow. 

Second, his errors say they are from a file close error and that the x keyboard compiler could not create some required files because of lack of space...

So I need to see the output of 
```

df -hT | grep -v '/snap/'

```

---

### Post by #&amp;thj^% on 2022-03-24
You ninja'd me ;)
Your in good hands now I'll just watch.

---

### Post by MAFoElffen on 2022-03-24
@1fallen - 

We are all in different time zones. Is very early afternoon here.Is evening where the OP is... Not sure of your time zone. I have to go to work in about 3 hours, to work a closing shift... So may that's when I have to drop out of this tonight. I would appreciate your help if that happens.

It may be a space problem. But to correct it, he may have to do cli, where he will need to be talked through that at a basic level. I know you have some ZFS experience. (where others here do not.)

The initial way to see his Xorg.0.log file would be to mount a USB drive for read/write and copy it to that, so he can get it to his other PC to post it. The other way would be to talk him through mounting and activating his ZFS pools from a LiveCD... I know you have been following Yann's 'boot-info' thread, where I explained to Yann how I do that, via terminal logs... but that was at a different skill level than this OP would need. That would have to be "translated" to Andrew's skill level for him to do that.

Andrew says he is online and ready. Let's see now this goes.

---

### Post by #&amp;thj^% on 2022-03-24
> **MAFoElffen said:**
> @1fallen - 

We are all in different time zones. Is very early afternoon here.Is evening where the OP is... Not sure of your time zone. I have to go to work in about 3 hours, to work a closing shift... So may that's when I have to drop out of this tonight. I would appreciate your help if that happens.

It may be a space problem. But to correct it, he may have to do cli, where he will need to be talked through that at a basic level. I know you have some ZFS experience. (where others here do not.)

The initial way to see his Xorg.0.log file would be to mount a USB drive for read/write and copy it to that, so he can get it to his other PC to post it. The other way would be to talk him through mounting and activating his ZFS pools from a LiveCD... I know you have been following Yann's 'boot-info' thread, where I explained to Yann how I do that, via terminal logs... but that was at a different skill level than this OP would need. That would have to be "translated" to Andrew's skill level for him to do that.

Andrew says he is online and ready. Let's see now this goes.
About the same as my time zone, Andrew is in the UK, so I'll do my best to represent.
BTW dinner will be in the fridge. :P

---

### Post by MAFoElffen on 2022-03-24
Since mounting a USB Flash Drive to this broken system is just temporay and you had problems doing that previously had problems... I'm going to tell you in a manner that is going to be like hitting it with a sledge hammer (over-done).

Before inserting the Flash Drive
```

sudo fdisk -l

``` 
Insert the Flash Drive
```

lsblk

```
Look for an added device... /dev/sdx, where x is a letter of the new device/drive. for example purposes below, lets ay the new device was /dev/sdf

Then you will create a directory in your home directory, where it is easy for you to find
```

mkdir /home/andrew/storage

```
Now you will mount the Flash Drive to that directory, with read/write permissions set to "everyone"
```

sudo mount /dev/sdf1 /home/andrew/storage -o umask=000
chmod 777 /home/andrew/storage

```
Then copy the Xorg log to the drive
```

cp /home/andrew/.local/share/xorg/Xorg.0.log /home/andrew/storage/

```
If successful.then unmount the USB, before removing it (so the filesystem is properly closed)
```

sudo umount /dev/sdf1

```

---

### Post by MAFoElffen on 2022-03-24
It will not let me edit the last post... on the second command, just redo the 'fdisk' command again, a second time and look for the difference.

---

### Post by #&amp;thj^% on 2022-03-24
> **MAFoElffen said:**
> Since mounting a USB Flash Drive to this broken system is just temporay and you had problems doing that previously had problems... I'm going to tell you in a manner that is going to be like hitting it with a sledge hammer (over-done).

Before inserting the Flash Drive
```

sudo fdisk -l

``` 
Insert the Flash Drive
```

[S]lsblk[/S]  ## so this one is to run sudo fdisk -l twice

```

Just so I'm on the same page look at my view and confrim.

---

### Post by andrewcorser on 2022-03-24
> **MAFoElffen said:**
> So I need to see the output of 
```

df -hT | grep -v '/snap/'

```

Here is a link to the disk usage report:

[https://andrewcorser.com/NAS/diskusagedf.png](https://andrewcorser.com/NAS/diskusagedf.png)

sorry - this crossed in the ether with your subsequent posts.  I will now do the stuff from your #10...

---

### Post by #&amp;thj^% on 2022-03-24
> **andrewcorser said:**
> Here is a link to the disk usage report:

[https://andrewcorser.com/NAS/diskusagedf.png](https://andrewcorser.com/NAS/diskusagedf.png)

sorry - this crossed in the ether with your subsequent posts.  I will now do the stuff from your #10...

Yep your **" /dev/nvme0n1p2 "** Is at or shows 100% full, the rest looks good.
I'll wait to see what else turns up.

---

### Post by MAFoElffen on 2022-03-24
Confirmed on your precious post about your understanding of what I said. But before that... From the results of your last post:

/dev/nvme0n1p2, which is your mount "/" (root partitiion) is full at 100%. Your need some space there. do this via
```

rm -fr /tmp/*.*
sudo apt clean
sudo apt autoremove

```
Then check your space usage again...
```

df -hT | grep -v '/snap/'

```
What we are trying to get is about at least 20% free... If it is, then reboot and see if your XServer init's on it's own. If not, then we will check your ZPool snap shots and delete old snapshots to free up space.

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> Yep your **" /dev/nvme0n1p2 "** Is at or shows 100% full, the rest looks good.
I'll wait to see what else turns up.

and ref mkdir /home/andrew/storage:

it reports No space left on drive.

(I have two screenshots coming along...one with less /home/andrew/.local/share/xorg/Xorg.0.log...which is still empty)

---

### Post by #&amp;thj^% on 2022-03-24
> **MAFoElffen said:**
> Confirmed on your precious post about your understanding of what I said. But before that... From the results of your last post:

/dev/nvme0n1p2, which is your mount "/" (root partitiion) is full at 100%. Your need some space there. do this via
```

rm -fr /tmp/*.*
sudo apt clean
sudo apt autoremove

```
Then check your space usage again...
```

df -hT | grep -v '/snap/'

```
What we are trying to get is about at least 20% free... If it is, then reboot and see if your XServer init's on it's own. If not, then we will check your ZPool snap shots and delete old snapshots to free up space.
Copy That.

---

### Post by andrewcorser on 2022-03-24
This is the contents of Xorg.0.log:

[https://andrewcorser.com/NAS/xorglog.png](https://andrewcorser.com/NAS/xorglog.png)

And this is the attempt to mkdir:

[https://andrewcorser.com/NAS/nospacelsblk.png](https://andrewcorser.com/NAS/nospacelsblk.png)

---

### Post by MAFoElffen on 2022-03-24
On making more space and planning what more to remove, this output might help
```

cd /
sudo du -h --separate-dirs --all --threshold=1G | more

```

EDIT: What is surprising is that this failed in this manner, and that it didn't fail in another way (ZFS). With ZFS pools, usually sometime between 10%-20% free left, ZFS starts throwing warnings and then if that continues, toggles the filesystem into a read-only state. LOL

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> Copy That.

the first line rm -fr /tmp/*.* gives me a rather frightening list of systemd files that it says I cannot remove:

[https://andrewcorser.com/NAS/rm-frtemp.png](https://andrewcorser.com/NAS/rm-frtemp.png)

---

### Post by andrewcorser on 2022-03-24
> **MAFoElffen said:**
> On making more space and planning what more to remove, this output might help
```

cd /
sudo du -h --separate-dirs --all --threshold=1G | more

```

EDIT: What is surprising is that this failed in this manner, and that it didn't fail in another way (ZFS). With ZFS pools, usually sometime between 10%-20% free left, ZFS starts throwing warnings and then if that continues, toggles the filesystem into a read-only state. LOL

[I]du: option '--separate-dirs' doesn't allow an argument
Try 'du--help' for more information
[/I]

---

### Post by MAFoElffen on 2022-03-24
Do it without the -f (force) flag...
```

rm -r /tmp/*.*

```
It gives those warnings as those files are open and in use... That is okay that it cannot remove an open file.

EDIT:
The 'du' command should find file that are over 1GB that might be candidates to delete to save/reclaim space. If you want to keep some of those, and if they are just user data files, maybe moved (copy to target, then removed from source) to another partition(?)

EDIT2: 
Sorry for the many edits.Ttrying to do as much as possible before I have to go to work...

---

### Post by MAFoElffen on 2022-03-24
> **andrewcorser said:**
> [I]du: option '--separate-dirs' doesn't allow an argument
Try 'du--help' for more information
[/I]

Hmmm. That iwa cut and pasted from my machine when I tested to make sure it was the output we needed...

Let me copy that again from my terminal history...
```

sudo du -h --separate-dirs --all --threshold=1G | more

```
If that still errors on yours, then do 
```

sudo du -h --all --threshold=1G | more

```

---

### Post by MAFoElffen on 2022-03-24
I have about an hour and a half before I have to get offline and go to work... Trying to get you helped.

---

### Post by andrewcorser on 2022-03-24
> **MAFoElffen said:**
> Do it without the -f (force) flag...
```

rm -r /tmp/*.*

```
It gives those warnings as those files are open and in use... That is okay that it cannot remove an open file.

EDIT:
The 'du' command should find file that are over 1GB that might be candidates to delete to save/reclaim space. If you want to keep some of those, and if they are just user data files, maybe moved (copy to target, then removed from source) to another partition(?)

EDIT2: 
Sorry for the many edits.Ttrying to do as much as possible before I have to go to work...

I did rm -r /tmp/*.* and it just asked me if I wanted to descend into each of the write-protected directories, and then if I wanted to remove them (to which I said y) and then told me it couldn't remove each one as the Operation not permitted.

I don't understand, really, why there is no available space on /dev/nveme0n1p2: that is a 250 Gb ssd that the os is installed on, but I don't save anything on there.  Everything is saved on the zfs pool. Is something telling the system to allocate all of the space on partition 2 to 'Used'?

---

### Post by andrewcorser on 2022-03-24
> **MAFoElffen said:**
> Hmmm. That iwa cut and pasted from my machine when I tested to make sure it was the output we needed...

Let me copy that again from my terminal history...
```

sudo du -h --separate-dirs --all --threshold=1G | more

```


This got me started: I will remove one of the directories here and see if that gives us some space...

---

### Post by MAFoElffen on 2022-03-24
That (du command string) will list the individual files to remove. Not to remove the whole directories.

Also another direction to reclaim space from output of your old ZFS snapshots...
```

zfs list -r -t snapshot -o name,used,space,referenced,creation

```

---

### Post by #&amp;thj^% on 2022-03-24
Great Minds, and ninja'd again
While your there see if this pulls anything, if so add another screenshot:
```
zfs list -t snapshot
```

---

### Post by MAFoElffen on 2022-03-24
@1fallen -- LOL. Great minds think alike: Posts 27 & 28...

---

### Post by andrewcorser on 2022-03-24
> **andrewcorser said:**
> This got me started: I will remove one of the directories here and see if that gives us some space...

OK.  From sudo du -h --separate-dirs --all --threshold=1G | more

I can now see some directories which I have removed, and df has shown me that I have 1.2G available on partition2 of the ssd nvme0n1.

Then I thought: will it reboot to a graphics interface?  And it has!!  Hurray!!

...Oh, but wait a minute: I have the graphics interface, but the directory that had all of my zfs files on it is there...but empty.  And doing lsblk shows that the zfs pool drives are not mounted...

...so the next thing is how to get those back...

BUT THIS IS GREAT PROGRESS!!  THANKS, MAFoElffen!!  And 1fallen!!

---

### Post by MAFoElffen on 2022-03-24
I'm seeing time tick down before I have to get offline for work...

Before I go, here is a script shared for both Andrew and 1fallen, that I use as maintenance on my ZFS servers... Where eventually the automated ZFS snapshots will fill the bpool and old snapshots need to be removed...
```

#!/bin/bash
# MAFoElffen, <mafoelffen@ubuntu.com>, 2021.12.28, last modified: 2022.02.23
# Purpose: ZFS Snapshots bpool maintenance

function ZfsShowFreeSpace ()
{
    zfs list -o space
    zpool list
}

function ZfsListBpool() {
   zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | less
}

function GetZfsBpoolSnapshotCount()
{
    ZfsSnapshotCount=$(zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | wc -l)
    line_count="$(($ZfsSnapshotCount-1))"
    echo -e "There are $line_count snapshots in bpool."
}

function ZfsTrimLast5()
{
    # Command for removing is: zsysctl state remove --system <statename>
    zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | \
         head -n 5 | \
         cut -c 35-40 | \
         xargs -n 1 zsysctl state remove --system
}

function ShowMenu() {
    
    while [[ "$menu_response" !=  "5" ]]
    do
        clear
        echo -e "=== ZFS BPool Maintenance ==="
        echo
        echo -e "1 - Show space in Zpools"
        echo -e "2 - Show list of BPool Snapshots."
        echo -e "3 - Show count of BPool Snapshots"
        echo -e "4 - Destroy oldest 5 BPool SnapShots"
        echo -e "5 - Exit"
        echo 
        read -p "Enter a valid menu response from 1 through 5:  " menu_response
        case $menu_response in
            1) ZfsShowFreeSpace;;
            2) ZfsListBpool;;
            3) GetZfsBpoolSnapshotCount;;
            4) ZfsTrimLast5;;
            5) exit;;
            *) echo -e "The response was not a valid choice.";; 
        esac
        
        echo
        read -p "Press any <Enter> key to continue" trashbin
    done
}

ShowMenu


```

---

### Post by #&amp;thj^% on 2022-03-24
> **andrewcorser said:**
> 
...Oh, but wait a minute: I have the graphics interface, but the directory that had all of my zfs files on it is there...but empty.  And doing lsblk shows that the zfs pool drives are not mounted...

...so the next thing is how to get those back...

BUT THIS IS GREAT PROGRESS!!  THANKS, MAFoElffen!!  And 1fallen!!
I had faith, nice to see your machine again with a gui.
Give me a minute, I'll see if we can get those back for you.

---

### Post by MAFoElffen on 2022-03-24
@1fallen-- Can I hand this off to you now? I have get ready to leave for work. If stuck, look at my terminal notes to Yann (Hints: See if he can manually mount and activate his rpool, then look at his fstab to see where he is mounting that rpool from there)...

Happy to hear this is finally making progress.

(Offline)

---

### Post by #&amp;thj^% on 2022-03-24
The snapshots listed in .zfs/snapshot/ are automatically mounted on demand, as they are being browsed, and are automatically unmounted when no longer in use.

Doing a simple "ls" in a directory is apparently not enough to be considered 'demand'. You will need to cd into the directory in question and THEN issue the "ls" command.
Sorry you might need to show:
```
 zfs list

```

You may also need to set snapdir=visible for the filesystem.
It should resemble this:
```
zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              301M   531M       96K  /boot
bpool/BOOT                                         300M   531M       96K  none
bpool/BOOT/ubuntu_8xe1pq                           300M   531M      162M  /boot
rpool                                             6.13G  10.8G       96K  /
rpool/ROOT                                        6.04G  10.8G       96K  none
rpool/ROOT/ubuntu_8xe1pq                          6.04G  10.8G     4.20G  /
rpool/ROOT/ubuntu_8xe1pq/srv                        96K  10.8G       96K  /srv
rpool/ROOT/ubuntu_8xe1pq/usr                       296K  10.8G       96K  /usr
rpool/ROOT/ubuntu_8xe1pq/usr/local                 200K  10.8G      144K  /usr/local
rpool/ROOT/ubuntu_8xe1pq/var                       534M  10.8G       96K  /var
rpool/ROOT/ubuntu_8xe1pq/var/games                  96K  10.8G       96K  /var/games
rpool/ROOT/ubuntu_8xe1pq/var/lib                   529M  10.8G      353M  /var/lib
rpool/ROOT/ubuntu_8xe1pq/var/lib/AccountsService   156K  10.8G      100K  /var/lib/AccountsService
rpool/ROOT/ubuntu_8xe1pq/var/lib/NetworkManager    324K  10.8G      140K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_8xe1pq/var/lib/apt              84.7M  10.8G     84.6M  /var/lib/apt
rpool/ROOT/ubuntu_8xe1pq/var/lib/dpkg             56.9M  10.8G     47.2M  /var/lib/dpkg
rpool/ROOT/ubuntu_8xe1pq/var/log                  4.56M  10.8G     2.19M  /var/log
rpool/ROOT/ubuntu_8xe1pq/var/mail                   96K  10.8G       96K  /var/mail
rpool/ROOT/ubuntu_8xe1pq/var/snap                  200K  10.8G      136K  /var/snap
rpool/ROOT/ubuntu_8xe1pq/var/spool                 224K  10.8G      112K  /var/spool
rpool/ROOT/ubuntu_8xe1pq/var/www                    96K  10.8G       96K  /var/www
rpool/USERDATA                                    89.4M  10.8G       96K  /
rpool/USERDATA/oem_sju5rn                         89.1M  10.8G     71.2M  /home/oem
rpool/USERDATA/root_sju5rn                         192K  10.8G      128K  /root

```

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> I had faith, nice to see your machine again with a gui.
Give me a minute, I'll see if we can get those back for you.

Thanks, 1fallen!


It seems to me that the problem with the graphics may have been caused by the ssd (nvme0n1) that we designed to just have the os on it being filled up by a cloud storage system - Tresorit - I have been using (instead of Google Drive).  The directories on that ssd that were shown by doing du were the names of directories that were in the zfs pool, but with the word tresor inserted - to start with I just assumed they were the directories from the pool, but my supposition now is that they were synched by Tresorit onto the home directory, and thereby mounted onto the ssd, rather than the zfs pool, which then filled up all the space there.

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> The snapshots listed in .zfs/snapshot/ are automatically mounted on demand, as they are being browsed, and are automatically unmounted when no longer in use.

Doing a simple "ls" in a directory is apparently not enough to be considered 'demand'. You will need to cd into the directory in question and THEN issue the "ls" command.
Sorry you might need to show:
```
 zfs list

```

You may also need to set snapdir=visible for the filesystem.
It should resemble this:
```
zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              301M   531M       96K  /boot
bpool/BOOT                                         300M   531M       96K  none
bpool/BOOT/ubuntu_8xe1pq                           300M   531M      162M  /boot
rpool                                             6.13G  10.8G       96K  /
rpool/ROOT                                        6.04G  10.8G       96K  none
rpool/ROOT/ubuntu_8xe1pq                          6.04G  10.8G     4.20G  /
rpool/ROOT/ubuntu_8xe1pq/srv                        96K  10.8G       96K  /srv
rpool/ROOT/ubuntu_8xe1pq/usr                       296K  10.8G       96K  /usr
rpool/ROOT/ubuntu_8xe1pq/usr/local                 200K  10.8G      144K  /usr/local
rpool/ROOT/ubuntu_8xe1pq/var                       534M  10.8G       96K  /var
rpool/ROOT/ubuntu_8xe1pq/var/games                  96K  10.8G       96K  /var/games
rpool/ROOT/ubuntu_8xe1pq/var/lib                   529M  10.8G      353M  /var/lib
rpool/ROOT/ubuntu_8xe1pq/var/lib/AccountsService   156K  10.8G      100K  /var/lib/AccountsService
rpool/ROOT/ubuntu_8xe1pq/var/lib/NetworkManager    324K  10.8G      140K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_8xe1pq/var/lib/apt              84.7M  10.8G     84.6M  /var/lib/apt
rpool/ROOT/ubuntu_8xe1pq/var/lib/dpkg             56.9M  10.8G     47.2M  /var/lib/dpkg
rpool/ROOT/ubuntu_8xe1pq/var/log                  4.56M  10.8G     2.19M  /var/log
rpool/ROOT/ubuntu_8xe1pq/var/mail                   96K  10.8G       96K  /var/mail
rpool/ROOT/ubuntu_8xe1pq/var/snap                  200K  10.8G      136K  /var/snap
rpool/ROOT/ubuntu_8xe1pq/var/spool                 224K  10.8G      112K  /var/spool
rpool/ROOT/ubuntu_8xe1pq/var/www                    96K  10.8G       96K  /var/www
rpool/USERDATA                                    89.4M  10.8G       96K  /
rpool/USERDATA/oem_sju5rn                         89.1M  10.8G     71.2M  /home/oem
rpool/USERDATA/root_sju5rn                         192K  10.8G      128K  /root

```


Yes, that looks familiar from before this whole graphics issue, but doing <zfs list> now returns <no datasets available>

---

### Post by #&amp;thj^% on 2022-03-24
That would do it!
So now have you found everything

---

### Post by #&amp;thj^% on 2022-03-24
Ok, this enters new waters for me, but what shows with:
```
sudo zfs list -t snapshot
```
and will this show anything:
```
zpool list
```
maybe and hopefully this:
```
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool   960M   301M   659M        -         -     2%    31%  1.00x    ONLINE  -
rpool  17.5G  6.15G  11.4G        -         -     7%    35%  1.00x    ONLINE  -

```
LAST EDIT:
```
id
uid=29999(oem) gid=29999(oem) groups=29999(oem),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),123(lpadmin),134(lxd),135(sambashare)

```

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> Ok, this enters new waters for me, but what shows with:
```
sudo zfs list -t snapshot
```

no datasets available

> **1fallen said:**
>  and will this show anything:
```
zpool list
```

no pools available

> **1fallen said:**
>  maybe and hopefully this:
```
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool   960M   301M   659M        -         -     2%    31%  1.00x    ONLINE  -
rpool  17.5G  6.15G  11.4G        -         -     7%    35%  1.00x    ONLINE  -

```
LAST EDIT:
```
id
uid=29999(oem) gid=29999(oem) groups=29999(oem),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),123(lpadmin),134(lxd),135(sambashare)

```

id returned:
uid=1000(andrew) gid=1000(andrew) groups=1000(andrew),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),132(lxd),133(sambashare)

---

### Post by #&amp;thj^% on 2022-03-24
EDIT: Please use MAFoElffen code below first post # 41

So far I haven't been able to reproduce your problem, I've always been back and running with:
```
zpool import -d /dev/disk/by-id tank
```
Your id code looks ok.

---

### Post by MAFoElffen on 2022-03-24
Thought I would check as I was going out the door...

Hint. Try: 
```

sudo -i
zpool import -N -R /mnt rpool
zfs list 

```
If that works, look at the fstab, if not there, add a moint-point to directory structure, then add to fstab. If there then 
```

mount -a

```
and debug why it is not mounting...

Bye for now. Out the door.

---

### Post by andrewcorser on 2022-03-24
> **1fallen said:**
> EDIT: Please use MAFoElffen code below first post # 41

So far I haven't been able to reproduce your problem, I've always been back and running with:
```
zpool import -d /dev/disk/by-id tank
```
Your id code looks ok.

YAY! zpool import -d /dev/disk/by-id tank did it!!

Everything is back there now!!

Well Done 1fallen!  You are a star! (as is MAFoElffen!)


Now it is there in this session, will the pool be imported if I reboot the system?


[[...and I will have to do something about Tresorit filling up the wrong drive...!]]]

---

### Post by #&amp;thj^% on 2022-03-24
We just didn't want to leave a bad taste with your forum experience. 
Before you reboot lets have a look at:
```
cat /etc/fstab
```
and make sure UUID's line up, in fact just paste back whats shown please
mine:
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot/efi was on /dev/sda2 during installation
UUID=958D-F921  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub	/boot/grub	none	defaults,bind	0	0
UUID=61979fc8-7692-4830-a9bd-f099b76f0510	none	swap	sw	0
```
UUID's can be checked with:
```
sudo blkid
/dev/sda2: UUID="958D-F921" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="fc75d552-7e98-4308-a9ef-4e383b5ca1d0"
/dev/sda3: UUID="61979fc8-7692-4830-a9bd-f099b76f0510" TYPE="swap" PARTUUID="59829140-fb8b-604a-914c-eb8ae09138cd"
/dev/sda4: LABEL="bpool" UUID="2131494397538411336" UUID_SUB="6918461006960061841" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="b50b813c-380e-3347-af7c-3fb2803e1486"
/dev/sda5: LABEL="rpool" UUID="12696067411613050178" UUID_SUB="17344244843498502668" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="27ce7637-ea2c-7a47-b8c9-1ef985354ddb"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sda1: PARTUUID="3e2ee31e-d9a2-49d0-b70b-d75ea7980cec"
```

---

### Post by #&amp;thj^% on 2022-03-25
After all this, I'm going to have to take a step back on my stance with ZFS.
I put this system through a literal hell.
first by filling "/" to 100% capacity then correcting, importing pools back to get a working system.
Then a Version upgrade from impish to jammy, *but during that process I did a forced shutdown the system was about 1/3 of the way, through installing just under 1600 packages. I had 575 packages that were corrupt & mis-configured.(Nothing I would suggest any user to do, in fact I strongly warn against that stupidity.)
Rebooted to a non working desktop (oops something went wrong), repaired the package manager and my pools and Bob's yer Uncle. A fully operational system. I'm not ready to throw this on my production machine's just yet, but to me this speaks volumes for ZFS. (had to give the deserved credit back)
I'll keep it around for a bit more time. (Time Tested)

---

