---
title: "fstab mounting wrong root partition"
date: 2008-02-10
forum: General Help
---

### Post by gamo on 2008-02-10
Hi,

I copied my /-partition with dd from /dev/hda2 to /dev/hdc2 (to have a backup). After a while I noticed that every second time when I reboot my computer, Gutsy mounts /dev/hdc2 as root partition. This obviously happens because Ubuntu uses UUID's in /etc/fstab and dd copied the UUID as well.

But is it normal that every second time it uses hda2 as root, and every other time it uses hdc2? How does it decide which one to use? And the funny thing is that it always shows up as hda2 if i check it with *df* or *mount*. As you can see below, it is currently using hdc2 as root even though it says that it is using hda2:

```
root@ubuntu:/media# df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/hda2              19G   11G  7.4G  58% /[/COLOR]
varrun                506M  220K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M   16K  506M   1% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc3              92G   62G   26G  72% /home
/dev/hdc1              20G   15G  5.2G  74% /media/windows
/dev/hda3             109G   41G   62G  40% /media/backup
[COLOR="Red"]/dev/hda2              19G  8.2G  9.2G  47% /media/realroot
/dev/hdc2              19G   11G  7.4G  58% /media/backuproot[/COLOR]
```

I had some funny moments before i realized what was happening. It was a bit odd to see that a folder which I previously deleted seems to be there again after reboot, or Ubuntu is offering some updates which i already installed yesterday :-) First thought was that my hard drive is about to die.

Now that i know what is wrong, i also know that i should use /dev/hda2 in fstab instead of UUID. But I'm still curious to know if this is a bug or "normal behaviour"?

---

### Post by logos34 on 2008-02-10
replace the 'root=[COLOR="Red"]UUID=xxx[/COLOR]' in /boot/grub/menu.lst with 'root=**/dev/hda2**'.  that should solve the problem

---

### Post by chrisccoulson on 2008-02-10
The neater solution would be to change the UUID of your backup partition. In a terminal:
```
sudo tune2fs /dev/hdc2 -U random
```

You can check to see if it has changed by doing:
```
vol_id /dev/hda2
vol_id /dev/hdc2
```
...and comparing the results

---

### Post by gamo on 2008-02-11
Thank you for the suggestions, but I think that both of them have some obstacles?

If I change the UUID, the problem will arrive again if I refresh the backup (take a new dd copy). 
Then if I edit menu.lst, it appearantly changes the UUID back after next kernel update.

---

### Post by chrisccoulson on 2008-02-11
Yes, if you change the UUID of the partition, you will need to change it again after the next backup

If you change the grub entries to point to /dev/hda2 as opposed to UUID, you can prevent your changes from being replaced at the next kernel upgrade by also replacing the UUID with /dev/hda2 on the line that begins '# kopts'.

---

### Post by gamo on 2008-02-11
OK, I'll modify that as well and see what happens after next kernel update. Thanks a lot for the advice.

I still wonder why it claimed that /dev/hda2 was root every time. Similar UUID shouldn't cause that. It would have been a lot easier to find out the problem if the device name in *df* or *mount* listing would have been hdc2 when it used it.

---

### Post by gamo on 2008-02-13
It seems that editing the '# kopt' line did not help. It was replaced with the UUID again after last kernel upgrade. What I did was that I changed the last line of this:
```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=605cd24a-c06b-4e5b-94b0-24da7386a8ab ro

```
to this:
```

# kopt=root=/dev/hda2 ro

```

I assume that you meant that line? these are the only lines if I search kopt from the file.

Maybe I should change the UUID of the backup partition..

---

### Post by chrisccoulson on 2008-02-13
Yeah, thats the line I meant. No idea why it got changed back - I didn't realise update-grub modified that line

---

### Post by sryth on 2008-02-18
Easiest fix is to change it for now, and install mondo rescue (from the ubuntu repos) to use for backups.  Simple software.  Free.  Makes full disaster recovery backups or configurable for less, and won't have that problem anymore.

---

