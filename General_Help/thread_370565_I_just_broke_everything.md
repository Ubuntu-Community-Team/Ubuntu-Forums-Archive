---
title: "I just broke everything"
date: 2007-02-25
forum: General Help
---

### Post by s|k on 2007-02-25
Okay so I've been using xubuntu, but then I did a dumb thing and did sudo apt-get install ubuntu-desktop which broke after it started depacking

The whole computer froze. I rebooted and it crashed. When it was depacking I saw it removed some xubuntu dependencies. Anyhow so I rebooted again and hit esc during grub loading and went into recovery mode and tried to apt-get remove ubuntu-desktop but apparently because dpkg was interrupted I'm screwed. If I do dpkg --configure -a as I am told to, the whole process freezes at 'Setting up gconf-editor (2.16.0-0ubuntu2). 

Do I have any other options besides reinstalling from scratch?

Thanks.

---

### Post by dcstar on 2007-02-25
> **s|k said:**
> Okay so I've been using xubuntu, but then I did a dumb thing and did sudo apt-get install ubuntu-desktop which broke after it started depacking

The whole computer froze. I rebooted and it crashed. When it was depacking I saw it removed some xubuntu dependencies. Anyhow so I rebooted again and hit esc during grub loading and went into recovery mode and tried to apt-get remove ubuntu-desktop but apparently because dpkg was interrupted I'm screwed. If I do dpkg --configure -a as I am told to, the whole process freezes at 'Setting up gconf-editor (2.16.0-0ubuntu2). 

Do I have any other options besides reinstalling from scratch?

Thanks.

Sometimes those steps can take a very long time, so I would wait (and check the CPU usage to make sure something is still happening) for a while before giving up on it.

---

