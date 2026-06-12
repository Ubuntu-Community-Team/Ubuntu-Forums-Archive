---
title: "Can't update Thunderbolt NVM with Software Center on Dell XPS 13 9360 17.10"
date: 2018-01-04
forum: General Help
---

### Post by jstolarski on 2018-01-04
Hi!  I'm running Ubuntu 17.10 on a Dell XPS 13 9360.  It looks like the system firmware can be updated from the Software Center, in the Updates section.

  [ATTACH=CONFIG]278053[/ATTACH]  

Updating the system BIOS has worked okay before when initiated from the Software Center, but when I try to update "Thunderbolt NVM for Xps Notebook 9360" by clicking the adjacent Update button, this error message appears:
  
[ATTACH=CONFIG]278054[/ATTACH]  

I don't understand what this error message means: ```
Unable to update "Thunderbolt NVM for Xps Notebook 9360" could not find thunderbolt device at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/0000:02:00.0/0000:03:00.0/domain0/0-0
```  What does this error message mean? How can I get the update to install?  (I rebooted to see if a restart would help. It had no effect, and the error message still comes up when I try to update the Thunderbolt NVM. I also checked for the issue on a search engine- no relevant results.)

---

### Post by shgun-xzan on 2018-01-07
I believe this is linked to this issue : [https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1741509](https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1741509)

I have noticed that if I plug my DA-200 dongle, the update can start but then fails.
I believe it's because it wakes the controller then the controllers goes back to sleep and its is not found again.

---

### Post by jstolarski on 2018-01-25
> **shgun-xzan said:**
> I believe this is linked to this issue : [https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1741509](https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1741509)

I was able to get the firmware update to complete successfully by upgrading with ```
sudo apt dist-upgrade
``` and running these commands from the terminal (not as the superuser):

```

fwupdmgr refresh
fwupdmgr update

```

as found in the linked page in the quoted post.

---

### Post by zordid86 on 2018-01-25
Hi,
thank you for your answer. It is still not working. I tried your suggested commands and got this output on console:

```
zordid@silversurfer:~$ fwupdmgr refresh
Fetching metadata https://s3.amazonaws.com/lvfsbucket/downloads/firmware.xml.gz
Downloading…           [****************************************]
Fetching signature https://s3.amazonaws.com/lvfsbucket/downloads/firmware.xml.gz.asc
Downloading…           [****************************************]
zordid@silversurfer:~$ fwupdmgr update
Downloading 21.00 for XPS13 9360 Thunderbolt Controller...
Fetching firmware https://fwupd.org/downloads/eac3961ba9bd466f6e34d9276c27d524395d7c3c-NN1TN_NVM21.00.cab
Downloading…           [****************************************]
Updating 21.00 on XPS13 9360 Thunderbolt Controller...
Decompressing…         [-                                       ]
could not validate firmware: Error reading from file: Input/output error. See https://github.com/hughsie/fwupd/wiki/Thunderbolt:-Validation-failed-or-unknown-device for more information.
zordid@silversurfer:~$ 

```

---

### Post by birddodger on 2018-01-25
After weeks of having it fail, I was also able to successfully update by doing the following 

```
sudo apt update
sudo apt upgrade
```
--- an update to fwupd was ready --
then...
```
sudo service fwupd restart
sudo fwupdmgr refresh
sudo fwupdmgr update
```

J

---

### Post by zordid86 on 2018-01-27
> **birddodger said:**
> After weeks of having it fail, I was also able to successfully update by doing the following 

```
sudo apt update
sudo apt upgrade
```
--- an update to fwupd was ready --
then...
```
sudo service fwupd restart
sudo fwupdmgr refresh
sudo fwupdmgr update
```

J


Hey @birddodger, thank you very much. Executing your proposed steps finally got me to the goal of updating the firmware. 

-Stefan

---

### Post by linus-lin on 2018-02-15
Worked for me as well. Thanks!

---

### Post by mwildam on 2018-06-28
I had the same effect but all that did not help in my case. What was my solution: sudo fwupdmgr get-devices  => Look up thunderbolt device id;
sudo fwupdmgr get-updates deviceid  => Manual download update link to local file;
sudo fwupdmgr install localfilenametocab  => After finished you need to reboot to see device again.

---

