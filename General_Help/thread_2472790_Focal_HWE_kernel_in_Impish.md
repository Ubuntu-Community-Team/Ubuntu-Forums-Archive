---
title: "Focal HWE kernel in Impish?"
date: 2022-03-12
forum: General Help
---

### Post by DuckHook on 2022-03-12
A bit of a head scratcher for me, but I'm sure my more knowledgeable peers have insightful answers.

I have a new, virgin Impish install. Yet, oddly, it comes with what looks like the Focal HWE kernel (I've highlighted):
```
duckhook@Zeus:~$  dpkg --get-selections | grep linux
console-setup-linux				install
libnvpair3linux					install
libselinux1:amd64				install
libuutil3linux					install
libzfs4linux					install
libzpool4linux					install
linux-base					install
linux-firmware					install
**linux-generic-hwe-20.04				install**
linux-headers-5.13.0-30				install
linux-headers-5.13.0-30-generic			install
linux-headers-5.13.0-35				install
linux-headers-5.13.0-35-generic			install
linux-headers-generic-hwe-20.04			install
linux-image-5.13.0-30-generic			install
linux-image-5.13.0-35-generic			install
linux-image-generic-hwe-20.04			install
linux-modules-5.13.0-30-generic			install
linux-modules-5.13.0-35-generic			install
linux-modules-extra-5.13.0-30-generic		install
linux-modules-extra-5.13.0-35-generic		install
linux-sound-base				install
pptp-linux					install
util-linux					install
zfsutils-linux					install
```
I definitely didn't add this kernel. It already came bundled. Note that the expected generic kernel is also there, but the HWE kernel is included by default.

[list]
[*]Why would Canonical do that?
[*]Is there a downside to uninstalling it?
[/list]
My query is purely for curiosity. It's my main box and I have no intention of monkeying with it—I'm not fixing what ain't broken.

---

### Post by #&amp;thj^% on 2022-03-12
It's been talked about for a day or now, AU calls it a mistake. 
And a Bug report: [https://launchpad.net/ubuntu/+source/linux-hwe-5.13/5.13.0-30.33~20.04.1](https://launchpad.net/ubuntu/+source/linux-hwe-5.13/5.13.0-30.33~20.04.1)
>  Is there a downside to uninstalling it?
None for me  and you'll still have "linux-5.13.0-30-generic"
```
 dpkg --get-selections | grep linux
console-setup-linux                             install
libselinux1:amd64                               install
linux-base                                      install
linux-firmware                                  install
linux-generic-hwe-20.04                         install
linux-headers-5.13.0-28-generic                 install
linux-headers-5.13.0-30-generic                 install
linux-headers-generic-hwe-20.04                 install
linux-hwe-5.13-headers-5.13.0-28                install
linux-hwe-5.13-headers-5.13.0-30                install
linux-image-5.13.0-28-generic                   install
linux-image-5.13.0-30-generic                   install
linux-image-5.4.0-100-generic                   install
linux-image-5.4.0-99-generic                    deinstall
linux-image-generic                             install
linux-image-generic-hwe-20.04                   install
linux-modules-5.13.0-28-generic                 install
linux-modules-5.13.0-30-generic                 install
linux-modules-5.4.0-100-generic                 install
linux-modules-5.4.0-99-generic                  deinstall
linux-modules-extra-5.13.0-28-generic           install
linux-modules-extra-5.13.0-30-generic           install
linux-modules-extra-5.4.0-100-generic           install
linux-modules-extra-5.4.0-99-generic            deinstall
linux-sound-base                                install
pptp-linux                                      install
util-linux                                      install
me@me-standardpci440fxpiix1996:~$ uname -r
5.13.0-30-generic

```

---

### Post by DuckHook on 2022-03-12
Thanks for the quick response 1fallen.

I'm losing a few steps when it doesn't even occur to me to do a simple websearch which would have told me what I needed to know. :oops:

On topic: that's some bug&#8212;some mistake.

Jammy is less than one month away. I'm going to wait for that dust to settle before deciding what to do with this (if it's still hanging around after the release upgrade). Not losing sleep over it.

---

### Post by #&amp;thj^% on 2022-03-12
With all the changes and freeze's, it would peak my interest to see how it's received and reviewed by credible sources not just user opinions. :)

---

### Post by DuckHook on 2022-03-13
For the lurkers out there:

To follow up, it turns out that a default install of Impish does ***NOT*** come with the generic kernel:```
duckhook@Zeus:~$  apt policy linux-generic
linux-generic:
  Installed: (none)
  Candidate: 5.13.0.35.44
  Version table:
     5.13.0.35.44 500
        500 http://ca.archive.ubuntu.com/ubuntu impish-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu impish-security/main amd64 Packages
     5.13.0.19.30 500
        500 http://ca.archive.ubuntu.com/ubuntu impish/main amd64 Packages

```
It comes ***ONLY*** with the Focal HWE kernel. Therefore, do ***NOT*** remove the HWE kernel from your system, or at least don't do so until you manually install linux-generic. Otherwise, you will have nerfed your system and it won't boot unless you do some chroot magic with a LiveUSB. Lucky that I didn't remove the HWE kernel without further checking.

This must be the gist of the bug that 1fallen linked to. Parsing bug reports is a dark art in itself. I need to run down to Diagon Alley for the right wand.

---

### Post by #&amp;thj^% on 2022-03-13
However, the Linux 5.13 HWE (Hardware Enablement) kernel included in the Ubuntu 20.04.4 point release is intended only for new installations. Therefore, users running Ubuntu 20.04 LTS with the stock kernel (e.g. Linux 5.4), won&#8217;t receive the newer kernel when performing an upgrade. They will have to manually install it if they want to use the newer kernel from Ubuntu 21.10.
Well I almost shot myself right in the foot.
```

 apt list --installed | grep linux-generic

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-generic-hwe-20.04/now 5.13.0.30.33~20.04.17 amd64 [installed,upgradable to: 5.13.0.35.40~20.04.20]
```
This is a patched kernel affected by CVE-2022-0847:[https://ubuntu.com/security/CVE-2022-0847](https://ubuntu.com/security/CVE-2022-0847)

---

### Post by DuckHook on 2022-03-13
Now I'm really confused.

My understanding of your link is: presumably, the bug was fixed with```
impish		Released (5.13.0-35.40)
```
I don't see what this has to do with Impish installing the Focal HWE kernel by default instead of its own stock linux-generic. Note that, as per my post #5 linux-generic is already on```
—snip—
  Candidate: 5.13.0.35.44
—snip—
```…which, being a later kernel, should already be patched.

In any case, mine is a virgin Impish install, so it had no chance to inherit any Focal detritus. It was also installed a few months ago, prior to the bug, and I don't recall a system upgrade that switched from linux-generic to linix-generic-hwe-20.04 (though I admit it could have happened during an upgrade cycle and I wasn't paying sufficient attention).

I'm surprised that other forum members have not noticed this earlier.

---

### Post by #&amp;thj^% on 2022-03-13
> **DuckHook said:**
> Now I'm really confused.

My understanding of your link is: presumably, the bug was fixed with```
impish		Released (5.13.0-35.40)
```
I don't see what this has to do with Impish installing the Focal HWE kernel by default instead of its own stock linux-generic. Note that, as per my post #5 linux-generic is already on```
—snip—
  Candidate: 5.13.0.35.44
—snip—
```…which, being a later kernel, should already be patched.

In any case, mine is a virgin Impish install, so it had no chance to inherit any Focal detritus. It was also installed a few months ago, prior to the bug, and I don't recall a system upgrade that switched from linux-generic to linix-generic-hwe-20.04 (though I admit it could have happened during an upgrade cycle and I wasn't paying sufficient attention).

I'm surprised that other forum members have not noticed this earlier.
Nothing about kernels is intuitive in understanding, as it reads (and not my understanding) [focal 	Needed] Still!
But fixed with version 5.13.0.35.40~20.04.20
Other users have discovered this: [https://ubuntuforums.org/showthread.php?t=2472662](https://ubuntuforums.org/showthread.php?t=2472662)

---

### Post by DuckHook on 2022-03-13
Ya know, 1fallen?

I really need to get a brain transplant.

In fact, I read that thread a few days ago. It never occurred to me that my issue had anything to do with the "dirty pipe" vulnerability (do'h) #-o

So, I imagine that the Focal HWE kernel was subbed for the mainline kernel at some time very recently. I just wasn't paying attention when it happened. I don't have unattended upgrades turned on and I pride myself on knowing what is being installed on my system, but I obviously missed this one.

So, all is okay. I'll wait for the mainline kernel to get patched. Don't know what Canonical plans to do then. Maybe switch us back to the mainline, but it's not a big deal to me either way since everything works fine right now.

Just for kicks and giggles, I'm going to check out what kernel is installed on my development Jammy partition.

---

### Post by #&amp;thj^% on 2022-03-13
> **DuckHook said:**
> Ya know, 1fallen?

I really need to get a brain transplant.


Nah You don't need a brain transplant. You've just been pre-ocupied with other stuff. (Here in the forums)
Your still sharp as tack. ;)

---

### Post by Impavidus on 2022-03-14
linux-generic and linux-generic-hwe-20.04 are, on impish, both empty metapackages pulling in, via another set of metapackages, the latest 5.13 kernel and headers. Meaning, they are identical. That doesn't appear very useful, but not harmful either. Maybe it has some use for upgrades from 20.04 to 21.10 for users with the hwe kernel on 20.04.

Note that removing a kernel metapackage doesn't remove the kernel. It only stops automatic kernel upgrades.

---

### Post by DuckHook on 2022-03-14
> **Impavidus said:**
> linux-generic and linux-generic-hwe-20.04 are, on impish, both empty metapackages pulling in, via another set of metapackages, the latest 5.13 kernel and headers. Meaning, they are identical. That doesn't appear very useful, but not harmful either. Maybe it has some use for upgrades from 20.04 to 21.10 for users with the hwe kernel on 20.04.

Note that removing a kernel metapackage doesn't remove the kernel. It only stops automatic kernel upgrades.
Thanks for the clarification. Your explanation/reminder really helps. At least, for this ultra-suspicious user it does.

---

