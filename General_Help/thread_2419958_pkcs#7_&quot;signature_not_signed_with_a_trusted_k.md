---
title: "pkcs#7 &quot;signature not signed with a trusted key&quot;"
date: 2019-05-27
forum: General Help
---

### Post by anderbuntu on 2019-05-27
Hi

Today I received below error during boot and SYstem not booted to KDE, system waiting for login credentials from terminal...

OS: Kubuntu 18.04
[I]
I was googling around and seems its related to Secure boot, but no HW change was made...[/I]

Any advice ?

Secure boot is turned OFF also.

A.

---

### Post by CatKiller on 2019-05-27
I don't think that message is related; I think it's just the last message displayed.

You aren't clear on your symptoms. Has the boot hung, or is it that your graphical login isn't being launched?

---

### Post by anderbuntu on 2019-05-28
Hi 

Yes, just GUI not started, here is my output>
Only thing I installed before was app :  firejail, not sure if its related

Here is full output from console :

Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 4.18.0-20-generic x86_64)
* Documentation: [https://help.ubuntu.com](https://help.ubuntu.com) * Management: [https://landscape.canonical.com](https://landscape.canonical.com) * Support:
[https://ubuntu.com/advantage](https://ubuntu.com/advantage)
* Ubuntu's Kubernetes 1.14 distributions can bypass Docker and use contai
directly, see [https://bit.ly/ubuntu-containerd](https://bit.ly/ubuntu-containerd) or try it now with
snap install microkas --classic
* Canonical Livepatch is available for installation. - Reduce system reboots and improve kernel security. Activate at:
[https://ubuntu.com/livepatch](https://ubuntu.com/livepatch) userluser: $ [ 39.767066] PKCS#7 signature not signed with a trusted ke [ 39.808108) PKCS#7 signature not signed with a trusted key [ 39.816389) PKCS#7 signature not signed with a trusted key [ 39.8223051 PKCS#7 signature not signed with a trusted key
1
user@user :$ sudo su [sudo] password for user: root@user:/home/user# init 5 root@user :/home/user# startx
/etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found xinit: giving up xinit: unable to connect to X server: Connection refused xinit: server error root@user:

---

### Post by anderbuntu on 2019-05-28
As you can see I tried to launch GUI from command line ( by root with commands startx or init 5) 
but not successfull.

[COLOR=#000000]user@user :$ sudo su [sudo] password for user: 

root@user:/home/user# init 5 

root@user :/home/user# startx[/COLOR]
[COLOR=#000000]/etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found xinit: giving up xinit: unable to connect to X server: Connection refused xinit: server error root@user:[/COLOR]

---

### Post by CatKiller on 2019-05-28
> **anderbuntu said:**
> Only thing I installed before was app :  firejail, not sure if its related 

Could well be. A quick look at what that does - prevent non-whitelisted programs from accessing files or executing - sounds exactly like your issue.

---

### Post by anderbuntu on 2019-05-28
OK, even if I  already removed this pkg firejail from cmd line by apt remove...
After removal still not starting GUI,
Is it normal ?

A.

---

### Post by CatKiller on 2019-05-28
I have no idea. I've never used it.

---

### Post by Rubi1200 on 2019-05-28
What changes did you make with firejail, meaning which apps did you add to it?

Try this:

```
sudo apt autoremove --purge firejail
```

```
sudo apt clean
```

```
sudo apt autoclean
```

```
sudo apt update
```

Post back if there are any errors and please use code tags (Go Advanced >> look for # and paste between).

Thanks.

---

### Post by anderbuntu on 2019-05-28
Hi

I used with firejail only chromium & firefox app.
Let me check your commands...

---

### Post by anderbuntu on 2019-05-28
Before I used firejail with below commands:

firejail chromium
firejail firefox

A.

---

### Post by anderbuntu on 2019-05-28
Hi
So also these commands not fixed my issue > [COLOR=#000000][FONT=&quot]sudo apt autoremove --purge firejail  ...[/FONT][/COLOR]


reg. [COLOR=#000000]/etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found[/COLOR]

Ater my investigation for below error, seems that I have missing these files:

[COLOR=#000000]/usr/bin/X
[/COLOR][COLOR=#000000]/usr/bin/Xorg[/COLOR][COLOR=#000000]
[/COLOR]

Its very strange. How they can disappeared.

---

### Post by CatKiller on 2019-05-28
> **anderbuntu said:**
> 
Ater my investigation for below error, seems that I have missing these files:

[COLOR=#000000]/usr/bin/X
[/COLOR][COLOR=#000000]/usr/bin/Xorg[/COLOR][COLOR=#000000]
[/COLOR]

Its very strange. How they can disappeared.
Well, those files are provided by the xserver-xorg-core package. If you've removed that then you've probably also removed other important packages.

---

