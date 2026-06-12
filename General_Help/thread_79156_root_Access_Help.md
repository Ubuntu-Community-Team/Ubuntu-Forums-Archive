---
title: "root Access Help"
date: 2005-10-19
forum: General Help
---

### Post by Jeff Hunter on 2005-10-19
Okay, I have a slight issue.  This may just be the way the system was built, and if it is I will just have to live with it, oh well.  But I would still like to give it a try.

My issue is two-fold:
1) I cannot log in as root (desktop, not shell)...I don't know if it has a root desktop, if I am just using the wrong login, or what, but right now I am more comfortable doing some things in the GUI, and some of them require admin access to do...just don't know enough about the shell commands to do them manually yet.  Is there any way to log into the root account in the GUI?  I know I have done it with a different distro, but I suppose that might not be available in this one.

2) I cannot seem to get my root password to cover my admin functions, and it keeps wanting my user password...that doesn't seem too secure, and I am wondering if there is a way to block regular access from root priviledges without creating extra accounts.  I managed to change some of the passwords, but several still ask for the wrong password, and it gets frustrating trying to remember which prompt wants my root password and which one wants my user password.  Is this just the way it is supposed to be?

Thanks in advance!  BTW, I am not uncomfortable using a shell terminal or the shell itself, so if any solutions you have go through that, I would actually preferr that (trying to get to know more commands, so forth).

---

### Post by wjp.reg on 2005-10-19
A good place to start with that sort of question is the "lifesaver" button on the top taskbar - gnome help, check out "USers Administration" and it should answer your question for you.  The root thing is built into by design :KS

Sorry guy, it's under this link [file:///usr/share/ubuntu-docs/generic/faqguide/C/faqguide.xml]("file:///usr/share/ubuntu-docs/generic/faqguide/C/faqguide.xml")

---

### Post by skar42 on 2005-10-20
After I installed Ubuntu, first thing I did was to boot into recovery mode and then reset the root password:

> passwd root

Then reboot.

Now I can use the SU command to drop a teminal window into root "mode". Running your system as root is very bad. Use a standard user and SU to root when needed.

---

### Post by yoyoned on 2005-10-20
I'll assume you are using gnome and therefore GDM.  (GDM is the graphical login manager.)  From the Gnome menu System>Administration>Login Screen Setup

On the Security tab there is a checkbox to alow root to login with GDM.

Remember that this is disabled by default for a reason.  Be very careful.

---

### Post by Jeff Hunter on 2005-10-20
[QUOTE=yoyoned]I'll assume you are using gnome and therefore GDM.  (GDM is the graphical login manager.)  From the Gnome menu System>Administration>Login Screen Setup

On the Security tab there is a checkbox to alow root to login with GDM.

Remember that this is disabled by default for a reason.  Be very careful.[/QUOTE]
Main reason I want to be able to do this is to edit files that require admin priviledges without going into the terminal and using sudo.  Is that laziness?  Not really.  More like practicality and understanding that I don't know enough about the CLI to comfortably work with that stuff from the CLI just yet, and giving me the ability to do it graphicly until I am more comfortable.

Maybe I will just learn to live with it anyway...after all, I've learned my fastest when that was the only way to get something done.  If it wern't for the fact that Hoary doesn't auto-mount my file systems, I wouldn't know how to yet, or how to edit my fstab to make it auto-mount.

Thanks for the advice!  I appriciate it.  Tootles!

---

### Post by ymmotrojam on 2005-10-20
This thread shows how to enable the root account :) 
[http://www.ubuntuforums.org/showthread.php?t=79610](http://www.ubuntuforums.org/showthread.php?t=79610)

---

