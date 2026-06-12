---
title: "remove KDE from Ubuntu 13.04"
date: 2013-04-29
forum: General Help
---

### Post by Nitewalker on 2013-04-29
I uploaded and install the KDE desktop after I installed Ubuntu 13.04, I have tried to remove it but am having no luck, tried using suggestions found online but no luck....what do I need to do?  Thanks

---

### Post by GreenLizzard on 2013-04-29
> **Nitewalker said:**
> I uploaded and install the KDE desktop after I installed Ubuntu 13.04, I have tried to remove it but am having no luck, tried using suggestions found online but no luck....what do I need to do?  Thanks

Me too, that said I am now doing an apt-get purge kde*.*.  We'll see if I get to re-install the server!

---

### Post by mastablasta on 2013-04-29
what do you mean? you followed this?: [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

not eKDe might be needed with certain KDE applications if you installed them

---

### Post by ibjsb4 on 2013-04-29
As you found out, the remove/purge command will not work in this case.  Mastablasta has given you the solution.

---

### Post by Nitewalker on 2013-04-29
I followed the link that was listed by "mastablasta", and this is what I got:

[sudo] password for nitewalker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'plasma-widget-telepathy-presence' is not installed, so not removed
E: Unable to locate package kubuntu-docs
E: Unable to locate package libkdcraw21
E: Unable to locate package libkipi9
E: Unable to locate package libktorrent4
E: Unable to locate package libktpcommoninternalsprivate3
E: Unable to locate package libokularcore1abi1
E: Unable to locate package plasma-widget-telepathy-chat
nitewalker@laptop:~$ 

I am trying to remove this from Ubuntu 13.04 that I had loaded KDE onto after I updated from 12.10?

---

### Post by ibjsb4 on 2013-04-29
13.04 has yet to be implemented by psychocats so there may be a bit of a difference.  Do you still see kde in your ubuntu install?

---

### Post by Nitewalker on 2013-04-29
During boot it shows Kubuntu in list of systems an the desktop screen says Kubuntu, but if I check what version of Linux I am using from the terminal it says Ubuntu 13,04?

---

### Post by ibjsb4 on 2013-04-29
Does Nautilus still have a built in search function, Im not sure, but if it does:

In terminal:

```
gksudo nautilus
```

Go to "File System" and search **kde**.  What do you come up with?  Also you may need to ..

[http://ubuntuforums.org/showthread.php?t=2139594&p=12621740&viewfull=1#post12621740](http://ubuntuforums.org/showthread.php?t=2139594&p=12621740&viewfull=1#post12621740)

---

### Post by Nitewalker on 2013-04-29
when I ran search in natilus came up with nothing when used KDE as search data, also on other suggestion of checking root, it is listed as sudo

---

### Post by Nitewalker on 2013-04-29
Don't know if this helps or not but thought would include

nitewalker@laptop:~$ cat /etc/issue
Ubuntu 13.04 \n \l

nitewalker@laptop:~$ gksu-properties
nitewalker@laptop:~$ cat /proc/version
Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013
nitewalker@laptop:~$

---

### Post by ibjsb4 on 2013-04-29
Did you search KDE or kde, makes a difference.

What display manager are you running?  If its kdm you can remove it, but first change back to lightdm.

[http://ubuntuforums.org/showthread.php?t=1860704&p=11345936&viewfull=1#post11345936](http://ubuntuforums.org/showthread.php?t=1860704&p=11345936&viewfull=1#post11345936)

---

### Post by kamranm1200 on 2013-04-29
Well, 13.04 is fairly new, so it might have some bugs. But they are always fixed once new updates are released. Just try doing either one of these two commands, they might help:

sudo apt-get remove kde-desktop

sudo apt-get remove kubuntu-desktop

Let me know if they work or not.

---

### Post by ibjsb4 on 2013-04-29
The psychocats command remove kubuntu-desktop and no such package as kde-desktop.

---

### Post by Nitewalker on 2013-04-29
ran search both KDE & kde, nothing on either one came up, am using lightdm as far as I can tell, not sure of how to check?

---

### Post by ibjsb4 on 2013-04-29
See whats listed in

/etc/x11/default-display-manager

---

### Post by Nitewalker on 2013-04-29
/usr/sbin/lightdm

---

### Post by ibjsb4 on 2013-04-29
Take a look in /usr/share/xsessions

---

### Post by matt_symes on 2013-04-29
Hi

@nitewalker.

Is it just the Kubuntu splash screen that is left ? 

If it is then you can edit your alternatives symlinks to get rid of it and then update-initramfs.

```
sudo apt-get purge kubuntu-desktop
```

```
sudo update-alternatives --config default.plymouth
```

Select...

```
ubuntu-logo.plymouth
```

Then...

```
sudo update-initramfs -u
```

Kind regards

---

### Post by Nitewalker on 2013-04-30
Follow hint that matt_symes left, all seems to be cleared up better now....thanks to everyone who added comments, really appriciated:popcorn:

---

