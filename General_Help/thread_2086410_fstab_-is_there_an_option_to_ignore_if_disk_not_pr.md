---
title: "fstab -is there an option to ignore if disk not present?"
date: 2012-11-20
forum: General Help
---

### Post by rocket777 on 2012-11-20
I have a system with a quick connect/removable hard-drive, i.e. it's in a tray and there's a button which lets me connect or disconnect the drive at boot up. It's an IDE drive and connects to the IDE bus only if set to on.

I only use this occasionally, but for convenience I placed an entry into /etc/fstab to mount it on boot up.

Now, unbuntu (10.04) hangs on boot waiting for me to type "s" if I want to skip the mount (when the drive is not connected).

I would like to know if there's an option I can put in that tells the system to just ignore this drive when it cannot be found - or at minimum, to have a timeout I can set so the boot up completes. This system is usually remotely started (via a wake on lan) so I'm not always there to type on the keyboard.

---

### Post by steeldriver on 2012-11-20
nobootwait maybe?

[http://manpages.ubuntu.com/manpages/precise/man5/fstab.5.html](http://manpages.ubuntu.com/manpages/precise/man5/fstab.5.html)

---

### Post by efflandt on 2012-11-20
A quick peek at **man fstab** finds maybe **nofail**

"do not report errors for  this  device  if  it  does  not exist."

---

### Post by rocket777 on 2012-11-20
> **steeldriver said:**
> nobootwait maybe?

[http://manpages.ubuntu.com/manpages/precise/man5/fstab.5.html](http://manpages.ubuntu.com/manpages/precise/man5/fstab.5.html)


That's the one!!!:KS

I'll have to bookmark those manpages, I forgot about the man command for file formats.

Thanks!! :popcorn:

---

### Post by Wim Sturkenboom on 2012-11-21
> **rocket777 said:**
> That's the one!!!:KS

I'll have to bookmark those manpages, I forgot about the man command for file formats.

Thanks!! :popcorn:
They're on your system; why bookmark :lolflag:

```

man whatever

```

---

### Post by dcstar on 2012-11-22
> **rocket777 said:**
> 
..........
I would like to know if there's an option I can put in that tells the system to just ignore this drive when it cannot be found - or at minimum, to have a timeout I can set so the boot up completes. This system is usually remotely started (via a wake on lan) so I'm not always there to type on the keyboard.

Use the "noauto" option in the fstab line, but you will have to manually mount it when you want to use it:

```
sudo mount -a
```

---

### Post by Morbius1 on 2012-11-22
> **dcstar said:**
> Use the "noauto" option in the fstab line, but you will have to manually mount it when you want to use it:

```
sudo mount -a
```
Nope.

From man mount:
> 
The command
                     mount -a [-t type] [-O optlist]

(usually given in a bootscript) causes all filesystems mentioned in fstab  (of  the proper  type and/or having or not having the proper options) to be mounted as indicated, **[COLOR=Blue]except for those whose line contains  the  noauto  keyword[/COLOR]**.

---

