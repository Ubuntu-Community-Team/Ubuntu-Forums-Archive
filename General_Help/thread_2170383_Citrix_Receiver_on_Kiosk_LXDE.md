---
title: "Citrix Receiver on Kiosk LXDE"
date: 2013-08-26
forum: General Help
---

### Post by f0olyc0oly on 2013-08-26
Hi,

I created a user account and had it auto login. I removed the write access (chmod 555) to home directory so that I can disable the saving of files of user.
Problem is when I clicked on the Citrix Receiver, it won't open.

I edited the permission again (chmod 775) to let the user have write access and voila Citrix Receiver was able to open.
Any idea on how to retain the no write access to the home directory and still be able to run Citrix Receiver?

I checked the permission of the .ICAClient folder, it's still the same with or without the write access.

Cheers and regards.

---

### Post by rai_shu2 on 2013-08-26
Removing write access does make life very difficult for any given application I can think of. Probably the best you could do would be to mount your $HOME to RAM, although I've never actually tried that. You'd have to add a line to /etc/fstab like:

```
tmpfs           /home/kiosk    tmpfs   defaults        0       0
```

---

### Post by f0olyc0oly on 2013-08-26
> **rai_shu2 said:**
> Removing write access does make life very difficult for any given application I can think of. Probably the best you could do would be to mount your $HOME to RAM, although I've never actually tried that. You'd have to add a line to /etc/fstab like:

```
tmpfs           /home/kiosk    tmpfs   defaults        0       0
```

may i ask what would this do?

also, i'm just trying to find out what folder inside the /home/<user> would the Citrix Receiver need in order for it to work? :(

---

### Post by Kevin_Arnold on 2013-08-26
Most applications write data to hidden files in your home folder. Putting it in memory would make everything reset when the computer is rebooted.  

But, you could just find the hidden file that the citrix client uses and make it writable and then the rest of the directory read only.

Type
```
 ls -al 
``` 
At ~ and see if the are any citrix files or folders.

---

### Post by f0olyc0oly on 2013-08-26
> **Kevin_Arnold said:**
> Most applications write data to hidden files in your home folder. Putting it in memory would make everything reset when the computer is rebooted.  

But, you could just find the hidden file that the citrix client uses and make it writable and then the rest of the directory read only.

Type
```
 ls -al 
``` 
At ~ and see if the are any citrix files or folders.

I checked the user directory without the write permission and another directory which has a write permission. It has the same permissions for all the folder except this one. **.gvfs**

**Without write permission**
```
d?????????  ? ?           ?           ?           ? .gvfs
```

**With write permission**
```
drwx------ 1 connect connect  4096  Aug 8 19:09 .gvfs
```

---

### Post by rai_shu2 on 2013-08-27
What exactly is flagging $HOME as read-only supposed to fix? Maybe there's another approach you could use that would prove to be more convenient than even putting it in RAM.

---

### Post by Kevin_Arnold on 2013-08-27
It sounds like the OP basically wants a kiosk that is only for the citrix client. The OP doesn't want people to use the machine to actually save stuff or use it like a regular computer. Correct me if I'm wrong.

---

### Post by rai_shu2 on 2013-08-28
The thing is, a computer is a device that moves data. That's the whole point. Preventing one piece of hardware or another from operating is just masking the issue. I'm wondering what the REAL issue is.

---

