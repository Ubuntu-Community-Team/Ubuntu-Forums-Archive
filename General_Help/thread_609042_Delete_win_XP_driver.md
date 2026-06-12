---
title: "Delete win XP driver"
date: 2007-11-10
forum: General Help
---

### Post by harveyphillips on 2007-11-10
Can Ubuntu or other Linux distro  be used to find a Windows XP Trojan Horse and delete it? 

I know where the file is located: c:\windows\ system32\drivers\wiki.sys; AVG virus checker found wiki.sys but can't delete it, can't even quarantine it. Windows won't delete it.

Suggestions?

Harvey

---

### Post by markusf21 on 2007-11-10
Shouldn't be too hard. This is how I would do it.
1. ```
sudo apt-get install ntfs-config
```
2. Applications --> system tools --> ntfs configuration tool
3. check appropriate box and click OK
Now you can read and write to your windows partition
4. Places --> Computer and find your windows partition
5. Navigate to the file and delete it

---

### Post by oilchangeguy on 2007-11-10
> **harveyphillips said:**
> Can Ubuntu or other Linux distro  be used to find a Windows XP Trojan Horse and delete it? 

I know where the file is located: c:\windows\ system32\drivers\wiki.sys; AVG virus checker found wiki.sys but can't delete it, can't even quarantine it. Windows won't delete it.

Suggestions?

Harvey

you say windows won't delete it. what did you do to try? also turn off system restore, your internet connection. and reboot the computer, and see if avg will delete it then. or from my computer open the c: drive and locate the file, you should be able to delete from there.

---

### Post by harveyphillips on 2007-11-13
Did I get to Markusf21?  Hopefully so.  Sounded like a nice simple solution. Problem is I don't know where to key-in the code

Harvey

---

### Post by markusf21 on 2007-11-18
in the terminal
Applications --> Accessories --> Terminal
Or just use Synaptic under System --> Administration

---

