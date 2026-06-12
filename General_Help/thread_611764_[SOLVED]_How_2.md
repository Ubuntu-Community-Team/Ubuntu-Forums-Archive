---
title: "[SOLVED] How 2"
date: 2007-11-13
forum: General Help
---

### Post by fuente on 2007-11-13
I am very new to this thing. Just 2 weeks old in the Linux world. So please help me

I am using Ubuntu 7.10 Gutsy Gibbon and I write a letter using OpenOffice.org Word processor. How do I get this document to open on my sister windows xp OS computer with Microsoft Office.

Another problem is, I set up the Samba server and I tried accessing the Linux OS pc from a windows OS pc and it keep on requesting user name and password.  I tried using my login name and password for both the windows and linux PC, but to know avail. What am I not doing that I need to do. The good thing is i am able to access the linux OS PC from another Linux OS PC with no problem. It did not request a login and password.

Thank You in advance.

---

### Post by aysiu on 2007-11-13
> **fuente said:**
> I am very new to this thing. Just 2 weeks old in the Linux world. So please help me

I am using Ubuntu 7.10 Gutsy Gibbon and I write a letter using OpenOffice.org Word processor. How do I get this document to open on my sister windows xp OS computer with Microsoft Office. Try saving it as a .doc file instead of .odt

---

### Post by ddrichardson on 2007-11-13
Which version of Windows?

---

### Post by airbornemist6 on 2007-11-13
He said xp.

My suggestion, either follow aysui's advice or install open office on her computer!

Also, I found a way to set up your linux box to run as an ftp server, it's much more simple than samba. I'll edit my post with the link in a second, I need to find it first
EDIT:
Here's the link, that took unnecessarily long xD
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by ddrichardson on 2007-11-13
> **airbornemist6 said:**
> He said xpActually he said his sister's PC was XP, I was unclear as to the machines he is trying to connect.

---

### Post by airbornemist6 on 2007-11-13
Ah, I see your point, my bad. Either way, the link I posted will work almost universally

---

### Post by fuente on 2007-11-13
thank u, but I am still not clear on 

How to connect to access the Linux pc from windows. The samba server is set up. I can see the linux computer on the server, but when I try to access it, a request for a login and passwd comes up, and I try all login and passwd I know.

The ftp solution will not work for me, because I may need to format files on the windows computer, so it shouldnt be read only.

help please. i need to move fwd

---

### Post by ddrichardson on 2007-11-13
How about using VNC if you need to remotely control the other PC? It's a peer to peer connection based on IP address.

---

### Post by aysiu on 2007-11-13
This video tutorial should help you:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by dpar on 2007-11-13
Great link, aysiu. I've been trying to get this one figured out too. 

Thanks

---

### Post by ljonesj on 2007-11-13
you have to add your self to smbusers open a terminal and do this

You need to add yourself to smbusers, setting your password. To do that:

sudo smbpasswd -a your_user_name

Now restart samba:

sudo /etc/init.d/samba restart

and try logging in from Windows gain. If the first command complains that you already exist, do it without the '-a' (ie: 'add') to just set your password.
__________________

---

### Post by luvdemheels on 2007-11-13
ljones,
Isn't there a gui that could have done that for him?? He should be able to do this without the command line.

---

