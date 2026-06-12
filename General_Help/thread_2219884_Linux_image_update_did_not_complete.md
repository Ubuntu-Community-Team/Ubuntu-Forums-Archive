---
title: "Linux image update did not complete"
date: 2014-04-25
forum: General Help
---

### Post by ardvark on 2014-04-25
I was applying the latest Linux image update that was available today. During the applying of that change when it got to "Configuring linux-image-3.2.0-61-generic-pae" it stopped and did not complete. Being a novice at this point, what are my options? Are there things I can check or re-apply the update before I reboot the PC?  Is there something corrupted is this update?

Linux version 12.04

---

### Post by warp99 on 2014-04-25
You could reinstall the package before you reboot if you think it failed:

```
sudo apt-get install --reinstall linux-image-3.2.0-61-generic-pae
```

---

### Post by ardvark on 2014-04-25
Thanks for the quick response, but this also brings up another questions. The update manager is still running (both Update Manager & Applying Changes screens are showing on the desktop). Do I have to somehow kill those processes before rerunning the update? Second, at this point I don't know if this was the last update to be configured, if it wasn't, what would happen to the other updates?

---

### Post by warp99 on 2014-04-25
Kill both apps and just go to the terminal for the updates:

```
sudo apt-get update

sudo apt-get upgrade
```

See if that solves the problem before doing anything else.

---

### Post by ardvark on 2014-04-25
I've killed those processes but now when I try 'sudo apt-get update' I get this:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Does something else need to be cleared out?
I did see this process running " linux-image-3.2.0-61-generic-pae.postinst ", could this be the culprit?

---

### Post by matt_fussell2 on 2014-04-25
> **ardvark said:**
> I've killed those processes but now when I try 'sudo apt-get update' I get this:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Does something else need to be cleared out?
I did see this process running " linux-image-3.2.0-61-generic-pae.postinst ", could this be the culprit?

Have you tried the solution to the lock file issue suggested in this [Ask Ubuntu thread]("http://askubuntu.com/questions/335794/could-not-get-lock-var-lib-apt-lists-lock")?

---

### Post by warp99 on 2014-04-25
Another process is using apt. Use the link that matt_fussell2 gave and kill the process using apt, then update and upgrade.

---

### Post by ardvark on 2014-04-25
The processes listed are (2)  /sbin/aptd & the process I listed above "linux-image..." cannot be killed with signal 15, so it says.
Can I try the rmv ..../lock message anyway?

---

### Post by warp99 on 2014-04-25
Try the following:


```
sudo kill -9 <process>
```

The process aptd does not need to be killed, that's a daemon.

---

### Post by ardvark on 2014-04-26
I'm not sure what happened, but I was browsing and it just locked up. Had a desktop, cursor was moving, but couldn't select anything. Clock was not updating on the desktop. So I reset the PC. Amazingly it booted up, must have got far enough along in the update. I did check for available updates and it went through some clean-up and I had to reboot. Hopefully everything is back to normal.

---

### Post by Impavidus on 2014-04-26
You killed update-manager without giving it a chance to release its lock. That's what caused the error mentioning the lock. At that point no other process was using it.

The post install script of linux-image-3.2.0-61-generic-pae hung for some reason. Whether it got far enough to allow you to boot or not far enough to give you any trouble booting I cannot say, but you can check by running the command **uname -r**. If it shows you something with 3.2.0-61 the script got far enough to allow you to boot (as you booted the new kernel), if it shows something with 3.2.0-60 it did'nt get far enough to cause any booting troubles (as it didn't modify the grub menu). Hopefully the problems were resolved automatically. To check, run```
sudo apt-get update
sudo apt-get dist-upgrade
```and see whether it reports any errors. You can also run```
dpkg --list linux-image* | grep -v '^un\|^rc'
```If it lists any package on a line not starting with ii something is wrong. Else, you're probably OK.

---

### Post by ardvark on 2014-04-26
Thanks Impavidus for the added checks, everything checks out OK..

---

