---
title: "Is this kernel version correct?"
date: 2023-02-15
forum: General Help
---

### Post by monkeybrain20122 on 2023-02-15
I am on Jammy and the current kernel is 5.15.0-60, which sounds about right

Today running apt update it shows an update to kernel 5.19.0.32.33 in the package linux-image-generic-hwe-22.04

Is this right?? Sounds kind of drastic version jump (the same version as linux-image-generic-hwe-22.04-edge)

---

### Post by ian-weisser on 2023-02-15
The version bump in the linux-generic-hwe-22.04 package is expected. It's 22.04.2

See [https://discourse.ubuntu.com/t/ubuntu-22-04-2-delayed-until-february-23/33319](https://discourse.ubuntu.com/t/ubuntu-22-04-2-delayed-until-february-23/33319) for the release discussion.

Keep in mind that 22.04.2's date of 23 Feb is for the installer release. The updated packages and version bumps don't wait for that date. 

$ rmadison linux-generic-hwe-22.04 | grep jammy
 linux-generic-hwe-22.04 | 5.15.0.25.27         | jammy            | amd64, arm64, armhf, ppc64el, s390x
 linux-generic-hwe-22.04 | 5.15.0.60.58         | jammy-security   | amd64, arm64, armhf, ppc64el, s390x
[B] linux-generic-hwe-22.04 | 5.19.0.32.33~22.04.9 | jammy-proposed   | amd64, arm64, armhf, ppc64el, s390x
 linux-generic-hwe-22.04 | 5.19.0.32.33~22.04.9 | jammy-updates    | amd64, arm64, armhf, ppc64el, s390x[/B]
[/code]

You're quite right that the new (stable) kernel is the same as -edge. That's the goal at release time.

---

### Post by monkeybrain20122 on 2023-02-16
Hi, Thanks for the explanation.

I did the update but the 5.19 kernel seemed to have broken something, shut down took longer than before. So I just removed linux-generic-hwe and installed linux-genric (so my 5.15 will get security updates). Maybe just wait for a few months and try 5.19 again.

Does it mean that my system will stay in 22.04.1? (not that it matters either way)

---

### Post by lucant on 2023-02-16
Here I updated to the new kernel, 5.19..., and everything works even better than the 5.15 kernel... . For example, when booting with kernel 5.15, several ACPI error messages would appear.
Now with kernel 5.19 these ACPI errors no longer appear... Another one appears: mvme mvme0: failed to set APST feature (2) ... rs

---

### Post by ian-weisser on 2023-02-16
> **monkeybrain20122 said:**
> Does it mean that my system will stay in 22.04.1?

False distinction.

The truth is that 22.04.x = 22.04 + ordinary apt updates

22.04.1 and 22.04.2 are **not** a separate releases of Ubuntu. They are simply updates/re-spins of the install .iso image to prevent new folks from downloading GB of old updates. It's simply 22.04 with those apt updates baked in.

---

### Post by Impavidus on 2023-02-17
The version number of your installed Ubuntu system changes with an update to the base-files package. It doesn't depend on the kernel you've installed. And that version number is pretty much irrelevant for your installed system.

---

### Post by ajgreeny on 2023-02-17
And whether your system automatically moves to the 5.19 kernel series depends on which point release of the installation .iso file you used.

In the past, though it may have now changed, if you used the non point release version or the .1 point release you would have stayed on the 5.15 series and moved to the 5.19 series only if you originally started with the .2 iso file, which is supported for the full support time of the release.

---

### Post by Impavidus on 2023-02-17
> **ajgreeny said:**
> In the past, though it may have now changed, ...
IIRC, on Xubuntu and Ubuntu Server, it's still like that. On Ubuntu, you get put on the hwe kernels by default. I don't know about the other flavours.

---

### Post by ajgreeny on 2023-02-18
> **Impavidus said:**
> IIRC, on Xubuntu and Ubuntu Server, it's still like that. On Ubuntu, you get put on the hwe kernels by default. I don't know about the other flavours.
Thanks for that info.
I always use Xubuntu so unfortunately my knowledge of the default gnome Ubuntu is limited often to guesswork.

---

### Post by maglin2 on 2023-02-18
I see I've now arrived at 22.04.2 (a few days early) and updated to kernel 5.19

```
~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.2 LTS"
PRETTY_NAME="Ubuntu 22.04.2 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.2 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
~$ uname -a
Linux 5.19.0-32-generic #33~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Jan 30 17:03:34 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
~$ 
```

---

