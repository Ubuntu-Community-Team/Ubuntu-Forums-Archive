---
title: "Gnome desktop is not usable"
date: 2008-05-17
forum: General Help
---

### Post by dg2445 on 2008-05-17
I apologize if this isn't the correct place to ask this question or if it has been 

asked before. I'm a relatively new Ubuntu user and am having a problem with my 

desktop.

I'm using Hardy and had it working correctly until I installed an update last week. 

Unfortunately I don't know what update caused the problem. I believe it was one of the 

group that required a reboot on Tuesday or Wednesday.

The problem is the machine loads most of the desktop but then stops. The mouse and keyboard are somewhat responsive and all the desktop icons are loaded. The toolbar (I'm only using one) is visible but has no icons on it. I cannot access it's properties and I cannot access any of the icons on the desktop. When I click on them it's like they're not really there at all. 

Interestingly I'm also using gDesklets and those do work. I can access them using F9 and modify them as I wish. One of the desklets is a shell and it works as well.

I'm running the Gnome desktop with Compiz and have installed the proprietary Nvidia drivers.

Could someone please point me in the right direction? This is a bit of an emergency - I'm stuck using XP.

Thank you very much.

Dave

---

### Post by vmantva on 2008-05-17
I believe our [problems]("http://ubuntuforums.org/showthread.php?p=4973794") are related. I also noticed that mine stopped working this week after a particularly large update. It seems this problem is more widespread then I thought. Ill let you know if I find out anything.

---

### Post by dg2445 on 2008-05-17
They may well be. I'll be sure to post if I find a solution.

My transition was going so well...

---

### Post by dg2445 on 2008-05-18
I really hate doing this but "bump".

---

### Post by Sef on 2008-05-18
1) Have you booted into recovery mode?  At the start of the boot, press escape.

2) Do not bump unless 24 hours have passed since the last post.  Otherwise you could get an infraction.

---

### Post by dg2445 on 2008-05-18
Thank you Sef. I wasn't aware of the "bump" policy. I'll refrain in the future.

I did try booting into recovery mode. I ran "repair damaged packages" and it fixed nothing. Then I tried "repair x-server" and it did make a difference. Unfortunately the problem has not been resolved yet.

I have dual monitors and repairing the x-server caused them to stop working properly - they now both display the same thing. That's no big deal of course.

the toolbar now does display the correct information, but none of it is accessible. I can right-click on the desktop and also use any desktop icons. If I right-click on the desktop and choose "create launcher", the process appears to hang up and nothing happens. The machine is not completely hung up however, I can still use desktop icons and applications loaded at startup (Miro).

Do you have any other suggestions?

Thank you for your time.

---

### Post by dg2445 on 2008-05-19
I think I resolved this problem. I simply reinstalled the Ubuntu desktop using the following:

sudo apt-get install ubuntu-desktop

It wasn't a perfect fix as some of my settings have changed but nothing too difficult to deal with.

At least I can relegate XP to a gaming platform once again.

---

