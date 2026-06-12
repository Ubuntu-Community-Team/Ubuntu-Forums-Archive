---
title: "Pick a Firewall"
date: 2006-11-02
forum: General Help
---

### Post by CWBillow on 2006-11-02
I've been pretty satisfied in Windows relying on ZoneAlarm for my firewall protection, but this won't operate in Linux Os's...

So what do I do for the firewall fix?  Is there any free or reasonably priced alternative that can do the job?  Also, what about AV?

Regards,
Chuck Billow

---

### Post by boban on 2006-11-02
You already have firewall - iptables. But for easy configuration try firestarter (it's in repos).

I personally don't use AV under linux, but you can try clamAV...

---

### Post by CWBillow on 2006-11-02
K... thanks.

Chuck

---

### Post by ehird on 2006-11-02
Yeah, you don't really need either of those on Linux.

---

### Post by CWBillow on 2006-11-02
Now I wish I'd taken a "copy" of the article I was reading just this eve from CNet or ZDNet, that hackers et al have of late turned their gaze toward Linux installs... 

Or doesn't this apply here?  And how come not?  I would think that the same people that have learned to raise such problems everywhere else wouldn't be happy to just let Linux in all of it's flavors and permutations lay there undisturbed.

Regards,
Chuck Billow

---

### Post by Ramses de Norre on 2006-11-02
A firewall is certainly useful on a Linux system, but as said before it's already there and configured. You can install firestarter if you like to tweak the configuration a bit.

AV on the other hand isn't needed on Linux because there just aren't real Linux viruses (only a couple proof of concept ones). It's only useful to scan a drive shared with windows. (And it's still easier to scan from windows than.)

---

### Post by boban on 2006-11-02
> **CWBillow said:**
> Now I wish I'd taken a "copy" of the article I was reading just this eve from CNet or ZDNet, that hackers et al have of late turned their gaze toward Linux installs... 

Or doesn't this apply here?  And how come not?  I would think that the same people that have learned to raise such problems everywhere else wouldn't be happy to just let Linux in all of it's flavors and permutations lay there undisturbed.

Regards,
Chuck Billow

I think that this article you mention is nothing more than FUD. I occasionally read stuff like "new linux exploits", "attack on linux", etc. But always it turns out that either its clearly spreading FUD or there are some little prerequisite - like root privileges.

IMO - linux user base is still to low to attract hackers et al ;-), the security model that linux offers is very reliable and robust and linux users are (most of the time) knowing what they are doing :)

Nevertheless - one can never ignore security.

---

### Post by galileon on 2006-11-02
mainstream linux doesnt have an outbound firewall protection like windoze, although SELinux and Apparmor in SUSE have something like this...

but you dont have to worry about inbound connections, they are silently rejected...

---

### Post by CWBillow on 2006-11-02
>>
It's only useful to scan a drive shared with windows. (And it's still easier to scan from windows
<<
So a "Windows scan" of a drive will "see" and scan a Linux partition as well?

---

### Post by galileon on 2006-11-02
not usually...windoze uses a deprecated filesystem called ntfs...if you want it to support the superior ones used by linux, you'd need to install additional drivers (ext2/ext3)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

that way your windoze virus scanner can check ur linux partition for windoze virusses...

---

### Post by bionnaki on 2006-11-02
use a router.

---

### Post by CWBillow on 2006-11-02
Well, that's a nice change -- built-in protection etc... I'm just used to being paranoid...

---

### Post by CWBillow on 2006-11-02
> **galileon said:**
> 
[http://www.fs-driver.org/](http://www.fs-driver.org/)

that way your windoze virus scanner can check ur linux partition for windoze virusses...


Nice tip... thanks.

CB

---

