---
title: "cannot download attachment in gmail under firefox"
date: 2022-01-24
forum: General Help
---

### Post by centguy2 on 2022-01-24
i cannot download pdf attachment in gmail inside firefox browser.

The weird thing is that this happens to one Ubuntu machine but not the other.  Both machine has

the same 

uname -a 

5.13.0-27-generic #29~20.04.1-Ubuntu SMP Fri Jan 14 00:32:30 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


I remove .cache but problem still persists. How can it be so inconsistent?

---

### Post by TheFu on 2022-01-25
Are they running the same OS and same version of firefox installed from the same location?
Did you clone the settings from the working setup to the other one?
Does it work in safe-mode (that's a firefox startup option)?

---

### Post by centguy2 on 2022-01-25
Able to download gmail attachment system:

```

root@ubuntu-inspiron:~# uname -a
Linux ubuntu-inspiron 5.13.0-27-generic #29~20.04.1-Ubuntu SMP Fri Jan 14 00:32:30 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
root@ubuntu-inspiron:~# apt list --installed | grep firefox

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

firefox-locale-en/focal-updates,focal-security,now 96.0+build2-0ubuntu0.20.04.1 amd64 [installed]
firefox/focal-updates,focal-security,now 96.0+build2-0ubuntu0.20.04.1 amd64 [installed,automatic]

```

Unable to download gmail attachment system:

```


root@ubuntu40:~# uname -a
Linux ubuntu40 5.13.0-27-generic #29~20.04.1-Ubuntu SMP Fri Jan 14 00:32:30 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
root@ubuntu40:~# apt list --installed | grep firefox

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

firefox-locale-en/focal-updates,focal-security,now 96.0+build2-0ubuntu0.20.04.1 amd64 [installed]
firefox/focal-updates,focal-security,now 96.0+build2-0ubuntu0.20.04.1 amd64 [installed,automatic]


```

---

### Post by TheFu on 2022-01-26
> **TheFu said:**
> Are they running the same OS and same version of firefox installed from the same location?
Did you clone the settings from the working setup to the other one?
Does it work in safe-mode (that's a firefox startup option)?

I'll ask again ... 

Are they running the same OS?  The kernel is NOT the OS. What OS is used?
Did you clone the settings from the working setup to the other one?
Does it work in safe-mode (that's a firefox startup option)?

---

### Post by centguy2 on 2022-01-26
i thought my previous post clearly shows the uname -a output are exactly the same, that means the kernels are the same. Sorry I do not know what you are trying to get at.

If you insist the answers:

Are they running the same OS?  The kernel is NOT the OS. What OS is used?   Yes. Both systems are freshly installed and both have updated to the latest version using apt update; apt upgrade
Did you clone the settings from the working setup to the other one? No. I do not clone. In fact why would I clone? I am a simple user, i don't know how to clone firefox or firefox setting. I must have missed something from you again.
Does it work in safe-mode (that's a firefox startup option)? Sorry how to start in the safe-mode?  

If I am desperate to download the attachment, I would forward that email in gmail to my company Exchange inbox and using the same browser but different tab, I can download the pdf attachment. It is quite dumb this way.

---

### Post by TheFu on 2022-01-26
The same kernel can be used on different OS releases.  That was the question.  Which OS releases? Are those the same?  **lsb_release -a** can show it.

When *uname -a* was shown, I left the 'simple user' perspective. Sorry.  Firefox settings are binary compatible, so copying the stuff in ~/.mozilla/ from the working system to the non-working system will effectively clone all settings.  Ensure that firefox is NOT running on either system when you do this.  I'd use rsync, but it really shouldn't matter.  sftp would be fine.

firefox -safe-mode
Firefox has a manpage like most program on the system. These explain all options.
```
       -safe-mode
              Start firefox in safe-mode. This disables all third-party exten&#8208;
              sions,  and  may be necessary if you are having problems with an
              extension you installed.
```

There are likely some privacy defaults that got set in 1 setup, but not the other.

I good way to test if an issue is with the program, the system settings or a user-specific setting is by creating a new user, then login under that new user with all the default settings and try the task with the program.  

Another trick is to use a Try Ubuntu flash drive - that's just an install flash drive. Plug it in, boot is up and run firefox then try the same download. IF the program isn't installed, just install it in this environment. Anything installed will be gone. Nothing is saved.  You can make a flash drive that does save stuff, but I've never bothered.  A few tools do it - mkusb is one. There are others.

---

### Post by centguy2 on 2022-01-27
On the "problematic" firefox, the ubuntu has this:

```

root@ubuntu40:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

```

This is not giving any more information than   Linux ubuntu40 5.13.0-27-generic #29~20.04.1-Ubuntu SMP Fri Jan 14 00:32:30 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
?


Anyway,  from what you have described, I thought of a simple way.

Stop all firefox browsers.
mv .mozilla old.mozilla
restart firefox

Now, the attachment is downloadable!

So "evil"!!

Thanks for the hints!

---

### Post by TheFu on 2022-01-27
Use **lsb_release -a** to see which OS **BOTH** systems think they are running.  18.04 and 20.04 can have the same kernels, but they are very different OSes.
Here's an 18.04 OS:
```
$ uname -r
5.4.0-96-generic
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.6 LTS
Release:        18.04
Codename:       bionic

```
And here's a 20.04 release:
```
$ uname -r
5.4.0-96-generic
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal
```
Same kernel. Different OSes.

Regardless, **happy that you found the issue.**  It was the local settings that were different.  If you want them to be identical and have all addons, plugins, bookmarks, etc IDENTICAL between both systems, just clone those directories.  Running both instances side-by-side and checking through all the "settings", you may have found which setting is was.  My FF setups have lots of about:config changes, that aren't available through their GUI, to allow/prevent certain defaults.  

For example, I disable IPv6 on my systems and FF freaks out about that. There is a setting to force FF not to use IPv6, since (at least at the time), it wouldn't render any pages.  

FF has a few other settings meant to prevent accessing some specific ports that 99.99% of people don't need to access.  My BNC-Bouncer runs on a port that FF refuses to allow access, so I had to override it.  A BNC-bouncer is an IRC server that ensures I don't miss anything on a multitude of different IRC servers and channels just because my IRC client isn't running.  It is like a DNS cache server (which all Ubuntu systems have enabled by default), just for another old protocol, IRC.

No GUI page except about:config to alter these settings. Much easier to clone the working system onto my other workstations - Linux workstations, Linux laptops, BSD desktop, MacOS, and Windows. They all use the same cross-platform settings and data files. Addons that aren't compiled work between the systems too.  Most are just javascript, so those work on all the platforms.

You get the idea.

---

