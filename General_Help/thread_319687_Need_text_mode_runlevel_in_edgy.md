---
title: "Need text mode runlevel in edgy"
date: 2006-12-16
forum: General Help
---

### Post by JTux on 2006-12-16
Hi

I need help with enabling a text mode runlevel in Edgy. I should be able to choose this in grub boot list
 
Any form of help is much appreciated.

Thank you
:)

---

### Post by ciscosurfer on 2006-12-16
> **JTux said:**
> Hi

I need help with enabling a text mode runlevel in Edgy. I should be able to choose this in grub boot list
 
Any form of help is much appreciated.

Thank you
:)There are other ways to do it, but you can always CTRL-ALT-F2 through CTRL-ALT-F6 your way into a text command prompt.  Use CTRL-ALT-F7 to get back to the GUI.

Now that /etc/inittab is gone in Edgy, you need to mess around with the files located under /etc/event.d (although, according to some docs I've read, /etc/inittab will work just fine with Upstart if it is present.  To learn more about how to modify Upstart, gunzip the following document on your drive and the read it within your terminal.  Or, skip the -c switch, and open the document in your favorite editor once it's been gunzipped```
gunzip -c /usr/share/doc/upstart/README.Debian.gz
```From the README:>                               Edit the /etc/inittab file, if you installed edgy fresh you'll need to create it.  Locate, or write, the following line:
    id:N:initdefault:
Where N is the default runlevel, change this to match.

---

### Post by firecrotch on 2006-12-16
As far as I know (from reading other forums) it is not possible (at least not using GRUB).  I could be wrong though.

---

### Post by bodhi.zazen on 2006-12-16
At install the run levels are all the same.

The default run level is 2. If you want to boot to the CLI at this run level:
```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```
* This disables GDM

Reboot.

If you want to keep the default booting to a GDM, but want to change the behavior of another run level (say 3)

```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/s13gdm
```

Now add an entry in /boot/grub/menu.lst to boot to run level 3

At the end of the kernel line add a "3" (without quotes)
Lilke this> kernel=/boot/vmlinuz.... root=/dev/..... ro quiet splash **[color=darkred]3[/color]**

---

### Post by ciscosurfer on 2006-12-16
> **bodhi.zazen said:**
> At install the run levels are all the same.

The default run level is 2. If you want to boot to the CLI at this run level:
```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```* This disables GDM

Reboot.

If you want to keep the default booting to a GDM, but want to change the behavior of another run level (say 3)

```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/s13gdm
```Now add an entry in /boot/grub/menu.lst to boot to run level 3

At the end of the kernel line add a "3" (without quotes)
Lilke this> kernel=/boot/vmlinuz.... root=/dev/..... ro quiet splash **[COLOR=darkred]3[/COLOR]**Thanks for the tips!  I learn something new everyday! :D

---

### Post by bodhi.zazen on 2006-12-16
> **ciscosurfer said:**
> Thanks for the tips!  I learn something new everyday! :D

That is one of the best features of the Ubuntu forums 8)

---

### Post by JTux on 2006-12-16
> **bodhi.zazen said:**
> 

If you want to keep the default booting to a GDM, but want to change the behavior of another run level (say 3)

```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/s13gdm
```

Now add an entry in /boot/grub/menu.lst to boot to run level 3

At the end of the kernel line add a "3" (without quotes)
Lilke this

Did this, but the graphical login screen is still displayed after booting. When I login using this screen, gnome is loaded as usual :confused:

---

### Post by JTux on 2006-12-16
after booting into runlevel 2, even doing ```
sudo telinit 3
``` wont stop X.

---

### Post by bodhi.zazen on 2006-12-16
Interesting.

Apparently Edgy is now using Upstart. I have no idea how to change run levels at boot. 

I would irc freenode.irc #ubuntu

---

### Post by ciscosurfer on 2006-12-17
> **JTux said:**
> Did this, but the graphical login screen is still displayed after booting. When I login using this screen, gnome is loaded as usual :confused:

> **JTux said:**
> after booting into runlevel 2, even doing ```
sudo telinit 3
``` wont stop X.

> **bodhi.zazen said:**
> Interesting.

Apparently Edgy is now using Upstart. I have no idea how to change run levels at boot. 

I would irc freenode.irc #ubuntuHmm.  [Read my original post in the this thread]("http://ubuntuforums.org/showpost.php?p=1893360&postcount=2").  It might help.

---

### Post by koenn on 2006-12-17
X / gdm is started in every runlevel exept 1, 
so if it has been started in runlevel 2, the change of
```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/s13gdm
```
will NOT stop it. It will only prevent it from starting in runlevel 3 (if it is not already running)

To stop a service in a given runlevel, use "K". 
e.g.
```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/**K**87gdm
```
will*** stop*** gdm when entering runlevel 3 if it is already running (eg when your coming from an other runlevel where gdm was started)

---

### Post by ciscosurfer on 2006-12-17
You can still create an /etc/inittab file if you're running Edgy, modigy the init level>  Edit the /etc/inittab file, if you installed edgy fresh you'll need to create it. Locate, or write, the following line:
    id:N:initdefault:
Where N is the default runlevel, change this to match.                                                                                   [I]Taken from the /usr/share/doc/upstart/README.Debian.gz gunzipped file located on all installations of Edgy.

[/I]This page might help as well: [http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)
Set your default runlevel in the /etc/inittab that you create to be runlevel 1 for example set this line to read```
id:1:initdefault:
```

---

### Post by JTux on 2006-12-26
> **JTux said:**
> after booting into runlevel 2, even doing ```
sudo telinit 3
``` wont stop X.

Doing ```
start-stop-daemon --stop --name gdm
``` kills the gui.:)

---

### Post by JTux on 2006-12-28
> **koenn said:**
> 
```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/**K**87gdm
```


That solved the problem. 

Thank you everyone for your help:)

---

