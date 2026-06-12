---
title: "No more root. AHH!"
date: 2006-07-21
forum: General Help
---

### Post by Harold P on 2006-07-21
I just locked myself out of root permission (sudo).

```

harold@ubuntu:~$ sudo su
sudo: unable to lookup ubuntu via gethostbyname()
harold@ubuntu:~$

```

I edited my /etc/hosts file and changed ubuntu to box

```
harold@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost **box**
127.0.1.1 **box**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
harold@ubuntu:~$
```

but, since it's a file that must be edited by root, I can't change it back, and I'm pretty sure that's my problem. 

anyone have a clue on how to fix this?

---

### Post by simonn on 2006-07-21
> **Harold P said:**
> 
but, since it's a file that must be edited by root, I can't change it back,

Bootdisk?

---

### Post by Harold P on 2006-07-21
I thought about going on a live cd, mounting the drive, editing it back.

But, I just want to know if there's an easier approach.

---

### Post by aysiu on 2006-07-21
Boot into recovery mode.

---

### Post by Jucato on 2006-07-21
Have you tried rebooting? I think you have to reboot when you change hostnames. I'm not 100% sure.

---

### Post by Harold P on 2006-07-21
> **Fenyx said:**
> Have you tried rebooting? I think you have to reboot when you change hostnames. I'm not 100% sure.
Yep. I'll go into recovery mode and see what I should do from there.

---

### Post by Jucato on 2006-07-21
I meant just rebooting normally, without going to recovery mode.

---

### Post by ifokkema on 2006-07-21
> **Fenyx said:**
> I meant just rebooting normally, without going to recovery mode.
It's not the changing of the hostname that causes the problem, the problem is that the hostname doesn't match the entries in /etc/hosts, so that sudo won't work anymore.

---

### Post by Harold P on 2006-07-21
I had already rebooted before, but I had not tried recovery mode. 

After I went into recovery mode, I just did:

```
nano /etc/hosts
```

(didn't need sudo, because I'm root) and changed back what I had messed up.

---

### Post by 3rdalbum on 2006-07-21
I can't believe it, I'm not the only one who did something like this!

(mine was more difficult; I changed the hostname in the control panel and then in recovery mode it wouldn't let me get to the control panel! In the end I found the /etc/hostname file and put my original hostname back again :-)  )

---

### Post by ifokkema on 2006-07-22
If you want to change your hostname, FIRST change /etc/hosts and add your new hostname (link it to 127.0.0.1). DON'T remove the current hostname from that file yet. After that, you can change your hostname in /etc/hostname or using a GUI.

---

### Post by digitalchef on 2006-08-03
ok i have the same exact problem but im not very good with linux . if someone could plz help me throught the process i would greatly apricate it . thanks digitalchef

---

### Post by tim- on 2006-08-04
whenever i've changed it in the network configuration in gnome i've simply had to reboot and everything is ok...it always puzzled me why the system went haywire when changing the hostname (you'd think the gui would do it in a proper way not to break the system temporarily)

---

### Post by ifokkema on 2006-08-04
> **digitalchef said:**
> ok i have the same exact problem but im not very good with linux . if someone could plz help me throught the process i would greatly apricate it . thanks digitalchef

- Reboot the machine into Recovery mode.
- When booted, check the hostname of the PC.
```
cat /etc/hostname
```
- Then, make an entry in /etc/hosts to match your hostname.
```
nano /etc/hosts
```
Make a line that reads:
```
127.0.0.1       HOSTNAME
```
(HOSTNAME should be your hostname, read from /etc/hostname.)
- Reboot in normal mode, everything should now work.

In the future, when you want to change your hostname, first add an entry in /etc/hosts with your new hostname, then change it.

---

