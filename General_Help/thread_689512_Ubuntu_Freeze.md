---
title: "Ubuntu Freeze"
date: 2008-02-06
forum: General Help
---

### Post by gobuntu on 2008-02-06
Dear comunity,

Just to report that I have had this happen a couple of times. It is not more due to the conditions, as described; also, it is not a very serious problem, at least here.

I use an ethernet cable directly to the phone company modem DSL.

This problem is as follows:

Not realizeing that the ethernet cable is NOT plugged in, I boot into Ubuntu Feisty (it has all upgrades and works fine), and Ubuntu boots all OK.

Then I click the Firefox (also latest and up-to-date), which triggers "Server not found". 

Then I connect ethernet cable in and refresh Firefox, which does bring the webpage.

And, AT THAT MOMENT, all is frozen: Mouse no-move no click, keyboard no response, workspaces don't shift, nada.

The only way is pushing the OFF button and keeping it pushed for a few seconds till computer turns OFF.

Then rebooting all works fine, including the internet, since by now I do have the ethernet cable plugged in prior to start.

My laptop is a HP dv82US, which works all OK as far as I know.

I don't believe I have experienced ths problem with XP.

Hoperully someone may check to see if this is an Ubuntu problem (or Firefox?), and leads to correction.

Thanks.

---

### Post by kevstar31 on 2008-02-08
Post the output of *cat /var/log/dmesg*
also you might be able to restart the computer when it is frozen using the following key strokes in order:
Ctrl+Alt+Sysrq+s
Ctrl+Alt+Sysrq+u
Ctrl+Alt+Sysrq+b( or Ctrl+Alt+Sysrq+o to just turn the computer off)

---

