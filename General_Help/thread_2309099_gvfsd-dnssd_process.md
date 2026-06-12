---
title: "gvfsd-dnssd process?"
date: 2016-01-07
forum: General Help
---

### Post by cogset on 2016-01-07
I've been noticing this gvfsd-dnssd process in Lubuntu 14 for a while  now, I've never seen it in older releases neither I'm seeing it in  Ubuntu-Mate 15.04, which makes me wonder what is this about.

A  quick search may point towards the avahi service, which I have  completely removed from the system , minus a few avahi libraries that  had some dependencies: so why is this process still spawned?

Does it have something to do with wireless networking?

---

### Post by v3.xx on 2016-01-07
Its in mate 16.04

[ATTACH=CONFIG]266606[/ATTACH]

---

### Post by cogset on 2016-01-08
So what? Do you have avahi installed/running?

I'm 100% positive that I don't have this process in Ubuntu-Mate 15.04, neither I  remember seeing it in Ubuntu 10.04 or 12.04 (please note that I always remove avahi because I simply don't need it at all) : so why is there in Lubuntu 14.04 even if avahi is removed?

That is, assuming this gvfsd-dnssd process is actually spawned by avahi and not something else: the difference in my Lubuntu OS is that it is installed on a laptop as opposed to a desktop pc, so maybe wireless networking comes into play as well?

---

### Post by Morbius1 on 2016-01-08
Well, let's see ...................

```
apt-cache depends lubuntu-desktop
```
Yields among other things:
> Depends: gvfs-backends
And:
```
dpkg -L gvfs-backends | grep dnssd
```
gvfs-backends includes that process:
> /usr/lib/gvfs/gvfsd-dnssd
So your desktop was built requiring it.

---

### Post by cogset on 2016-01-26
Sure, I understand gvfs-backends is part of a standard installation.

What I still do not understand is why this gvfsd-dnssd process is triggered in Lubuntu 14 but I've never seen it in Ubuntu 15.04, even if it's clearly part of this system too:

```
dlocate -L gvfs-backends|grep dnssd
/usr/lib/gvfs/gvfsd-dnssd
```

but a search for this particular process in   15.04 with pgrep _always_ returns a blank.

Apparently something is triggering this process in Lubuntu 14, so again I'm wondering if it has something to do with wireless networking or something like shared printers and such (although, having disinstalled avahi and samba I don't think I should be seeing it) .

---

### Post by Morbius1 on 2016-01-26
Ubuntu 15.04 replaces upstart with systemd so I don't know how that affects all this.

If I start with a cold boot and run Ubuntu 15.04 and go to System Monitor you are absolutely correct. gvfs-dnssd is nowhere to be found.

If I run Nautilus however and select Browse Network gvfs-dnssd does in fact show up as a running process in System Monitor. 

Perhaps it's just a design difference between Lubuntu and Ubuntu. Ubuntu invokes it when required.

---

### Post by cogset on 2016-02-28
I think it may be the file browser triggering this process in LXDE as well, perhaps it searches for samba shares or other similar devices, even if it should not IMHO: if I have removed applications that may actually use gvfs-dnssd like samba or avahi, what's  the point of starting that process anyway?

---

