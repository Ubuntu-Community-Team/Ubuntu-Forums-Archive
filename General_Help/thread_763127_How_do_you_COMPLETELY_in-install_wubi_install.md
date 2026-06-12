---
title: "How do you COMPLETELY in-install wubi install"
date: 2008-04-22
forum: General Help
---

### Post by thedoorguy on 2008-04-22
I un-installed wubi and it removed everything but the little menu right when I started the computer that asks you to  select windows or ubuntu.  

How do I get rid of that menu??

Now that I have install ubuntu by disk, when I select windows from the menu it installed... _it_ drops to the old wubi 2 selection menu.

Thanks in advance for your help.

thedoorguy aka Richard

---

### Post by ago on 2008-04-22
[https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267](https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267)

---

### Post by thedoorguy on 2008-04-23
> **ago said:**
> [https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267](https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267)

That Guide does not tell me how to get rid of the menu.  I already uninstalled, removed ubuntu from windows.... only the menu remains.  At that menu, selecting either windows or ubuntu, loads windows.

The only place I found any mention of the menu in windows was the config.sys file.  I deactived the line item but the menu still comes up.  Where else would wubi have posted a command?

thedoorguy

---

### Post by ago on 2008-04-23
> **thedoorguy said:**
> That Guide does not tell me how to get rid of the menu.  I already uninstalled, removed ubuntu from windows.... only the menu remains.  At that menu, selecting either windows or ubuntu, loads windows.

The only place I found any mention of the menu in windows was the config.sys file.  I deactived the line item but the menu still comes up.  Where else would wubi have posted a command?

thedoorguy

The guide is for XP and Vista, for 98 you have to edit config.sys, remove the menu block.

---

### Post by thedoorguy on 2008-04-23
> **ago said:**
> The guide is for XP and Vista, for 98 you have to edit config.sys, remove the menu block.

That worked!  Thanks ago!  You are a big help!  Wish I could get your kind of help on a couple of other non-wubi related threads I've got going. One has received 1 reply, the other, 0. Where is one suppose to go for help if they can't get it on the forum? It is really frustrating.

Thank You!

thedoorguy aka Richard

---

### Post by ago on 2008-04-23
I learnt linux by trying to fix things by myself (with some google help).... It takes longer but you  are far better off in the long term... ;)

---

