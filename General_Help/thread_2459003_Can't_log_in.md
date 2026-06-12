---
title: "Can't log in"
date: 2021-03-08
forum: General Help
---

### Post by Phil Binner on 2021-03-08
I'm running XUbuntu and using it as a server. I have a 225 gb ssd, one small SATA drive, one 3tb SATA drive with the network share, and 2 4TB SAS drives attached to an SAS controller card.  The intention was to use the two SAS disks as cyclic backups, but I do not have that working properly yet. The SSD is supposed to be for boot only, but the software install partitioned it as 

/dev/sda1  513mb FAT32
/dev/sda2  513mb FAT32  boot
/dev/sda3
/dev/sda4 Ext4  222gb
    /dev/sda5  Ext4 extended  222 gb

I am providing the above from memory.  It may not be precicely correct as i can't log in to check it any more.  It may or may not be relevant.

The problem started with a software update.  It first reported that it couldn't download the packages, and then that there was no room to install them.  It suggested that I empty the recycle bin - it was already empty - and then run 

sudo apt clean

in a terminal.

After running sudo apt clean I tried the software updater again, but it wouldn't load.  No message or failure, it just didn't load.  I decided on a clean start and re-started the computer.  It restarted as normal up to the login screen, but when I enter my password it flicks to a black screen screen with the message

/dev/sda5/: clean,245250/14589952 files, 58294701/58344448 blocks

The message lasts about 1/2 to 3/4 of a second, so it took a lot of tries to get the whole message.  I know my password is correct and accepted, because if I get it wrong it says so.

has anyone any idea what is going on, or will I have to start again by re-loading the software.

Thanks in anticipation.

---

### Post by TheFu on 2021-03-09
Well, looks like your OS drive is full.   Run:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and post the command and output. Please.

The 
```
 /dev/sda5/: clean,245250/14589952 files, 58294701/58344448 blocks
```
looks like an fsck was needed, so it got run. I wouldn't worry about it.

Rather than posting incorrect data, please run commands and copy/paste the 
[LIST]
[*]command
[*]output
[*]then wrap both, together, in code-tags so the forum software makes it readable for us.
[/LIST]
The details matter.  For example, I'm almost positive you've got sda4 and sda5 backwards, but that makes be suspect everything else too.
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
is another useful command. The output MUST be wrapped in code tags to be readable, however.

How-to code-tags: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
I've provided 3 examples above of using code-tags.

---

### Post by Phil Binner on 2021-03-09
Thanks but I'm afraid it's past that.  I've just re-loaded the software and I'll be resetting the network stuff shortly.  I couldn't have done the things you're asking for anyway, because i was completely locked out.  I just had the login window, then 3/4 second of the message, and then back to login.  The command prompt was not available.  There is probably another way of getting in, but unfortunately I don't know it.

Had I been able I would have gone in and got the correct data.  What I presented was what I was able to.

Long term this is a worry, because the boot drive is a 225 Gb SSD, and there should have been nothing on it to speak of.  Certainly the recycle bin was empty, and I do not use this machine for regular processing.  It's just the server.

I suspect this is something to do with the backup processes I've been trying to set up on the SAS drives.  When I've got it going again I'll investigate that further.

Anyway, thanks for trying.  Before I close this thread, I'd appreciate knowing what I should have done to get back in when I was locked out.

---

### Post by TheFu on 2021-03-09
> **Phil Binner said:**
> Thanks but I'm afraid it's past that.  I've just re-loaded the software and I'll be resetting the network stuff shortly.  I couldn't have done the things you're asking for anyway, because i was completely locked out.  I just had the login window, then 3/4 second of the message, and then back to login.  The command prompt was not available.  There is probably another way of getting in, but unfortunately I don't know it.

Had I been able I would have gone in and got the correct data.  What I presented was what I was able to.

Long term this is a worry, because the boot drive is a 225 Gb SSD, and there should have been nothing on it to speak of.  Certainly the recycle bin was empty, and I do not use this machine for regular processing.  It's just the server.

I suspect this is something to do with the backup processes I've been trying to set up on the SAS drives.  When I've got it going again I'll investigate that further.

Anyway, thanks for trying.  Before I close this thread, I'd appreciate knowing what I should have done to get back in when I was locked out.

Yes you could have.  You'd boot from the installer media - usually a flash drive - then choose "Try Ubuntu" and open the terminal to run those commands.  Having a flash drive with the same major release as the installed one, don't worry about having the same DE, is very handy to solve issues like this.

I suspect your backup efforts failed and the target disk wasn't mounted, so everything was backed up onto the / disk - 225G - until it filled 100%.  There are methods to validate that the target disk is mounted as part of your backup script.  Some people have an empty file in the top of the mounted disk. I check the output of the **mount** command for the expected mounted disk myself.   This is a common issue.  We've all done the same thing.

Pro-Tip: always use a *real mount* for storage.  That means either running the **sudo mount option0 option1 option2 option3** command or putting those into the /etc/fstab file.  Don't expect any GUI tool to create a permanent *real mount*.

I suspect other aspects of your backups could be tuned as well.  Periodic mirroring everything is seldom the best solution for backups.  The only time I'd suggest/use periodic mirroring is for huge media files.  Everything else really needs automatic, versioned, daily, backups. Rather than wasting 3x the storage to have 3 copies, for 1.3x the original storage you can probably have 60-90 days of versioned backups. These run speedo-fast - like 2-5 minutes for each version.

---

### Post by Phil Binner on 2021-03-10
Thanks.  I was coming to the same conclusion as to what went wrong.  I haven't got the SAS disks and their controller configured properly, but that is a different issue.  I'll close this thread for now and explore that later.

---

