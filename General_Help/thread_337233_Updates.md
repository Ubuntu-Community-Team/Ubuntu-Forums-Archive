---
title: "Updates"
date: 2007-01-12
forum: General Help
---

### Post by PowerPLay on 2007-01-12
I have an 8510GZ Laptop that i have just gotten Ubuntu installed on. It took quite a deal of thought to do it though. I just dove into linux a week ago and i had to learn how the rebuild kernels and such so i could install my display driver in command format. Being a Windows user all my life i think you can see that this was not an easy task. 

Well i got past all that and now I have a stable OS running but I've run across another problem.  I get the desktop running and all and the first thing I do is update the system through the update icon in the task bar. all goes well during install but after I restart I get a fudged up screen a pale pink with lines going vertically going through it. Kinda of like hosed monitor looks with a magnet on it. Whats the deal, or at least which update is doing that so i can kill it and keep the rest of the system updated.

If you need to know more about what display driver I'm talking about here it is: 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by brt on 2007-01-12
if you have installed updates like a new kernel image and you are using a selfcompiled display driver you must recompile the graphics driver. 

you will have to do this every time after you have updated you kernel.

---

### Post by PowerPLay on 2007-01-12
Oh, so i'll have to redo everything from that guide above again. Or just start from the recompile the kernel part. I'm new at this, I'm sorry.  And it did the same thing on my friends computer that installed ubuntu fine by default (no extra driver installs here). Do i have to recompile his too?

---

### Post by brt on 2007-01-12
just redo the part:
> 
Compile the kernel module:

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

sudo shutdown -r now

```

> And it did the same thing on my friends computer that installed ubuntu fine by default (no extra driver installs here). Do i have to recompile his too?

No, if you didn't compile drivers on that machine, you wont need to do it ... [-( ;)

---

### Post by PowerPLay on 2007-01-13
Right, but i got the same screen malfunction on his machine. I'm not real sure the only problem is my driver install. I think one of the updates is screwing up the install.

---

