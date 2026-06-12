---
title: "Slow boot with errors...."
date: 2019-06-04
forum: General Help
---

### Post by Furycd001 on 2019-06-04
HI. As of the past week or so my system has been a tad slow to boot and I now see ["this error"]("https://i.imgur.com/Sc019Gz.jpg") on boot. I'm running 16.04.06 & have not changed anything on my system recently. Please halp thank you.

---

### Post by Bashing-om on 2019-06-04
jonny6; Hello

As a start; I would confirm that the referenced UUID in fact does not exist:
```

ls /dev/disk/by-uuid -alh

```

Then see what in fact does exist:
```

sudo fdisk -lu
sudo blkid -c /dev/null -o list
cat /etc/fstab

```

in an effort to find out where the numbers do not match - and why.

[INDENT]we can do that
[/INDENT]

---

### Post by Furycd001 on 2019-06-05
Thank you for replying. I ran each command and piped the output to termbin.com. That way everything stayed intact. Click on each command below to see the output....[B]

[ls /dev/disk/by-uuid -alh]("https://termbin.com/ug5d")[/B]


**[sudo fdisk -lu]("https://termbin.com/9eup") << This command also output "Partition 2 does not start on physical sector boundary".**


[**sudo blkid -c /dev/null -o list**]("https://termbin.com/8lyy")


[**cat /etc/fstab**]("https://termbin.com/d5cs")

---

### Post by Bashing-om on 2019-06-05
jonny6 - Hummm ...

Surprise - surprise  the swap partition is identified !.. so far so well. So - why the system screaming so about the swap partition ?

what shows:
```

swapon --summary

```
as I do note there was a disk change from the initial install from sdb to sda --- but the UUID is correct in /etc/fstab.

[INDENT][INDENT]the hunt is on and
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Furycd001 on 2019-06-06
[swapon --summary]("https://termbin.com/2zws")

When I installed the system I done it through the mini.iso. Maybe something might just not be installed ??

---

### Post by Bashing-om on 2019-06-06
jonny6; Hummmm ...

No issue there either - down the rabbit hole - deeper - we go :)

Let's look:
Does this file exist ?
```

ls -al /etc/uswsusp.conf

```
I do not expect that it does.

How about here ?
```

cat /etc/initramfs-tools/conf.d/resume

```
Where the listed UUID should be the same as in the swap line in the /etc/fstab file.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by Furycd001 on 2019-06-07
**ls -al /etc/uswsusp.conf**
```
ls: cannot access '/etc/uswsusp.conf': No such file or directory
```

**cat /etc/initramfs-tools/conf.d/resume**
```
RESUME=UUID=a7f0e1e4-5b00-467e-9cdc-3d7f51affe30
```

---

### Post by Bashing-om on 2019-06-07
jonny6; Sheesshh ..

That is the extent of my knowledge. All we look at is correct.
Perhaps others here can suggest a reason that the seek for swap times out ?
I too would like to know.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by cruzer001 on 2019-06-07
```
systemctl status systemd-udevd.service
```
Anything there that Bashing-om has not already covered?

---

### Post by Furycd001 on 2019-06-08
> **Bashing-om said:**
> jonny6; Sheesshh ..

That is the extent of my knowledge. All we look at is correct.
Perhaps others here can suggest a reason that the seek for swap times out ?
I too would like to know.
[INDENT][INDENT]got to be a reason
[/INDENT]
[/INDENT]


Thank you very much for helping....

---

### Post by Furycd001 on 2019-06-08
> **cruzer001 said:**
> ```
systemctl status systemd-udevd.service
```
Anything there that Bashing-om has not already covered?

[**systemctl status systemd-udevd.service**]("https://termbin.com/enpi")

---

### Post by Bashing-om on 2019-06-08
jonny6;

Still here - see how this works out.

[INDENT]it is a learning process\
[/INDENT]

---

### Post by cruzer001 on 2019-06-08
I see nothing, sorry :(

---

### Post by Rubi1200 on 2019-06-08
Can we please see the output for the following:

```
journalctl -b | grep swap
```

---

### Post by Furycd001 on 2019-06-10
> **Rubi1200 said:**
> Can we please see the output for the following:

```
journalctl -b | grep swap
```

[**journalctl -b | grep swap**]("https://termbin.com/plcn")

---

### Post by Rubi1200 on 2019-06-10
So, here is an interesting discrepancy from all the various outputs you have posted.

All the various commands, including the one I asked for, show /root as being on sda1 and swap on sda5.

But, here is the thing: fstab shows something else [https://prnt.sc/nzumon](https://prnt.sc/nzumon)

fstab says /root was on sdb1 and swap on sdb5, very curious since all the other outputs show sda1 and sda5 respectively.

How have you been booting until now without errors?

Was the original install on another drive and you changed it perhaps?

---

### Post by Furycd001 on 2019-06-10
> **Rubi1200 said:**
> So, here is an interesting discrepancy from all the various outputs you have posted.

All the various commands, including the one I asked for, show /root as being on sda1 and swap on sda5.

But, here is the thing: fstab shows something else [https://prnt.sc/nzumon](https://prnt.sc/nzumon)

fstab says /root was on sdb1 and swap on sdb5, very curious since all the other outputs show sda1 and sda5 respectively.

How have you been booting until now without errors?

Was the original install on another drive and you changed it perhaps?

Ok So originally I had default xubuntu installed, but it was kind of bloat from the amount of software & stuff that I installed over time. I went and done a full re-install using the the [16.04 Netboot iso]("http://cdimages.ubuntu.com/netboot/") on a usb drive. I booted the usb as usual and went through the installation selecting the minimal xubuntu option & selecting to wipe the drive in the partition setup stage. Everything went fine and I've been using the system daily until these errors started showing on boot. I've not moved any drives or plugged anything into the computer other than my usb mouse, usb hd for backups & usb pendrive for copying files. There was only two things plugged into the computer during the installation. The usb mouse & the usb pendrive to do the installation....

---

### Post by Rubi1200 on 2019-06-10
Interesting, hmm.

Well, somehow fstab seems to have the incorrect information (at least from all you have posted).

Either that or swap has somehow become corrupted.

I think you need to edit fstab and change the partitions from sdb1 and sdb5 to sda1 and sda5 but I want to check first whether that will cause problems or not so please wait until I get back to you.

Thanks.

---

### Post by Furycd001 on 2019-06-10
> **Rubi1200 said:**
> Interesting, hmm.

Well, somehow fstab seems to have the incorrect information (at least from all you have posted).

Either that or swap has somehow become corrupted.

I think you need to edit fstab and change the partitions from sdb1 and sdb5 to sda1 and sda5 but I want to check first whether that will cause problems or not so please wait until I get back to you.

Thanks.

Ok. Thank you very much for helping & for checking :)

---

### Post by oldfred on 2019-06-10
Do not think the reference to sda in # line in fstab matters as long as UUID is correct. And UUID looks correct.

Drives do change order and that can change anything that uses drive or device reference. BIOS & grub use drive like hd0 and when booting Ubuntu may use device like /dev/sda1. So that is why they changed to use UUID, which should only change if partition is reformatted.
I have had issues of grub seeing wrong drive whenever I reboot with a flash drive plugged in. Flash drive may be sdd when plugged in, but on reboot it becomes sda and every other drive changes device letter. But system is ok, since using UUIDs.

I have not seen a damaged swap. It just is unformatted space to write into.
But this suggests reformatting it which will change UUID, so you then have to update UUID in fstab and 
       if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid 
[https://askubuntu.com/questions/614463/swap-doesnt-seem-to-mount-after-update](https://askubuntu.com/questions/614463/swap-doesnt-seem-to-mount-after-update)

---

### Post by Rubi1200 on 2019-06-10
I thought I was onto something but apparently not.

The only other references I could find to those specific errors mentioned in the first post was a possible corruption of the swap partition.

The suggested solution was to reformat swap but I honestly do not know if that will work.

Any other ideas?

---

### Post by Furycd001 on 2019-06-10
> **Rubi1200 said:**
> I thought I was onto something but apparently not.

The only other references I could find to those specific errors mentioned in the first post was a possible corruption of the swap partition.

The suggested solution was to reformat swap but I honestly do not know if that will work.

Any other ideas?

Thank you for checking :) If I'm not mistaken newer versions of Ubuntu have switched to using a swap file ?? If that's the case then maybe upgrading could be a solution ??

---

### Post by oldfred on 2019-06-10
I have a swap partition during a test install it just used it. I wanted the swap file just to see if it worked.
It was a lot of steps, but if you follow them, you can delete a swap partition and add a swap file.
If you reinstall, be sure to either delete swap partition first or you can click on swap partition and say do not use which I did do on another test install.
Be sure to remove old entry from fstab and add new entry. And edit /etc/initramfs-tools/conf.d/resume to avoid issues.

       [https://wiki.manjaro.org/index.php?title=Add_a_/swapfile](https://wiki.manjaro.org/index.php?title=Add_a_/swapfile)
[https://devanswers.co/guide-creating-swap-space-ubuntu-16-04/](https://devanswers.co/guide-creating-swap-space-ubuntu-16-04/)
fred@cosmic-z97:~$ sudo fallocate -l 2G /swapfile
[sudo] password for fred: 
fred@cosmic-z97:~$ ls -lh /swapfile
-rw-r--r-- 1 root root 2.0G Jun 26 15:19 /swapfile
fred@cosmic-z97:~$ sudo chmod 600 /swapfile
fred@cosmic-z97:~$ ls -lh /swapfile
-rw------- 1 root root 2.0G Jun 26 15:19 /swapfile
fred@cosmic-z97:~$ sudo mkswap /swapfile
Setting up swapspace version 1, size = 2 GiB (2147479552 bytes)
no label, UUID=0231a740-006b-4d3b-ad96-bc963a45be9c
fred@cosmic-z97:~$ sudo mount -a
fred@cosmic-z97:~$ sudo swapon /swapfile
fred@cosmic-z97:~$ sudo swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/sda4 partition 1.9G   0B   -2
/dev/sdb7 partition 2.1G   0B   -3
/swapfile file        2G   0B   -4
fred@cosmic-usbssd:~$ y
swapon: /swapfile: insecure permissions 0644, 0600 suggested.
fred@cosmic-usbssd:~$ sudo chmod 0600 /swapfile
fred@cosmic-usbssd:~$ ls -lh /swapfile
-rw------- 1 root root 2.0G Jul  5 12:56 /swapfile

---

### Post by Furycd001 on 2019-06-10
> **oldfred said:**
> I have a swap partition during a test install it just used it. I wanted the swap file just to see if it worked.
It was a lot of steps, but if you follow them, you can delete a swap partition and add a swap file.
If you reinstall, be sure to either delete swap partition first or you can click on swap partition and say do not use which I did do on another test install.
Be sure to remove old entry from fstab and add new entry. And edit /etc/initramfs-tools/conf.d/resume to avoid issues.

       [https://wiki.manjaro.org/index.php?title=Add_a_/swapfile](https://wiki.manjaro.org/index.php?title=Add_a_/swapfile)
[https://devanswers.co/guide-creating-swap-space-ubuntu-16-04/](https://devanswers.co/guide-creating-swap-space-ubuntu-16-04/)
fred@cosmic-z97:~$ sudo fallocate -l 2G /swapfile
[sudo] password for fred: 
fred@cosmic-z97:~$ ls -lh /swapfile
-rw-r--r-- 1 root root 2.0G Jun 26 15:19 /swapfile
fred@cosmic-z97:~$ sudo chmod 600 /swapfile
fred@cosmic-z97:~$ ls -lh /swapfile
-rw------- 1 root root 2.0G Jun 26 15:19 /swapfile
fred@cosmic-z97:~$ sudo mkswap /swapfile
Setting up swapspace version 1, size = 2 GiB (2147479552 bytes)
no label, UUID=0231a740-006b-4d3b-ad96-bc963a45be9c
fred@cosmic-z97:~$ sudo mount -a
fred@cosmic-z97:~$ sudo swapon /swapfile
fred@cosmic-z97:~$ sudo swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/sda4 partition 1.9G   0B   -2
/dev/sdb7 partition 2.1G   0B   -3
/swapfile file        2G   0B   -4
fred@cosmic-usbssd:~$ y
swapon: /swapfile: insecure permissions 0644, 0600 suggested.
fred@cosmic-usbssd:~$ sudo chmod 0600 /swapfile
fred@cosmic-usbssd:~$ ls -lh /swapfile
-rw------- 1 root root 2.0G Jul  5 12:56 /swapfile

Thank you very much for this super detailed reply. Going to give this a go tomorrow, but for now this thread is solved. Thank you everyone that offered help....

---

### Post by cruzer001 on 2019-06-10
Yet another oldfred enter in my ubuntu collection.  Thanks :)

---

