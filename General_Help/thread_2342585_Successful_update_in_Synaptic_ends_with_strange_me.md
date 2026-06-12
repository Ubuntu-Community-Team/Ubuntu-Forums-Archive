---
title: "Successful update in Synaptic ends with strange message"
date: 2016-11-08
forum: General Help
---

### Post by Edward_Diener on 2016-11-08
Using Synaptic Package Manager to update packages in 16.04 LTS I receive after a successful update:

"W: Can't drop privileges for downloading as file '/var/cache/apt/archives/partial/systemd-sysv_229-4ubuntu12_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)"

What does this mean and how do i fix this ?

---

### Post by ajgreeny on 2016-11-08
Have you made any changes to the cache, **/var/cache/apt/archives**, that synaptic uses when installing or updating packages?

I have several virtual machines of different DE versions of *ubuntu 16.04 which I run as guests in VBox on my Xubuntu 14.04.  I have made symbolic links from a folder that is shared between host and guest in the home of the host OS to /var/cache/apt/archives in all those guests so in effect, I use the same /var/cache/apt/archives for all those guest OSs, thereby saving a lot of time and duplicate downloads of packages when updating.

I always get that error message after synaptic has done its job, though the package mentioned, in your case **systemd-sysv_229-4ubuntu12_amd64.deb**, is always different, depending on what packages have been dealt with.  Clicking OK (or is it Ignore; I can't remember which?) gets rid of the error and everything works fine with all packages installed or updated as expected.

---

### Post by PaulW2U on 2016-11-08
> **Edward_Diener said:**
> What does this mean and how do i fix this ?
You might want to look at bug report [#1570141]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1570141") which was raised in April of this year and indicates that the **warning** (not an error) is seen frequently in Ubuntu 16.04. The final two comments of the bug report suggest that there is a "fix" that will remove the warning but I haven't tried it so I can't tell you that it works.

Conclusion: It's a known problem that so far the developers have yet to deal with.

---

### Post by Edward_Diener on 2016-11-08
Thanks, I will try the fix but will not worry about it otherwise.

---

### Post by bearlake on 2016-11-08
> **PaulW2U said:**
> You might want to look at bug report [#1570141]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1570141") which was raised in April of this year and indicates that the **warning** (not an error) is seen frequently in Ubuntu 16.04. The final two comments of the bug report suggest that there is a "fix" that will remove the warning but I haven't tried it so I can't tell you that it works.

Conclusion: It's a known problem that so far the developers have yet to deal with.

Thanks for the info, seen this as well.

---

