---
title: "[SOLVED] Holding Back a Package"
date: 2007-07-22
forum: General Help
---

### Post by arsenic23 on 2007-07-22
Ok, so the newest wine update broke a lot of things for me and I decided to role back to the previous version and hold it there. Rolling back to the previous version with apt was easy enough, but then I needed to stop it from updating it every time I update.  Unfortunately the apt-get man and the actual layout of my /etc/apt folder differ a fair bit.  So after looking around /etc/apt/apt.conf.d for a while I changed the contents of *50unattended-upgrades* by adding a line that I thought would keep if from installing new versions of wine, like so:

```
// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu feisty-security";
//      "Ubuntu feisty-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//      "vim";
        "wine";
};

```

This doesn't seem to work, so I'm going to have to ask;  What is the correct way to hold back updates to a package?

---

### Post by arsenic23 on 2007-07-22
Ok, I found out that this doesn't work because *50unattended-upgrades* does not do what I thought it did.  I still haven't figured out how to stop wine from updating with everything else.

---

### Post by laidback on 2007-07-22
In Synaptic there's Package>Lock Version...does this help?

---

### Post by arsenic23 on 2007-07-22
> **laidback said:**
> In Synaptic there's Package>Lock Version...does this help?
Thanks alot, it never occured to me to even startsynaptic, in fact I've never used it.
I did eventually find what I was looking for here:
[https://answers.launchpad.net/ubuntu/+question/9434](https://answers.launchpad.net/ubuntu/+question/9434)

But now I have two ways to do it, thanks.

---

