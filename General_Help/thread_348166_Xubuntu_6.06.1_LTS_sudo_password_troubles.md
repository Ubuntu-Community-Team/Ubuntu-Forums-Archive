---
title: "Xubuntu 6.06.1 LTS: sudo password troubles"
date: 2007-01-28
forum: General Help
---

### Post by jolyqr on 2007-01-28
Hello

I have recently installed Xubuntu 6.06.1 LTS on my lap top.
Things were doing well till I attempted to access my wireless internet connection, by running the "network-admin" application.

Since that day, it's completely impossible for me to access applications that are inside the "System" folder (applications that need a password to be run)

When I type the right password, the system displays the following message :

"The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key

I've got the above message when the password is correct !!

When I type on my purpose a wrong password, the following message is displayed :

"Failed to run network-admin
Wrong password"

I don't understand anything.
I have even changed my password, but the problems remains...
Is that possible to remove the password prompting message from the system applications?

Tell me what you think about that problem...

Cheers !!

---

### Post by taurus on 2007-01-28
Can you post the output of these two files from a terminal here?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by jolyqr on 2007-01-28
> **taurus said:**
> Can you post the output of these two files from a terminal here?

```
cat /etc/hostname
cat /etc/hosts
```


If you're referring to the error messages, they'are displayed on some kinds of graphical pop up windows (similar to those from Windows OX)...

---

### Post by taurus on 2007-01-28
Can you post the contend of those two files here?

---

### Post by jolyqr on 2007-01-28
> **taurus said:**
> Can you post the contend of those two files here?

I'm pretty new in Linux world, I don't really know how to do it...

---

### Post by taurus on 2007-01-28
Open a terminal, Applications -> Accessories -> Terminal, and type in each command.  Paste the output of the first command here and then run the second command and paste the output of that second command here as well.

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by jolyqr on 2007-01-28
> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, and type in each command.  Paste the output of the first command here and then run the second command and paste the output of that second command here as well.

```
cat /etc/hostname
cat /etc/hosts
```


cat /etc/hostname :
UbuntuBostek

cat /etc/hosts
127.0.0.1 localhost UbuntuBosstek
127.0.0.1 UbuntuBosstek

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhosts ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by taurus on 2007-01-28
> **jolyqr said:**
> cat /etc/hostname :
UbuntuBostek

cat /etc/hosts
127.0.0.1 localhost UbuntuBosstek
127.0.0.1 UbuntuBosstek

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhosts ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Okay, I think here is your problem.  The name in /etc/hostname (UbuntuBostek) is not the same as in /etc/hosts (UbuntuBosstek).  Therefore, you need to boot into recovery mode from GRUB menu and edit your /etc/hosts.

```
nano -w /etc/hosts
```
Make your /etc/hosts to look like this.

```

127.0.0.1 localhost
127.0.1.1 UbuntuBostek

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhosts ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Exit it by holding down <Ctrl> while pressing x.  Then save it with Y and Return.

Now, reboot your machine with

```
shutdown -r now
```
Log in with your name and password and open a terminal, Applications -> Accessories -> Terminal, and see what happens when you run this command.

```
sudo aptitude update
```

---

### Post by jolyqr on 2007-01-28
> **taurus said:**
> Okay, I think here is your problem.  The name in /etc/hostname (UbuntuBostek) is not the same as in /etc/hosts (UbuntuBosstek).  Therefore, you need to boot into recovery mode from GRUB menu and edit your /etc/hosts.

[...........]




Sorry, I forgot to tell you that my lap top can't access the internet because of those troubles. 
So i have copied the messages from my laptop terminal and wrote them by hands.
I made a mistake, I should have written "UbuntuBosstek".... There is no problem on them, they're both identical.

---

### Post by taurus on 2007-01-28
But look at the first two lines in /etc/hosts again!  See how I removed the UbuntuBosstek from the first line and changed the number on the second line to 127.0.1.1.

---

### Post by jolyqr on 2007-01-28
> **taurus said:**
> But look at the first two lines in /etc/hosts again!  See how I removed the UbuntuBosstek from the first line and changed the number on the second line to 127.0.1.1.


I have removed the "UbuntuBosstek" from the 1st line.
The second line was my mistake, this was already correct.

As i don't have any Internet connection, do I need to type the following : sudo aptitude update ?

I went to the system folder, the problem is still there...

---

### Post by jolyqr on 2007-01-28
I think the best solution would be to remove the password prompt from accessing those programs, but I don't know if this is possible...

---

