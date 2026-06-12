---
title: "Unity Tweak Tool destroyed my desktop"
date: 2013-04-30
forum: General Help
---

### Post by GreggyZed on 2013-04-30
I have been running Ubuntu 12.10 on my laptop for quite sometime with no problems.  Today I upgraded to 13.04 and had no problems until I used the Unity Tweak Tool to change the theme. I can't remember which theme I selected but it was one of the defaults and it caused my desktop to freeze. Now when I turn it on the login screen works but after logging in only the cursor and the desktop background appears. I can't even use the keyboard to open a terminal or anything and am stuck typing this out on my phone. If any of you have any ideas on how to fix this huge problem that has come out of nowhere, I would greatly appreciate it.

---

### Post by JRV on 2013-04-30
Tell us what Unity tweak tool you were using.  Was it MyUnity, Unsettings, or Ubuntu-tweak?

Try this:

<CTRL>-F1 to get to a terminal

```
unity --reset
```

---

### Post by grahammechanical on 2013-04-30
Can you use the keyboard to right click the desktop? If so, do a right click on the desktop and select Change Desktop Background. That will open System Settings and from there you can get to the Appearance utility and select either Ambiance or Radiance. Unity Tweak tool can do things that Appearance cannot do. It can do many of the things that the Compiz Configuration Settings Manager (CCSM) Ubuntu Unity Plugin can do but it is still very much under development as is Unity and we should accept the same warning for various tweak tools that are given for CCSM:

> **An advanced tool. Use with Caution**. This tool allows you to deeply configure Compiz's settings. Some options may be incompatible with each other. Unless used with care, it is possible to be left with an unusable desktop.

Regards.

---

### Post by manishiitg on 2013-04-30
it destroyed my desktop as well

---

### Post by hil4vitkutin on 2013-05-01
> **JRV said:**
> Tell us what Unity tweak tool you were using.  Was it MyUnity, Unsettings, or Ubuntu-tweak?

Try this:

<CTRL>-F1 to get to a terminal

```
unity --reset
```

There is a tool named 'Unity Tweak Tool',  and I guess GreggyZed used it in order to change settings.

In raring ringtail, you can not open a terminal window by pressing CTRL+F1. Try CTRL+ALT+F1.

You can then try logging in there, and after that type ```
unity --reset
```
However, I would suggest you to install dconf-tools and try to reset using it. I have found this method the best way to get the resetting done.

```

sudo apt-get install dconf-tools

dconf reset -f /org/compiz/

setsid unity

```

---

### Post by nevle on 2013-05-03
hi
not sure if it was ubuntu tweak to tool or not but i am using gnome3 desktop on 12.10, a recent upgrade. I am on a laptop and dont usually shut down but when i did i found that i have the same problem.used ctr-alt-t to get terminal and unit to get desktop. followed the above instructions but it made no difference, i get a login page with no options and when i login i just get the wallpaper, any help? Have lost all my gnome3 extentions and themes.

---

### Post by hil4vitkutin on 2013-05-03
[FONT=arial]Let me ask a few questions:

What do you mean by "no options"? Do you mean that you can't select the session you want to log on?
Did you follow my instructions? They will affect only Unity, not Gnome 3. 

However, you can reset your Gnome 3 like this:

1. Enter the terminal. If you have only the wallpaper, access the terminal by CTRL+ALT+F1 (You might need to enter your log on infromation at this point). CTRL+ALT+T should also make the trick. Then enter the following:
```

[B]rm -rf .gnome .gnome2 .gconf .gconfd .metacity
[/B]
```

2. Now your Gnome 3 settings should be restored. Press CTRL+ALT+F7 and log in. If you are still unable to get the Gnome 3 interface back, try rebooting at this stage.

If the steps above do not work after reboot, let's see what else could help.
[/FONT]

---

### Post by nevle on 2013-05-03
hi
thanks for your quick reply, at the login page i used to get a choice of sessions-ubuntu,gnome, etc but now there is none of those, i click on my pic  and it goes to my current wallpaper. No left/right click options, i can get terminal only with crt-alt-t. tried all of the above- no change (crl-alt-F7 didn't do anything)

---

### Post by hil4vitkutin on 2013-05-03
Well, okay let's try reinstalling your Gnome 3. Get to the terminal and type
```

sudo apt-get install --reinstall gnome-shell

```

[FONT=arial]Then let me know what it did.[/FONT]

---

### Post by nevle on 2013-05-03
just installed fluxbox, session didn't appear at login page but started from the terminal OK.

---

### Post by hil4vitkutin on 2013-05-03
Ubuntu 12.10 doesn't seem to detect your fluxbox, because you don't get  the options for selecting the session... You should have at least **two **valid sessions to be able to select among them.

[(http://askubuntu.com/questions/230241/why-am-i-missing-the-ubuntu-icon-on-the-log-in-screen]("http://askubuntu.com/questions/230241/why-am-i-missing-the-ubuntu-icon-on-the-log-in-screen"))

Maybe you should try reinstalling Gnome 3 with the instructions I posted and see if it gets listed at the login?

---

### Post by nevle on 2013-05-03
OK, reinstalled gnome-shell as above, no change. checked tweak tool, no extensions no themes ?? how do i start gnome shell from the terminal?

---

### Post by nevle on 2013-05-03
ok reinstalled gnome-shell but no change to anything..

---

### Post by philinux on 2013-05-03
> **JRV said:**
> Tell us what Unity tweak tool you were using.  Was it MyUnity, Unsettings, or Ubuntu-tweak?

Try this:

<CTRL>-F1 to get to a terminal

```
unity --reset
```


Unfortunately that doesn't work any more on 12.10 and later. 

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by hil4vitkutin on 2013-05-03
> **philinux said:**
> Unfortunately that doesn't work any more on 12.10 and later. 

Well this misconception was already corrected but thanks anyways :D

Do you philinux know any easy solution for nevle's problem? It seems to be quite complicated.

Nevle: You can start the Gnome shell from terminal by typing
```
 gnome-shell 
```

If I'm alone to solve this, I might need some time to get this sorted out...

---

### Post by nevle on 2013-05-03
just rebooted and after i got the terminal up i tried gnome -shell and there are many errors- something a bout ibus outdated??
also my usr/share/xsessions/  has flux,ubuntu,gnome,gnome classic in it.
exact error-
JS LOG: IBus version is too old
    JS ERROR: !!!   Exception was: Gio.DBusError: Error calling StartServiceByName for org.gnome.Shell.CalendarServer: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gnome-shell/gnome-shell-calendar-server received signal 5
 JS ERROR: !!!     message = '"Error calling StartServiceByName for org.gnome.Shell.CalendarServer: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gnome-shell/gnome-shell-calendar-server received signal 5"'
    JS ERROR: !!!     fileName = '"/usr/share/gjs-1.0/overrides/Gio.js"'
    JS ERROR: !!!     lineNumber = '240'
    JS ERROR: !!!     stack = '"0 anonymous(null)@/usr/share/gjs-1.0/overrides/Gio.js:240
1 CalendarServer()@/usr/share/gnome-shell/js/ui/calendar.js:213
2 anonymous()@/usr/share/gnome-shell/js/ui/calendar.js:242
3 wrapper()@/usr/share/gjs-1.0/lang.js:204
4 anonymous()@/usr/share/gjs-1.0/lang.js:145
5 anonymous()@/usr/share/gjs-1.0/lang.js:239
6 anonymous()@/usr/share/gnome-shell/js/ui/dateMenu.js:184
7 wrapper()@/usr/share/gjs-1.0/lang.js:204
8 anonymous([object Object])@/usr/share/gnome-shell/js/ui/dateMenu.js:151
9 wrapper([object Object])@/usr/share/gjs-1.0/lang.js:204
10 anonymous([object Object])@/usr/share/gjs-1.0/lang.js:145
11 anonymous([object Object])@/usr/share/gjs-1.0/lang.js:239
12 anonymous("role" = ""dateMenu"")@/usr/share/gnome-shell/js/ui/panel.js:1155
13 wrapper(""dateMenu"")@/usr/share/gjs-1.0/lang.js:204
14 anonymous("box" = [object _private_St_BoxLayout], "elements" = [object Array])@/usr/share/gnome-shell/js/ui/panel.js:1166
15 wrapper([object Array], [object _private_St_BoxLayout])@/usr/share/gjs-1.0/lang.js:204
16 anonymous()@/usr/share/gnome-shell/js/ui/panel.js:1120
17 wrapper()@/usr/share/gjs-1.0/lang.js:204
18 anonymous()@/usr/share/gnome-shell/js/ui/panel.js:969
19 wrapper()@/usr/share/gjs-1.0/lang.js:204
20 anonymous()@/usr/share/gjs-1.0/lang.js:145
21 anonymous()@/usr/share/gjs-1.0/lang.js:239
22 start()@/usr/share/gnome-shell/js/ui/main.js:144
23 <TOP LEVEL>@<main>:1
"'
Window manager warning: Log level 32: Execution of main.js threw exception: Gio.DBusError: Error calling StartServiceByName for org.gnome.Shell.CalendarServer: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gnome-shell/gnome-shell-calendar-server received signal 5

---

### Post by rrich1974 on 2013-05-03
just do a clean install and never use this kind of tools again.

---

### Post by hil4vitkutin on 2013-05-03
If you give me some time, I will try to look for a solution! Reinstall is the last resort, if we can't find any working solution for this.

Thanks for posting the error :)

---

### Post by philinux on 2013-05-03
I'm still waiting for the OP to get back in the thread.

---

### Post by nevle on 2013-05-03
Thanks hil4vitkutin, I've only recently install 12.10 and don't really want to do it again if i can get this fixed. Unity seems to work ok, but no hot corner and strangely i can only start synaptic through the terminal although it does give me a fonts error.

---

### Post by hil4vitkutin on 2013-05-04
> **philinux said:**
> I'm still waiting for the OP to get back in the thread.

I hope GreggZed has the same kind of problem as nevle does :P

---

### Post by hil4vitkutin on 2013-05-04
Huh? Could you clarify what do you mean by those "hot corners," do you mean that you can't set them up?

Does Unity start up normally after login? And do you want to get your Gnome 3 still working :P

First, fix if you have broken packages (if you have any)
```
[FONT=arial]
sudo apt-get -f install[/FONT]

```

Make sure you have all these installed (run this to see if you have):
```

sudo apt-get install gnome-shell metacity libcaribou0 libcaribou-common gir1.2-upowerglib-1.0 gir1.2-telepathyglib-0.12 gir1.2-json-1.0 libmutter0a gir1.2-caribou-1.0 gir1.2-gck-1 libmozjs185-1.0 mutter-common gnome-shell-extensions gir1.2-polkit-1.0 gir1.2-gcr-3 gir1.2-gkbd-3.0 gnome-icon-theme-full gir1.2-telepathylogger-0.2 gir1.2-gtop-2.0 gir1.2-coglpango-1.0 gnome-themes-standard gdm gjs gir1.2-accountsservice-1.0 gir1.2-ibus-1.0 gir1.2-gdesktopenums-3.0 xserver-xephyr gtk2-engines-pixbuf gir1.2-mutter-3.0 libgjs0c gir1.2-xkl-1.0    gir1.2-cogl-1.0    gnome-themes-standard-data gir1.2-clutter-1.0

```

---

### Post by nevle on 2013-05-04
Hi, reinstalled all those packsges, got 2 errors-unable to locate libmutter0a and gnome-themes-standard-data (have libmutter0 , gnome-themes-standard ). I am using fluxbox at the moment but usually use gnome-shell and would like to get it fixed. After logging in and getting my wallpaper, where am i, i cant be in a window manager otherwise i couldnt start fluxbox or unity without getting an error. If i understand correctly i have to fix gnome-shell which will then appear at my login page with the other options, the packages i reinstalled should have fixed gnome-shell?
Just rebooted-same as before-login drops me into a screen with my wallpaper, nothing else. I open a terminal and type wichever wm i want(apart from gnome3)

---

### Post by hil4vitkutin on 2013-05-05
> **nevle said:**
> If i understand correctly i have to fix gnome-shell which will then appear at my login page with the other options, the packages i reinstalled should have fixed gnome-shell?

Hello again. Yes this is exactly what I thought, but it didn't seem to work...

Do you have any session alternatives when you log in?

---

### Post by nevle on 2013-05-05
hi no alternatives. I installed fluxbox but it didn't appear at login so how can i manually add another wm to my sessions?? file/dir . Or perhaps i just don't turn off my computer.. :)

---

### Post by hil4vitkutin on 2013-05-05
Does [this]("http://askubuntu.com/questions/4645/how-do-you-add-a-new-window-manager-to-the-gdm-menu") help?

The content of your new gnome.desktop should look like this
```

[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```

Make sure that it's allowed to be run as an excecutable.

But this still won't fix the issue you are having when launching gnome-shell...


Also, would you post a list of the packages you have installed? Let's make sure that you have the required packages. You get the list by running
```
dpkg --get-selections > installed-software
```

I did some research on the internet, and your problem seems to be most likely related to broken packages. I'm running out of suggestions if re-installing the packages didn't work either :-k

---

### Post by nevle on 2013-05-05
i created a new .desktop file in xsessions, excecutable. Re-booted. same. I uploaded installed packages file for you but i think it might be time to consider re installing ubuntu, perhaps 12.04.  i'll wait for your reply, the computer still mostly works hmmm perhaps kde (no!)..a glass of cider maybe.

---

### Post by hil4vitkutin on 2013-05-05
Want to give one more try? :D

It looks like you do not have the following packages installed (see the list in step 2). You are also missing a few font packages, which could explain the font errors you got when starting synaptic via terminal. That last one is a package many other packages depend on, and you should have it installed. 

So what you could try for the last time is completely uninstalling and reinstalling the following. 

**1.** Get to your terminal, and start the synaptic package manager as sudo (sudo synaptic, I think you are familiar with this). It would be better if you don't start any WM at this point, stick to the terminal.

**2. **Mark the following packages for "complete removal". I want to emphasize *completely* :) 

evolution
*evolution-data-server*

[I]fonts-khmeros-core    
fonts-nanum
fonts-tlwg-garuda[/I]
*ttf-punjabi-fonts*

*lightdm-remote-session-uccsconfigure*

**3. **Install the packages above you just uninstalled (be sure to mark them all! :D )

**4. **Reboot and cross your fingers.

:P

---

### Post by nevle on 2013-05-05
hi hil4vitkutin, 
My login page remains the same (no options) BUT i now get straight into gnome3 desktop. YAY!
Even my font problem appears to have gone, and I can live with the login page quirk.
I can't thank you enough for all the time that you have spent on helping me with this problem, these forums are one of the main reasons i first used and continue to use ubuntu.
thanks

---

### Post by hil4vitkutin on 2013-05-05
Hi there!

Phew, what a relief that that worked :D Now I can spend all nights just watching movies ;)

Nice to hear that your major problems are now fixed if we don't count that "login page quirk" &#8211; I must now just hope that the original poster of this thread can utilise the same solution you did :) . I can still try to look for an answer why the options don't appear to the login page. I'll contact you by PMs, I think it's a separate issue and doesn't belong to this thread :P

You'll hear from me.

p.s. I don't really watch movies that much ;)

---

### Post by it.helpdesk.getech on 2014-03-17
&#65279;I am backup and running again. I call myself running the unity Tweek tool. Everything was running great until I decided to click on the desk top section what ever I click on my desk went by,by.. I want to think you here I don't know witch one here I use but my desk is back and my unity side bar is back. You guys save me the hassle of re-imaging my Ubuntu Laptop. Thank you, Thank you, Thank you...:)

---

