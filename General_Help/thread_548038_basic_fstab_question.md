---
title: "basic fstab question"
date: 2007-09-10
forum: General Help
---

### Post by eponymous on 2007-09-10
ok i've tried as many things as i can find on the forums/google and still no luck.

in edgy i had my windows shares mounting on boot. now they only mount after boot using the mount command in terminal

if this like works, how do i translate it to fstab? share is RO in windows and i don't have a password....

```
mount -t smbfs \\192.168.1.x\Sharename \home\shares\MountPoint
```

thanks! this is getting really annoying. i don't reboot often but it should be so easy!

---

### Post by merlinus on 2007-09-10
Maybe try front slashes  instead of back slashes???

---

### Post by JKyleOKC on 2007-09-10
> **eponymous said:**
> 
if this like works, how do i translate it to fstab? share is RO in windows and i don't have a password....

```
mount -t smbfs \\192.168.1.x\Sharename \home\shares\MountPoint
```You may be running into a timing problem. This line won't work until Samba is running, and Samba can't run until your network is up. However fstab is often processed before these events take place!

Try adding your mount command to the /etc/rc.local script, just above the line that reads "exit 0" so that it's the very last thing executed before exit. The default rc.local doesn't have any other commands in it, but its purpose is to give you a chance to do things automatically at boot time after all the standard actions have taken place. You'll need to do "sudo mousepad" to edit the script with root privileges -- and be sure to change all those slashes to forward rather than reverse!

---

### Post by eponymous on 2007-09-12
> **JKyleOKC said:**
> You may be running into a timing problem. This line won't work until Samba is running, and Samba can't run until your network is up. However fstab is often processed before these events take place!

Try adding your mount command to the /etc/rc.local script, just above the line that reads "exit 0" so that it's the very last thing executed before exit. The default rc.local doesn't have any other commands in it, but its purpose is to give you a chance to do things automatically at boot time after all the standard actions have taken place. You'll need to do "sudo mousepad" to edit the script with root privileges -- and be sure to change all those slashes to forward rather than reverse!

haha yes those backslashes were not in my actual fstab, just mistyped when i posted. i'm a noob but i can at least look at the other mount instructions in fstab and emulate them.

trying this rc.local thing now.... thanks!

---

