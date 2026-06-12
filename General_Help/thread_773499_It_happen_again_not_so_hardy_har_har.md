---
title: "It happen again not so hardy har har"
date: 2008-04-28
forum: General Help
---

### Post by rab4567 on 2008-04-28
I lost my launch panels for the second time after another reinstall  and think its the vedio card (nvidia geforce 6150 LE) on a hp a1450n AMD 4200 x2 2gb. Perhaps it a bug in hardy or an error on the iso disc that had hardy. But I cannot access anything not even the terminal can anyone help me? See before and after

---

### Post by -grubby on 2008-04-28
Gnome panel is probably crashing. Though it isn't a permanent solution, if it crashes you can always press alt+F2 and enter "gnome-panel", which should give you your panel back

---

### Post by schauerlich on 2008-04-28
Press alt+F2 and enter "gnome-panel" to get your panel back. Go to System>Preferences>Sessions and add gnome-panel to your session. That way, should your panel decide not to start on its own, your sessions file will tell it to.

---

### Post by bingoUV on 2008-04-29
> **rab4567 said:**
> I lost my launch panels for the second time after another reinstall  and think its the vedio card (nvidia geforce 6150 LE) on a hp a1450n AMD 4200 x2 2gb. Perhaps it a bug in hardy or an error on the iso disc that had hardy. But I cannot access anything not even the terminal can anyone help me? See before and after

 Have you retained your /home partition from last install?

---

### Post by rab4567 on 2008-04-29
The first thing I did was to hit alt. f2 but to no avail, the only thing I can do is change the back ground and get the  help page (f1). Its like everything is there but I can't get to it.

PS Oh yeah I can take screen shot but thats it very strange.

---

### Post by retrow on 2008-04-29
I had improvised to a solution when my gnome-panel was accidentally removed because I autoremoved something and didn't read what else it removed.

I see you have a hard disc icon on your desktop. Right click on that icon (or any folder icon for that matter) >> Open With other application >> Use a custom command >> **Type in** *gnome-terminal* >> open

When you have a gnome-terminal open, you can open gnome-panel, and then go from there.

---

### Post by rab4567 on 2008-04-29
OK update I rebooted to the login page and notice  a little options icon which allows me access to the gnome terminal. Great I typed in 

sudo apt-get install gome-panel

boom got everything back but got some errors MMM got any ideas I think its got something to do with  the screen resolution.

---

### Post by rab4567 on 2008-04-29
Thanks guys for all the help I've been watching the forums for similar problems people are having with the panels this is the fix

Press CTRL + ALT + F2
login and password
sudo apt-get remove gnome-panel  
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop
restart

I would like to know what is causing this because if I am going to install hardy on people's computers this could be a deal breaker.

I'm back

---

