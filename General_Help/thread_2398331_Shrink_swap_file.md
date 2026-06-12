---
title: "Shrink swap file"
date: 2018-08-10
forum: General Help
---

### Post by raleigh3 on 2018-08-10
I want to shrink my swap file from 2 Gb to 1 Gb.

I thought Gpart would do it.

How do I do that ?

---

### Post by &amp;KyT$0P# on 2018-08-10
1) Temporarily stop the system using the swapfile
```
sudo swapoff -a
```

2) delete the swapfile
```
sudo rm -v [COLOR="#FF0000"]/path/to/your/swapfile[/COLOR]
```

3) create a new file of 1 GB size in exactly the same place as your old one was
```
sudo dd if=/dev/zero of=[COLOR="#FF0000"]/path/to/your/swapfile[/COLOR] bs=1M count=1024
```

4) use [FONT=Courier New]mkswap[/FONT] to turn the file from (3) into a swapfile
```
sudo mkswap [COLOR="#FF0000"]/path/to/your/swapfile[/COLOR]
```

5) For added security, set permissions on swapfile
```
sudo chmod 0600 [COLOR="#FF0000"]/path/to/your/swapfile[/COLOR]
```

6) reboot


Replace [COLOR="#FF0000"]/path/to/your/swapfile[/COLOR] with the actual full path to your swapfile.

Does it work?

---

### Post by #&amp;thj^% on 2018-08-10
You will have to remove the old file first:
Run the following commands:
```

sudo swapoff -a -v
sudo rm /swapfile
#back up /etc/fstab:
sudo cp /etc/fstab /etc/fstab.bak
sudo sed -i '/\/swapfile/d' /etc/fstab
```

Now add the 1 Gig file
Adjust this to meet the needs of your own system: (I set this as 1Gig)

```
sudo fallocate -l 1G /swapfile
```

verify that the correct amount of space was reserved by :

```
ls -lh /swapfile
```

Make the file only accessible to root by typing:

```
sudo chmod 600 /swapfile
```

Verify the permissions change by typing:

```
ls -lh /swapfile

-rw------- 1 root root 1.0G Apr 25 11:14 /swapfile
```

As you can see, only the root user has the read and write flags enabled.

now mark the file as swap space by:

```
sudo mkswap /swapfile
```

After marking the file, we can enable the swap file, allowing our system to start utilizing it:

```
sudo swapon /swapfile
```

We can verify that the swap is available by typing:

```
sudo swapon --show
NAME      TYPE       SIZE USED PRIO
/dev/sda2 partition    3G   0B   -2
/swapfile file      1024M   0B   -3

```
As you can see i never used a swapfile instead I used a partition and just now added a swap file.

Make the Swap File Permanent:
NOTE:Back up the /etc/fstab file in case anything goes wrong:

```
sudo cp /etc/fstab /etc/fstab.bak
```

You can add the swap file information to the end of your /etc/fstab file by typing:

```
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

---

### Post by raleigh3 on 2018-08-10
What I did was comment out the swap file line in fstab and rebooted.

Swap now shows as zero.

Is that method ok. ?

---

### Post by #&amp;thj^% on 2018-08-10
If you have enough RAM.
I often run with no swap enabled. Its just a choice only you can make with your system.

---

### Post by raleigh3 on 2018-08-10
Yes, I have 8 Gb. 

Never have come close to using more than a small percentage.

---

