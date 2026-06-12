---
title: "package maintainance mistake:failed to install nvidia driver from Ubuntu Software App"
date: 2023-11-05
forum: General Help
---

### Post by the-user-888 on 2023-11-05
It was all good before I did `apt dist-upgrade -y`

and nvidia driver failed to load. So I uninstalled all nvidia drivers in tty mode by `apt autoremove --purge nvidia-*`, and I signed in the system and tried to reinstall nvidia driver using the Ubuntu Software App (22.04).

Error occured here. 



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293010&stc=1[/IMG]

The dependency packages have **wrong package names **as you can see from the screenshot.

it's a mistake from ubuntu package maintainers. Please fix it. Thanks!

----
The quick "fix" is that I downgraded the nvidia driver version to 525 and it worked.

---

### Post by MAFoElffen on 2023-11-06
So file a bug on it at Launchpad, to try to get the people who maintain the packages in the Repo's to fix it...

It does no good to tell us, except to warn us of that. No one here is connected to Canonical. We are all just volunteers. None of are the maintainers.

Once you file it, then please post the link to the Bug Report here.

---

### Post by ian-weisser on 2023-11-06
> **the-user-888 said:**
> The dependency packages have **wrong package names **as you can see from the screenshot.

Well, that's one possible interpretation.

Another is that you overlooked something during your uninstall, and still have a package installed that requires the older version.

While the former is not impossible, it is very, very rare. I recall only a couple such in the past decade. A "wrong package name" would usually be discovered during testing.
The latter is much more likely. We see those every day.

Perhaps you might humor us and troubleshoot it like the latter.

---

### Post by MAFoElffen on 2023-11-06
Sorry if that came across a bit course...

I believe I have posted this a few times on this forum over the last decade... I always try to remove NVidia drivers before installing a new version of them. I do not trust the Software & Updates app to do that for me. I do it from the commandline.
```

sudo apt remove --purge nvidia* cuda*

``` 
gets most, if not all. I always verify that to make sure there is nothing left-over. If you want to check that, verify that with
```

apt list *nvidia* --installed

```
You can see what that means when things "are installed":
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list *nvidia* --installed
Listing... Done
libnvidia-cfg1-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-common-390/jammy-updates,jammy-updates,jammy-security,jammy-security,now 390.157-0ubuntu0.22.04.2 all [installed,automatic]
libnvidia-compute-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-compute-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-decode-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-decode-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-encode-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-encode-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-fbc1-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-fbc1-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-gl-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-gl-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-ifr1-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-ifr1-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 i386 [installed,automatic]
linux-modules-nvidia-390-6.2.0-32-generic/jammy-updates,jammy-security,now 6.2.0-32.32~22.04.1 amd64 [installed,auto-removable]
linux-modules-nvidia-390-6.2.0-33-generic/jammy-updates,jammy-security,now 6.2.0-33.33~22.04.1+1 amd64 [installed,automatic]
linux-modules-nvidia-390-6.2.0-36-generic/jammy-updates,jammy-security,now 6.2.0-36.37~22.04.1 amd64 [installed,automatic]
linux-modules-nvidia-390-generic-hwe-22.04/jammy-updates,jammy-security,now 6.2.0-36.37~22.04.1 amd64 [installed]
linux-objects-nvidia-390-5.13.0-25-generic/now 5.13.0-25.26~20.04.1+1 amd64 [installed,local]
linux-objects-nvidia-390-6.2.0-32-generic/jammy-updates,jammy-security,now 6.2.0-32.32~22.04.1 amd64 [installed,auto-removable]
linux-objects-nvidia-390-6.2.0-33-generic/jammy-updates,jammy-security,now 6.2.0-33.33~22.04.1+1 amd64 [installed,automatic]
linux-objects-nvidia-390-6.2.0-36-generic/jammy-updates,jammy-security,now 6.2.0-36.37~22.04.1 amd64 [installed,automatic]
linux-signatures-nvidia-6.2.0-32-generic/jammy-updates,jammy-security,now 6.2.0-32.32~22.04.1 amd64 [installed,auto-removable]
linux-signatures-nvidia-6.2.0-33-generic/jammy-updates,jammy-security,now 6.2.0-33.33~22.04.1+1 amd64 [installed,automatic]
linux-signatures-nvidia-6.2.0-36-generic/jammy-updates,jammy-security,now 6.2.0-36.37~22.04.1 amd64 [installed,automatic]
nvidia-compute-utils-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
nvidia-driver-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed]
nvidia-kernel-common-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
nvidia-kernel-source-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
nvidia-prime/jammy,jammy,now 0.8.17.1 all [installed,automatic]
nvidia-settings/now 525.60.13-0ubuntu1 amd64 [installed,local]
nvidia-utils-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]
xserver-xorg-video-nvidia-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed,automatic]

```
So in the past, I used to recommended that as
```

sudo apt remove --purge nvidia* libnvidia* linux*nvidia*

```
for the just-in-cases... But later shortened that to just "nvidia*" because that usually just works...

But back on Bug Reports... I file a lot of bug reports. I verify if something is actually a bug, or just something done differently... As users that care, we can do "our part" to make things work, by reporting things that do not work as expected. That is a way we can make that system work to improve what is here. Understood?

---

