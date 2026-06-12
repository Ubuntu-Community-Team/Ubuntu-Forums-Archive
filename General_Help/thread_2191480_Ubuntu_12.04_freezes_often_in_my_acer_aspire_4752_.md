---
title: "Ubuntu 12.04 freezes often in my acer aspire 4752 laptop"
date: 2013-12-02
forum: General Help
---

### Post by giridharanbtech on 2013-12-02
I'm using ubuntu 12.04 for more than 6 months. But my ubuntu freezes way too often. My cursor not moving at all. 

Because of this problem I had to hard reboot my system often. 

So can anyone tell me whats wrong with my system? 

Here is my details

```

giri@ubuntu:~$ sudo uname -a
Linux ubuntu 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```


```
giri@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

```

Memory : 5.6 GiB
Processor : Intel® Core&#8482; i3-2350M CPU @ 2.30GHz × 4 
Graphics : Unknown
OS Type : 64-bit
Disk : 116.8 GB

---

### Post by ranger1021994 on 2013-12-02
Check your autostart applications
It is likely an application maybe causing that
Or maybe some flawed setting.

---

### Post by 1991sudarshan on 2013-12-03
I use ubuntu 12.04 in my acer apire one D257 netbook. I face the same problem. But my ram is just 1GB. You have 5.6 GB , that should do well. Unity takes up lot of memory and firefox too. Why don't use fluxbox for a while. It is minimalistic and works very efficiently. Could you please tell us using what kind of application makes your distros get frozen? ```
sudo apt-get install fluxbox
```

---

### Post by slooksterpsv on 2013-12-03
Go to a tty ALT+F1 or ALT+F2 and login and run top to see what's running in the background.

---

### Post by giridharanbtech on 2013-12-03
I don't think it has anything to do with setting and autostart apps. Because this problem appears even in fresh ubuntu install.

---

### Post by giridharanbtech on 2013-12-03
> **slooksterpsv said:**
> Go to a tty ALT+F1 or ALT+F2 and login and run top to see what's running in the background.

Actually my keyborad keys not working at all when ubuntu get frozen

---

### Post by slooksterpsv on 2013-12-03
Next time you reboot look at the log files in /var/log - there may be something going on that it's causing the kernel to panic - such as a faulty video driver.

---

### Post by ranger1021994 on 2013-12-20
> **giridharanbtech said:**
> I don't think it has anything to do with setting and autostart apps. Because this problem appears even in fresh ubuntu install.

I had a problem similar to this but my cursor moved.
It turned out that gnome-screensaver was causing this
I uninstalled it and replaced it with xscreensaver.


At boot, you can try going to tty1 by pressing CTRL+ALT+F1 and then login
Try this ```
watch -n1 "ps aux > ~/Desktop/ps.txt"
```

The above command will list every process running on the system and output it to a text file by the name of ps.txt
"watch -n1" will make sure this command runs every second

You can analyze the ps.txt and see which program was running right before Ubuntu became non responsive

---

