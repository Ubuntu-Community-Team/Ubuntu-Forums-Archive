---
title: "Kill Firefox ?"
date: 2007-07-06
forum: General Help
---

### Post by grekei on 2007-07-06
Have recently made fresh install of xubuntu "feisty".Firefox has been working ok but to day I tried to open it and got message that it was already running and to reboot to start again.I have rebooted several times but still no firefox, just repeat of message.I have uninstalled it and reinstalled it and got same result.I saw some where in my attempt at a solution that it was occupying space in the cache.I was going to try and kill the process from the command line but I am very new to this and can not find what I need to proceed.I have been reading tutorials and "Man" and probably will eventually find a solution if I study long enough .My immediate problem is ,some programmes are calling up firefox to load "docmentation & help files" and are still calling even though I have installed "Epiphany" and made it the default browser.I actually like "Epiphany" and will keep using it but I need to put firefox to sleep, it is obviously dragging on system resources .When I was running straight Ubuntu "Feisty",Firefox crashed a lot but I could always get it back ok.From my end with what little experience I have it feels like the problem is Firefox itself not the environment its running in.Any clues out their?Please.

Cheers Greg:)

---

### Post by Ayuthia on 2007-07-06
You might need to go into gconf-editor (Press alt-F2 and type gconf-editor). to change the calling of firefox as the browser.  Open up Desktop->gnome->applications->at->browser and change exec to be your favorite browser.

If you need to kill firefox, you can try going under System->Adminstration->System Monitor and select the processes tab.  Look for firefox and right click on it.  It should give you an option to kill the process.   If that does not work, you might try going into the Terminal and type:
ps -ef|grep firefox

If firefox is running, it should show up as a process and have a number attached to it.  It will be the first number after the username.  For example:
[FONT="Courier New"]
jayhawk@jayhawk:/$ ps -ef|grep firefox
jayhawk   8137 26283  0 14:21 pts/0    00:00:00 grep firefox
jayhawk  24213     1  0 07:22 ?        00:00:00 /bin/sh /usr/bin/firefox-granparadiso
[/FONT]
In this scenario, the process number is 24213 for firefox (I am running the alpha version of firefox so your firefox name will be different).  Just type:
kill 24213
Then check again by using the ps -ef grep firefox command.  If it is still there, you can use:
sudo kill -9 24213
And that should kill it.

Hope this helps.

---

### Post by grekei on 2007-07-06
Thanks for that.I am using the Xforce desktop ,so menus are a bit different but the similar GUI app. worked a treat.Firefox gave me the option to restore last session or start a new one,which I did and it seems to be working ok.Epiphany is working as the default browser,it was only embedded links in  various"how to's" that were calling up Firefox which I don't mind if it works or I know how to fix it when it does not.I will keep working on my command line ability and learn from this.
  Would still like to know why Firefox is crashing so regularly in "Feisty" ubuntu and xubuntu . My computer is an older Compaq notebook with a intel celeron 2800 Mhz CPU and 750Meg Ram .I hope its not a machine resources issue.If it is, it perhaps should not be the default browser for a supposedly "lighter" desktop system.
   Anyway,thanks again for the support and the solution.

   Cheers,Grekei:D

---

