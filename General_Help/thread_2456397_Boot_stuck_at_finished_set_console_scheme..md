---
title: "Boot stuck at: finished set console scheme."
date: 2021-01-11
forum: General Help
---

### Post by uv0 on 2021-01-11
I am using raspberry pi 4 4gb ram. I installed ubuntu server 20.04 on it it worked fine. On that i install kubuntu-desktop. It downloaded completely, installed all components and then after 5 min i rebooted it. The boot is stuck at output.

    Starting set console scheme. 
    Finished terminate plymouth boot screen. 
    Started LSB: automatic crash report generation. 
    Finished set console scheme. 
Please see image for complete console output.

[IMG]https://i.stack.imgur.com/MpyK4.jpg[/IMG]

Please help.

---

### Post by agvantibo on 2021-01-12
Let it sit for an hour - it will right itself out.
Connect it to the Internet (Ethernet) and just let it cloud-init.

It worked for me, and should for you.

After it boots, share what does systemd-analyze report. You will see what happened, and took so long. Also try dmesg and journalctl.

---

### Post by uv0 on 2021-01-15
How to manually start sddm and kde-plasma-desktop. 
systemd is broken when i boot each time and try to start manually it says systemctl: command not found. 
I have to reinstall systemd then systemctl starts but for
systemctl start sddm
Screen blinks and again to terminal. 
I will try what u told n get back

---

### Post by uv0 on 2021-01-16
No effect kept it for 2 hours

---

### Post by deadflowr on 2021-01-17
sddm might be problematic on a pi.
Look at this for a possible solution or some momentum:
[https://github.com/wimpysworld/desktopify/issues/19]("https://github.com/wimpysworld/desktopify/issues/19")

---

