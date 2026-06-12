---
title: "Package help please"
date: 2023-10-11
forum: General Help
---

### Post by mattrix2 on 2023-10-11
Relative newbie here.
I have rotten internet, and just browsing let  alone downloading packages, quickly chews up my data allowance.

But, I can download deb's at the library.
Can some one help or point me to a good site to explain the ins & outs of doing this.

Or suggest a better solution.

Thanks in advance.

---

### Post by ActionParsnip on 2023-10-11
Does the library system use Ubuntu and the same version you use?

---

### Post by ian-weisser on 2023-10-11
In Network Manager, mark your "rotten internet" connection as a Metered Connection.

Connections that are Metered won't be used for Unattended Upgrades (deb) nor for Snap Refreshes.

It's unclear if your library has available wireless, or if you are downloading debs on a library system and sneakernetting.
If the library has wireless, then Network Manager will know when it's on an unmetered connection and apt/snapd will work automatically on that connection.

---

### Post by Holger_Gehrke on 2023-10-11
There's a tool in the repositories named 'apt-offline'. It's meant for exactly your kind of situation. The only problem I can see with this is that it needs to run both on your machine to generate the list(s) of packages to get and on a machine connected to the internet - in your case the machine at the library - to do the actual downloading. I don't know whether you're going to be allowed to install it there, especially since it's a Python program and you need to have a Python interpreter to run it. There is a version of it that should run on Windows available on github.

Holger

---

### Post by HermanAB on 2023-10-12
You can make your own installation server at the library.  What it entails is you simply download everything - about 15 GB I think.  Then use that repository to install things on your machine(s).  It is not difficult to do this.

Here is something to read: [https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html?m=1](https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html?m=1)

---

### Post by mattrix2 on 2023-10-13
Thanks everyone.
Unfortunately my computer system is not portable, that would be the obvious solution.
The library is pretty restrictive about what you can do on their computers; browsing, using office etc; nothing can be installed or saved on them.

apt-offline looks possible if it provides a human readable list of stuff that I can download manually to usb.
I'll set the network manager to metered, but I guess that means no more updates ever.

---

### Post by ActionParsnip on 2023-10-13
Is the library PC Ubuntu based?

---

### Post by mattrix2 on 2023-10-13
> **ActionParsnip said:**
> Is the library PC Ubuntu based?

No. It is Windows 10 or something.

---

### Post by ActionParsnip on 2023-10-13
There is cdimage.ubuntu.com/jammy/daily-live/pending/
You can grab that ISO and use it as a package source and update

---

### Post by ian-weisser on 2023-10-13
> **mattrix2 said:**
> I'll set the network manager to metered, but I guess that means no more updates ever.

Only if you want it that way.
It's trivial to change that setting and manually run updates on your own schedule.

---

