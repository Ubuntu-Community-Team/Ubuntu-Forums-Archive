---
title: "Kde &gt; Open apps as root?"
date: 2006-10-28
forum: General Help
---

### Post by Thund3rstruck on 2006-10-28
Given all the publicity of KDE lately I decided to make a switch to Kubuntu Edgy Eft rather than upgrade ubuntu installation. 

I'm having an issue after the fresh install where anytime I attempt to open a GUI application (as root, sudo) such as kwrite or kate I get a large error such as:

```

Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5841' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Shutting down running client.

```

Can anyone tell me what is going on? I'd rather not have to edit every config file with text based editors such as vi/nano

Thanks

---

### Post by kidders on 2006-10-28
Hi there,

Ignoring the fact that you really shouldn't be running apps as root, you could correct this issue by loosening the security on your X server.

Can you use kdesu to run things as root?

---

### Post by Thund3rstruck on 2006-10-28
> Ignoring the fact that you really shouldn't be running apps as root

Well you have to edit config files with root.. Thanks for the reply. kdesu worked but this concerns me because I thought that basically gnome and kde were interchangable as far as functionality goes

---

### Post by kidders on 2006-10-28
Hey again,

Gnome & KDE have some important differences, but they are basically interchangeable, much of the time. Your particular issue has to do with the security configuration of your X server though, which is quite separate from your graphical environment per se.

I imagine your X session's default behaviour is to refuse to let apps that it isn't convinced are part of it interfere with it. You can override this if you like, but I wouldn't really recommend it.

---

### Post by arvs on 2006-10-31
Does anyone know how to change this behavior?

---

### Post by aysiu on 2006-10-31
Read these links:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by kidders on 2006-10-31
You could start your X server with the "-ac" switch to disable security, but it wouldn't be clever. Is there something specific you're trying to do?

---

