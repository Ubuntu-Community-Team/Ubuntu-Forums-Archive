---
title: "Xubuntu 13.04, blank screen on installation"
date: 2013-10-15
forum: General Help
---

### Post by han2 on 2013-10-15
Hello,

When trying to install Xubuntu 13.04 using a USB installer I get a blank screen. I can't even access the "live cd / installation" screen. I've tried the same USB installer on my HP 6720 laptop and it works flawlessly.

I'm assuming the problem is related to the Nvidia GT610 I have on my desktop computer.

Any ideas?

Regards.

---

### Post by TheFu on 2013-10-15
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by sudodus on 2013-10-15
You can try some boot options. I suggest you start with ***nomodeset***. See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by han2 on 2013-10-15
Thanks, sudodus and TheFu. I'll check it.

Edit: It worked with nomodeset and vga=791.

Regards.

---

