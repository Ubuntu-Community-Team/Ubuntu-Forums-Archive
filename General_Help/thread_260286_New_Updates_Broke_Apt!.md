---
title: "New Updates Broke Apt!"
date: 2006-09-18
forum: General Help
---

### Post by web250 on 2006-09-18
I'm trying to install the new updates released today (2.6.15-27) and now Apt is broken.

The error is:
E: Malformed 1st word in the Status line
E: Error occurred while processing libgtk1.2 (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I really need these updates, after the ones from 2 days ago made my machine extremely unstable.

---

### Post by Ramses de Norre on 2006-09-18
Look for syntax faults in /var/lib/dpkg/status in the libgtk1.2 section or near the beginning of the file.

---

### Post by compuguy1088 on 2006-09-18
Theres something funky with this update, because now I can't get my wireless drivers compiled.........

---

### Post by rarstar on 2006-09-18
hmmm, my pc updated about 30 mins ago, now i can't get wine or vmware to work

any ideas?

i think i noticed kernel-headers among the updates

---

### Post by web250 on 2006-09-18
Ok, fixed it, here's how:

Reinstall dpkg, dpkg-dev, and apt via synaptic. Which then installed the new kernel, fglrx, etc... that had errored earlier.

Now I'm in the -27 kernel...hopefully it is more stable than -26.

---

### Post by compuguy1088 on 2006-09-18
> **rarstar said:**
> hmmm, my pc updated about 30 mins ago, now i can't get wine or vmware to work

any ideas?

i think i noticed kernel-headers among the updates

Nm I figured out what was wrong with me....Apparently it didn't update the kernel-headers, so I had to install that, problem solved :).

---

### Post by BLTicklemonster on 2006-09-18
Eek. I updated, and now I'm afraid to reboot! Anyway, glad I found this before I rebooted :) .

---

### Post by Ramses de Norre on 2006-09-18
I upgraded, rebooted and everything worked perfect;) Don't worry too much.

---

### Post by spockrock on 2006-09-18
I can also say I have updated and rebooted with no problems.

---

### Post by jdong on 2006-09-18
To the OP, your dpkg database has somehow been corrupted.... That can't be caused by the update, but rather by some sort of hardware problem or hard shutoff on your end.

To the vmware people, the new update breaks the ABI, so all kernel modules must be recompiled. Run vmware-config.pl.

---

### Post by rarstar on 2006-09-18
hi, sorry for being a noob..

what's the abi?

would that account for wine breaking too?

how do i recompile the kernel modules?

thanks in advance,
rar

---

### Post by Ramses de Norre on 2006-09-18
I don't know all details but I think the abi is the way modules etc communicate with the kernel on a binary level. So if the abi changes all kernel modules must be recompiled against this new kernel with its new abi.

---

### Post by jdong on 2006-09-18
> **rarstar said:**
> hi, sorry for being a noob..

what's the abi?

would that account for wine breaking too?

how do i recompile the kernel modules?

thanks in advance,
rar

ABI is the Application Binary Interface -- the way binary modules communicate with the kernel. When the ABI changes (or "breaks"), all binary modules need to be compiled from source again to match the new ABI. While all attempts are made at preserving the ABI from update to update, it's not always possible.

The kernel modules included with Ubuntu are recompiled automatically by Ubuntu's developers whenever the ABI changes. However, your own modules need to be recompiled yourself. This includes vmware. To reactivate the recompiling procedure for vmware, run **sudo vmware-config.pl** at a terminal.



This should not account for WINE breaking -- Wine should not be affected by changes to the kernel. How has Wine broke? What are the symptoms?

---

### Post by BLTicklemonster on 2006-09-18
Sweet! All that happened to me was I locked up on the kubuntu screen, so I rebooted and went to the recovery mode, and of course my nvidia drivers didn't load, so I typed in envy at the command line, and it loaded back up, took me to the desktop, I rebooted normal to the new kernel, and vmware works, and amarok works, and obviously firefox works!

---

### Post by ruimoura on 2006-09-19
On my system it broke vmware, and if i do the "sudo vmware-config.pl" it gives me this message at some point :

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The directory of kernel headers (version 2.6.15-26-386) does not match your
running kernel (version 2.6.15-27-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

```

What is wrong? Help ](*,)

---

### Post by Ramses de Norre on 2006-09-19
Install the new kernel headers, in your new kernel do this: ```
sudo aptitude install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
```

---

### Post by ruimoura on 2006-09-19
Thank you so much. Problem solved :)

---

### Post by jdong on 2006-09-19
ruimoura, make sure the package "linux-headers-386" is installed. This will prevent this mismatch from happening come time for the next update.

---

