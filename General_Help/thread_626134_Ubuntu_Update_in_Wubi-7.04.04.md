---
title: "Ubuntu Update in Wubi-7.04.04"
date: 2007-11-28
forum: General Help
---

### Post by bnmjosh on 2007-11-28
Okay, first of all I'd like to say hi to everyone here! I hope I'm not asking a really stupid question... But...........

I installed Ubuntu with Wubi-7.04.04 (the one you get when you click the download button on the site..)

Worked great, I might add I love how it just smoothly flows through and you don't have to hit anything until it's done. Very nice job fellows :)

But, once you have Ubuntu loaded up, the automatic updater thing pops up. So, you install the updates, restart, but after that......

The commands start up and whatnot, asks for your username and password. But not on the graphical page, it's just black bg with white text. Then, you get the password and everything all typed in... 

Well I don't know exactly what to do from there.. I was reading some posts before I did this and it said to type: 'sudo aptitude update' in the command line. I did this, it updated, then I rebooted with 'shutdown now'. But sadly, this didn't do anything, it all started up the same way again... Right now, I just finished deleting Wubi and I'm installing it again as I type. (Well, the installer's downloading the ISO, same bis :))

So, what I'm asking, is: Is there a way to update Ubuntu without screwing it up?

PS: Could someone explain to me how to change the resolution above 1024x768 please?

Thanks so much guys, I appreciate any help I can get!

And again, great job with Wubi!

---

### Post by bnmjosh on 2007-11-28
Hey everyone, one more question. I'm trying to install Wine, so I can use Windows Programs on Ubuntu. It gave me this:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

But I don't know where I'm supposed to put this.. Help please? Thanks!

---

### Post by ago on 2007-11-29
You put that in the terminal but remember that adding new repository means giving unlimited trust to the websitethe repoistory sits on, so first I would check that the repository website (budgetdedicated.com) is an authentic one... And double check the command, particularly when it starts with sudo. There have been a few attempts to trick users to do harmful things recently, so better to spend 5 minutes more and learn something in the process...

---

### Post by ago on 2007-11-29
Updating should work except for hald which may creating problems in some cases, UPGRADING to 7.10 will not work.

---

### Post by bnmjosh on 2007-11-29
Yeah.. I learned all about the terminal, those codes, and everything. First thing I did was read that post about frauds trying to ruin Ubuntu for some people.

But I don't know what I should do, whenever I use to automatic updates it just does what I said above. I don't know what to do, I'm just gonna leave it the way it is until I can find out what's wrong... Thanks though, for the advice :)

---

### Post by bnmjosh on 2007-11-29
I feel so stupid... All I had to do was look at the diagnostics of the error that occured when I tried to boot Ubuntu after the updates... It said the power cord on my video card wasn't plugged in, so I shut down, plugged it in, and now everything works...

So sorry guys, didn't pay attention... Thanks for trying to help though, I appreciate it greatly!

---

