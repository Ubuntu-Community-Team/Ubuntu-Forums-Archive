---
title: "[SOLVED] Deleting Read Only Files"
date: 2008-02-18
forum: General Help
---

### Post by stooshbunutu on 2008-02-18
I have a really messed up file on my memory stick that created a load of weird files and folders, al of which are read only.

What I want is a way to delete a read only folder and all of its contents in one foul swoop. All the files are in a folder named "zzzz garbage" so that is the folder I want to get rid of.

Any help would be greatly appreciated. Thanks :)

To help I have attached a screen-shot of the permissions tab of properties of that folder.

---

### Post by Yellow Pasque on 2008-02-18
Go to the directory that conatins the zzz garbage folder and:
```
sudo rm -rf zzzz\ garbage/
```

---

### Post by stooshbunutu on 2008-02-18
Thanks for such a speedy reply, I tried that and nice call but the files aren't recognised so it behaves as if the zzz garbage directory were empty. 

Is there a way I could delete the folder so that the contents would go with it

Cheerz :)

---

### Post by Yellow Pasque on 2008-02-18
I'm not quite sure what you mean by "it doesn't recognize the files"
Try the command again and add the verbose argument (-rfv). What output do you get?
> 
Is there a way I could delete the folder so that the contents would go with it?
THat's what the -r (recursive) switch should do, delte all files and folders that are children of the given folder

---

### Post by stooshbunutu on 2008-02-19
sorry for not being very specific but the files are seriously corrupt and display names with unknown characters and claim impossible file sizes in relation to the 4GB capacity of the memory stick they are on.

I have attatched a screen-shot to give you an idea (apologies that it is a win-explorer screen shot but I'm not on my computer at the moment

---

### Post by chrisccoulson on 2008-02-19
You probably need to run dosfsck on the volume tbh:
```
sudo dosfsck -r /dev/hd*
```
..where 'hd*' is your memory stick (hda, hdb, hdc, hdd, hde or whatever)

Make sure you unmount the volume before running dosfsck though

---

### Post by stooshbunutu on 2008-02-19
> **chrisccoulson said:**
> You probably need to run dosfsck on the volume tbh:
```
sudo dosfsck -r /dev/hd*
```
..where 'hd*' is your memory stick (hda, hdb, hdc, hdd, hde or whatever)

Make sure you unmount the volume before running dosfsck though

Thanks for the advice, just checking, what does this command actually do?

ps. my drive is located "/media/STOOSH/" so would I put this instead of the "/dev/hd*" ?

Cheers

---

### Post by chrisccoulson on 2008-02-19
dosfsck runs a filesystem check on the volume, and will help you repair the corrupt parts. I think this is probably what you need to do.

With your flash drive plugged in and mounted as usual, do:
```
cat /etc/mtab
```
...and look for the line with '/media/STOOSH' on it. The device node you need will be on that line. Before you run dosfsck, you must unmount the volume first:
```
sudo umount /media/STOOSH
```

---

### Post by stooshbunutu on 2008-02-19
```
stoosh@michael-ubuntu-laptop:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/STOOSH vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
```

This is what the cat /etc/mtab returned, soz to be nooby but which bit do I then use in the next command.

ps I really appreciate all the help you lot are giving

---

### Post by chrisccoulson on 2008-02-19
```
sudo umount /media/STOOSH
sudo dosfsck -r /dev/sda1
```
...should do the trick and hopefully come back with errors that it can repair

---

### Post by stooshbunutu on 2008-02-19
Ok, so THANK YOU SO MUCH! for your brilliant help, it is completely sorted out now and the disk was not harmed in any way, all the bad bits are gone and all the good bits remain

I have thanked all three of your very helpful posts and thank you again for really helping me out

All the best :)

---

### Post by chrisccoulson on 2008-02-19
No problem. Pleasure to be of assistance:)

---

### Post by Yellow Pasque on 2008-02-19
I have learned something here. Thank you, sir.

---

### Post by stooshbunutu on 2008-02-19
I think this is just proof that the ubuntu forums and community realy does work :)

---

