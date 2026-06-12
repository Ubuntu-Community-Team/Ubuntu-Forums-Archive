---
title: "Slow boot (used to be faster)"
date: 2018-12-13
forum: General Help
---

### Post by fynn-boeltau on 2018-12-13
Hello all,
i somehow have the problem that Ubuntu 16.04 takes a longer time than it used to take to boot.

Here is my dmesg output: [https://pastebin.com/BVum36Fh](https://pastebin.com/BVum36Fh)
Best,
fntastic

---

### Post by DuckHook on 2018-12-13
Welcome to the forums, fynn-boeltau.

Have you changed your physical configuration? Did you disconnect or turn off Bluetooth?

Please post output of:```
systemd-analyze blame
```

---

### Post by fynn-boeltau on 2018-12-14
No i haven't, i have however changed the size of my windows dual boot partition, but i think that was after the slow boot occured.

```
          7.561s NetworkManager-wait-online.service
          1.939s fwupd.service
          1.160s dev-sda5.device
           737ms snapd.service
           467ms dev-loop9.device
           464ms dev-loop11.device
           458ms dev-loop10.device
           457ms dev-loop8.device
           455ms dev-loop12.device
           416ms dev-loop13.device
           410ms dev-loop5.device
           399ms dev-loop7.device
           398ms dev-loop6.device
           243ms apparmor.service
           178ms upower.service
           149ms binfmt-support.service
           142ms dev-loop4.device
           126ms dev-loop1.device
           126ms dev-loop2.device
           120ms console-setup.service
           119ms networking.service
           118ms dev-loop3.device
           116ms dev-loop0.device

```

Thanks for your help!

---

### Post by DuckHook on 2018-12-14
According to this output, your boot isn't slow. Perhaps we should start with some definitions: what do you mean by slow. Please actually measure and quantify in seconds.

---

### Post by fynn-boeltau on 2018-12-16
It now takes 1min 45sec from grub to login screen.
Used to be <30sec. I do have an SSD.
Best, Fynn.

---

### Post by jeremy31 on 2018-12-16
Is the bluetooth plugged into a USB port,  I would remove it for boot if possible

---

### Post by fynn-boeltau on 2018-12-16
I don't have an external bluetooth device, I will try to turn off Wifi/Bluetooth during boot now and report back in.

edit: makes it faster by ~2 sec.

---

### Post by jeremy31 on 2018-12-16
upload new dmesg please

---

### Post by fynn-boeltau on 2018-12-16
[https://pastebin.com/QwNPs3LC](https://pastebin.com/QwNPs3LC)

---

### Post by jeremy31 on 2018-12-16
Do a ```
sudo -H gedit /etc/default/grub
```

Find the line with "quiet splash" and change it to "quiet splash ipv6.disable=1"
Then in terminal ```
sudo update-grub
```
Reboot

---

### Post by fynn-boeltau on 2018-12-16
this unfortunately did not fix it...

---

### Post by fynn-boeltau on 2019-01-07
*push*

---

### Post by fynn-boeltau on 2019-04-28
As the problem is still not fixed yet, I'd like to push another time.

---

