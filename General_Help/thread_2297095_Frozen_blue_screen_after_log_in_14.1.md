---
title: "Frozen blue screen after log in 14.1"
date: 2015-10-01
forum: General Help
---

### Post by Torvil on 2015-10-01
Not sure if I'm posting this in the correct place...
when booting up, I enter my password which takes me to a blank blue screen, with only a flashing cursor, then nothing.
I occasionally get a white box which flashes on/off in quick reputation asking for password, and box to switch user or unlock, but even if I enter password, it does nothing. 
I have so far tried the solution on this page which doesn't help;
[http://jiakaizhang.com/fix-frozen-after-login-in-ubuntu-14-04/](http://jiakaizhang.com/fix-frozen-after-login-in-ubuntu-14-04/)
I am very inexperienced and quite new to Linux from windows so please be gentle with replies. 
I'm using 14.1.
Can anyone help please?

---

### Post by Bucky Ball on 2015-10-01
Welcome. 14.1? There isn't one. Do you mean 14.10 or 14.04.1 LTS? If the former, it is no longer support and suggest you install 14.04 LTS (supported until 2019) or 15.04 (next January).

---

### Post by Torvil on 2015-10-01
I have ubuntu 14.1 written on the disc....in the absence of ubuntu gui how do I find out?
should I just re-install the version on the disc, and how do I do this please?

Thinking of it, it must be 14.10. My next question is how????;
do I install 14.04 LTS in my non co operating desktop?

---

### Post by howefield on 2015-10-01
Does the live disc boot to a desktop ?

System settings > Details > Overview will tell you which version it is.

---

### Post by Torvil on 2015-10-01
No even with the disc inserted, it longer boots. I cannot get as far as system settings

---

### Post by howefield on 2015-10-01
> **Torvil said:**
> No even with the disc inserted, it longer boots. I cannot get as far as system settings

OK, there will be an info file on the disk, 

```
.disk/info
```

which will tell you the version.  There is also a README.diskdefines file which is a bit more informative than the info file.

Assuming it is 14.10, to get 14.04 you would need to download the iso file from ubuntu.com and create a new live disk/USB medium, you can install over the existing 14.10 installation, but if 14.04.x cannot boot to the desktop in live mode, chances are that you will have the same problem when installed to the machine.

---

### Post by Torvil on 2015-10-01
Looks like I'm doomed then!

---

### Post by Torvil on 2015-10-01
> **howefield said:**
> OK, there will be an info file on the disk, 

```
.disk/info
```

which will tell you the version.  There is also a README.diskdefines file which is a bit more informative than the info file.

Assuming it is 14.10, to get 14.04 you would need to download the iso file from ubuntu.com and create a new live disk/USB medium, you can install over the existing 14.10 installation, but if 14.04.x cannot boot to the desktop in live mode, chances are that you will have the same problem when installed to the machine.

Land I get the following message 
"no such file or directory"


is there really ally no simple fix?

---

### Post by Bucky Ball on 2015-10-02
To find the version from a booted Ubuntu:

```
lsb_release -a
```

Is that what you're after?

---

### Post by howefield on 2015-10-02
Many issues like this are the result of a graphics card issue, many of which can be fixed or worked around.

Can you detail the hardware that you are trying to install Ubuntu on ?

---

### Post by Torvil on 2015-10-22
Ok I have checked the graphics card which seems fine, on another machine, and windows boots up on machine from another HDD. I think I willhave to re-install Linux, is there an easy walk through to help me go from the unrecoverable blue screen, remove and reinstall ubuntu please?

---

### Post by Torvil on 2015-11-02
Any further assistance guys?

---

### Post by Vladlenin5000 on 2015-11-02
> **Torvil said:**
> Ok I have checked the graphics card which seems fine...

We need to know which one.

---

### Post by Torvil on 2015-11-08
I have now identified it is 14.10.

i googled "how to replace Ubuntu with windows" and there was a nice clear walkthhrough which showed me how to install Ubuntu for a disc, shame I couldn't get this support on this forum.

It's all working now though. 

I just need need to work out how to spotify working now.

---

### Post by Bucky Ball on 2015-11-08
> **Torvil said:**
> I have now identified it is 14.10.

i googled "how to replace Ubuntu with windows" and there was a nice clear walkthhrough which showed me how to install Ubuntu for a disc, shame I couldn't get this support on this forum.

You got that information from a search which is better (always research before posting here), but why would you expect a Ubuntu forum to be a prime place to find information on how to replace Ubuntu with Windows? :-k :)

If your issue is solved, please see the first link in my signature. Good luck.

---

### Post by howefield on 2015-11-09
> **Torvil said:**
> I have now identified it is 14.10.

i googled "how to replace Ubuntu with windows" and there was a nice clear walkthhrough which showed me how to install Ubuntu for a disc, shame I couldn't get this support on this forum.
 
It helps when you show at least a modicum of wanting to help yourself and also to answer questions that you are asked. It really is a two way process most of the time.

> I just need need to work out how to spotify working now.

There is an easy walkthrough here.. [https://www.spotify.com/uk/download/linux/](https://www.spotify.com/uk/download/linux/) which talks you through adding a repository key, the repository itself and then installing the actual application. I much prefer using the [webplayer]("https://play.spotify.com/") as the linux version of spotify although works well is unsupported.

---

