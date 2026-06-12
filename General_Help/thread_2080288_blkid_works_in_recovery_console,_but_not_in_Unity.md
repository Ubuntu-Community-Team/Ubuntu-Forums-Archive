---
title: "blkid works in recovery console, but not in Unity"
date: 2012-11-03
forum: General Help
---

### Post by matthew_petty on 2012-11-03
Hi,

I'm trying to configure an NTFS drive to automount. I've done this before no problem, using both the manual method and ntfs-config.

This time, blkid doesn't work; it just hangs. So I can't manually edit fstab and ntfs-config hangs, too. blkid works fine in a recovery console, so I could set up my automount there, but I want to fix this for the future, too.

blkid -c /dev/null also hangs
blkid -g doesn't hang, but it doesn't fix anything either.

Any ideas?

PS - I'm running 12.10-amd64.

---

### Post by Paulgirardin on 2012-11-03
I am having the same problem: blkid hangs.
pysdm does not open
Mount manager option to mount drives at startup does not work.
I am trying to get internal ext4 drives to mount at startup.

---

### Post by ajgreeny on 2012-11-03
You must use blkid with root permissions. ```
sudo blkid
```will work.

---

### Post by Paulgirardin on 2012-11-03
no it doesn't - I am using sudo ,it asks for my password,I enter it then it just shows a flashing cursor for a long time.

---

### Post by ajgreeny on 2012-11-03
What abut ```
sudo blkid -c /dev/null
``` Does that work?  I do not think the options should make any difference, but it's worth a try.

---

### Post by matthew_petty on 2012-11-03
Thanks, but that isn't helpful. I know it requires root permissions and I already specified in the OP that I tried the new cache option.

---

### Post by Paulgirardin on 2012-11-03
Thanks for the suggestions

sudo blkid -c /dev/null does nothing either.

fstab has UUID for ./ and /Home


I have done the same as the OP and run blkid in a recovery console and manually edited fstab

---

### Post by ajgreeny on 2012-11-03
This does not answer your question as to why **sudo blkid** is not working, but you can get the info in a more roundabout way with the command```
ls -l /dev/disk/by-uuid/
```This will echo in terminal the files named the same as the UUIDs of the partitions, and as those files are just links, it will show you which device (partition) each relates to, such as
```
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 01b9131d-43fe-4b4e-be2b-b319de5a898a -> ../../sdb7
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 0e32eafa-1d98-408a-9fe5-8bf2b8526b0c -> ../../sdb6
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 1bfd912d-b6b6-4a68-9aaf-4139513772ec -> ../../sda5
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 9555e579-7173-40ff-b0ef-5c254e1e1bb4 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 979e595a-e18a-454e-8e5b-c62f3ff1cedf -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 c14b3a9a-b427-4ef6-a306-195e35cf9ee9 -> ../../sdb8
lrwxrwxrwx 1 root root 10 2012-11-03 13:21 e2554df2-7e16-4864-97c9-834d8bebecda -> ../../sda2

```
Are your partitions normal msdos or are you using GPT partitions?  I have no idea if that makes any difference to blkid, but just raise it as a possibility.

---

### Post by Paulgirardin on 2012-11-03
> **ajgreeny said:**
> This does not answer your question as to why **sudo blkid** is not working, but you can get the info in a more roundabout way with the command```
ls -l /dev/disk/by-uuid/
```This will echo in terminal the files named the same as the UUIDs of the partitions, and as those files are just links, it will show you which device (partition) each relates to, 
Are your partitions normal msdos or are you using GPT partitions?  I have no idea if that makes any difference to blkid, but just raise it as a possibility.

Yes that works.
thanks,I'll make note of that for next time.

It is a GPT system ,but I did not have this problem in 12.04

cheers

---

### Post by matthew_petty on 2012-11-03
Thanks. Here is the output of that command in case it is helpful:

```

lrwxrwxrwx 1 root root 10 Nov  3 08:38 14a8c8cd-9cea-4014-b1f2-4fbe15713378 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  3 08:38 70D6-1701 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov  3 08:38 8496c79a-8663-3cd7-b76e-9b7e6888fb8a -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov  3 08:38 b23993d0-0a46-42de-813a-daf0498c9850 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov  3 08:38 c3c9a1a0-ff30-4666-96bd-19bd10f9025c -> ../../sda6
lrwxrwxrwx 1 root root 10 Nov  3 08:38 eaeb5893-111c-48d4-819c-1f6f182d4bb0 -> ../../sda7

```

sdb is the drive I installed.

---

### Post by ajgreeny on 2012-11-04
To get the ntfs partition sdb1 to mount automatically at boot, first make a folder for the mountpoint with ```
sudo mkdir /mnt/windows
``` and then you can try adding this line to /etc/fstab
```
UUID=70D6-1701 /mnt/windows/    ntfs-3g        auto,user,rw 0 0
```You can edit fstab (after backing it up, just in case things go wrong) with ```
sudo cp /etc/fstab /etc/fstabbak
```for the backup, then ```
gksudo gedit /etc/fstab
``` to open it in gedit with root permissions.
After doing all this, before rebooting, run ```
sudo mount -a
``` to check all is well.  If no erors are seen it should work OK at next boot  That line in fstab assumes that ntfs-3g is installed so check that first.

---

