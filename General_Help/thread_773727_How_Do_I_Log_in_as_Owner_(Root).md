---
title: "How Do I Log in as Owner (Root)?"
date: 2008-04-29
forum: General Help
---

### Post by CharmCityCrab on 2008-04-29
I need to change one of my boot settings, specifically which of my dual-boot OS load by default in grub.  Basically, it's just a matter of changing a number in a file.

Unfortunately, the file only gives me read-only permissions because my username isn't the owner.  "Root" is the owner.  So, essentially, I need to log in as root, but the sign in after the switch user screen won't let me do it.

How do I do it?

---

### Post by pbpersson on 2008-04-29
> **CharmCityCrab said:**
> I need to change one of my boot settings, specifically which of my dual-boot OS load by default in grub.  Basically, it's just a matter of changing a number in a file.

Unfortunately, the file only gives me read-only permissions because my username isn't the owner.  "Root" is the owner.  So, essentially, I need to log in as root, but the sign in after the switch user screen won't let me do it.

How do I do it?

To gain root access at any time you can use the sudo command.  In terminal, you would cd to the directory and then for instance type:

sudo gedit <filename>

to use gedit to open the file with root access.  When it asks for a password, just type your user password.

---

### Post by FredB on 2008-04-29
You don't need to have root access all the time. Just said before, using sudo or gksudo (for graphical applications) will help you.

---

### Post by RudolfMDLT on 2008-04-29
You don't log in as root. It's a pretty long story, and I'm trying to find something that will explain it better than I can.

What file is it that you want to edit?

Open the terminal and paste the following, followed by the file you wish to edit.
>  /folder/folder/file


I think you want to edit the grub menu list?

> gksu gedit /boot/grub/menu.lst

If you aren't sure, post back - you might break your system. :) What exactly do you want to edit?

Cheers,

Rudolf

---

### Post by amingv on 2008-04-29
The Ubuntu security setting is different from other distros, the root account is disabled by default so you can't login as root, but you can acquire root privileges temporarily.
For example, to edit this file you have many options:

1. Issue this command :
```
gksudo gedit /boot/grub/menu.lst #change gksudo gedit for kdesu kate if you use KDE
```
2. Or this one:
```
gksudo nautilus #or kdesu dolphin if in KDE
```
and navigate to the file you want to modify
3. or:
```
sudo su
```
will give you a root console.

You can activate the root account for login, but is not recommendable; so I will not recommend it.
Needless to say, be careful when in root, make backups and double check.:)

---

### Post by RudolfMDLT on 2008-04-29
Okay - You just got A LOT of help, :) please save your self some head aches and give the following two articles a read. They are REALLY usefull and will put things in perspective:

[About Root]("https://help.ubuntu.com/community/RootSudo?highlight=%28root%29%7C%28What%29%7C%28is%29")

[New To Linux]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows")

Best of luck,

Rudolf

---

### Post by Michael.Godawski on 2008-04-29
As the posters above stated it already. The direct root access is not recommend. Even a small permission setting on the wrong file can cause the whole system to break. So it is not worth the hassle. 

Use sudo and gksudo instead. You gain temporary superuser privileges and you can do your tasks. There is a thread somewhere on the forums dealing with the root account. I will try to find it.

---

### Post by ad_267 on 2008-04-29
This is a good reference about root and sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CharmCityCrab on 2008-04-29
Thanks gang.

I'm still having some issues, though.  When I run the terminal commands that are recommended, I get a blank page on my screen.  I know in fact that it is not a blank page, though, because when I navigate to it through the graphical interface (Whatever the Unbuntu equivalent of Windows Explorer is), it has various words and numbers.  In fact, if it were truly a blank, my computer wouldn't boot in the first place, I'd imagine.

Anyone know why it's a blank page for me when I access it through terminal?  Is there a way to either fix that or to do my root editing through the graphical interface where the document displays properly?

---

### Post by Nunu on 2008-04-29
> **CharmCityCrab said:**
> Thanks gang.

I'm still having some issues, though.  When I run the terminal commands that are recommended, I get a blank page on my screen.  I know in fact that it is not a blank page, though, because when I navigate to it through the graphical interface (Whatever the Unbuntu equivalent of Windows Explorer is), it has various words and numbers.  In fact, if it were truly a blank, my computer wouldn't boot in the first place, I'd imagine.

Anyone know why it's a blank page for me when I access it through terminal?  Is there a way to either fix that or to do my root editing through the graphical interface where the document displays properly?

remembers when you gedit to use the same case as the file is labeled. In other words if a File starts with capital you must put it in when you gedit 

Example.

file name Demo

You should then type sudo -s gedit Demo

Or the file is named demO

You should enter sudo -s demO

Else gedit will see it as a new file which will be blank.

---

### Post by MangasColoradas on 2008-04-29
> **CharmCityCrab said:**
> Thanks gang.

I'm still having some issues, though.  When I run the terminal commands that are recommended, I get a blank page on my screen.  I know in fact that it is not a blank page, though, because when I navigate to it through the graphical interface (Whatever the Unbuntu equivalent of Windows Explorer is), it has various words and numbers.  In fact, if it were truly a blank, my computer wouldn't boot in the first place, I'd imagine.

Anyone know why it's a blank page for me when I access it through terminal?  Is there a way to either fix that or to do my root editing through the graphical interface where the document displays properly?

Do ```
sudo nautilus
``` and navigate to it through the window that pops up then if you are having trouble.

---

### Post by CharmCityCrab on 2008-04-29
> **Nunu said:**
> remembers when you gedit to use the same case as the file is labeled. In other words if a File starts with capital you must put it in when you gedit 

Example.

file name Demo

You should then type sudo -s gedit Demo

Or the file is named demO

You should enter sudo -s demO

Else gedit will see it as a new file which will be blank.

Thanks.  What I realize was going on is that I actually was typing "1st" with a one instead of "lst" with a lower-case L.  When I saw it followed by an st, my mind automatically associated it as being an abbreviation for "first", which is the only way I've ever seen it previously.  But thinking to look lower-case versus capital letters made me reevaluate.

So, long story short, I was able to adjust my boot order to what I preferred.  Thanks everyone!

---

### Post by CharmCityCrab on 2008-04-29
> **MangasColoradas said:**
> Do ```
sudo nautilus
``` and navigate to it through the window that pops up then if you are having trouble.

Thanks.  It's too late for me to use that tip this time as I've solved the issue, but it should come in really handy in the future.  I have a much easier time with graphical interfaces than command prompts.  15 years ago it was probably the other way around, but it's been a long time since MS-DOS, and I wasn't even all that proficient at that.

---

### Post by Nunu on 2008-04-29
> **CharmCityCrab said:**
> Thanks.  It's too late for me to use that tip this time as I've solved the issue, but it should come in really handy in the future.  I have a much easier time with graphical interfaces than command prompts.  15 years ago it was probably the other way around, but it's been a long time since MS-DOS, and I wasn't even all that proficient at that.

Don't worry its like riding a bike. :P

---

### Post by aysiu on 2008-04-29
It should be ```
gksudo nautilus
``` It's a good habit to get into - using *gksudo* for graphical applications and *sudo* for terminal applications.

---

### Post by garypdx on 2008-04-29
I may be off base but as I understand it, if you must have a root desktop and you're a brave soul, you need to give root a password with sudo. That's why the desktop ignores it, it doesn't have a password.

I'm unclear of the command passwd flags..can someone verify?

G

---

### Post by aysiu on 2008-04-29
You don't have to give root a password to accomplish root tasks. That's what the whole point of *sudo* is - to allow certain users the ability to assume root privileges for particular tasks.

---

### Post by RudolfMDLT on 2008-04-29
@aysiu - It's actually from you that I got in the habit of using gksu vs sudo. - Didn't you write something on the topic of sudo? I tried to find it, but couldn't, thought it might be helpful here. I may be wrong though...

---

### Post by aysiu on 2008-04-29
> **RudolfMDLT said:**
> @aysiu - It's actually from you that I got in the habit of using gksu vs sudo. - Didn't you write something on the topic of sudo? I tried to find it, but couldn't, thought it might be helpful here. I may be wrong though...
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

