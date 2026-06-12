---
title: "Question on Live Xubuntu CD useage."
date: 2015-04-30
forum: General Help
---

### Post by mikodo on 2015-04-30
Hi Everyone.

Quick dumb question.


I've had to wait, until now, to amalgamate my Ubuntu 10.4.2 desktop with whom I update Grub2 in, and my Xubuntu 12.04.1. I've saved all my Firefox stuff for both, yesterday in FF Sync. I am going to move my data to an external drive from both distro's to a data partiton on an external drive, then, change out drives on my one and only machine (destop tower), install Xubuntu 14.04.1 on it and eventually symblink it to a new data partiton/drive, that I will make on the new drive(s). I think I will use GPT for it.

I am now offline while I do this, and doing some stuff for the first time (GPT, data drive and symblink), starting tomorrow. I intend to stay off line, until I have the Xubuntu 14.04.1 installed.

Question. If I need to search for help with any of this, is it Okay, to use the live CD of Xubuntu 14.04.1, to search for answers, like I am using now? I don't think I should use either of the distros's now installed, as they are both now EOL but, I dunno.

Edit: I am shutting down, and will check here tomorrow from the live CD.

Thanks.

---

### Post by Dennis N on 2015-04-30
Well, Xubuntu 12.04 will continue to be supported for the non-Xubuntu specific packages and that is the majority on the OS, I would think. The cd on the other hand has had no updates since the iso was created, so the 12.04 seems safer to me (at least no riskier) being "out of support" only a couple of days. Does that make sense? But you could use the cd - since everything is backed up and safe, and you plan to reinstall soon, what is the risk?

---

### Post by mikodo on 2015-05-01
Thanks, Dennis N.

I needed to hear that . I will use 12.04 for a couple of more days, or so, until, I switch.

guess, I was just paranoid.

Yes, the data, is backed up.

In fact, I'm going run another rysnc, first thing again tomorrow. I'm really tired now.

Edit: I ran rysnc tonight. That took 10 secs. ;)

---

### Post by Bucky Ball on 2015-05-01
Just throwing this in in case you can use it. I have four installs (at last count) and one data partition. I generally let the installs install with NO /home partition so they create a /home folder inside /. Once installed, I then delete the folders in the /home partition and replace them with symlinks. All four installs use the same data directories so doesn't matter which install I'm booted into, if I change data, it is reflected in all the installs (as they all use the same data partitions). Firefox and Thunderbird profiles are also shared from the data partition (so Firefox setup and email is the same in all).

The syntax is:

> ln -s 'location to link to' 'name of symlink'

For example:
ln -s /media/data_drive/Documents /home/<username>/Documents

... where <username> is your user name. This last command will create a symlink in /home/<username> called 'Documents' linked to the real directory, /media/data_drive/Documents. That simple! ;)

If you already knew this stuff, sorry for reiterating. If not, hope you can use it and post if you have any questions about this. ;)

---

### Post by Dennis N on 2015-05-01
That should work. Good decisions on using GPT partition table and separate data partition. I have been using GPT for maybe two years now and it works very well even on my BIOS systems.

---

### Post by mikodo on 2015-05-01
> **Bucky Ball said:**
> Just throwing this in in case you can use it. 

Thanks, Bucky.

I really am tired, and I will *certainly read that tomorrow.

I think though, we have the same idea. One data partition, that can be symblinked from any distro.

nighty-nite.

---

### Post by Bucky Ball on 2015-05-01
> **mikodo said:**
> 

I think though, we have the same idea. One data partition, that can be symblinked from any distro.



That's it. When I back up I only need to backup one data partition, not four installs with data spewed hither and tither. Sleep well and may tomorrow bring a computing victory or three. ;)

---

### Post by mikodo on 2015-05-01
> **Bucky Ball said:**
> Firefox and Thunderbird profiles are also shared from the data partition (so Firefox setup and email is the same in all). 

*Pure* oldfred copy:

```
sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#sudo chmod 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
# find your UUID
sudo blkid
#Edit fstab with your UUID, use ext3 or ext4 depending on format:
gksudo gedit /etc/fstab
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 auto,users,rw,relatime 0 2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

You can delete oldMusic and other folders.
```

* I will just delete the folders too, in each new installs *first* then, do the above and the symlinking.

* Good old Carla Shroder, gives me insight on finding the GUID's.    "[Using the New GUID Partition Table in Linux]("https://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-")"

**Two more questions, Bucky or anyone: (If I find, I should start a new thread for these questions, I will).**

1) I have no idea, how to do this for Firefox and Thunderbird profiles. Is there is a link you can share, for me to read about that, (I really don't know what profiles are).

2) It seems somewhere in the recesses of mind, I remember someone saying that there is no reason to use "sudo", with chmod after sudo chown, as it invites an unnecessary   security risk. See below. Do I have that right?

```
sudo chown $USER:$USER /mnt/data

sudo chmod -R a+rwX /mnt/data
```

Thank you, again.

---

