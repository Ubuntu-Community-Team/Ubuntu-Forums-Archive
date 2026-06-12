---
title: "CUPS or Samba?"
date: 2005-05-26
forum: General Help
---

### Post by mobile.army on 2005-05-26
I've been trying to get my network set up to print items from my WinXP laptop to the printer attached to my Ubuntu desktop.

I've been through the forums and tried to do everything with CUPS and Samba that was suggested and here's where I'm at:

-My WinXP machine sees the computer when I try to add a network printer, but it doesn't see that the computer has a printer.

-I can see and use the Shared Files on my WinXP machine on the Ubuntu destop.

What might I not be doing correctly? Thanks for the help.

---

### Post by MrMunson on 2005-05-27
Hi!

Have you configured SMB to share the printer? 

I am running a much like setup at home. Have a Linux server (not Ubuntu but doesnt matter in this case) that shares both directories and my Samsung ML1510 laser printer connected to the Linux server using USB under CUPS. When I bring my M$ Win Xp work laptop home, I simply gave it the old
```
\\myhomeserversname\
``` in a Start --> Run line and pow, both the shared directories and my printer came up. Right-click on the printer and choose install or whatever it said, and Bob was my uncle.

If you want to use this setup, which I can only speak warm of, you must share the servers printer using SMB. I can't remember fro the top of my head how the SMB setup was sorted to share the printer. Hopefully someone else have all the details in their head. If not, post in this thread again and I shall try to publish a little quick'n'dirty How-To on the subject. Best of luck to you mate!  \\:D/

---

### Post by mobile.army on 2005-05-27
OK...so tonight I came home, turn on the computers and suddenly, while my linux box can see the windows xp stuff, windows xp doesn't see my linux box at all! Any idea where I should look? Would it just be easier to change the laptop over to linux as well?

---

