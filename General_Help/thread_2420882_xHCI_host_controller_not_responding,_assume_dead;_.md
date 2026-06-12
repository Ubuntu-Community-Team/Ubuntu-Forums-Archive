---
title: "xHCI host controller not responding, assume dead; HC died; cleaning up"
date: 2019-06-12
forum: General Help
---

### Post by flucoe2 on 2019-06-12
After upgrading the kernel to 5.0.0-15-generic, my usb and bluetooth devices would randomly stop working. Re-attaching, or reconnecting bluetooth devices doesn't help. Only restarting the laptop would help to recover connections. However, after a week or so, even if all usb/bluetooth devices work, when I turn the laptop off, it just doesn't. Instead, it gives the following message: 


```
xHCI host controller not responding, assume dead
HC died; cleaning up

```
The laptop would not turn off and had to manually be turned off pressing the power button.

I have no idea what is going on so all suggestions are welcome. It happens with both Ubuntu 19.04 and Pop OS 19.04.

Thanks.

---

### Post by &amp;wP*!) on 2019-06-12
Give us the snapshot of /var/log/syslog for the new 5.0.0-15 kernel.
And then boot the system with the old kernel  and upload the /var/log/syslog here.
Without this information it is as difficult as playing chess with grandmother.

---

### Post by flucoe2 on 2019-06-12
Which part would be useful? The files are huge.

---

### Post by &amp;wP*!) on 2019-06-12
Especially when you get freeze, copy-paste the last 20-30 lines of each log - that should be ok.

You can use [https://pastebin.com/](https://pastebin.com/) which might be easier and faster than uploading text here.

The output of "lspci -nnvv" might be helpful as well.

---

### Post by flucoe2 on 2019-06-12
Thanks, here is the ouput

[lspci-nnvv]("https://pastebin.com/CDmHTcKa")

[Last 40 lines of /var/log/syslog with 5.0.0-15 kernel]("https://pastebin.com/c6MhGZNT")

[Last 40 lines of /var/log/syslog with 5.0.0-13 kernel]("https://pastebin.com/KKBR28PT")

---

### Post by &amp;wP*!) on 2019-06-13
Apparently NVIDIA driver is keeping your CPU busy in 5.0.0-15. This can be seen in the log.

There are 3 workarounds proposed here:
[https://askubuntu.com/questions/1035528/ubuntu-18-04-systemd-udevd-uses-high-cpu-conflict-with-nvidia-graphics](https://askubuntu.com/questions/1035528/ubuntu-18-04-systemd-udevd-uses-high-cpu-conflict-with-nvidia-graphics)

Can you give a try?

---

### Post by flucoe2 on 2019-06-13
Thanks. I removed the NVIDIA driver. So far, so good.

---

