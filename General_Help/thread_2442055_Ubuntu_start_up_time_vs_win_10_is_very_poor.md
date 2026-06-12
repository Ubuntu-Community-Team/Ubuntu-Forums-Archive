---
title: "Ubuntu start up time vs win 10 is very poor"
date: 2020-04-29
forum: General Help
---

### Post by iamtheeggman2 on 2020-04-29
Hi,

I have ubuntu installed on a normal HDD and windows 10 on a SSD, SSD is obviously a lot faster however ubuntu 20.04 is taking 50 seconds to get to login password entry and then takes a further 10 seconds to get to the actual desktop.Windows 10 takes 10 seconds to password entry and 1 second to desktop. Is there anything I can do to improve boot up time? I looked at start up programs I don't need but 60 seconds is a lot slower than windows was on this HDD.

---

### Post by Autodave on 2020-04-29
Did you disable *fast start *on Windows?  Keep in mind that Win 10 does NOT shut down: it hibernates.  If you hibernate Ubuntu it will start much faster, too.

---

### Post by CelticWarrior on 2020-04-29
> **Autodave said:**
> Did you disable *fast start *on Windows?  Keep in mind that Win 10 does NOT shut down: it hibernates.  If you hibernate Ubuntu it will start much faster, too.

This^^^ and having one in a SSD and another in a HDD is really not comparable.

---

### Post by sgage on 2020-04-29
On my system (with SSD), booting Ubuntu takes about 10 seconds from grub menu to desktop.

---

### Post by iamtheeggman2 on 2020-04-29
> **Autodave said:**
> Did you disable *fast start *on Windows?  Keep in mind that Win 10 does NOT shut down: it hibernates.  If you hibernate Ubuntu it will start much faster, too.

Oh I had no idea it hibernated. I haven't changed any options named "fast start"

If I hibernated ubuntu will it mess up when connecting to the router? I think I had issues with windows hibernate because ip address were not static and so the ip from hibernate can conflict with another computer.

---

### Post by HermanAB on 2020-04-29
Use Suspend, then you machine will be ready the moment you press a key.  Rebooting is so 20th century...
;)

---

### Post by CelticWarrior on 2020-04-29
> **HermanAB said:**
> Use Suspend, then you machine will be ready the moment you press a key.  Rebooting is so 20th century...
;)

YES to suspension;
NO to hibernation, anywhere, even the [Fast Startup feature]("https://www.windowscentral.com/how-disable-windows-10-fast-startup"), even in single boot Windows.

Disagree about rebooting being outdated. With the new hardware, improved UEFI + Solid State storage, it's so fast that sometimes beats waking up from suspension and always beats waking up from hibernation and it's safer and it cleans up a lot of things giving us a clean slate.

---

### Post by ActionParsnip on 2020-04-29
Comparing boot time on a platter based storage to an SSD will be slower. You can disable startup services using this sort of thing:
[https://askubuntu.com/questions/912216/16-04-command-to-list-all-services-started-on-boot#912218](https://askubuntu.com/questions/912216/16-04-command-to-list-all-services-started-on-boot#912218)

For example, if you don't use a printer then having CUPS running is a waste of time. Reducing services makes your system leaner and boot faster

---

### Post by iamtheeggman2 on 2020-04-30
Well I run the command but it all looks appropriate but several services I don't need and many I don't know what they do and would prolly spend 1 hour googling them. I have space space on the SSD however its not easy to just transfer my installation over to the blank part of the SSD is it? As I only had ubuntu installed less than a week i suppose its not a huge issue to reinstall but my brother warnd me SSD are unreliable, he's been through 3 in 3 years and he isn't buying cheap crap either. I was using linux off a HDD and only using win10 on a SSD for occasional use.

---

### Post by yaminb on 2020-04-30
I didn't believe the difference between a HDD and SSD myself until I had it.

Believe it or not, that is the expected difference. 
I had Ubuntu installed on a 7200 RPM hd... boot waiting taking around a minute.
I tried installing a dual boot and mucked up everything and just decided, now is a good time to move to SSD.
Move to SSD. Ubuntu now started in like < 10 seconds.

Trust me on this, before I moved to SSD, I was also puzzled... like this can't be just an SSD. I have some threads on it if you want to search my history.
I was all into systemd and finding startup process and all kinds of stuff. I got some minor improvements... but nothing could get it down.

editing to answer question about reliability.
As you mentioned you had some concerns on reliability of SSD. I also heard that SSDs just die whereas harddrives degrade slowly.
Anyways, what I did was I installed Ubuntu on the SSD, but kept my /home on the harddrive.
That way my data/settings... is on the harddrive and back up on my NAS (I have been lazy about that :P )
Reinstalled a distro is not a big deal, and if my SSD should fail, I can reinstall it pretty quick and I have all my data.

But maybe try that if you're concerned with reliablity. Keep your /home on the HDD.

Also just some advice on dual booting from personal experience.
I'm sure it's possible to safely do it both windows and ubuntu on the same SSD, but if you can avoid it, i'd advise it.
Install them on separate drives, and with THEIR own EFI partitions.

---

### Post by oldfred on 2020-04-30
Saved some of the threads on slow boot.
Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) & 
[https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) & 
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

This is primarily what I have done.
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

If UEFI firmware update not supported (yet)
sudo apt-get purge fwupd

---

### Post by maxlewis on 2020-04-30
> **sgage said:**
> On my system (with SSD), booting Ubuntu takes about 10 seconds from grub menu to desktop.

The same to me, I use Lenovo Z51 (processor i3-5005u) laptop with WD SSD 256GB and 12GB DDR3.

---

### Post by iamtheeggman2 on 2020-05-01
> **yaminb said:**
> I didn't believe the difference between a HDD and SSD myself until I had it.

Believe it or not, that is the expected difference. 
I had Ubuntu installed on a 7200 RPM hd... boot waiting taking around a minute.
I tried installing a dual boot and mucked up everything and just decided, now is a good time to move to SSD.
Move to SSD. Ubuntu now started in like < 10 seconds.

Trust me on this, before I moved to SSD, I was also puzzled... like this can't be just an SSD. I have some threads on it if you want to search my history.
I was all into systemd and finding startup process and all kinds of stuff. I got some minor improvements... but nothing could get it down.

editing to answer question about reliability.
As you mentioned you had some concerns on reliability of SSD. I also heard that SSDs just die whereas harddrives degrade slowly.
Anyways, what I did was I installed Ubuntu on the SSD, but kept my /home on the harddrive.
That way my data/settings... is on the harddrive and back up on my NAS (I have been lazy about that :P )
Reinstalled a distro is not a big deal, and if my SSD should fail, I can reinstall it pretty quick and I have all my data.

But maybe try that if you're concerned with reliablity. Keep your /home on the HDD.

Also just some advice on dual booting from personal experience.
I'm sure it's possible to safely do it both windows and ubuntu on the same SSD, but if you can avoid it, i'd advise it.
Install them on separate drives, and with THEIR own EFI partitions.

Thank you for this response, it didn't make sense the SSD was 6-7 times faster than the HDD, is there any more than /home that I might want to move to the HDD should the SSD fail?

---

### Post by yaminb on 2020-05-01
> **iamtheeggman2 said:**
> Thank you for this response, it didn't make sense the SSD was 6-7 times faster than the HDD, is there any more than /home that I might want to move to the HDD should the SSD fail?

I'm honestly not that much of an expert, and I'd hate to give someone such backup advice in case I missed something.

However, I don't think anything else would be needed beyond /home :)

---

### Post by oldfred on 2020-05-01
You want to also backup /home from HDD to another device.
I backup /home, my data partitions, a list of exported installed applications, and some settings in /etc. Some suggest backing up all of /etc since small. I only edit grub and a couple of files, so copy those into /home. You do not necessarily restore an old /etc if into a new version as settings may be different. But good to have as reference.
If a serve configuration or applications you need additional folders in / , like database, web or other applications.

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

f you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)

---

