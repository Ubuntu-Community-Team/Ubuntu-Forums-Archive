---
title: "Why does LXC start nVidia services on an Intel graphics notebook"
date: 2019-07-25
forum: General Help
---

### Post by GhX6GZMB on 2019-07-25
I just installed LXC (linux containers) using PPA:

> sudo add-apt-repository ppa:ubuntu-lxc/lxc-stable
> sudo apt update
> sudo apt install lxc
> sudo apt upgrade

On subsequent boots or shutdowns I keep getting the message

"started bpfilter"

And boot is slower. Is there any way to avoid this? AFAIK bpfilter belongs to the nVidia drivers and is useless to me with an Intel chipset.

I was able to roll back the installation using TimeShift and the problem has disappeared, which points the finger unequivocally at LXC.

Thank You.

---

### Post by deadflowr on 2019-07-25
Berkeley Packet Filter (bpfilter)
It's a networking utility.
Not sure how it relates to nvidia.
It's kernel module.

But, yeah, lxc can add to boot time since it has to load the necessary services to run.

---

### Post by GhX6GZMB on 2019-07-25
Thanks, deadflowr,
my google-fu has failed me on this one. NVidia is not the culprit, LXC is.
That LXC adds some overhead is obvious, but it's not obvious to me why this happens before a container is even defined or started.
This happens at boot time.
Any ideas on how to stop this happening or load bpfilter later?

Thanks.

---

