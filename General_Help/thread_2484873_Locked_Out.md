---
title: "Locked Out"
date: 2023-03-13
forum: General Help
---

### Post by Daveski17 on 2023-03-13
Hello, I've locked myself out of my new StarLite 11-inch Ubuntu Linux Mini coreboot Laptop. I don't recall making a password. I've had three strokes, so I'm not cognitively all there lol. How do I get back in to my new notebook? Thanks.

---

### Post by yancek on 2023-03-13
Is this an OEM install with Ubuntu installed when you purchased the laptop?  If it was an OEM install there was no password and you should have been prompted to set one.  If you did not do or see that, go to the link below for instructions on how to do it.

[https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password/24024#24024](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password/24024#24024)

What happens when you try to boot?  Do you get to a log in screen where you are prompted to select a user and possibly enter a password?

---

### Post by Daveski17 on 2023-03-13
> **yancek said:**
> Is this an OEM install with Ubuntu installed when you purchased the laptop?  If it was an OEM install there was no password and you should have been prompted to set one.  If you did not do or see that, go to the link below for instructions on how to do it.

[https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password/24024#24024](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password/24024#24024)

What happens when you try to boot?  Do you get to a log in screen where you are prompted to select a user and possibly enter a password?

Thanks for the reply. Yes, it was purchased new with Ubuntu installed. I wasn't prompted to set a password as far as I recall. I just get a log-in screen. Thanks for the link.

---

### Post by MAFoElffen on 2023-03-13
Does it ever get to a Grub2 Boot menu on startup if you intermittently hit the esc or the left shift key during the boot up?

If so, then you could reset the password from a root prompt (after enabling networking, which also mounts the filesystem).

---

### Post by yancek on 2023-03-14
Did you purchase it from an individual or from a company which sells computers with Ubuntu preinstalled?
When you boot Ubuntu, do you see a screen with a user name at the log in page?  If so, is this a user you created?  You would need a password for this user and you would have needed to create it.  You can log in without a password but the user created would still need to have a password.   The first user created generally has root (sudo) permissions.  If you did not do this, have you been able to boot and log in at any time?

The suggestion above to reset the root (primary user) password.  Lots of sites with instructions on how to do this.

---

### Post by maglin2 on 2023-03-14
I bought a Star Lite back in 2020.
It came with Ubuntu OEM pre-installed and behaved as described by yancek in #2
(It's an eminently portable device and my choice was to do a fresh full disc encryption install over it though).

The suppliers are StarLabs [https://starlabs.systems/#](https://starlabs.systems/#)
I've always found their support very responsive and helpful. It might be simplest to have a chat with them.

---

### Post by Daveski17 on 2023-03-14
> **MAFoElffen said:**
> Does it ever get to a Grub2 Boot menu on startup if you intermittently hit the esc or the left shift key during the boot up?

If so, then you could reset the password from a root prompt (after enabling networking, which also mounts the filesystem).

I'll try that, thanks.

---

### Post by Daveski17 on 2023-03-14
> **maglin2 said:**
> I bought a Star Lite back in 2020.
It came with Ubuntu OEM pre-installed and behaved as described by yancek in #2
(It's an eminently portable device and my choice was to do a fresh full disc encryption install over it though).

The suppliers are StarLabs [https://starlabs.systems/#](https://starlabs.systems/#)
I've always found their support very responsive and helpful. It might be simplest to have a chat with them.

Thanks I appreciate the info.

---

