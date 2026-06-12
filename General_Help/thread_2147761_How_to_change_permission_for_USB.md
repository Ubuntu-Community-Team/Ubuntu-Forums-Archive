---
title: "How to change permission for USB"
date: 2013-05-23
forum: General Help
---

### Post by VeryFoggy on 2013-05-23
Somehow I turned off the "your hard drive is getting full" warning, and I filled that puppy up. The final moments reminded me of the scene in A.I. where the android boy starts eating, and then slowly shuts down, and there is nothing you can do to stop it. 

I pulled the drive, and have hooked it up to a working ubuntu computer as a USB drive. It is totally full, and I need to delete the files, or back them up. It will let me have read only access to about half the files, but it won't let me access the ones that it says are protected.

How do I get access to my files?

---

### Post by fj401971 on 2013-05-23
I believe what you're looking for is the the "chown" command...

```
chown user:group -R /media/harddrive/ 
```

where user is username; group is most likely username again; harddrive is location of usb drive;
[http://linux.die.net/man/1/chown]("http://linux.die.net/man/1/chown")

---

### Post by fj401971 on 2013-05-23
Or if the ownership is correct, then you're going to need to use the "chmod" command...

```
chmod u+rw -R /media/harddrive
```

For more details type the following in a terminal: 
```
man chmod
```

---

### Post by VeryFoggy on 2013-05-23
Getting closer to a solution. Used the line:

chown ubuntu:ubuntu -R /media/f3a2dd5b-2f4c-4008-89d1-5c76dd102162

Repeatedly got "Operation not permitted" in response


[ATTACH=CONFIG]242930[/ATTACH]

---

### Post by Topsiho on 2013-05-23
As this is a system command, which should be executed by root, you should put sudo in front of the command, and give your password when asked for.

Topsiho

---

### Post by VeryFoggy on 2013-05-23
Putting sudo in front worked. 

Thank you all.

---

### Post by Topsiho on 2013-05-23
Great.

Thank you for reporting this ...

Topsiho

---

