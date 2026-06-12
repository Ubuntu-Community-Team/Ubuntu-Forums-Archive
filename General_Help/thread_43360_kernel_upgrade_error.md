---
title: "kernel upgrade error"
date: 2005-06-21
forum: General Help
---

### Post by billiejoex on 2005-06-21
Hi all. I recently upgraded my system via apt-upgrade that automatically revealed a new kernel image (2.6.10-34.2). After downloading the package the installation went wrong and now i get the same error every time I do a system upgrade:

```

# apt-get upgrade
Setting up linux-image-2.6.10-5-386 (2.6.10-34.2) ...
/usr/sbin/mkinitrd: Cannot determine root device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-386 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.10-5-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The bad thing is that it always happens, also when I install a brand new system, every time i do a apt-upgrade
Is that a known bug?
How can I resolve the error message? 

Salud

---

### Post by Xian on 2005-06-21
[QUOTE=billiejoex]Hi all. I recently upgraded my system via apt-upgrade that automatically revealed a new kernel image (2.6.10-34.2). After downloading the package the installation went wrong and now i get the same error every time I do a system upgrade:[/QUOTE]
Let's try a couple of things.
Open a terminal and issue these commands:

```
$ sudo cp /etc/mkinitrd/mkinitrd.conf /etc/mkinitrd/mkinitrd.conf_backup
$ sudo gedit /etc/mkinitrd/mkinitrd.conf
```

When this file opens in the text editor, scroll down until you see this line:

```
ROOT=probe
```
Change "probe" to your actual root partition location.

For example, if you have your Ubuntu root partition on /dev/hda3 then you would want change the line above to appear as shown below. Just substitute your own system's real data.

```
ROOT=/dev/hda1
```
If you are unsure where your root partition is mounted then issue the command below and look for the line that starts '/dev/hdax on / type', where x is your partition number. That is your root partition location.

```
$ mount
```
Save the mkinitrd.conf file and see if there is any difference.

---

### Post by billiejoex on 2005-06-22
Really thank you. It works, now.

---

