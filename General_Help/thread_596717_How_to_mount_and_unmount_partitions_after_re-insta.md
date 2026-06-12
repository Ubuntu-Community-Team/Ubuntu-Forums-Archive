---
title: "How to mount and unmount partitions after re-install"
date: 2007-10-29
forum: General Help
---

### Post by bluepowder7 on 2007-10-29
ok, so i used to have Fawn installed, then upgraded to Gibbon, didn't like it so reinstalled Fawn back again.  i have separate partitions for the OSes, the swap, the boot, and my home stuff (where all my docs are located).  here's how the partitions were set up when i first got this laptop running with Fawn around 3 months ago:

sda1 is the 100meg boot
sda2 is a 2gig swap
sda3 is my 60meg "home" directory
sda 4 is an extended partition with:
  sda5 is an 8gig slot for the ubuntu OS 
  sda6, sda7, and sda8 are each 8gig slots for other OSes (nothing installed there now)

so, after doing the Fawn -> Gibbon -> Fawn thing, i seem to have the following difficulties:

1 - when i go Places -> Home Folder, i'm pretty sure that it's not going to sda3 since it doesn't list all my previously-made folders and the space remaining is shown as around 5gigs.  it looks like it made my home directory as part of the sda5 partition that the OS itself is on.  how do i fix this so that my home directory is actually the entire sda3 partition (which appears to have all my folders and files intact from the previous installs of Ubuntu)?

2 - on the desktop and on the left side of the file browser, it's showing me sda1, sda3, sda6, sda7, and sda8.  i'd like to unmount 6,7,8 since they're set aside for other OSes, but it won't let me do that - says "Cannot unmount the volume.  umount: /media/sda6 mount disagrees with the fstab"



on item 1, if i have to reinstall ubuntu and flag the partitions somehow (maybe i didn't do that correctly), it's quite doable since i did the "go back to Fawn" install earlier this afternoon.  if that's what i NEED to do, can you indicate the steps i need to take when the partition options come up during install?

---

### Post by ofb on 2007-10-29
um, one question. When you did the install, did you choose "Manual" from the partitioning options? After that the next panel shows your devices and their mount points and has little check-boxes so you can select which you'd like formatted.

There, you'd right-click /dev/sda3, select Edit, and from the mount-point drop-down, select /home. For /dev/sda5, you'd do that and select /.

Make sure the swap listed matches your desired swap. Make a check-mark to format only / (which was /dev/sda5).

At least that's what Ubiquity does in 7.10. I think Ubiqity was the same in 7.04, but maybe there are a few differences.

Anyhow... was that what you did?

---

### Post by bluepowder7 on 2007-10-29
yup, i went with the manual method so as not to bugger up the existing partitions.

ah, ok.  i see what step i skipped over.  i DID checkbox the sda5 partition to have it formatted and edited it's 'label' to be just / but i didn't edit the sda3 'label' to /home (i just left it and all the other labels alone)

should i edit the sda6, sda7, and sda8 drive labels to / as well instead of the /media/sda6 that i think it presets, or will that confuse the installer into not knowing which partition to use to install the OS into?

---

### Post by ofb on 2007-10-29
> **bluepowder7 said:**
> should i edit the sda6, sda7, and sda8 drive labels to / as well instead of the /media/sda6 that i think it presets, or will that confuse the installer into not knowing which partition to use to install the OS into?

That would totally confuse the installer. You'd be telling it that they are all targets for the new Ubuntu install.

Now you're getting to your other question about "Cannot unmount the volume. umount: /media/sda6 mount disagrees with the fstab".

In Ubuntu you can mount and then unmount volumes during a session, but you can't unmount something that was already mounted by the fstab. (At least not as a user, maybe as root.)

So I think you want to go into fstab and comment out (place "#" in front of) sda6-8.

I don't know why sda1 is showing up but I don't have a separate boot partition. My grub is nestled in the Win drive in a way that doesn't show up in fstab.

sta3 will cease to show up after the next install because you'll have made it /home

I think, anyway. Make sure this all makes sense to you.

---

### Post by ofb on 2007-10-29
> **ofb said:**
> So I think you want to go into fstab and comment out (place "#" in front of) sda6-8.

I'm presuming you just want them to not show up at all because they are targets for future OS's. If you want them to show up somewhere else or as something else, then you'd be editing their fstab entries to reflect that.

---

### Post by bluepowder7 on 2007-10-29
hmm...  can i just edit the fstab entries of sda3 and sda5 from within Ubuntu without having to reinstall the whole OS?  or has the "home directory" already been partly set up on the sda5 (OS) partition to the point that the only way to clean it all up is to reinstall?

---

### Post by mc4man on 2007-10-29
at the moment sda6,7,8 are just empty logical disks at the end of an extended partition, you can just as well delete them for now and make new one(s) in the future as needed

---

### Post by ofb on 2007-10-30
> **bluepowder7 said:**
> hmm...  can i just edit the fstab entries of sda3 and sda5 from within Ubuntu without having to reinstall the whole OS?  or has the "home directory" already been partly set up on the sda5 (OS) partition to the point that the only way to clean it all up is to reinstall?

Now you're getting into a question that I have yet to have answered satisfactorily. See my elongated thread,
[http://ubuntuforums.org/showthread.php?t=592158](http://ubuntuforums.org/showthread.php?t=592158)

Quick version is yeah, sure, you could /probably/ change your existing /home to /homeBAK, then mkdir /home, then change fstab so sda3 is mounted as /home.

That'll probably work because there isn't much difference between 7.10 and 7.04. Maybe minor breakage that you can take care of easy enough.

But as I say in the older thread I don't know exactly what Ubiquity does to upgrade an existing /home for a new install. There are probably subtle changes. And sometimes less subtle. There will be a few different applications installed, and several of your applications will be different versions. At some point there will be a mess up when using older/newer config files.

(Why are you asking about changing the fstab of sda5? I thought that was /, and you already got it right.)

---

### Post by bluepowder7 on 2007-10-30
bah!  you're right, i had sda5 already set up with the / label from the beginning.  sorry!

i can probably edit the labels of sda6, 7, and 8 without worrying about it too much - they're empty anyways and seeing them in the file manager is merely a cosmetic issue.  the bigger issue is the /home partition, which during my initial 7.04 install a few months ago was properly set up as /home, but during today's ditch-7.10-and-go-back-to-7.04 install i didn't label it right.  if i can change the label without having to do the whole install thing, it saves me quite a bit of time.

looking at your other thread, my /home partition was always only a /home partition, so MAYBE i can avoid the potential issue you brought up there.

hmm, i should probably back up all my crap first!!!

---

### Post by ofb on 2007-10-30
> **bluepowder7 said:**
> looking at your other thread, my /home partition was always only a /home partition, so MAYBE i can avoid the potential issue you brought up there.

Almost. My thread side-tracked into a whole demo of creating a /home partition when there wasn't one. The main question was:

> What I don't understand yet is how the clean install of 7.10 will import/merge/use the 7.04 /home partition.

I'm pretty darn sure it has to do /something/.

> hmm, i should probably back up all my crap first!!!

Absolutely. I've even had two drives fail at the same time.

Get backed up, and then if you feel like being a little risky/experimental, go ahead and try making /home into /homeBAK, then mkdir /home, then edit fstab to mount sda3 as /home. I wouldn't expect more than minor breakage. And you always have the quick recovery of just reversing those changes.

And of course you could still do it "properly" afterwards, and do a fresh install with sda3 as /home and sda5 formatted to be the new root. That should work fine. 

So it's not like you don't have options.

You should probably read through that thread so you pick up tips like don't change your username, computer name, password if you want the old /home to work on the new install. I tried to include all necessary details over there. I'm kinda rushing though here.

---

### Post by ofb on 2007-10-30
Hey, do a backup of /etc while you're at it. A lot of people just back up /home, but if you've done any modifications to your system config, you can save a lot of time by having the old /etc to refer to.

Like for instance I've got modifications to fstab and rc.local and hosts on my machine.

---

