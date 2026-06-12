---
title: "How do I login as root?"
date: 2008-03-15
forum: General Help
---

### Post by jewleestfu on 2008-03-15
Ubuntu 7.10
halp

---

### Post by PurposeOfReason on 2008-03-15
You don't. That is what the sudo and su commands are for.

Why do you need to be root?

---

### Post by sandysandy on 2008-03-15
why do u want to do it.

if u want to run command with root privileges use

[COLOR="Blue"]sudo[/COLOR] followed by command

u will be prompted for user password.

regards

---

### Post by Shazaam on 2008-03-15
Root login is disabled by default. If you need to do something as root you prepend "sudo" (without the quotes) before a command in terminal to get temporary root access.
```
sudo yourcommand
```
Can I ask you why you need to be root?

---

### Post by jewleestfu on 2008-03-15
<a href="http://forums.myspace.com/t/3838916.aspx?fuseaction=forums.viewthread&PageIndex=2&SortOrder=0">Quick summary of my early afternoon</a>

---

### Post by knutschr on 2008-03-15
If you start in recovery mode and write 
```
startx
```
you will be in root mode.

Try avoiding doing this! 

If you must run a program as root, use instead
```
gksu [program name]
```

---

### Post by jewleestfu on 2008-03-15
[HTML]http://forums.myspace.com/t/3838916.aspx?fuseaction=forums.viewthread&PageIndex=2&SortOrder=0[/HTML]

---

### Post by jewleestfu on 2008-03-15
jesus christ...lol

---

### Post by sandysandy on 2008-03-15
have a look at this thread

[http://ubuntuforums.org/showthread.php?t=603785](http://ubuntuforums.org/showthread.php?t=603785)

regards

---

### Post by PurposeOfReason on 2008-03-15
Does ```
sudo apt-get install wine
``` do anything? Say no to install if it does of course as you don't want it. This is just a test.

---

### Post by jewleestfu on 2008-03-15
prompted me for my password but then nothing.

Do I have to mention I'm a complete n00b?
lol

---

### Post by PurposeOfReason on 2008-03-15
> **jewleestfu said:**
> prompted me for my password but then nothing.

Do I have to mention I'm a complete n00b?
lol
This could be serious. Do you have a /etc/sources.list file?

---

### Post by sandysandy on 2008-03-15
kindly post complete details of the commands u gave.

try [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by knutschr on 2008-03-15
Type your password (you won't see that you are typing) and press [enter]

---

### Post by forrestcupp on 2008-03-15
You can do almost anything you would want to do with root in either the terminal, or nautilus, the file browser.  To use those as root without having to reboot, you can just type in a terminal:
```
gksu gnome-terminal
```
for a root terminal, or
```
gksu nautilus
```
for root permissions in nautilus.

You need to be very careful, though.

---

### Post by jewleestfu on 2008-03-15
Nothing

:'(

---

### Post by PurposeOfReason on 2008-03-15
> **jewleestfu said:**
> Nothing

:'(
Nothing for what? Please quote to make things easier.

---

### Post by jewleestfu on 2008-03-15
nada

---

### Post by jewleestfu on 2008-03-15
> **PurposeOfReason said:**
> Nothing for what? Please quote to make things easier.

@ you

---

### Post by PurposeOfReason on 2008-03-15
> **jewleestfu said:**
> @ you
How old is this install?
Put in the live cd again and check it for defects (at the first screen).

Somehow synaptic and aptitude did not get installed.

---

### Post by jewleestfu on 2008-03-15
Synaptic is installed...
I however cannot utilize it.

---

### Post by PurposeOfReason on 2008-03-15
> **jewleestfu said:**
> Synaptic is installed...
I however cannot utilize it.
What errors does it give you?

---

### Post by knutschr on 2008-03-15
You should tell us things more detailed.

---

### Post by robertchahine on 2008-03-15
to become root try :
sudo su

---

### Post by Sockerdrickan on 2008-03-15
what are the differences of sudo, su and gksu

---

### Post by PurposeOfReason on 2008-03-15
> **Tux0r said:**
> what are the differences of sudo, su and gksu
Sudo - root for just that command
su - become root in terminal until otherwise said
gksu - same as sudo but for GUI's

---

### Post by Sockerdrickan on 2008-03-15
> **PurposeOfReason said:**
> Sudo - root for just that command
su - become root in terminal until otherwise said
gksu - same as sudo but for GUI's

I can sudo nautilus too. why does gksu exist?

---

### Post by forrestcupp on 2008-03-15
> **Tux0r said:**
> I can sudo nautilus too. why does gksu exist?

Some people think sudoing a graphical program has the potential to mess permissions up.

Also, if you sudo nautilus and close the terminal, it closes nautilus too.  With gksu, nautilus stays open.

---

### Post by Sockerdrickan on 2008-03-15
> **forrestcupp said:**
> Also, if you sudo nautilus and close the terminal, it closes nautilus too.  With gksu, nautilus stays open.

Great :)

---

