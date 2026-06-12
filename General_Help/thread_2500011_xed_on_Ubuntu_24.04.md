---
title: "xed on Ubuntu 24.04"
date: 2024-08-18
forum: General Help
---

### Post by beingpolash on 2024-08-18
Has anyone used the "xed text editor" on Ubuntu 24.04 LTS? I've tried multiple PPAs to install, but none of them work. Any suggestions?

---

### Post by #&amp;thj^% on 2024-08-18
xed had issues with the Ubuntu code base, so there's that to consider.

Have a look here: [https://github.com/linuxmint/xed](https://github.com/linuxmint/xed)

I prefer it as well :).
```
xed --version
xed - Version 3.6.6

```

---

### Post by ajgreeny on 2024-08-18
I didn't actually install or run xed but I downloaded the three packages **xed**, **xed-common** and **xed-dbg** in an VM of Mint-22 and transferred those three packages to my Xubuntu 24.04 Desktop folder.
I then ran command ```
sudo apt install ./xed* -s
``` from the Desktop folder to simulate xed installation.
All appeared to go well with no errors reported but as I said, this was just a simulation not a full installation so I do not know what might happen after a real installation; I might try a full installation later but not on my main OS but perhaps a virtual system.

Watch this space!

---

### Post by #&amp;thj^% on 2024-08-18
> **ajgreeny said:**
> I didn't actually install or run xed but I downloaded the three packages **xed**, **xed-common** and **xed-dbg** in an VM of Mint-22 and transferred those three packages to my Xubuntu 24.04 Desktop folder.
I then ran command ```
sudo apt install ./xed* -s
``` from the Desktop folder to simulate xed installation.
All appeared to go well with no errors reported but as I said, this was just a simulation not a full installation so I do not know what might happen after a real installation; I might try a full installation later but not on my main OS but perhaps a virtual system.

Watch this space!

On Oracular I just used apt to Download them and ran dpkg with install -f all good here:
```
apt policy xed
xed:
  Installed: 3.6.6+wilma
  Candidate: 3.6.6+wilma
  Version table:
 *** 3.6.6+wilma 100
        100 /var/lib/dpkg/status

```

Still waiting for the OP

---

### Post by ajgreeny on 2024-08-19
I have yet to try Oracular but I guess from your post that xed is in the default repos which is not so for Noble.

When using xed in my Mint install I have seen few obvious differences of xed from mousepad but that may be simply due to the way I use them, ie, just as text editors not for anything eve close to coding.

---

### Post by #&amp;thj^% on 2024-08-19
> **ajgreeny said:**
> I have yet to try Oracular but I guess from your post that xed is in the default repos which is not so for Noble.


Nope not unless Wilma is a Ubuntu Repo::
```
xed/now 3.6.6+wilma amd64 [installed,local]
  Text editor

xed-common/now 3.6.6+wilma all [installed,local]
  Text editor (common files)

xed-dbg/now 3.6.6+wilma amd64 [installed,local]
  Text editor (debugging symbols)

```
Clem included it in mint only. I think Linux-Lite also has it, if I'm not mistaking.

---

### Post by ajgreeny on 2024-08-19
> **1fallen said:**
> Nope not unless Wilma is a Ubuntu Repo::
```
xed/now 3.6.6+wilma amd64 [installed,local]
  Text editor

xed-common/now 3.6.6+wilma all [installed,local]
  Text editor (common files)

xed-dbg/now 3.6.6+wilma amd64 [installed,local]
  Text editor (debugging symbols)

```
Clem included it in mint only. I think Linux-Lite also has it, if I'm not mistaking.
So I presume you added the Mint Wilma repos to your Oracular install?

---

### Post by #&amp;thj^% on 2024-08-19
Nope I just used apt to download the 3 .debs, from Mint then, from Xubuntu 24.10 I installed them.

Adding any Mint Repo Just is not a good practice. :) But you know that already.
To Help with how I did this is simple, from the Mint Live Iso:
```
apt download xed
apt download xed-common
apt download xed-dbg
```
Not on Ubuntu as seen:
```
 apt download xed
Error: Can't find a source to download version '3.6.6+wilma' of 'xed:amd64'

```
Moved all the .debs to folder over to Xubuntu, then Installed.

---

### Post by Dennis N on 2024-08-19
> Clem included it in mint only. I think Linux-Lite also has it, if I'm not mistaking. 

I remember when Clem Lefebvre created it for Cinnamon desktop when he and his team created Cinnamon. **Xed** is also available in Fedora's repository. Here's a screenshot of **gedit** (background) and **xed** (foreground) made on my Fedora Workstation (uses Gnome desktop).

---

### Post by #&amp;thj^% on 2024-08-19
Nice, Also not many know this but Pluma is a fork of Xed.
> **Dennis N said:**
>  is also available in Fedora's repository.
It is in Arch/Aur as well.

---

### Post by lilly33w on 2024-08-22
So I am looking for a solution myself to this too....

---

