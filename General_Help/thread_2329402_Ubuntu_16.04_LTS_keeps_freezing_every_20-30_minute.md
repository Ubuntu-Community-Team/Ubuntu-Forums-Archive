---
title: "Ubuntu 16.04 LTS keeps freezing every 20-30 minutes"
date: 2016-07-01
forum: General Help
---

### Post by miyupon on 2016-07-01
Hi there. I'm not completely new to Linux, I had Ubuntu installed back when Gutsy Gibbon was released and also had Debian installed. Decided to install Ubuntu again because Win10 kept annoying me.

Anyway, it's not working well. Ubuntu keeps freezing on me like every 20-30 minutes. There's no pattern here as far as I can see. Once it crashed when typing in an URL, once when making a call in Skype, once when configuring the Unity Launcher and so on. I have not mounted any drives, I've unplugged my HDMI cable from my TV, but nothing helped. I guess it might be a driver issue, but where do I even begin to look? I'm pretty sure my hardware is fine, since I haven't had issues like that in Win10. I also tried an older kernel, that I could chose under the advanced boot options, but this didn't help either. 

I have an intel CPU and GPU. It's an Acer ES1-711 notebook.

I know this is not a lot to work with, but I hope someone can help me out.

---

### Post by TheFu on 2016-07-02
Check the log files.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
They are your only hope, padawan.

Just because Windows works with some hardware, doesn't mean it is good.  Windows is well-known for ignoring hardware issues until it really breaks - damn the loss of data!

The only time I've seen NOTHING in log files and had lock ups was when all memory (real and virtual) was full.  How much RAM and swap does the system have?  6G plus combined?

---

