---
title: "HELP: Cannot login to Ubuntu"
date: 2007-08-21
forum: General Help
---

### Post by mgybran on 2007-08-21
Hello

I cannot login to any desktop or the root recovery desktop.  On my normal desktop the login display appears and I can enter my login credentials (apparently successfully) but the desktop fails to load.
On Root, in the recovery mode, I do not get the login screen at all, just a grey screen.
I 'think' I have booted successfully.  Am I correct in saying this?
I did notice in the recovery  mode that mounting 'all' the local file systems failed.

Mount: mount point......media\....  does not exist

Is this a clue to the cause?  I can see that my data on all file systems is secure when I use the live CD.

Is there any any diagnosis I can carry out to try to determine what the true cause is?
Possible there is a way of resetting previous mount points that are failing and mounting from the rescue command line?  If so, can anyone advise how to do this?

Thanks in advance

---

### Post by heimo on 2007-08-21
Try changing to virtual console ctrl+alt+F2, logging in, and checking available disk space with command df. Do you have free space?

---

### Post by mgybran on 2007-08-21
> **heimo said:**
> Try changing to virtual console ctrl+alt+F2, logging in, and checking available disk space with command df. Do you have free space?

Hi. Thanks for responding.  I see the following on /dev/sdb6:
1k blocks 25395192
Used 22229540 (22GB?)
Available 1875636 (1.8 GB?)
Use is 93%

Although 93% is in use, the 1.8GB should be enough free space right?

---

### Post by heimo on 2007-08-21
> **mgybran said:**
> Although 93% is in use, the 1.8GB should be enough free space right?

Right. Some time ago I had a strange, similar problem which was caused by localhost not being properly configured. You can try that too, if you haven't already solved this problem. Log in virtual console, and ping localhost. (command: "ping localhost") It should work, if it doesn't, Gnome may have trouble logging you in.

---

### Post by mgybran on 2007-08-21
> **heimo said:**
>   Log in virtual console, and ping localhost. (command: "ping localhost") It should work, if it doesn't, Gnome may have trouble logging you in.

I think the pinging has failed.  I expected 3 ping attempts but instead I get stuck on a neverending cycle of attempts when I ping localhost.  Currently at 322, I will kill the process soon.

Some background into this issue.  I had been having problems with a HAL initializing error.  I tried the following in an attempt to fix that.

sudo dpkg-reconfigure hal
sudo dpkg-reconfigure dbus
Reboot

I cannot say for sure that this was the cause, as I had also been having problems with my filesystems mounting. When I boot up into recovery mode I can see that the mounting of local file systems fails.

Is there command possibly that I can run that will load any required drivers or have you any other ideas?

---

### Post by astralsin on 2007-08-21
if you're getting valid ping replies, you're fine.  if you're getting network unreachable or ping timeout errors or something then you've got problems.

---

### Post by heimo on 2007-08-21
> **mgybran said:**
> have you any other ideas?

No, I'm lost. But I'd try to investigate that mounting problem further. Do you have separate home partition? You could run *mount* command on virtual console and see if it's mounted properly. You could also run *dmesg | less* and search for any errors and warnings.

---

### Post by mgybran on 2007-08-22
> **heimo said:**
> No, I'm lost. But I'd try to investigate that mounting problem further. Do you have separate home partition? You could run *mount* command on virtual console and see if it's mounted properly. You could also run *dmesg | less* and search for any errors and warnings.

Hi
I typed 'mount' and /dev/sdb6 was mounted (root partion)
Output from first line "/dev/sdb6 on / type ext3 (rw,errors=remount-ro)"
There are other lines outputted, none that I can see would be of interest.  No obvious errors. Not sure what you mean by a separate home partition, but I suspect the answer is no.  I do have a separate harddrive (IDE), but that is ntfs format. The harddrive that the Linux is installed on is SATA.

Some errors I found when running he command dmesg|less:
ext3 fs on sdb6, internal journal
ibm_acpi: ec object not found
No dock devices found
**Warning** 12V adapter driver [nvidia i2C adapter 1 at 1:00] forgot to specify physical device; fix it

---

### Post by mgybran on 2007-08-25
Well I tried the following:
sudo aptitude update
sudo aptitude upgrade
sudo aptitude reinstall hal dbus

Did not work. :(  I reinstalled.  Back in.

---

