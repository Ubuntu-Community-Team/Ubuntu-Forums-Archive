---
title: "How to boot in a text mode console?"
date: 2007-11-13
forum: General Help
---

### Post by luispa on 2007-11-13
How can I boot in a text mode console? In some distros it's enough to write single during the booting process.

Thank you very much in advance,

Luis Pablo

---

### Post by aysiu on 2007-11-13
Uninstall *gdm*?

---

### Post by paul.matthijsse on 2007-11-13
indeed with the "single" command!
When grub starts, press Esc and type e (for edit), then go to the line with the boot options and add "single" at the end. Just tried it in a VM with Kubuntu, and it doesn't load X, so in Ubu it must work as well.

---

### Post by az on 2007-11-13
> **paul.matthijsse said:**
> indeed with the "single" command!
When grub starts, press Esc and type e (for edit), then go to the line with the boot options and add "single" at the end. Just tried it in a VM with Kubuntu, and it doesn't load X, so in Ubu it must work as well.

You can just pick "recovery mode" from the list and you will get exactly the same thing.

---

### Post by luispa on 2007-11-13
Thank you very much for your help!!! The recovery option worked.

---

### Post by zippy028 on 2007-11-13
Isn't there something in a config file that can be changed. I am not sure with GRUB but I think with LILO I was able to set run level=3 and that would start most things including networking just not an X environment.

---

### Post by az on 2007-11-13
You would have to remove the gdm symlink in /etc/rc3.d for gdm to be removed from that runlevel.  Then, yes, appending a 3 to the end of your kernel line in grub would boot you into runlevel 3 which would then be X-less.

---

### Post by Christmas on 2007-11-13
Yes, what az pointed to you is the best option in my opinion. Or you can just "sudo chmod -x /etc/init.d/gdm" (replace gdm with kdm if you are using Kubuntu).

---

### Post by zippy028 on 2007-11-13
Thank you both that is what I needed to know.

---

### Post by mogliii on 2007-11-14
Hi,

I have a question that is, in a kind, related to this issue here.

I have a backup script, that backups with dd-command all relevant data to an usb drive, sends an log-file via email and shuts down the computer.

I was trying very hard to make this happen automatically, so that I just have to choose the right item in the grub menu and I can go to sleep, for example.

Now my attention got drawn on runlevels. Apparently Ubuntu 7.10 uses only 0, 1 (text mode), 2 (default, with X), 6 (reboot) and S.

So I changed the folder /etc/rc3.d in the following way that I removed the simlink to gdm, and created a new link to my script I want to execute. Its not the  backup script. It just appends the current `date` to a file and reboots. For debugging.

Now if I type into the console ```
sudo init 3
```
The computer reboots, and on reboot I can see that the date and time of just before was written into the file.

However, if I create a new GRUB Menu item (copy the default ubuntu) and append a 3 at the end and use this choice to boot, X is started and the computer does not restart.
```
who -r
```
yields Run-level 2

I found this entry in launchpad: 
[https://launchpad.net/ubuntu/+source/upstart/+bug/85014]("https://launchpad.net/ubuntu/+source/upstart/+bug/85014")

But the last entry there is dated from May. So I am very curious to hear from anybody if there is a new method to preselect runlevel with **upstart**.

Would greatly appreaciate your help!

---

### Post by bettlebrox on 2007-11-29
To disable X, just change to runlevel 2. As gutsy uses upstart instead of init you'll have to do the following:

[INDENT]How do I change the default runlevel?
-------------------------------------

Edit the /etc/inittab file, if you installed edgy fresh you'll need to
create it.  Locate, or write, the following line:

    id:N:initdefault:

Where N is the default runlevel, change this to match.
[/INDENT]

From /usr/share/doc/upstart/README.Debian.gz (read it using zless).

---

### Post by HermanAB on 2007-11-29
Run level 3 is what you want.  Toggle back and forth with:
# sudo init 3
and
# sudo init 5

Cheers,

Herman

---

