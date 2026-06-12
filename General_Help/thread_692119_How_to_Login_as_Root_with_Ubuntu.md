---
title: "How to Login as Root with Ubuntu"
date: 2008-02-09
forum: General Help
---

### Post by TrakerJon on 2008-02-09
First, this isn't a good idea for security reasons and you might corrupt systems files if you're not very careful...having said that, here's how:

1. Go to the **System** menu and select **Administration** then **User and Groups**.
2. Select the "**root**" user. 
3. Click on "**properties**" and change the existing password to something complex that you can also remember. 
4. Click **OK**.
5. Go to the **System** menu and select **Administration** then **Login Window**.
6. Select the "**Security**" tab and check "**Allow local system administrator login**". 
7. Click **Close**.
8. Logout and then type **root** for user followed by the **password** that you created for root.

---

### Post by p_quarles on 2008-02-09
Not only is it not a good idea, but it's unnecessary. There are ways of acquiring root privileges to any system function without running the entire system as root, and this is greatly preferable for a range of reasons.

---

### Post by billgoldberg on 2008-02-09
I'm pretty sure this isn't posted in the correct forum.

But why would you need a root if you have sudo?

---

### Post by taurus on 2008-02-09
That's sure one way to trash your system real quick, especially those newbies.  :roll:

---

### Post by mikewhatever on 2008-02-09
Don't know what's your reasoning for posting it in Absolute Beginners, IMO, a bad idea. The funny thing is that I've posted about it in Community Cafe a few hours ago.
[http://ubuntuforums.org/showthread.php?t=692023](http://ubuntuforums.org/showthread.php?t=692023)

---

### Post by p_quarles on 2008-02-09
> **mikewhatever said:**
> Don't know what's your reasoning for posting it in Absolute Beginners, IMO, a bad idea. The funny thing is that I've posted about it in Community Cafe a few hours ago.
[http://ubuntuforums.org/showthread.php?t=692023](http://ubuntuforums.org/showthread.php?t=692023)
Which is why I moved it to General Help. ;)

Again, to anyone considering doing this: this is neither necessary for *anything* nor is it supported.

---

### Post by quinnten83 on 2008-02-09
For my enlightenment, can somebody tell me what is the difference between running as root or using SUDO?
when I want to install, i need a sudo password, but apparently it is not the same as running as root.
the software gets installed just the same though, file permissions get changed and so forth, so what is the difference, why is running as one dangerous and using the other not...?

---

### Post by taurus on 2008-02-09
> **quinnten83 said:**
> For my enlightenment, can somebody tell me what is the difference between running as root or using SUDO?
when I want to install, i need a sudo password, but apparently it is not the same as running as root.
the software gets installed just the same though, file permissions get changed and so forth, so what is the difference, why is running as one dangerous and using the other not...?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by p_quarles on 2008-02-09
> **quinnten83 said:**
> For my enlightenment, can somebody tell me what is the difference between running as root or using SUDO?
when I want to install, i need a sudo password, but apparently it is not the same as running as root.
the software gets installed just the same though, file permissions get changed and so forth, so what is the difference, why is running as one dangerous and using the other not...?
When you use "sudo" with a command, you are running that individual command as root. 

There is nothing inherently more or less secure about using "sudo" vs. using a separate root account. They essentially work the same. 

Running an entire session as root, however, introduces a lot of new risks. When you log into Gnome as the root user, you are running every single application within that session as root. For some applications (such as the file manager or window manager) this creates the risk of messing up the system. For others, such as the web browser, this gives malicious code on web sites full access to your system. 

The bottom line is: root access should only be given to applications that need that access, and only when they need that access.

---

### Post by gn2 on 2008-02-09
Can't for the life of me think of a single reason why anyone would *need* to log in to X,K,Ubuntu as Root.

---

### Post by TrakerJon on 2008-02-09
OMG, you would think I shot somebody. It's a pain in the *** to use the command line for everything. It's a lot easier to move pictures and text files to other users of the computer or troubleshoot a variety of issues as root...enough said.

---

### Post by p_quarles on 2008-02-09
> **TrakerJon said:**
> OMG, you would think I shot somebody. It's a pain in the *** to use the command line for everything. It's a lot easier to move pictures and text files to other users of the computer or troubleshoot a variety of issues as root...enough said.
Easier, yes. Advisable, no.

The best practice here is to run individual applications as root. The entire graphical environment should not be run as the root user.

---

### Post by TrakerJon on 2008-02-09
Thanks mom.

---

### Post by bwhite82 on 2008-02-09
Linux is about preferences and options, if someone chooses to login as root by default, it is their choice to do so. It has already been stated, numerous times in this thread that its not a good idea to do so, so if one still chooses to do it, so be it!

---

### Post by p_quarles on 2008-02-09
> **TrakerJon said:**
> Thanks mom.
I'm not trying to tell you what to do. My point is that anyone new to Linux should understand precisely what the risks of this kind of practice are. Anyone choosing to follow your advice needs to be aware of the better alternatives before they make that choice.

---

### Post by sistoviejo on 2008-02-09
> **gn2 said:**
> Can't for the life of me think of a single reason why anyone would *need* to log in to X,K,Ubuntu as Root.

Just for the fun of it.
Because you can.
Etc.
:lolflag:

---

### Post by sistoviejo on 2008-02-09
> **Soldierboy said:**
> Linux is about preferences and options, if someone chooses to login as root by default, it is their choice to do so. It has already been stated, numerous times in this thread that its not a good idea to do so, so if one still chooses to do it, so be it!

I agree. Many distributions allow you to login as root by default.
New users shouldn't do it though.

---

### Post by quinnten83 on 2008-02-09
> **TrakerJon said:**
> OMG, you would think I shot somebody. It's a pain in the *** to use the command line for everything. It's a lot easier to move pictures and text files to other users of the computer or troubleshoot a variety of issues as root...enough said.

LOL,
among these circles,you might as well have shot somebody.
For moving files around I use gksudo nautilus, sure you have to type your password, but they tell me it is safer that way.I am the only user on my system though, so if my user configuration gets messed up, it might as well have been the root...!Or not, I don't know...

---

### Post by p_quarles on 2008-02-09
> **quinnten83 said:**
> so if my user configuration gets messed up, it might as well have been the root...!Or not, I don't know...
Definitely not the same thing. If you mess up the user configuration irreparably, all you have to do is create a new user. If you mess up the root configuration irreparably, you have to reinstall. 

Privilege separation is there for both security and system stability.

---

### Post by quinnten83 on 2008-02-09
> **sistoviejo said:**
> I agree. Many distributions allow you to login as root by default.
New users shouldn't do it though.

okay,
just read upon the thing and i understand it better thanks to the windows administrator analogy.
My two cents, if he wants to log in as root he should. Since sudo is pretty much "run as" in windows, stuff still gets done, but damage is confined to the user running the command. Good stuff.

Still, i worry about people running as root/admin, because it seems like a great way to infect other systems with vulnerabilities that you installed unwillinlgy on your computer. if everybody ran as root, hell would break lose because there would be no confirmation when installing software and programs can install themselves in the background, is my train of tought correct?

If so, then windows would be much more secure if people just ran it as regular users and when they need to install, run the program as administrator with "run as".

right?

---

### Post by TrakerJon on 2008-02-09
> **p_quarles said:**
> I'm not trying to tell you what to do. My point is that anyone new to Linux should understand precisely what the risks of this kind of practice are. Anyone choosing to follow your advice needs to be aware of the better alternatives before they make that choice.

Rightly so but I'm sure you would agree knowledge is power.

---

### Post by p_quarles on 2008-02-09
> **TrakerJon said:**
> Rightly so but I'm sure you would agree knowledge is power.
Absolutely. That's why I responded to your thread with additional information. ;)

---

### Post by gn2 on 2008-02-09
> **TrakerJon said:**
> knowledge is power

OK then, here's some knowledge to boost your power.

Press Alt+F2 then type ```
gksudo nautilus
```

then press Enter.

No need to log in as Root to alter files in Ubuntu.

Remember to close it when you're finished and be careful what you edit.

---

### Post by abstractcoder on 2008-02-09
> **TrakerJon said:**
> OMG, you would think I shot somebody. It's a pain in the *** to use the command line for everything. It's a lot easier to move pictures and text files to other users of the computer or troubleshoot a variety of issues as root...enough said.


Everyone has their own ways of doing things, but you won't have to worry about moving pictures around when you get hacked....

---

### Post by TrakerJon on 2008-02-10
> **abstractcoder said:**
> Everyone has their own ways of doing things, but you won't have to worry about moving pictures around when you get hacked....

Is that a promise or a threat?

---

