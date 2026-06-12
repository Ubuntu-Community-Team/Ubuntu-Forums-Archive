---
title: "How do I clean a flashdrive"
date: 2016-12-26
forum: General Help
---

### Post by Camilia on 2016-12-26
I have been trying to clean a flashdrive on PC with os ubuntu 16.04 

These are the commands I have used.
sudo umount -l /dev/sdbx
sudo dd if=/dev/zero of=/dev/sdbx

Replace x with your device ID.

Any other suggestions?

---

### Post by oldos2er on 2016-12-26
By "clean" do you mean format? Or wipe? Both gparted (partition editor, can be used to format) and the wipe program are in the repositories. But I'm not sure why you would need anything beyond the dd command you already used.

---

### Post by Bucky Ball on 2016-12-26
Yes. You have the answer in your post.

> Replace x with your device ID.

You are trying with this:

```
sudo umount -l /dev/sdbx
sudo dd if=/dev/zero of=/dev/sdbx
```

See the issue? You don't have a partition called 'sdbx'. You need to replace the 'x' with the number of the partition, i.e. sdb2, or whatever it is that you're trying to work on. 

Issue this command:

```
sudo blkid
```

Find the partition you are after and get the correct details. If it is sdb2, for instance, then:

```
sudo umount -l /dev/sdb2
sudo dd if=/dev/zero of=/dev/sdb2
```

In other words, 
> Replace x with your device ID.

Personally, I use Gparted and 'Device> Create new partition table. That should wipe the lot.

Hope that helps. :)

---

### Post by Camilia on 2016-12-26
I used these commands with name of flashdrive where x is
sudo umount -l /dev/sdbx
sudo dd if=/dev/zero of=/dev/sdbx

Just tried name of flashdrive where x is.
sudo dd if=/dev/zero of=/dev/sdX bs=1k count=0

Still have all of my excel and word documents on the flashdrive. I want it to be blank.

---

### Post by Camilia on 2016-12-26
> **Bucky Ball said:**
> 
Personally, I use Gparted and 'Device> Create new partition table. That should wipe the lot.

Hope that helps. :)
Tried Gparted and 'Device> Create new partition table and got this message-
2 partitions are currently active on device /dev/sda

Repasted the commands in the terminal and now PC does not recognizing flashdrive. Perhaps on my laptop at work I can fix it for it has windows.

Tred gparted again and still get the same message 
A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.
Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.

---

### Post by sudodus on 2016-12-26
I suggest that you try a tool that I developed recently and am still testing. It is intended to be easy to use, and it can Do USB Stuff - so I call it ***dus*** with the graphical front end ***guidus***. One of the things it can do is wipe a USB drive (overwrite with zeros). Another thing is restore to a standard drive for data storage. But the main task is to make USB boot drives. And in all these cases dus is helping you to find and address the target drive in the correct way, both to avoid writing to the wrong drive and to write *correctly* to the right drive.

```
sudo add-apt-repository universe  # this line only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install guidus        # dus with a GUI interface and zenity menus
```

See these links:

[Install guidus from the unstable PPA](https://help.ubuntu.com/community/mkusb/gui#from_the_unstable_PPA)

[dus - a revamped interface of mkusb and mkusb-nox](https://help.ubuntu.com/community/mkusb/gui#dus_-_a_revamped_interface_of_mkusb_and_mkusb-nox)

There is a short demo video at the following link by *ventrical*:

[Putting up 2 links to videos I made](https://ubuntuforums.org/showthread.php?t=1958073&page=25&p=13578017#post13578017)

---

