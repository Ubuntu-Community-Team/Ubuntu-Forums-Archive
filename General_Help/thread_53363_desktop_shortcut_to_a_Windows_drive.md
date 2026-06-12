---
title: "desktop shortcut to a Windows drive"
date: 2005-07-31
forum: General Help
---

### Post by JulesH on 2005-07-31
Hi,

I have altered fstab so I have read/write access to a FAT Windows hard drive partition in /media/windows/. Under root (sorry, I do have a root!), I can put a shortcut onto my desktop so I can access this anytime.

I tried to do the same in my user account, but there seems to be no way, as I don't have permissions to do it.

Can someone tell me how to do this? Do I temporaroly make my user account into root, or what?

regards,
Jules

---

### Post by titus1950 on 2005-07-31
[QUOTE=JulesH]Hi,

I have altered fstab so I have read/write access to a FAT Windows hard drive partition in /media/windows/. Under root (sorry, I do have a root!), I can put a shortcut onto my desktop so I can access this anytime.

I tried to do the same in my user account, but there seems to be no way, as I don't have permissions to do it.

Can someone tell me how to do this? Do I temporaroly make my user account into root, or what?

regards,
Jules[/QUOTE]


If you wont windows to show in Places> Computer>Desktop,just try this(example)

dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

Erase the **line** in front of your entry on fstab>save>reboot.

---

### Post by thagame on 2005-07-31
all i do is type 

> sudo /etc/init.d/dbus-1 restart 

gotta do it everytime you reboot or add it to autostart commands.
It adds Windows to Places menu and on my desktop

---

### Post by JulesH on 2005-08-02
Hi thagame,

Thanks. I tried this and it works for me. So how do I get this to autostart?

Titus, why do you erase the line before the new entry in fstab? I'm not sure what you mean...

Jules

---

### Post by Cordate on 2005-08-14
[COLOR=DarkGreen]Jules, there's another way to create this- check out **[this thread](http://www.ubuntuforums.org/showthread.php?t=38188&highlight=windows+partition+shortcut).[/COLOR]**
> Open up your file browser, navigate to where your folder that you want a link on your desktop is, drag and drop it to your taskbar. Then, drag the taskbar icon to your desktop. 
[COLOR=DarkGreen]Though when I tried this I couldn't get it to work quite right. there was some funny behavior- I wanted a link to a folder just off of the root folder, and my link to that opened the root folder instead. 
So then I found **[this](http://www.ubuntuforums.org/showthread.php?t=56044&highlight=windows+link+desktop) **:[/COLOR]
> one can make a link to a folder throught pressing shift and ctrl while drag and drop. This should do the trick. (This seems to be the only way creating a desktop-link.) 
[COLOR=DarkGreen]...and that seems to work perfectly. Good luck with yours![/COLOR] :)

[COLOR=DarkGreen]-Cordate[/COLOR]

---

### Post by wellery on 2005-08-14
[QUOTE=thagame]all i do is type 

 sudo /etc/init.d/dbus-1 restart

gotta do it everytime you reboot or add it to autostart commands.
It adds Windows to Places menu and on my desktop[/QUOTE]

How do you add it to the autostart commands if it requires to be run as root which requires you to enter the password?

---

### Post by jeffbacon on 2005-08-28
anyone have an answer to that last Q?

---

### Post by Maier on 2005-09-01
Sorry Im not even sure if this helps you.. im sure it will work, bit there has to be an easier way..

[http://ubuntuforums.org/archive/index.php/t-12071.html](http://ubuntuforums.org/archive/index.php/t-12071.html) 

Hope you figure it out :)

---

