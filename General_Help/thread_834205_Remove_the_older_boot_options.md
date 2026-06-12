---
title: "Remove the older boot options"
date: 2008-06-19
forum: General Help
---

### Post by dethredic on 2008-06-19
Hardy makes a new boot option when the kernal is updated or something like that. I now have in my boot up list like 14-19, and it takes up lots of space and takes time to get down to windows. Can how can I delete all of them except the 2 most recent?

---

### Post by justleen on 2008-06-19
Open up synaptic Sytem >  Administration > package manager

Do a search for "linux"  and then sort by "installed"

look foor linux-generic.xxx and linux-headers...

you can uninstall the versions you dont need.

---

### Post by NilsE on 2008-06-19
There are two ways you can do this.

1) You can just deleted all the entries for the older ones in the menu.list under /boot

or

2) Completely remove the older kernels using the Synaptic package manager which will also clean out the grub menu.  The kernels are called linux-image so just search on that and you will find all the installed versions in Synaptic

---

### Post by dethredic on 2008-06-19
> **NilsE said:**
> There are two ways you can do this.

1) You can just deleted all the entries for the older ones in the menu.list under /boot

or

2) Completely remove the older kernels using the Synaptic package manager which will also clean out the grub menu.  The kernels are called linux-image so just search on that and you will find all the installed versions in Synaptic

I could not find a menu.list under in my /boot. I checked hidden files too.

> 
phil@phil:~$ cd /boot
phil@phil:/boot$ gedit menu.list


That just opened up a blank document.

EDIT: I was unsure of which packages to remove from synaptic, so left them alone not wanting to screw something up.

---

### Post by housam on 2008-06-19
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by dethredic on 2008-06-19
great, thanks housam and others.

---

### Post by VMC on 2008-06-19
> **dethredic said:**
> great, thanks housam and others.

You will also find sources of older generics under "/usr/src/". They eat up a lot of storage.

Edit: type this from Terminal to get an idea: 

```
du -hc /usr/src|grep total
```

---

### Post by aimpau on 2008-06-19
Is it ok to remove older linux-headers-x.x.xx-xx-generic/386 files?

---

### Post by housam on 2008-06-19
> **aimpau said:**
> Is it ok to remove older linux-headers-x.x.xx-xx-generic/386 files?
yes it is ok if you do not use them

---

### Post by stchman on 2008-06-19
> **dethredic said:**
> Hardy makes a new boot option when the kernal is updated or something like that. I now have in my boot up list like 14-19, and it takes up lots of space and takes time to get down to windows. Can how can I delete all of them except the 2 most recent?

I do not recommend editing the menu.lst manually.  Remove the old kernels via Synaptic.

TO edit other GRUB boot options install startupmanager.

---

