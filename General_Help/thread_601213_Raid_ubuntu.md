---
title: "Raid ubuntu"
date: 2007-11-03
forum: General Help
---

### Post by morior on 2007-11-03
I have a Gigabyte 965P-DS3 board with two seagate 500's attached to the gigabyte sata controller.  The bios is setup to mirror the drives.  I am trying to set the raid drive up as one big ext3.  I have ubuntu/windows on a separate drive.  I've read various things about dmraid and mdadm, but I am lost.  I am on 7.04 right now and need help.  please point me in the right direction or talk to me like I'm four.  I need detailed instructions on what to do next.

---

### Post by morior on 2007-11-03
bump for help

---

### Post by fjgaude on 2007-11-03
One way is to use mdadm. For that you would in your BIOS set the two drives as Linear or JBOD, however the raid program calls independent devices.

Then with mdadm you would create the raid0 array like so:

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/yyy /dev/zzz
```

Then create the filesystem on the array:

```
sudo mkfs -t ext3 /dev/md0
```

```
sudo mdadm -D /dev/md0
cat /proc/mdstat
```

to display and make sure you have created it correctly.

Then after you have created a mount point on your inplace / directory, /media/raid you would mount the array:

```
sudo mount /dev/md0 /media/raid
```

The other way using dmraid is not as clear in my opinion. You might want to read this help column:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_the_mdadm.conf_Configuration_File](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_the_mdadm.conf_Configuration_File)

Let us know how you do.

---

### Post by Tanker Bob on 2007-11-04
Checkout the tutorial at [http://www.iki.fi/kuparine/comp/ubuntu/en/raid.html](http://www.iki.fi/kuparine/comp/ubuntu/en/raid.html). That's how I set my RAID1 up and it worked like a charm.

---

### Post by morior on 2007-11-04
With the mdadm The bios won't see it as a riad  device correct?  how will the windows operating system view it? With the next one, I think your trying to install ubuntu on raid, I have ubuntu installed I just need to access the raid device from within ubuntu.  now am I all wrong here?

---

### Post by fjgaude on 2007-11-04
> **morior said:**
> With the mdadm The bios won't see it as a riad  device correct?  how will the windows operating system view it? With the next one, I think your trying to install ubuntu on raid, I have ubuntu installed I just need to access the raid device from within ubuntu.  now am I all wrong here?

No, the BIOS will not see it as raid, and when you boot into windows the array will not be seen.

I guess if you wish to see the array in windows you will have to make the array an ntfs one, eh?

So you make the BIOS create the raid0 array, then in ubuntu use dmraid to show and then mount the array.

First download dmraid using Synaptic. The try:

```
sudo dmraid -tay
```

You will mount the array using the /dev/mapper/xxxx_nnnnnnn shown by using:

```
sudo dmraid -r
```

Create a mount point:

```
sudo mkdir /media/raid
sudo mount /dev/mapper/xxxx_nnnnnnn -t ntfs-3g /media/raid
```

That's about the best I can do to assist. I think there are how-tos to show this more in detail.

---

### Post by morior on 2007-11-04
I booted back into windows and formatted to ntfs.  Switched back to ubuntu and it shows up.  both drives show up.  I'll have to experiment to see if it syncs up or not.  I might also have to experiment to see if I can format the drive to ext3.  So far I can share files between the two and that was the most important.

---

### Post by fjgaude on 2007-11-04
Good show. If you format to ext3 I'm not sure how you will see the array when you are booted into Windows. Anyway... you are learning as I'm learning. <smile>

---

### Post by Tanker Bob on 2007-11-04
Glad that you found a solution!

---

