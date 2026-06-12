---
title: "KDE4 and Synaptic or Adept root login"
date: 2008-01-11
forum: General Help
---

### Post by knutschr on 2008-01-11
I am now exploring KDE4. Very exciting :)
When I start Synaptic or Adept they both won't accept my password.
When i do
```
sudo bash
synaptic
```
Synaptic opens with root privileges.

Someone else experiencing this?

---

### Post by taurus on 2008-01-11
You mean you can't run this?

```
gksudo synaptic
```
What is the output of this command then?

```
id
```

---

### Post by articpenguin on 2008-01-11
i think its a kdesu bug. Its happing to me. I use gksu instead and that works

---

### Post by knutschr on 2008-01-11
> **taurus said:**
> You mean you can't run this?

```
gksudo synaptic
```
What is the output of this command then?

That worked, like my password works in terminal elsewhere too.
I is in the little window that appears after starting from menu my password is refused.

> ```
id
```
> knut@Knut:~$ id
uid=1000(knut) gid=1000(knut) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),109(admin),115(netdev),117(powerdev),1000(knut)


---

### Post by articpenguin on 2008-01-11
you are in the admin group so that wouldnt be the problem with the adept or synaptic problem.

---

### Post by jarviw on 2008-01-14
I have the same problem...
fresh install of Kubuntu 7.10 KDE4 today, and none of the programs inside KDE4 asking for root privilege will take my user password.  I can use sudo in terminal, not kdesu, and I don't have gksudo installed (in many sense, I don't want to install any GNOME)... I was able to install things via apt-get, and even synaptic worked. but kpackage wouldn't work...
here's my id:

uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),109(admin),1000(user)

---

### Post by knutschr on 2008-01-14
Fintan at Kubuntu forums had a solution that works:
> The workaround that I used was to open a terminal in kde4 and do:
```
sudo passwd
```
just retype your normal (kubuntu user)password three times and all is set.

---

### Post by nsleiman on 2008-01-17
thanks a lot :) it worked fine

---

