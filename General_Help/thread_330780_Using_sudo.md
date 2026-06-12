---
title: "Using sudo"
date: 2007-01-03
forum: General Help
---

### Post by rioghal on 2007-01-03
How do I make it so that sudo asks for a password everytime regardless of when I last ran sudo? I know that the system has a time-out for sudo, but I"d like to have it so that I am asked everytim for the password when using sudo, regardless of the last time I used sudo. Can this be done?

---

### Post by paparucino on 2007-01-03
> **rioghal said:**
> How do I make it so that sudo asks for a password everytime regardless of when I last ran sudo? I know that the system has a time-out for sudo, but I"d like to have it so that I am asked everytim for the password when using sudo, regardless of the last time I used sudo. Can this be done?
I think you should read "man sudo" and mainly "man sudoers" where authenticate is explained.
Working with those file Should help you.

---

### Post by melancholeric on 2007-01-03
backup /etc/sudoers first, then

sudo visudo

then, add 

timestamp_timeout=0

to the line that starts "Defaults"

save & exit.

---

### Post by rioghal on 2007-01-04
> **melancholeric said:**
> backup /etc/sudoers first, then

sudo visudo

then, add 

timestamp_timeout=0

to the line that starts "Defaults"

save & exit.
Thank you so much. I needed this because of being away from my computer very often in a busy environment and I don't feel like entering the screensaver lock password 100 times a day :)

---

### Post by nsleiman on 2007-01-04
> **rioghal said:**
> Thank you so much. I needed this because of being away from my computer very often in a busy environment and I don't feel like entering the screensaver lock password 100 times a day :)

maybe you just need to adjust the screensaver settings for not entering the password..

---

### Post by rioghal on 2007-01-07
> **nsleiman said:**
> maybe you just need to adjust the screensaver settings for not entering the password..
Well, that wasn't what I was worried about. Suppose I run an app via sudo and then leave my desk 5 minutes later. Someone could come along and run 'sudo rm -rf /' and then the system is destroyed. Forcing the user to use the password evertime sudo is used would avoid that scenario.

---

### Post by aysiu on 2007-01-07
> **rioghal said:**
> Well, that wasn't what I was worried about. Suppose I run an app via sudo and then leave my desk 5 minutes later. Someone could come along and run 'sudo rm -rf /' and then the system is destroyed. Forcing the user to use the password evertime sudo is used would avoid that scenario.
Whether or not you change the sudo timeout, that's up to you.

But if your stated reason for doing so is fear of someone walking up to your dsktop and destroying your Ubuntu installation, I'm sorry to say that changing the sudo timeout isn't enough.

Anyone who has physical access to your computer has root access. First of all, there's recovery mode, which makes you root. Then, there's booting up a live CD, which also essentially makes you root. Lastly, someone with malicious intent could just take a screwdriver and steal your hard drive... or a jackhammer and smash your computer.

In other words, you'd better trust people who have physical access to your computer or... don't give them physical access to your computer. Lock it in a big safe and lock the screen while you're away from it.

---

### Post by rioghal on 2007-01-07
> **aysiu said:**
> Whether or not you change the sudo timeout, that's up to you.

But if your stated reason for doing so is fear of someone walking up to your dsktop and destroying your Ubuntu installation, I'm sorry to say that changing the sudo timeout isn't enough.

Anyone who has physical access to your computer has root access. First of all, there's recovery mode, which makes you root. Then, there's booting up a live CD, which also essentially makes you root. Lastly, someone with malicious intent could just take a screwdriver and steal your hard drive... or a jackhammer and smash your computer.

In other words, you'd better trust people who have physical access to your computer or... don't give them physical access to your computer. Lock it in a big safe and lock the screen while you're away from it.
I took the 'recovery' options out of /boot/grub/menu.lst for just that reason. The only options in that file now are two kernel options that boot to the desktop, no recovery available.

Bios is set to boot to the hard disk first, with a bios password so others can't change the boot sequence.

My physical hard drive is in the datacenter, which is very secure. If someone were going to bypass all that security, they wouldn't go through all that trouble just for my hard drive. Besides, any important data is encrypted on disk and would be useless if someone stole the hd.

I was just looking to twart the pranksters (read: children) at my place of work.

---

### Post by aysiu on 2007-01-07
> **rioghal said:**
> I took the 'recovery' options out of /boot/grub/menu.lst for just that reason. The only options in that file now are two kernel options that boot to the desktop, no recovery available.

Bios is set to boot to the hard disk first, with a bios password so others can't change the boot sequence.

My physical hard drive is in the datacenter, which is very secure. If someone were going to bypass all that security, they wouldn't go through all that trouble just for my hard drive. Besides, any important data is encrypted on disk and would be useless if someone stole the hd.

I was just looking to twart the pranksters (read: children) at my place of work.
I think, in that case, you should set a quick key combination to lock the screen for when you're away.

---

### Post by rioghal on 2007-01-07
> **aysiu said:**
> I think, in that case, you should set a quick key combination to lock the screen for when you're away.
That sounds like probably the best solution. I"m kinda nervous about messing around with sudoers anyway. Thanks.

---

### Post by aysiu on 2007-01-07
> **rioghal said:**
> That sounds like probably the best solution. I"m kinda nervous about messing around with sudoers anyway. Thanks.
You may have already known this, but you can easily set this up by going to System > Preferences > Keyboard Shortcuts

I set mine to Control-Alt-L

---

### Post by rioghal on 2007-01-07
> **aysiu said:**
> You may have already known this, but you can easily set this up by going to System > Preferences > Keyboard Shortcuts

I set mine to Control-Alt-L
Oh, well, that figures. I did it the long way - by setting a new Metacity keybindings in gconf using "gnome-screensaver-command --lock" as the command. The way you mentioned is much faster. Oh well, live and learn :)

---

### Post by Pobega on 2007-01-07
> **melancholeric said:**
> backup /etc/sudoers first, then

sudo visudo

then, add 

timestamp_timeout=0

to the line that starts "Defaults"

save & exit.

Is this safe to do? I want to make sudo not remember my password (I'll use sudo -i for longer command chains) but when I go to save it it tells me:

> >>> sudoers file: syntax error, line 12 <<<
What now? 
Options are:
  (e)dit sudoers file again
  e(x)it without saving changes to sudoers file
  (Q)uit and save changes to sudoers file (DANGER!)

---

### Post by melancholeric on 2007-01-07
Well, if visudo complains about syntax errors do not save the file. Here's what i had on that line:

```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0
```

---

### Post by Pobega on 2007-01-07
Thanks, I put it in the wrong place! Now it works for me, thanks a lot ;D

---

