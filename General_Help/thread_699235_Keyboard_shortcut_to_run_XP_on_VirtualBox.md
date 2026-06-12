---
title: "Keyboard shortcut to run XP on VirtualBox"
date: 2008-02-17
forum: General Help
---

### Post by geo909 on 2008-02-17
Hello everybody!
I have Windows XP installed in Virtualbox and I'm pretty happy with it.

I was wondering if it is possible to assign a keyboard shortcut (or a desktop icon) that opens XP in Virtual Box...

I mean, clicking Ctrl+Win_key or clicking on a windows icon on the desktop to make XP start without starting the virtualbox window etc..

Do you think that is possible?

---

### Post by geo909 on 2008-02-19
*bump*

---

### Post by amingv on 2008-02-19
I don't commonly use Gnome, so please bear with me if I miss something...

Right-click on an empty space on your desktop, select "Create Launcher" (IIRC) Give it any name you like and put this in the command section:
```
VBoxSDL -fullscreen -vm 'WinXP'
```
Where 'WinXP' is the name of your virtual machine, within quotes. Save it and you should be able to run it by double-clicking on the icon.

You can use the same command and assign it to any key sequence you like.

---

### Post by geo909 on 2008-02-19
Thanks!! That almost did the job!

The thing is that I can't see Ubuntu anymore, I have to shut XP up..

Is there a way to do the same thing and, let's say open my virtual machine fullscreen in one of my 4 desks and also have keyboard shortcuts to move from one desk to another?

---

### Post by amingv on 2008-02-19
You can exit fullscreen mode by pressing your Host Key + F (your host key is the right Ctrl key by default) and switch back in the same way. I have seen the desktop switching in some videos, but I don't know how to do it. Perhaps someone else here does?

---

### Post by HermanAB on 2008-02-19
Just leave the -fullscreen out?

---

### Post by herbster on 2008-02-19
In my flux menu I have:

```
VBoxManage startvm "Windows XP"
```

---

### Post by geo909 on 2008-02-20
> **herbster said:**
> In my flux menu I have:

```
VBoxManage startvm "Windows XP"
```


Yes, that did exactly the job I wanted!!

For some reason, the other way, the host key didn't work for me. Also I had no keyboard shortcuts to move from one desk to the other.

Thanks again to all of you for taking the time to answer.

Before I close the thread, do you have an idea if it is possible to make Virtualbox run on startup, let's say on my 4th desk by default?! OK, I know it's not important, it would be nice, though...

---

### Post by herbster on 2008-02-20
Are you using regular Gnome? If so I can only tell you to go to System > Preferences > Sessions and click Add and add it to the startup sessions, ensuring the checkbox is checked next to it when done adding, in the list of programs in Sessions right there. I don't know how you'd have it retain the workspace in Gnome, only in flux.

---

### Post by geo909 on 2008-02-21
> **herbster said:**
> Are you using regular Gnome? If so I can only tell you to go to System > Preferences > Sessions and click Add and add it to the startup sessions, ensuring the checkbox is checked next to it when done adding, in the list of programs in Sessions right there. I don't know how you'd have it retain the workspace in Gnome, only in flux.

Yes, regular gnome. I do know the sessions-thing, but I was wondering if it was possible to run a program in 'sessions' on a certain desktop. Of course, that's a minor thing, though, but anyway..

---

