---
title: "End process in ubuntu"
date: 2013-01-23
forum: General Help
---

### Post by babakflame on 2013-01-23
Dear guys
Hi
 When some programs like document viewer or multimedia players do not respond, I mean I can not close them, Is there any way like windows to make them end process ?

---

### Post by HermanAB on 2013-01-23
kill
killall
xkill

---

### Post by dino99 on 2013-01-23
you can use System Monitor and/or htop to list & kill the desired process(es)

and also google around "ubuntu killall"

---

### Post by omeomi on 2013-01-23
'killall' if you know the name or ID of the process 
'xkill' if it has a window

---

### Post by Impavidus on 2013-01-23
Kill & friends send SIGTERM (terminate signal) to the process in question by default. This is a kind request to the process to terminate, giving it a chance for creating emergency backups and proper clean-up. If it doesn't work you can use **kill -9**, which will send SIGKILL, causing immediate termination of the process.

---

### Post by furything on 2013-01-23
Why don't you just use terminal? 
To get complete list
```
sudo ps -A
```Then as previous post use kill with the id you want to close?
so VLC is Id 3145
```
sudo kill 3145
```or follow
 [http://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/](http://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/)
with grep to list just the process you want

---

### Post by babakflame on 2013-01-28
Dear guys
When my ubuntu hangs, I do not have access  to terminal, So how can I use kill directive?

  regards
  Babakflame

---

### Post by Impavidus on 2013-01-28
If your entire screen has frozen you could try ctrl+alt+F2 to switch to a console and use the commands there. Return to your graphical interface with ctrl+alt+F7. If nothing else works, type alt+SysRq+{r, e, i, s, u, b}. This will properly shutdown your computer and reboot.

---

### Post by raja.genupula on 2013-01-28
[http://www.howtogeek.com/107217/how-to-manage-processes-from-the-linux-terminal-10-commands-you-need-to-know/](http://www.howtogeek.com/107217/how-to-manage-processes-from-the-linux-terminal-10-commands-you-need-to-know/)

i found this link which can help you.

---

### Post by MoebusNet on 2013-01-28
The easiest way to force a misbehaving application window to close will be to use the force-quit *applet*:

[https://help.ubuntu.com/community/Applets](https://help.ubuntu.com/community/Applets)

This is a GUI way to put your mouse pointer on a misbehaving window for an application that refuses to close, and issue the force-quit command to that application. You use it by clicking on the force-quit applet icon on your task bar, then clicking on the misbehaving application window.

Maybe this is what you had in mind; hope it helps.

EDIT: With Unity the default desktop environment (I use Cinnamon), it is a little more involved to get a force-quit icon for the Unity Bar:

[http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/](http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/)

---

### Post by babakflame on 2013-02-01
DearBuddies
Hi
Thanks for all ur helps. I think that with ur helps I solved my problem.:guitar::guitar::guitar:

   Regards
    Babakflame

---

