---
title: "Installing Swiftfox on Fiesty"
date: 2007-04-28
forum: General Help
---

### Post by mskadu on 2007-04-28
Hi,

I just noticed that Epiphany seems to be running faster than firefox. My system seems to become jerky when i start FF and becomes worse as i keep it running for a while. Note that i have done no "about:config" tweaks and am running FF as it came. I have had it since 6.0x.

I am trying to get swiftfox specifically compiled for 32 bit Pentium4. But "sudo apt-get install swiftfox" tells me 

```

user1@server1:~$ sudo apt-get install swiftfox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swiftfox

```Can any one help?

---

### Post by NilsE on 2007-04-28
Add this to your sources.list

```
http://getswiftfox.com/builds/debian/branch unstable non-free

```
Then you can install it from package manager

---

### Post by mskadu on 2007-04-28
Thank you for your response. But. dont you mean:

```
deb [http://getswiftfox.com/builds/debian/branch](http://getswiftfox.com/builds/debian/branch) unstable non-free
```In any case, I am getting the following:

```
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release    
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages
Err [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages
  404 Not Found
Fetched 6B in 1s (5B/s)
Failed to fetch [http://getswiftfox.com/builds/debian/branch/dists/unstable/non-free/binary-i386/Packages.gz](http://getswiftfox.com/builds/debian/branch/dists/unstable/non-free/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```at the end of my "sudo apt-get update"

Any suggestions?

I also just realized. Is [http://getswiftfox.com/](http://getswiftfox.com/) down?

> **NilsE said:**
> Add this to your sources.list

```
http://getswiftfox.com/builds/debian/branch unstable non-free

```Then you can install it from package manager

---

### Post by NilsE on 2007-04-28
Add it to your sources.list file (not as input to the apt-get command) and install it from the GUI synaptic package manager.  There are multiple versions at that source location.

And yes, it looks like it is down now anyway.

---

### Post by hyperair on 2007-04-28
I ran the installer from getswiftfox.com. Not advisable, I know, but it worked pretty fine.

---

### Post by mskadu on 2007-04-28
Which sources.list is this. I modified /etc/apt/sources.list

> **NilsE said:**
> Add it to your sources.list file (not as input to the apt-get command) and install it from the GUI synaptic package manager.  There are multiple versions at that source location.

And yes, it looks like it is down now anyway.

---

### Post by NilsE on 2007-04-28
Yes, the /apt/sources.list.  And I was wrong you do need the deb in front

```
deb [http://getswiftfox.com/builds/debian/branch](http://getswiftfox.com/builds/debian/branch) unstable non-free
```

---

### Post by mskadu on 2007-04-28
I suppose i will have to wait until swiftfox.com wakes up. 

> **NilsE said:**
> Yes, the /apt/sources.list.  And I was wrong you do need the deb in front

```
deb [http://getswiftfox.com/builds/debian/branch](http://getswiftfox.com/builds/debian/branch) unstable non-free
```

---

### Post by aldenhg on 2007-04-28
Use Automatix.

---

### Post by inigmatus on 2007-04-29
Swiftfox is dead and the site is offline. Please read FYI here:

[http://ubuntuforums.org/showthread.php?t=427060](http://ubuntuforums.org/showthread.php?t=427060)

---

### Post by hyperair on 2007-04-29
I wonder if anybody will pick up after Swiftfox. If it really dead for good, I don't know how I'll survive without it.

---

### Post by dcstar on 2007-04-29
> **hyperair said:**
> I wonder if anybody will pick up after Swiftfox. If it really dead for good, I don't know how I'll survive without it.

Someone may post a HOWTO on how to compile your own version of Firefox optimised for your CPU - which is exactly what Swiftfox was/is.

---

