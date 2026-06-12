---
title: "root account problem?"
date: 2007-08-07
forum: General Help
---

### Post by stlouis1 on 2007-08-07
i think i have a problem with the root account. im not sure, maybe this is normal

but what happens, is if i type a command at the console and use sudo, it'll ask me for the password, and i can type the password, and itll move on just fine

but if i type su, and enter the password, it gives me an authentication failure

and if i try to login as root at the login screen, it doesnt work either

is this normal, or can i fix this?

---

### Post by stchman on 2007-08-07
> **stlouis1 said:**
> i think i have a problem with the root account. im not sure, maybe this is normal

but what happens, is if i type a command at the console and use sudo, it'll ask me for the password, and i can type the password, and itll move on just fine

but if i type su, and enter the password, it gives me an authentication failure

and if i try to login as root at the login screen, it doesnt work either

is this normal, or can i fix this?

Ubuntu does not have su.  Typing sudo -s will give you a root terminal if you like.

---

### Post by aysiu on 2007-08-07
This is normal, and you do not need to fix it.

If you feel you need to "fix it," please make a convincing case for doing so. Or describe what you think cannot be accomplished through *sudo*.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Majorix on 2007-08-07
```
sudo su
```

You forgot sudo again :D

---

### Post by stlouis1 on 2007-08-07
ok, so thats normal? i wasnt sure, i just started using kubuntu, i was semi used to fedora before, but kubuntu is seeming to be more functional, for me at least.

what about actually loging in as root at the login screen?


edit// i just tried to install doom3, and it wouldnt take my root password to let me install it to the /usr/... folder, so i had to install it to my home folder.

---

### Post by Songwind on 2007-08-07
To install a game for all users you need to run the installer with "sudo"

---

### Post by stlouis1 on 2007-08-07
it wouldnt let me do that with teh ut2k4 install, said it wasn't a command. i just went in my user management and root was disabled, i enabled it, im gonna try with quake 4 in a minute

---

### Post by RedSquirrel on 2007-08-07
> **stlouis1 said:**
> what about actually loging in as root at the login screen?

Logging in as root from the login screen is like running with scissors, in my opinion. You could run 'sudo -i' in a terminal if you feel you have to, but I have found sticking with plain sudo works rather well.

I highly recommend the link that aysiu provided. It was one of the first things I read about Ubuntu--even before installing Ubuntu, actually :).

---

### Post by stlouis1 on 2007-08-07
i guess i missed that link, must of thought it was part of his sig....

anyway, as far as running with scissors, im pretty good at that. so..........i think i found out how to enable it here

[http://www.ducea.com/2006/06/21/ubuntu-how-to-enable-the-root-account/](http://www.ducea.com/2006/06/21/ubuntu-how-to-enable-the-root-account/)

---

### Post by bodhi.zazen on 2007-08-07
yes, at first sudo is foreign, but after a while it grows on you.

---

### Post by aysiu on 2007-08-07
> **bodhi.zazen said:**
> yes, at first sudo is foreign, but after a while it grows on you.
Well, the funny thing for me is that I came from Windows running as administrator to getting culture shock in Mepis with the user/root account thing. Once I got used to user/root, I switched to Ubuntu and got culture shock again in Ubuntu with the sudo account thing.

Having experienced all three extensively (running as root, running root and user separately, and running a sudoer account), I have to say that *sudo* makes the most sense, and my wife (a Mac OS X user) also agrees, since Apple uses *sudo* for its admin accounts as well.

---

### Post by RedSquirrel on 2007-08-07
> **stlouis1 said:**
> anyway, as far as running with scissors, im pretty good at that. so..........

:)

I remember in an old version of SuSE, if you logged in as root from the login screen, it would allow you to do that but it would change your background to a red one with exploding bombs on it. Very pretty while at the same time suggestive. (They might still have that feature...)



> **bodhi.zazen said:**
> yes, at first sudo is foreign, but after a while it grows on you.

My feeling exactly. When I first read about sudo, I thought, "Bah!" :evil:, but I'm used to it now.

---

