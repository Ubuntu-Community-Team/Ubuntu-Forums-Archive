---
title: "[SOLVED] Network in Thunar"
date: 2008-03-23
forum: General Help
---

### Post by ultraloveninja on 2008-03-23
I am using opengeu with thunar on 7.10 and i am trying to get it to connect to network folders on other computer/machines.

I have read through this:
[http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba](http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba)

But i am completely lost.

so far i have installed the fusesmb, but when it starts going into the part about the XFCE Applications and /etc/modules  i get nowhere casue i am not sure what XFCE is and i don't have a modules folder.

any help in what i need to do is greatly appreciated.
thanks!

---

### Post by mali2297 on 2008-03-23
As you don't use Xubuntu, it might be best to use the terminal to set up FuseSmb. Try to follow these [instructions]("https://help.ubuntu.com/community/FuseSmb"). 

If you don't have a file /etc/modules, just create it.
```

sudo nano /etc/modules

```
Enter the line ```
fuse
``` Save (Ctrl+o) and quit (Ctrl+x).

---

### Post by ultraloveninja on 2008-03-23
thank you for the reply.

i will try that.

---

### Post by ultraloveninja on 2008-03-24
ok, so everything got installed ok, but when i get to this part:
cd Network
ls -R

it just comes back as this:
.:

am i supposed to put like an IP address or a network path in somewhere?

kinda lost again.

---

### Post by mali2297 on 2008-03-24
You might have to wait a few minutes after you've entered
```
fusesmb Network
```

You can also try using xSMBrowser (available for installation in the *universe* repository).

> 
xSMBrowser is a tool for navigating SMB Networks (Samba, SMB, CIFS). It retains the features of the program it was based upon (Microsoft's Network Neighborhood), but adds convenient features for Unix users. These include mounting, ability to change networks on-the-fly, and conveniences such as a Stop Button.


---

### Post by ultraloveninja on 2008-03-24
when i put in the fusesmb network command, i get back 'test' and that's it.

i installed xSMBBrowser, but i am not sure where it went or how to load it up and use it.

---

### Post by ultraloveninja on 2008-03-24
ok...nevermind.

it seems to be working now.

yeah...

odd.

---

