---
title: "Unable to open Synaptic Package Manager on lubuntu"
date: 2014-07-07
forum: General Help
---

### Post by Tim_Graffam on 2014-07-07
I recently setup a new VM with lubuntu 14.04. Synaptic Package Manager worked after the initial install, but at some point since then Im now no longer able to launch it.

When trying to do so from the programs menu, I get prompted for admin password, but nothing happens after. When trying to launch from the terminal I get the following error:

```
E: Could not open lock file /root/.synaptic/lock - open (20: Not a directory)
```

Ive tried every manner of apt-get possible - *update, upgrade, dist-upgrade, -f install, remove/reinstall* - as well as *dpkg --configure -a*.

Any thoughts on how to get this working again?

Thanks in advance!!

---

### Post by slickymaster on 2014-07-07
> **Tim_Graffam said:**
> I recently setup a new VM with lubuntu 14.04. Synaptic Package Manager worked after the initial install, but at some point since then Im now no longer able to launch it.

When trying to do so from the programs menu, I get prompted for admin password, but nothing happens after. When trying to launch from the terminal I get the following error:

```
E: Could not open lock file /root/.synaptic/lock - open (20: Not a directory)
```

Ive tried every manner of apt-get possible - *update, upgrade, dist-upgrade, -f install, remove/reinstall* - as well as *dpkg --configure -a*.

Any thoughts on how to get this working again?

Thanks in advance!!

Close all package management related GUIs. This is usually a sign that something else is installing or removing software and has locked the apt database while it performs the actions. The programs that can do this are the Software Center, the Update Manager or the the apt-get or aptitude command line utilities.

---

### Post by Tim_Graffam on 2014-07-07
I get this error immediately after rebooting/logging in, prior to opening anything beforehand. Ive also perused my task manager and not seeing anything that looks to be a package mgmt application.

Is there something else I should be looking at?

Thanks.

---

### Post by slickymaster on 2014-07-07
You can use```
sudo lsof /var/lib/dpkg/lock
``` to find the process that owns the lock file. If empty, assume the lock is left over from a previous boot and can be removed, by a ```
sudo kill -9 <PID>
```You get the <PID> from ```
lsof
``` output.

---

### Post by Tim_Graffam on 2014-07-07
I get the following error when trying to run the first command:
```
$[FONT=arial]sudo lsof /var/lib/dpkg/lock
[/FONT][FONT=arial]lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1066927081/gvfs[/FONT]
[FONT=arial]      Output information may be incomplete.[/FONT]

```

---

### Post by slickymaster on 2014-07-07
Try to delete the lock file with the following command:```
sudo rm /var/lib/apt/lists/lock
```You may also need to delete the lock file in the cache directory```
sudo rm /var/cache/apt/archives/lock
```After that, try opening Synaptic again.

---

### Post by Tim_Graffam on 2014-07-07
Still getting the same error even after removing those two locks. 

Not sure if it matters, but I am able to launch Synaptic without an issue when not running as root. Of course Im not able to apply updates when run in this mode.

Any other thoughts?

---

### Post by slickymaster on 2014-07-07
You can force the lock off by removing the file,** but it's not recommended without first closing the program that's holding the lock safely**, since you could cause corruption or interrupt an installation```
sudo fuser -cuk /var/lib/dpkg/lock
sudo rm -f /var/lib/dpkg/lock   
```
And the same command can be used for the apt cache lock```
sudo fuser -cuk /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/lock
```

---

### Post by Tim_Graffam on 2014-07-08
> **slickymaster said:**
> You can force the lock off by removing the file,** but it's not recommended without first closing the program that's holding the lock safely**,[COLOR=#000000] since you could cause corruption or interrupt an installation[/COLOR]

Any other suggestions on how to determine what it locking the file to avoid from corrupting things as you mention?

---

### Post by slickymaster on 2014-07-08
As I said previously the lock is placed when an apt process is running, and is removed when the process completes. If there is a lock with no apparent process running, this may mean the process got stuck for some reason.

You can try to catch the processes containing the word apt, at least.```
ps aux | grep apt
```If you see an **apt-get** process or an **aptitude** process that looks stuck, you can try```
kill processnumber
```and if that doesn't work try```
kill -9 processnumber
```

---

### Post by Tim_Graffam on 2014-07-08
Cant catch a break here... after running the first command ([COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock[/FONT][/COLOR]), the following is displayed and the entire system freezes.

[COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][IMG]https://dl.dropboxusercontent.com/u/603045/lock.png[/IMG]

---

### Post by slickymaster on 2014-07-08
Sorry, but to be honest I ran out of suggestions. Maybe someone else might pop-up with a fresh mind and be able to sort it out.

Good luck.

---

### Post by ibjsb4 on 2014-07-08
Did you purge when you reinstalled?
```
sudo apt-get remove --purge synaptic
```

---

