---
title: "Should I be running antivirus software... and are you?"
date: 2006-08-08
forum: General Help
---

### Post by kbuel on 2006-08-08
I was just wondering how many of you run antivirus programs on your linux boxes.  I never have but am wondering if I should.  I've never heard of a linux virus's... but that doesn't mean there aren't any. Are there many out there and am I at risk?

Thanks for any input you all can give me!

---

### Post by jpkotta on 2006-08-08
I never have, and I haven't heard many recommendations to do so.  One of the strengths of Linux (at least right now anyway) is that you don't have to have AV software sucking up resources.  You should run a firewall, such as Firestarter, though.

---

### Post by aysiu on 2006-08-08
You're not at risk, and there aren't many out there.

Don't be stupid and do create strong passwords.

---

### Post by true_friend on 2006-08-08
but people like me who are using dual boot system may get virus in hdd and want to remove it throuhg manual scanning. antivirus may be required like panda antivirus.

---

### Post by hanzomon4 on 2006-08-08
You are in virtually no danger. There are some viruses that can infect linux, but I believe they were made by people who test software and OS for vulnerabilities (tell me if I;m wrong).. not people looking to actually infect real users

As far as whether or not you should run anti-virus software on Ubuntu/Linux?
Some people say that you should... because even though a virus can't do much to your linux system you could still pass viruses to windows users or your windows box if you dual boot.

I run anti-virus software because...

1.I want to be proactive.
2.Habit formed in windows
3.With out anti-virus software you probably wouldn't know if you had a virus

But honestly you don't NEED anti-virus software under linux... my 2 cents

---

### Post by hanzomon4 on 2006-08-08
> **jpkotta said:**
>   You should run a firewall, such as Firestarter, though.

Thats true, but firestarter is just a front-in to iptables

The linux kernel has a firewall built-in (iptables), on Ubuntu it allows all traffic by default, but your're still safe because you have no services, like ssh, that use ports by default (Correct me if I'm wrong).. except internet stuff.

You can configure iptables with firestarter, but you can also do it by hand.
Doing by hand may seem hard at first, but I think doing it in this way teaches you more about security and gives you better control.

here's a link to a howto on configuring iptables by frodon [ HOWTO: Set a custom firewall (iptables) and Tips]("http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables")

---

