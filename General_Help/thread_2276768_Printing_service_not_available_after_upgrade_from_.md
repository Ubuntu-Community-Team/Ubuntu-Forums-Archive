---
title: "Printing service not available after upgrade from 14.10 to 15.04"
date: 2015-05-04
forum: General Help
---

### Post by Joseph_Raymond on 2015-05-04
I have upgraded from Lubuntu 14.10 to Lubuntu 15.04 via the Software Updater and now CUPS won't run.  In the printer configuration area I get a message that simply says "Printing service not available. Start the service on this computer or connect to another server."  I've tried starting CUPS and have even looked at it in Boot Up Manager to verify it isn't running.  It isn't.  You start it, it seems to start, but apparently doesn't...or immediately fails.

Where do I start/what do I do to get this going again?  I need to be able to print.

---

### Post by cariboo on 2015-05-04
To start cups use the following command:

```
sudo service cups start
```

it should print out an error message if it doesn't start.

---

### Post by tgalati4 on 2015-05-05
You can look in /var/log/cups for error messages as well.  Try performing updates, reboot, then check updates again.  Sometimes a new library or patch will get loaded to fix these problems.

```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

---

### Post by Joseph_Raymond on 2015-05-05
> **cariboo said:**
> To start cups use the following command:

```
sudo service cups start
```

it should print out an error message if it doesn't start.

I enter in that command, it asks for my password, I hit enter and it runs and returns me back to my command prompt.  No errors.  But, CUPS still isn't running.

---

### Post by Joseph_Raymond on 2015-05-05
> **tgalati4 said:**
> You can look in /var/log/cups for error messages as well.  Try performing updates, reboot, then check updates again.  Sometimes a new library or patch will get loaded to fix these problems.

```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

I tried doing update, upgrade, reboot.  It installed 6 upgrades, no help though.  Also of note, in Bootup Manager, it shows CUPS as not started, you start it, it says "service started", refreshes the screen, and...it still shows CUPS as not running.

I checked for logs, error_log, access_log, and page_log were all empty.  error_log.1, access_log.1 and page_log.1 had some older entries from a week ago or so, I think from before I did the upgrade to 15.04.

Anything else I can try?  Would the logs that have content help you at all?

---

### Post by tgalati4 on 2015-05-06
CUPS is a complicated framework with lots of pieces.  If one piece fails, then the server shuts down, sometimes without any errors in the logs.  I recall a bug in 12.04 where CUPS would fail if avahi (Bonjour-like service discovery) was not running.

So you performed an in-place upgrade from 14.10 to 15.04.  Although this is easy to do, regressions are common because of the mixture of old and new system settings.  A clean installation is recommended.

I like to keep an LTS system (14.04 in this case) running at all times in case I need to print.  It's helpful to set aside the time to troubleshoot possible regressions when upgrading to the latest distro.

Try purging cups then reinstalling.

```
sudo apt-get purge cups
sudo apt-get install cups
```

Install your printer and try printing.

---

### Post by Joseph_Raymond on 2015-05-06
> **tgalati4 said:**
> CUPS is a complicated framework with lots of pieces.  If one piece fails, then the server shuts down, sometimes without any errors in the logs.  I recall a bug in 12.04 where CUPS would fail if avahi (Bonjour-like service discovery) was not running.

So you performed an in-place upgrade from 14.10 to 15.04.  Although this is easy to do, regressions are common because of the mixture of old and new system settings.  A clean installation is recommended.

I like to keep an LTS system (14.04 in this case) running at all times in case I need to print.  It's helpful to set aside the time to troubleshoot possible regressions when upgrading to the latest distro.

Try purging cups then reinstalling.

```
sudo apt-get purge cups
sudo apt-get install cups
```

Install your printer and try printing.

I had already tried the purge.  I suppose a clean install is going to be the way to go.  Any recommendations on the best practice backing up user accounts/data before doing this?  I have important documents already backed up, but if there is a way to easily backup personal preferences etc, or the entire account that would be great.

---

### Post by SeijiSensei on 2015-05-06
Back up the entire contents of /home, or at a minimum, the contents of /home/yourusername.

---

### Post by Joseph_Raymond on 2015-05-06
> **SeijiSensei said:**
> Back up the entire contents of /home, or at a minimum, the contents of /home/yourusername.

When I redo the system, afterward can I simply copy those files back over and I'll have my users back etc?

---

### Post by SeijiSensei on 2015-05-06
Yes.  All the users' configurations are saved as "hidden" files (ones beginning with a dot) in their home directories.  Of course any files they have saved with be in those directories as well.

That's why it's a common practice, especially on servers, to create a separate partition for /home rather than having it be part of the root.  In the Ubuntu installer, choose "something else" when the partitioning step happens.  Then create two partitions, one for / and one for /home.  (On a multi-boot system, I'd create a separate small /boot partition as well.)  The root partition need not be much bigger than 20 GB.  On my reasonably new Kubuntu 14.04 machine, root occupies only 6 GB.  

On a large drive, you might also consider leaving an equivalent amount of space empty in case you want to test out a new version of the OS later on.  Then you can install that version to the empty space and choose the version at boot.  You can decide whether to use the same /home partition, or let the new version create /home in its own filesystem.  That would make sense if you're testing; you can copy over your own home directory from the old /home partition into /home on the new installation to make sure things work correctly.  You'll want a separate /boot in this situation as well.  It doesn't need to be bigger than 256 MB.  On that 14.04 machine, /boot is less than 50 MB, but I have only one kernel installed.  After a kernel upgrade, that figure will probably about double since I'll then have a new kernel and the one I'm using now as a backup.

When you reinstall, use 14.04LTS.  It is supported through 2019.  Anything before 16.04 will have short lifespans.  If you want to experiment with interim releases, use a different machine or a virtual machine with something like [VirtualBox](http://www.virtualbox.org).

---

### Post by Joseph_Raymond on 2015-05-06
Yeah, I might go back to 14.04, I just like playing with the more modern OS.  Also, I don't really *have* to print, I can print from my windows box, I just like being able to print.  Thanks for the help, it's been very valuable.

---

