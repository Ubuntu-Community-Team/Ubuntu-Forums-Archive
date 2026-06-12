---
title: "Log in Nightmare"
date: 2012-10-22
forum: General Help
---

### Post by frank cox on 2012-10-22
i have been using Lubuntu for several years w/ very  few problems but lately I reinstalled it on my laptop and a customers machine and it refuses to log on after a time . I have used the same user name -password on all my machines for years so it is correct and I have reinstalled 3 times and it will work for a day to a week and then refuse to log on.

---

### Post by offgridguy on 2012-10-22
Is it doing the same on both machines?

---

### Post by frank cox on 2012-10-22
> **offgridguy said:**
> Is it doing the same on both machines?

I reloaded the customers machine and it has worked for 3 days now. It is a pain to reinstall on the laptop as the DVD is fried. Until i get a new one I have to pull the drive and install from another machine
Thanks for replying

---

### Post by frank cox on 2012-10-22
Whan I dropped to a root shell it said root instead of my username

---

### Post by Cheesehead on 2012-10-22
> **frank cox said:**
> Whan I dropped to a root shell it said root instead of my username

That seems normal. The # shell is indeed the 'root' account, not the 'frank' account.


When it refuses your password, is your account still listed in /etc/passwd and /etc/shadow?
Add a second account with the same password. Are the hashes in /etc/shadow identical?

---

### Post by frank cox on 2012-10-22
> **Cheesehead said:**
> That seems normal. The # shell is indeed the 'root' account, not the 'frank' account.


When it refuses your password, is your account still listed in /etc/passwd and /etc/shadow?
Add a second account with the same password. Are the hashes in /etc/shadow identical?

No , with every Ubuntu distro I have ever used it gives the username when you drop to root prompt. How do I access  etc/passwd or etc/shadow if I can't boot?

---

### Post by mardybear on 2012-10-23
> **frank cox said:**
> No , with every Ubuntu distro I have ever used it gives the username when you drop to root prompt. How do I access  etc/passwd or etc/shadow if I can't boot?
Hi Frank...

My experience is similar, i use Ubuntu 10.04 and when using the root account in terminal it says root@grumpy-desktop (that's me).

If the DVD drive is fried you could alternatively boot from a USB stick (Ubuntu live, Puppy Linux, etc). Using a live boot like Puppy Linux should pretty much give you full 'control' of the system and let you to check/change your configuration files as needed.

mardybear

---

### Post by ~LoKe on 2012-10-23
If you're in the "root shell" you're using the root account on the system, not the user.  For example, on my PC I'm **n0c**@monkey.  If I go to a root shell, I'd be **root**@monkey.  They're two different accounts, and depending on how you installed the OS, they could have different passwords.

---

