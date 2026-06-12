---
title: "KDE su always fails"
date: 2007-08-15
forum: General Help
---

### Post by inflamous on 2007-08-15
I'm using Feisty on a Dell laptop, I have shadow passwords enabled and a root password.

The problem I have is that I can use the super user's password only works when I use the command su.  It never works with kdesu, sudo or any program where I need the admin privileges...

I did do ctrl+alt+F1, logged in, did su and entered startx to get into a desktop environment as the super user, but for some reason, it erased my windows from grub and replaced it with ubuntu and ubuntu recovery mode (I kept a backup of my menu.lst so I managed to fix that problem), so I'm not doing that again because that wasted time.

Any suggestions on how I can bypass the password so that I can at least update ubuntu?

---

### Post by dougfractal on 2007-08-15
> I have shadow passwords enabled and a root password
you mean 
> sudo su
passwd? and you entered your new root passwd?

"sudo  -s"   gives you a su type shell   
The password is your login passwd for sudo not the root password

but command like **su -c "apt-get upgrade"**   still work with root password.

any help?

---

### Post by inflamous on 2007-08-15
Thanks for the reply

I got the root password while installing kubuntu (I had the debconf set to low and it gave me the options to enable shadow passwords and to choose a root password).

Right now I'm on windows, so I'll have to try *su -c "apt-get upgrade"* later.

The problem I had was that when I tried to get updates for ubuntu using the program on the taskbar, I entered the root password and it kept telling me "Conversation with su failed".

---

