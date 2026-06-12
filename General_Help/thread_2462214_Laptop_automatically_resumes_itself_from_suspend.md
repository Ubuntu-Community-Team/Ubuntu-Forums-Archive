---
title: "Laptop automatically resumes itself from suspend"
date: 2021-05-16
forum: General Help
---

### Post by burn-a-church on 2021-05-16
Hi,

Since upgrading to Kubuntu [FONT=monospace][COLOR=#000000]21.04, my laptop (Lenovo Thinkpad E595) resumes itself from suspended state automatically after a few hours.[/COLOR]
I always suspend my system overnight, and I was quite surprised that, when I wake up, the system is already on.
According to the syslog, the resume was triggered many hours earlier, when I was still sleeping.
That has happened for the **third time** now. Which makes suspend useless for me, unfortunately.

I attached the syslog from today.
I shut down the system at [FONT=monospace][COLOR=#000000]04:01:32[/COLOR].[/FONT]
It resumed itself at [FONT=monospace][COLOR=#000000]11:24:29
However, I only actually opened the lid at [FONT=monospace][COLOR=#000000]14:01:34[/COLOR]. Before that, it should not have been running.[/FONT]
[/COLOR]
After having the same problem yesterday, i had assumed the problem might be 'fwupd', because that was one of the earliest messages after the resume[FONT=monospace].
Therefore, I disabled that service. But that doesn't seem to have changed anything.

Syslog: https://pastebin.com/raw/rGpgc9uB
(I somehow couldn't upload it as an attachment)

[/FONT][/FONT] [/FONT]Any ideas what I could do about that?
I did not have that issue with Kubuntu 20.10.

Kind Regards,

---

### Post by juan-baptiste-0 on 2021-07-08
I have been having this issue too but on kubuntu 20.04, quite annoying !!

---

