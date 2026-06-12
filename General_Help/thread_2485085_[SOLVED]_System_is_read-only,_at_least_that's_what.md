---
title: "[SOLVED] System is read-only, at least that's what dpkg thinks."
date: 2023-03-19
forum: General Help
---

### Post by qaqak on 2023-03-19
SOLUTION:

I fixed it!

Turns out I had a sysext mounted to /usr which was read-only. Removing the extension fixed the problem.



When I try to install a new package, dpkg always complains saying that the filesystem is read-only, even though it shows as read-write in /proc/mounts. The only read-only filesystems I found were provided by snaps.

Is there any way to fix this?

---

### Post by guiverc on 2023-03-19
If a file-system flips from RW (*read write*) to RO (*read-only*) without a user commanding it, it's usually the result of corruption being detected & the *flip* from RW to RO will be explained in *logs*, and protects against loss of data.

It should be explored by an administrator of the system, via reading of logs etc, and problem found, as it could be a warning of hardware issues (eg. PSU giving out poor power causing *good* components to misbehave, RAM problems, failing disk etc).  It should not be ignored or worked around, but explored.

You've given few specific details (*no clues as to Ubuntu product/release*), so I've been generic in this reply.

---

### Post by qaqak on 2023-03-20
I can write to the filesystem, but apparently dpkg cannot.

---

### Post by MAFoElffen on 2023-03-20
Could you please run the [UbuntuForums 'system-info" script]("https://github.com/UbuntuForums/system-info") from either (<--} that link or install it from this [PPA]("https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info/")? Select upload to pastebin and copy down the URL to point to in a post here. That will provide us with info on your hardware, what the current state is, and info about the configuration.

Then run this, and add to a post the output either as a Text attachment, or posted within code tags:
```

sudo dmesg -l err,warn

```
That will provide us with any sys log errors and warnings.

---

### Post by qaqak on 2023-03-20
[https://termbin.com/8htu](https://termbin.com/8htu)

---

### Post by MAFoElffen on 2023-03-20
And the sys log dmesg output?

I can see a glimpse of what it looks like now. Good foundation of what should be sound hardware. Dual-boot between Windows and Ubuntu, which is installed on a BTRFS-on-root filesystem, encrypted, but running Linux Kernel 6.2. The sources shed a bit more light on the customization, with PopOS and System76 repo's. 

None of the storage is near being full, so the r/o condition is not being trigger from that.

That leaves looking at your dmesg output to see if there is anything there that can shed light. Note that sometimes, that condition can be a chicken-before-the-egg affair, where it might go into an r/o condition and not be able to write the specific error to sys log in time. In that case, you might have to add a kernel cache boot parameter, to catch things before that condition occurs and closes it's teeth.

EDIT-- Note that Linux Kernel 6.2 for me, does not play well yet with my ZFS-on-root native encrypted systems.

---

### Post by qaqak on 2023-03-22
Actually, I have windows on a separate drive, and my Linux drive is unencrypted.

I checked dmesg, and I couldn't find any fs related warnings or errors.

---

### Post by MAFoElffen on 2023-03-22
Then I don't have enough information to say why it is telling dpkg that it is r/o...

What if, at boot, on the Grub2 Menu, advanced startup, recovery menu option, select 'fsck' to check the filesystem for errors?

You would think that any of that would show up in dmesg, but worth a try. Flipping over to r/o with dpkg would throw a write error... Otherwise, I have no other ideas of the why...

Anyone else have an idea?

---

### Post by qaqak on 2023-03-23
I fixed it!

Turns out I had a sysext mounted to /usr which was read-only. Removing the extension fixed the problem.

---

