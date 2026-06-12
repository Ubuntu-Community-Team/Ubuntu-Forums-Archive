---
title: "How does Ubuntu decide when to apply downloaded security updates?"
date: 2016-04-19
forum: General Help
---

### Post by unflavored on 2016-04-19
I have automatic daily security updates enabled. Sometimes, like today, I manually check updates and there are security updates ready, already downloaded, and not installed. How does Ubuntu decide when to install them? Are there any relevant configuration files?

---

### Post by sammiev on 2016-04-19
Hi,

In your software settings you can choose what you want done when a security update is available.

---

### Post by unflavored on 2016-04-19
Yes I've done that, it's set to daily download and install automatically. But it doesn't install immediately upon download. I don't know how long these security updates were waiting to install, probably just a few hours, but I'd like to make them install immediately. That's what I think "automatically" ought to do.

---

### Post by sammiev on 2016-04-19
Hi,

What version of Ubuntu are you using?

There is a difference between Install Immediately and download and install automatically.

Check the settings again.

---

### Post by unflavored on 2016-04-19
14.04. The settings are checked.

---

### Post by grahammechanical on 2016-04-19
I think it depends on what we define as "security updates." The Ubuntu developers may have a more narrow definition than you. Most security fixes are in response to the discovery of a vulnerability that had the potential to become an attack vector but without actually being used as an attack vector. I think that a lot would depend on how urgent the need for the security fix to be passed out to the user is.

Here is a recently list of Updates & security.

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue462#Updates_and_Security_for_12.04.2C_14.04_and_15.10](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue462#Updates_and_Security_for_12.04.2C_14.04_and_15.10)

Regards.

---

### Post by unflavored on 2016-04-19
> **grahammechanical said:**
> I think it depends on what we define as "security updates." The Ubuntu developers may have a more narrow definition than you.  No, I mean these are the updates marked as security updates when I run Software Updater. I just want to know if there's a way to make them install as soon as they download, instead of waiting for whatever Ubuntu is waiting for.

---

### Post by unflavored on 2016-04-19
It's [USN-2950-1](http://www.ubuntu.com/usn/usn-2950-1/) I'm talking about. That came out yesterday, but I manually check for updates today and they are just sitting there, already downloaded, not installed yet.

---

### Post by unflavored on 2016-04-20
Something in /etc/apt/apt.conf.d/ maybe?

---

### Post by Bucky Ball on 2016-04-20
If you reboot the machine are they still sitting there waiting to install?

---

### Post by unflavored on 2016-04-20
> **Bucky Ball said:**
> If you reboot the machine are they still sitting there waiting to install?  That's a good question, I didn't think to try it but I will next time.

---

