---
title: "Japanese (SCIM, SKIM..) input in Xubuntu"
date: 2007-05-04
forum: General Help
---

### Post by ubuntu27 on 2007-05-04
Salut! I have a friend who has an old computer with WIndows 98 Operating System. I haven't seen her computer personally but I bet it is really old since it has win98. The thing is that she want her computer to be able to input Japanese, and since I doubot that it will run UBuntu, maybe I could try Xubuntu in it.

So, is there a way to have Japanese input in Xubuntu? All the guides that I found are for either KDE or GNOME, but not Xfce...

Anobody experienced in this?

---

### Post by ubiwankanubi on 2007-05-04
find a guide that shows how to install scim. scim will work on xfce.

I use chinese and japanese on feisty, i don't remember all the steps, but i think it was pretty simply, sudo synaptic, mark scim and scim plugins for japanese. I think that's pretty much it, unless i'm missing a step.

oh yeah, this is it:

[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

You can install CJK input via ubuntuaddon or do it via internet.
Ubuntu already comes with Chinese, Japanese and Korean fonts preinstalled.

To install via internet (universe repositories must be enabled)
sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-chinese scim-hangul scim-tables-zh scim-tables-ja scim-tables-ko

Add SCIM to startup for X11
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

---

### Post by ubuntu27 on 2007-05-04
Thank you Ubiwan Kenobi. :)

---

### Post by Sef on 2007-05-04
If you use Feisty, I would suspect that would be much easier.   I was able able to get Korean going (for the first time) without using any command lines.

---

### Post by bren21 on 2007-05-04
I would suggest following the tutorial [here]("http://ubuntuforums.org/showthread.php?t=338991&highlight=japanese"). It got japanese working on Feisty for me. I use gnome but it should work on xubuntu

---

### Post by ubuntu27 on 2007-05-05
Yeah, so Xubuntu uses gtk just like Ubuntu... :) there should not bne a probelm then.
THe only thing that I think that it will be a problem is that... who knows how much HD space her computer has.

---

