---
title: "Ubuntu 16.04: No launcher, no panel, unity problem"
date: 2016-09-14
forum: General Help
---

### Post by mukmakmuk on 2016-09-14
[COLOR=#111111][FONT=Ubuntu]I have a huge problem which has been adressed often: My launcher, panel, etc. is gone.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My system is Ubuntu 16.04 (on a notebook) and I was installing some themes (flatabulous, paper, arc, also installed ubuntu-tweak-tool and gtk-theme-config) and I don't know what exactly triggered it, but before I noticed the launcher and menu panel was gone.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I should note that my laptop was connected to my TV (and I put the display on the TV only) and I set the display to be scaled by a factor (1.35) on the TV and now that I have disconnected the TV, on the built-in monitor, the display still appears scaled! I tried reseting the scaling via system settings, but that doesn't work. Weird thing is also that when I login, the mouse stays at normal size for few moments and then gets enlarged now![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It gets wierder: When I login as a guest, the launcher and everything appears as it should (with correct scaling)! Also, when I type "unity" or something similar in the terminal, the menu panel appears for a second before disappearing again! It seems like something is overriding the unity or something like that.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What I have tried so far: All the 'dconf reset' and 'setsid unity' didn't work. I installed compiz-settings-things, tried enabling unity plugin (and enabled opengl, etc etc) and rebooted, and it didn't help. Also tried reinstalling ubuntu-desktop, unity, etc., no change. I'm slowly going crazy since I have the feeling I tried almost every solution I found via google. I also already uninstalled all themes I installed, but nothing changed.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If someone could help me, that would be GREAT! I'm going mad here T_T[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**EDIT:** I could reset the scaling by installing unity-tweak-tool again and change the font scaling setting there, so the whole problem might be related to this tool (changing the unity settings doesn't do anything though). I also realize that I can't resize windows, only maximize them.

[/FONT][/COLOR]**EDIT2 (Solved):**[COLOR=#111111][FONT=Ubuntu] I created a 2nd account (where unity worked without problems, of course) and compared the home directory of both accounts (the broken one and the new, normal, working one) and randomly deleted / renamed setting files and folders (the ones starting with "."; I clicked "show hidden files" before) in the broken directory which were different from the new account. Especially I also deleted the cache. When I logged back to the old account, suddenly the launcher (and panel) worked again. NO IDEA what exactly 'repaired' the problem, but for now, I'm just glad it works again. The icons on the launcher are reset, i.e. I have to dock my programs to it again, but I can definitely do that much.[/FONT][/COLOR]

---

### Post by ventrical on 2016-09-14
Hey .. great  work !

Regards..

---

### Post by x-contact-u on 2016-09-15
Just been climbing up the walls with the same problem - thanks for the post, it helped me fix it. 

I think this does the job:
1)  right-click on desktop and choose Open Terminal
2)  $ cd .config/dconf
3)  $ cp user user.bak

That will give you a back-up of your user profile, which is hopefully ok. 

Now remove the cache and user profile and log back in...
1)  Open a hard terminal using [Crtl]+[Alt]+[F1] - and log in
... I got tips from here [http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears#76951](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears#76951) but that method didn't work
2)  $ cd ~
3)  $ mv .cache x.cache
... note that you can delete 'x.cache' this at a later date
4)  $ cd .config/dconf
5)  $ rm user
6) Return to desktop using [Crtl]+[Alt]+[F7] or [Crtl]+[Alt]+[F8]

This should give you back a basic launcher and menu bar (as if you'd installed for the first time).

Now reinstate the user profile ... if that doesn't work maybe you could try a back-up if you have one?
1)  Open a hard terminal again using [Crtl]+[Alt]+[F1] - and log in if necessary
2)  $ cd ~/.config/dconf
3)  $ rm user
4)  $ cp user.bak user
5)  $ kill -9 -1

Final command should log you out. Fingers-crossed, when you log back in your desktop will be restored.

I hope that helps.

All the best.

---

### Post by HereInOz on 2016-09-15
I have had the same problem on two Toshiba laptops, and I solved it by installing Bleachbit, (right click the desktop > Open Terminal > sudo apt-get install bleachbit) and cleaning the system cache.  After that, the launcher and top panel returned.

Nothing else worked.

In case you are not all that familiar with the Terminal, run Bleachbit from the terminal with sudo bleachbit and that will open the Bleachbit GUI.  Close Bleachbit by using CTRL-C in the terminal, then sudo reboot in the terminal to restart.

---

