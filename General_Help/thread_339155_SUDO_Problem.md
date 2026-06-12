---
title: "SUDO Problem"
date: 2007-01-15
forum: General Help
---

### Post by Graham1 on 2007-01-15
Please help :(. All of a sudden, I can't logon as sudo anymore (from terminal, sudo -i). When I do and enter sudo's password, it returns me to the prompt & (not #). Any ideas what has gone wrong? I can't seem to access anything now ](*,).

:)

---

### Post by taurus on 2007-01-15
Any error (or output) if you run this from a terminal?

```
sudo aptitude update
```

---

### Post by earobinson on 2007-01-15
or even better run ```
sudo whoami
``` and post the output

---

### Post by Graham1 on 2007-01-15
> **taurus said:**
> ```
sudo aptitude update
```

Displayed "Password:". I entered my sudo password but the same thing (i.e back at $)

:)

---

### Post by Graham1 on 2007-01-15
> **earobinson said:**
> ```
sudo whoami
```

Tried this after the first suggestion but it just returned me back to the prompt.

:)

---

### Post by taurus on 2007-01-15
Paste the outputs of these commands here.

```
id
cat /etc/hostname
cat /etc/hosts
```

---

### Post by Graham1 on 2007-01-15
> **taurus said:**
> ```
id
cat /etc/hostname
cat /etc/hosts
```

user@tablet:~$ id
uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),1000(user)
user@tablet:~$ cat /etc/hostname
tablet
user@tablet:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
user@tablet:~$ 

:)

---

### Post by taurus on 2007-01-15
What happens to your /etc/hosts?  You also need to belong to group admin besides adm if you want to use sudo.  Right now, I bet your network is acting up too since there is something wrong with your /etc/hosts?

---

### Post by Graham1 on 2007-01-15
I'm not connected to any network (i.e other local computers). I go through a wireless router/firewall to the internet which is working fine. When I used SUDO before, I just typed "sudo -i" and the password and everything was fine. Not sure what happened between then and now :???:.

:)

---

### Post by taurus on 2007-01-15
Again, is the output that you included above the whole /etc/hosts?  It looks a little odd to me...

---

### Post by Graham1 on 2007-01-15
> **taurus said:**
> Again, is the output that you included above the whole /etc/hosts?  It looks a little odd to me...

That's all it outputs.

:)

---

### Post by taurus on 2007-01-15
Okay, we need to do two things.  We need to add your username to group admin in /etc/group so you can use sudo again and we need to fix your /etc/hosts.

Boot into recovery mode from GRUB menu and at the prompt, run

```
nano /etc/group
```
Scroll down until you see the line with "admin:x:114" and add your username to the end of it.  It would now look like this.

```
admin:x:114:user
```
Save it by holding down <Ctrl> while pressing x.  Type Y for yes and Return.

Next, edit /etc/hosts.

```
nano /etc/hosts
```
Delete everything in there right now and paste the following lines to it.

```

127.0.0.1       localhost
127.0.1.1       tablet

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Save the changes.  If not sure, paste the outputs of these two commands here so I can check before you reboot.

```
id
cat /etc/hosts
```

---

### Post by Graham1 on 2007-01-15
Back :D. Done the above and typing "id" now displays the following:-

uid=0(root) gid=0(root.

:)

---

### Post by taurus on 2007-01-15
When you are in the recovery mode, you are root so id will displays that output.  Run this then.

```
id user
```

---

### Post by Graham1 on 2007-01-15
> **taurus said:**
> ```
id user
```

user@tablet:~$ id user
uid=1000(user) gid=1000(user) groups=1000(user),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin)
user@tablet:~$

:)

---

### Post by taurus on 2007-01-15
And /etc/hosts still looks good, right?  Reboot and see if you, user, can use sudo again.

```
shutdown -r now
```

---

### Post by Graham1 on 2007-01-15
Actually, I had already rebooted and logged back in. Hosts file is fine and I can now logon with sudo :D. Do I need to undo any changes or am I ready to go?

:)

---

### Post by taurus on 2007-01-15
You are all set now.  ;)

---

### Post by Graham1 on 2007-01-15
Thank you so much for your help taurus. Not only have you fixed my system but I've learnt something too.

\\:D/

---

### Post by taurus on 2007-01-15
Glad to hear that you've learned something new too.  Enjoy your Ubuntu.

---

### Post by tf37 on 2007-01-18
Just joined today - many - many thanks.
Had the same problem, but I must have removed myself with a group, or user setting.](*,) 
This help me fix that :) 
too cool 8) 
Am like what I see in Ubuntu 6.10
Plus I found here how to fix my sound card issue - 
Thanks to you all for the great support & help given.
Terry

---

