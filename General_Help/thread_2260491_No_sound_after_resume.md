---
title: "No sound after resume"
date: 2015-01-12
forum: General Help
---

### Post by meanmrmustard on 2015-01-12
I've recently adjusted power settings to have the hard disk sleep after an hour.
Now when I resume sound does not work.
Jack is not installed.

Logging out and then into a second account doesn't work nor does restarting Pulse Audio or reloading the alsa module.

The only thing I've found that gets sound running again is rebooting.

What could be causing this behavior and how can I fix it?

---

### Post by Yellow Pasque on 2015-01-12
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by meanmrmustard on 2015-01-12
[http://www.alsa-project.org/db/?f=db1aca67337a78458fe8d4c88bb8a1cdb80e9dd1](http://www.alsa-project.org/db/?f=db1aca67337a78458fe8d4c88bb8a1cdb80e9dd1)

---

### Post by Yellow Pasque on 2015-01-12
If you're talking about the M-Audio card, then I bet a newer kernel would fix the issue: [https://github.com/torvalds/linux/commit/8c1d843460f42417d6b9553147a1a04ca1470602](https://github.com/torvalds/linux/commit/8c1d843460f42417d6b9553147a1a04ca1470602)
The LTS utopic kernel includes that fix, or you can try a mainline upstream kernel.

---

### Post by meanmrmustard on 2015-01-12
I tried the utopic generic kernel. On install I got:
```
Error! Bad return status for module build on kernel: 3.14.13-031413-generic (x86_64)
Consult /var/lib/dkms/nvidia-331/331.113/build/make.log for more information.
```


The file mentioned does not exist.
Is it simply that I need to re-install the nvidia driver - or maybe a supported nvidia driver - manually or something more serious?

---

### Post by Yellow Pasque on 2015-01-12
Hmm. Where did you get a 3.14.x kernel? Ubuntu 14.04 uses 3.12.x and 14.10 uses 3.16.x kernel.
Yeah, you may need to install an updated nvidia driver to use a newer kernel. The 340.65 driver can be obtained here: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by meanmrmustard on 2015-01-12
Followed some old instructions (from July 2014) here:
[http://www.itworld.com/article/2696669/open-source-tools/install-linux-kernel-3-14-13-in-ubuntu-14-04.html](http://www.itworld.com/article/2696669/open-source-tools/install-linux-kernel-3-14-13-in-ubuntu-14-04.html) 

I've never had to upgrade a kernel outside normal updates - that must be how I ended up with v. 3.13.09?
So the 3.16.x can be used on my 14.04.1 box?

Also, I'm unsure of the wisdom of using an untrusted PPA and have worked through many issues with various nvidia drivers in the past,though I believe this shouldn't be a problem, yes?
I'm using a GeForce GT 620 video card and found one driver wouldn't work in the last couple Ubuntu versions,- it was labelled  'proprietary'  rather than just the one labelled 'proprietary, tested' which the updater calls the recommended version.

---

### Post by Yellow Pasque on 2015-01-12
> Also, I'm unsure of the wisdom of using an untrusted PPA
It's your call. I've seen good feedback on this PPA and I've recommended it before. I actually have an 8400GS and use the 340.65 driver here on Debian.

As for the kernel, I would install a separate upstream kernel instead of messing with the LTS utopic kernel (the 3.16 one found in the repos) because you may not be able to easily roll it back if you wish (I'm not sure). AN actual Ubuntu user may be able to comment on that.
Example instructions: [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels)
I'd probably go with this kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.8-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.8-vivid/)
A 3.18 kernel might work, but even the 340.65 nvidia driver may not work with that.

---

### Post by meanmrmustard on 2015-01-12
I took your advice and used the 3.17.1 kernel and the issue is resolved and the nvidia driver did not need to be re-installed.
Thanks very much for your input, the links you provided gave me all the info i needed.

---

### Post by Yellow Pasque on 2015-01-12
You're welcome.

---

