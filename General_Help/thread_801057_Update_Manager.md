---
title: "Update Manager"
date: 2008-05-20
forum: General Help
---

### Post by crazyhorse on 2008-05-20
When notified of new updates, I click on the 'orange gear' icon and update manager starts.
However, when I click on "install updates" it does nothing but check for new updates and then it stops. With the updates still listed, in other words, it does not download anything.
Please help me if possible.

---

### Post by cdtech on 2008-05-20
Have you tried the command line:

sudo apt-get update

What happens?
This will show a verbose output with what's going on.

---

### Post by Ryadt on 2008-05-20
try in terminal
sudo apt-get upgrade

---

### Post by crazyhorse on 2008-05-20
This is what it said

us.archive.ubuntu.com hardy-backports/universe Packages

Fetched 150kB in 2s (58.7kB/s)                     
W: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Kevbert on 2008-05-20
It's looking for a CD in the drive.  Try disabling the CD in System-Admin-Software Sources (it may be under both the default and third party tabs).

---

### Post by cdtech on 2008-05-20
Or you could "sudo pico /etc/apt/sources.list" and comment out the CDROM line.

---

### Post by crazyhorse on 2008-05-20
tried both to no avail.:(

---

### Post by drs305 on 2008-05-20
Have you tried a different server? Update manager most likely uses the server listed in synaptic. Open synaptic, settings, repositories, download from, other and try 'select best server'.

I also looks like your sources.list may not be searching any online repositories. Open sources.list and see if everything is commented out. It has happened to a couple of other people recently.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by cdtech on 2008-05-20
> **crazyhorse said:**
> tried both to no avail.:(

What do you get at the command line now?

---

### Post by crazyhorse on 2008-05-20
"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

OK This is weird.
I did the Synaptic thing and got the above message after it reloaded.
Then I tried the update manager and it said my system is up to date!!!!!!!:confused:

---

### Post by drs305 on 2008-05-20
Please post the results of:
```
cat /etc/apt/sources.list
```

I think either your sources.list is not correct or you are not connecting to any online server (or both).

---

### Post by cdtech on 2008-05-20
I see you didn't comment the cdrom in the sources.list.

---

### Post by crazyhorse on 2008-05-20
I unchecked it during the synaptic check, then rechecked it before doing the update manager.

---

