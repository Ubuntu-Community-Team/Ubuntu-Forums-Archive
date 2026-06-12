---
title: "Ubuntu 14.04 LTS having problem with Brightness and Touchpad hotkey."
date: 2015-04-22
forum: General Help
---

### Post by priyabrata-chak on 2015-04-22
[HR][/HR]I've installed Ubuntu 14.04 on my IdeaPad Z570 Laptop.
Initially, when the system is fresh, all hot-keys except the brightness control was working perfectly fine.

I went through various solutions threads in this forum and stack-over and finally got the brightness control to work with :

```
sudo sh -c 'echo "blacklist ideapad_laptop" >> /etc/modprobe.d/blacklist.conf'
```

After I did a reboot, everything works fine and suddenly I realised that Fn+F6 which is a hotkey to enable/disable touch pad {which was working before } isn't working now.

This is getting really frustrating and looking forward to a solution to this problem.

Best Regards
Priyabrata

---

