---
title: "ubuntu Server edition screenshot?"
date: 2007-10-29
forum: General Help
---

### Post by APMT19 on 2007-10-29
Does anyone have a screenshot of ubutu server edition, i just want to see what it looks like before installing it.

---

### Post by constchar* on 2007-10-29
I'm not entirely sure but I think USE is command-line only by default.
I was thinking of installing it myself on an older computer to run a Half-Life
server if I should install Fiber Optic, which just got installed on my street :D

---

### Post by PilotJLR on 2007-10-29
You got it... it is command line only be default. So not really much to see.

---

### Post by Crafty Kisses on 2007-10-29
> **PilotJLR said:**
> You got it... it is command line only be default. So not really much to see.
Yep, there it is, in all it's glory.

---

### Post by andyfromtucson on 2007-10-29
If all you want is a server for home or development use just install the regular desktop edition of Ubuntu and then install the various server programs you want, like Apache2, etc. There is a LAMP package that will install Apache-MySQL-PHP if thats what  you want.  As far as I can tell, the Server Edition is more targeted at full-on production environments.

---

### Post by derbouka on 2007-11-01
Actually I'm using an Ubuntu Desktop edition to run as a server. Will I gain more( I mean performance at least) by using the Server Edition?
Is there any benchmarks on this?

Best regards!

---

### Post by notwen on 2007-11-01
> **PilotJLR said:**
> You got it... it is command line only be default. So not really much to see.

That's one clean CLI. *nod* =p

---

### Post by Therion on 2007-11-01
> **PilotJLR said:**
> You got it... 
Is that a .jpg??   Tsk, tsk...  

Doesn't really do it a proper justice, now does it?

---

### Post by PilotJLR on 2007-11-01
haha - yeah, a screenshot nonetheless!

How about this instead:
```

$

```

---

### Post by jwxie on 2008-01-30
> **PilotJLR said:**
> You got it... it is command line only be default. So not really much to see.

thank you

---

### Post by _sAm_ on 2008-01-30
> **derbouka said:**
> Actually I'm using an Ubuntu Desktop edition to run as a server. Will I gain more( I mean performance at least) by using the Server Edition?
Is there any benchmarks on this?

Best regards!

I also want to know that, what is the main different between the server and the desktop edition? Will there bee any point in installing Ubuntu server and then the gui that I want(and need)? And will it bee any point using a 64bits os for a simple home server?

---

### Post by ghandi69_ on 2008-02-03
> **_sAm_ said:**
> I also want to know that, what is the main different between the server and the desktop edition? Will there bee any point in installing Ubuntu server and then the gui that I want(and need)? And will it bee any point using a 64bits os for a simple home server?

Basically, the differences between the server edition and the desktop edition are huge.  

The Desktop Edition comes with everything the ubuntu team things you would need on a desktop computer.  Media players, open office, video players, codecs for bluethooth, wireless, blah blah, and so on.

The server edition basically comes with nothing(there are a few options you can check during installation, such as ssh, mysql, or apache etc...)

I for one, like knowing what is all on my computer, so I usually start with the server edition, and just add Desktop environments or window environments or applications as I see fit.

I also have a apache/ampache/samba/ssh/mysql headless server running with no GUI at all.  Anyway, I hope this helps.

---

### Post by Delkster on 2008-02-03
> **derbouka said:**
> Actually I'm using an Ubuntu Desktop edition to run as a server. Will I gain more( I mean performance at least) by using the Server Edition?
Is there any benchmarks on this?

The graphical desktop of course uses memory that could otherwise be used e.g. for disk cache, thus potentially offering better disk performance. The desktop edition may also have some daemons (services) running on the background that are not installed by default in the server edition, and they use a few CPU cycles now and then.

Whether there is any practical difference depends on the characteristics of your system and the situation. For example, if your server doesn't need to access large amounts of data on the disk and it already has a few hundred megs to spare for disk cache, having more free probably doesn't make that much of a difference.

---

