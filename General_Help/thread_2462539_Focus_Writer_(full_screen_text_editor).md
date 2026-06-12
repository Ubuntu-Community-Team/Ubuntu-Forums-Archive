---
title: "Focus Writer (full screen text editor)"
date: 2021-05-23
forum: General Help
---

### Post by dddman on 2021-05-23
I would like to boot direct to Focus Writer instead of booting to the desktop. Since I'm not getting any good hits on this me thinks I may be trying to do something dumb or too much beer or both.

---

### Post by mIk3_08 on 2021-05-23
I don't really get what you mean. what you mean on writer? you mean text editors?
Text Environment? We have a lot of text Environment here.
We have GNU Emacs, Gedit, Vim, Nano text editor we also have python text editor language programing.
If you are about to do this text writer during on boot. we have server environment or you must 
have to do a secure pipe file script communication connection via client to server.
I don't really know what you are about to do but I hope this can give you an idea on the text writer.
I assume if you want an application writer we also have libre office writer. all of these are free to use.

---

### Post by dddman on 2021-05-23
I loaded it thru the software store, but here's  the site.

[https://gottcode.org/focuswriter/](https://gottcode.org/focuswriter/)

After login, I would go direct to Focus Writer

edit
drinking more beer must of helped, got a hit

[https://www.simplified.guide/linux/automatically-run-program-on-startup](https://www.simplified.guide/linux/automatically-run-program-on-startup)

---

### Post by mIk3_08 on 2021-05-23
ah! i see. what you mean, you want to load the Focus Writer during the start up boot? I think you can configure that one via start up application. just add up the app to the start up application then add a login script with your user and password so that when it boots up it opens directly to the app and logs you in.

---

### Post by dddman on 2021-05-23
Your talking about adding FW to here
[ATTACH=CONFIG]288531[/ATTACH]
And add a start script here.  Well that's way easier than the above method.  Thanks

---

### Post by mIk3_08 on 2021-05-23
Yes. I think the different is that the apps FW will only starts during the boot up but it will not directly opens that apps when your in the desktop environment. The instructions above will help you loads and opens the apps automatically when you gets into the desktop environment which is way cooler than the start up app. I think I must have to save that steps and guide too. Thanks

---

### Post by dddman on 2021-05-23
I followed the instructions 
[https://www.simplified.guide/linux/automatically-run-program-on-startup#automatically-run-program-on-gnome-startup](https://www.simplified.guide/linux/automatically-run-program-on-startup#automatically-run-program-on-gnome-startup)

and first try did nothing.

/usr/share/applications/focuswriter.desktop
I can double click on the desktop file and the FW program comes up.

/.config/autostart contains:

[Desktop Entry]
Type=Application
Exec=/usr/share/applications/focuswriter.desktop
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=FW
Name=FW
Comment[en_US]=autoswitch
Comment=autoswitch

**Edit**
A reinstall did nothing.

Systemd instructions are easy to follow, but the instructions dead ends with a 404.  Creating a systemd unit file.

Cron/rc.local both over my head.

I will either have to make autostart or systemd work.

---

### Post by dddman on 2021-05-23
Gnome will auto start a program at boot by pointing it to /usr/bin/focuswriter instead of /usr/share/applications/focuswriter.

This thread is getting marked solved, however... 

This is a tablet and my on screen keyboard comes up automatically, but is now hidden behind the text editor at boot :-?

---

### Post by dragonfly41 on 2021-05-23
xdotool can change window stack ..
[https://www.linux.org/threads/xdotool-%E2%80%93-window-stack.10687/](https://www.linux.org/threads/xdotool-%E2%80%93-window-stack.10687/)

---

### Post by dddman on 2021-05-23
Hello dragonfly41

That is a possibility.  I would prefer a GUI or maybe a gnome extension.  That is just about next on the to do list.

My automania is not yet finished.  I want to sign into windows and direct boot to Ubuntu which will now of course automatically bring up FW.  Win10 always in the background from the startup; an out of sight out of mind thing and that should be doable with Virtualbox.

---

