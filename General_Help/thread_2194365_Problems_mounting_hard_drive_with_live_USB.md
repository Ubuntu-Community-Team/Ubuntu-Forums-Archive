---
title: "Problems mounting hard drive with live USB"
date: 2013-12-18
forum: General Help
---

### Post by riceroma on 2013-12-18
Hello. All

This is the problem I am having, when I mount a hard drive. To scan with rkhunter.

Using this, sudo mount /dev/sda6 /mnt/safe  mount goes good, but when I cd into /mnt/safe all I see are the files on the live USB? I am thinking this is not what I should be scanning. Shouldn't I be seeing the files on /dev/sda6 ? I can if I use sudo chroot /mnt/safe but when I run a scan with rkhunter I get this error sudo: unable to resolve host ubuntu, followed by sudo: rkhunter: command not found. What am I doing wrong here.

When using  sudo mount /dev/sda6 /mnt/safe  I should be seeing files of sda6 in /mnt/safe or am I all worng here.

Thanks

Sorry I should have said, running Ubuntu 13.10 and doing all of the above using live usb with ubuntu 13.10

---

### Post by deadflowr on 2013-12-18
It would probably help to know the rkhunter command you tried to use.
Sometimes the command might be, in general, correct but the syntax is off.
Post it.

I would also suggest when mounting, if not sure that it IS mounted, maybe do a little digging.
Run an ls command in the /mnt/safe folder, and see if the files/folders listed are the ones in the partition you wanted to try to mount.

---

### Post by riceroma on 2013-12-18
Hello. Deadflowr

First thanks ;-) For replying to my question. Yes sorry I should have shown the command used. Here you go.

sudo rkhunter --checkall --skip-keypress --tmpdir /mnt/safe I've also used --binddir and sudo rkhunter -c

And yes to answer your question, after using this command  sudo mount /dev/sda6 /mnt/safe  than I ls into /mnt/safe

again it always seems to put me into /mnt/safe on the live USB ? But as I said above if I chroot into /mnt/safe and again I ls
the files, for /dev/sda6 show up in /mnt/safe but again I can't run rkhunter on /mnt/safe after using chroot ? When I try this is the error
I keep receiving. sudo: unable to resolve host ubuntu and sudo: rkhunter: command not found. I've also tried using a different mount point, like /media/safe and so on.

Many thanks

---

### Post by riceroma on 2013-12-18
Hi. Deadflowr

Not really sure if you're logged in, I dd some more checking, and this is what I came up with.
When using mount I could see that /dev/sda6 /media/safe Is mounted, so I gave this a try once more.
chroot /media/safe and when I did mount again this is what came up.

sudo mount
sudo: unable to resolve host ubuntu
/dev/sda6 on /  type ext4 (rw, errors=remount-ro)

Now I am not 100% sure on this, but doesn't unable to resolve host ubuntu, mean it can't locate my ubuntu install on /media/safe ?
And when using chroot this (rw, errors=remount-ro) Is saying it can't remount /media/safe ? Any help at all.

Thanks

---

### Post by Iowan on 2013-12-18
Looks like you have the hostname halfway modified.
(Need to modify */etc/hostname*, and */etc/hosts*)
If you  haven't modified either, then this is meaningless help :)

---

### Post by deadflowr on 2013-12-18
For what you want, chkrootkit might be the better option.
rkhunter, from what I gather, scans the whole filesystem.
When you mount the /dev/sda6 as /media/safe, it gets added to the file system running on the usb.
So, in that regard, while the rkhunter might show it scanning the usb, it is also scanning the /media directory and all it's contents.
chroot into the sda6 partition will only work if you have the rkhunter tools in the sda6 partition.
Basically, you would need to run the chroot with networking enabled, as so you could grab the packages for rkhunter.

Back to my main point,
chkrootkit has an option to point to anywhere as the root (/) directory.
And will scan that as the root (/).

And disregard the options in rkhunter for both bindir and tmpdir. They're options for how rkhunter works and have no bearing on the scanning of the file system, or which parts of the system get scanned.

Don't know if any of this still makes sense.


For what's it's worth though, rkhunter has a configuration file in /etc/rkhunter.conf.
Don't know much about what it can do(outside of whitelisting/blacklisting), but their might be an option or ability to make the program run on specific parts of a system.
Could be worth a look, if chkrootkit isn't what you want.

---

### Post by riceroma on 2013-12-19
Hi. Deadflowr

I can't thank you enough, to answer your question yes it makes sense ;-) I notice when running a scan with rkhunter there was some activity on the USB, so it had to be scanning elsewhere. Duh /media/safe ;-) As for chkrootkit I noticed very little activity going on with the USB, so I am going to say it's scanning /media/safe ;-) I guess what I'm saying is I believe you were right all along. You and yours have a blessed holiday! Once more many thanks.

@Lowan

Thanks for the reply, have a blessed holiday ;-)

---

