---
title: "[SOLVED] KDE 4 won't die..."
date: 2008-05-31
forum: General Help
---

### Post by vvvladut on 2008-05-31
I did a fresh install of Kubuntu KDE 4 but then I dedided I didn't like it so I went and installed KDE 3.5. I like KDE 3.5 a lot and so I wanted to get rid of all the KDE 4 packages. I removed most of the KDE 4 packages manually, then I followed someone's advice and ran this:

```
$ sudo aptitude purge ~nkde4
```

This removed about 40 other packages which I had missed before and so I thought I had got rid of all of KDE 4 for good. And I did, with one exception:

**The login menu has a KDE 4 theme (I think it's named Oxygen), including the mouse cursors. Whatever theme I try to select from the settings manager is does not change the current theme! How do I change it and get rid of it for good??**

Many thanks!

---

### Post by zekica on 2008-05-31
Can you try in terminal:
**sudo dpkg-reconfigure kdm**

or uninstalling **kdm-kde4**

---

### Post by vvvladut on 2008-05-31
> **zekica said:**
> Can you try in terminal:
**sudo dpkg-reconfigure kdm**

or uninstalling **kdm-kde4**

kdm-kde4 is not installed

I ran the first command and it did not produce any output. I logged out and back in, and the login manager is the same KDE 4 one...what now? Is there no way to get rid of it?

---

### Post by disturbedite on 2008-05-31
that doesn't make any sense at all.  if you are getting the kde4 login, then kdm-kde4 has to be installed.
is kdm installed?  if it is, then you should execute that command (sudo dpkg-reconfigure kdm) & set it to kdm instead of kdm-kde4.

---

### Post by vvvladut on 2008-05-31
> **disturbedite said:**
> that doesn't make any sense at all.  if you are getting the kde4 login, then kdm-kde4 has to be installed.
is kdm installed?  if it is, then you should execute that command (sudo dpkg-reconfigure kdm) & set it to kdm instead of kdm-kde4.

```
ankavlad@ankavlad-desktop:~$ sudo apt-get purge kdm-kde4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kdm-kde4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

As I said, kdm-kde4 is not installed...

I did execute that command and it did not prompt me for anything...

```
ankavlad@ankavlad-desktop:~$ sudo dpkg-reconfigure kdm
ankavlad@ankavlad-desktop:~$
```

It didn't do anything...now what?

---

### Post by Zorael on 2008-05-31
Owkay. There's a kde3 *and* a kde4 variant of that theme you're describing (Circles). Likely you're running kde3's kdm and you just need to reset it to use the default one.

Disclaimer: This is the terminal way. There's like a GUI one to do it too, with some random app I don't know about. Make backups of files along the way if you want to be on the safe side.


Check the contents of [FONT="Courier New"]/etc/X11/default-display-manager[/FONT]. It should say '**/usr/bin/kdm**'.
```
$ cat /etc/X11/default-display-manager
/usr/bin/kdm
```

Now, make sure [FONT="Courier New"]/etc/kde3/kdm/kdmrc[/FONT] has its theme set to '**@@@ToBeReplacedByDesktopBase@@@**' and that [FONT="Courier New"]backgroundrc[/FONT] in the same directory has the background set to '**default_blue.jpg**'. This command will check it for you.
```
$ grep default_blue.jpg /etc/kde3/kdm/backgroundrc > /dev/null && grep -i tobereplaced /etc/kde3/kdm/kdmrc > /dev/null && echo All is well
```
If it *didn't* output 'all is well', then we'll need to restore one of those files to its original state. If so, post their contents - within code tags, please.

Now, open up [FONT="Courier New"]/etc/default/kdm.d/20_kubuntu_default_settings[/FONT]. Make sure **USETHEME=** is set to "**true**", and that **THEME=** is set to "[FONT="Courier New"]/usr/share/apps/kdm/themes/kubuntu[/FONT]" *or* "[FONT="Courier New"]/usr/share/apps/kdm/themes/kubuntu-no-userlist[/FONT]", depending on whether you want the userlist or not.

---

### Post by Zorael on 2008-05-31
As for the cursor, enter this in a terminal.
```
$ sudo update-alternatives --config x-cursor-theme

There are 7 alternatives which provide `x-cursor-theme'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/share/icons/DMZ-White/cursor.theme
          2    /usr/share/icons/DMZ-Black/cursor.theme
          3    /etc/X11/cursors/core.theme
          4    /etc/X11/cursors/redglass.theme
          5    /etc/X11/cursors/whiteglass.theme
          6    /etc/X11/cursors/handhelds.theme
          7    /etc/X11/cursors/oxy-white.theme

Press enter to keep the default[*], or type selection number:
```
DMZ-White is the Kubuntu (kde3?) default. oxy-white is the kde4 one.

---

### Post by dr.koljan on 2008-05-31
Just switch to GNOME :P

Or if you like KDE3 this much, you could just completely remove all the packages starting with a "k" ***EXCEPT FOR*** klibc-utils and klogd, then install kubuntu-desktop metapackage. This way you will have only kde3-related packages with fresh configuration files.

---

### Post by vvvladut on 2008-05-31
OK, let's take it from the...bottom:

1. I did run the cursor theme changing command, and indeed it was set to oxy-white. I changed it to DMZ-White. Let's hope it stays this way.

2. The contents of /etc/X11/default-display-manager do say /usr/bin/kdm, just like you said.

3. The grep command spit out something nasty at first, but then I noticed you had a typo in there, so I ran it again and now it says:

```
ankavlad@ankavlad-desktop:~$ grep default_blue.jpg /etc/kde3/kdm/backgroundrc > /dev/null && grep -i tobereplaced /etc/kde3/kdm/kdmrc > /dev/null && echo All is well
All is well

```

4. I opened /etc/default/kdm.d/20_kubuntu_default_settings and this is what's in it:

```
USETHEME="true"
THEME="/usr/share/apps/kdm/themes/kubuntu"
USEBACKGROUND="true"
WALLPAPER="/usr/share/wallpapers/kubuntu-wallpaper.jpg"
USESYSTEMLOCALE="true"
FACESOURCE="PreferUser"
```

So...what next?

---

### Post by Zorael on 2008-05-31
Huh. Everything *looks* right. Terminal output of this?
```
$ ps -A | grep -i kdm
```

edit:
> Just switch to GNOME :P
Pah. KDE >> Gnome = Xfce. :>

---

### Post by vvvladut on 2008-05-31
```
ankavlad@ankavlad-desktop:~$ ps -A | grep -i kdm
 1685 ?        00:00:00 kdm
 5065 ?        00:00:00 kdm
 5106 ?        00:00:00 kdm

```

I have no idea what this means, does this look all right?

---

### Post by vvvladut on 2008-05-31
> **dr.koljan said:**
> Just switch to GNOME :P

Ummm...no.

> **dr.koljan said:**
> Or if you like KDE3 this much, you could just completely remove all the packages starting with a "k" ***EXCEPT FOR*** klibc-utils and klogd, then install kubuntu-desktop metapackage. This way you will have only kde3-related packages with fresh configuration files.

Ummm...no. I already did something similar once. I've got the feeling it's nothing big so I want to fix it if possible without reinstalling anything.

---

### Post by Zorael on 2008-05-31
Yes, it means you're properly running kde3 and not kde4.

After performing changes, how are you restarting X? With Ctrl+Alt+Backspace? You just may need to switch to a tty terminal (Ctrl+Alt+F1), log in, and restart kdm from there.
```
$ sudo /etc/init.d/kdm force-reload
```
edit: If you're rebooting, then you needn't do that, something else it causing it.

---

### Post by TrashmanL on 2008-05-31
Since I installed KDE4, I have had problems running sudo. (I have those listed in another thread). To restore gdm using the dpkg command above, instead of using sudo in KDE/GNOME, select "Console Login" from the login options in kdm, login as root, then run the command (or run gdm, login as root, run a terminal, then run the command). That's what worked for me so I could restore some functionality to my computer.

---

### Post by vvvladut on 2008-06-01
I did the force-reload thing, and...finally, it worked! Thanks zorael! I see my regular mouse cursor theme and I can modify the settings. I think what happened was that I did have the KDE 3 login manager all along, only it was stuck with a KDE 4 theme, and the settings wouldn't change! Strange...

But wait, I still have a small problem... Now my settings are saved when I go to System Settings > Advanced > Login Manager - I get to change the fonts, mouse theme, background and whatnot. However, I see in System Settings > General > Appearance a tab named KDM Theme Manager. This is apparently supposed to assign an overall theme to the login manager, but it doesn't work! Nothing happens regardless of what theme I choose.

How is this supposed to work anyway? Does this supersede the settings from the Login Manager applet? What is the purpose of this if it doesn't work and why isn't it integrated with the other applet (which works)?

---

### Post by Zorael on 2008-06-01
Again, that theme (Circles) is included in both kubuntu-desktop and kde4-kdm. I don't think kde3 and kde4 themes are otherwise compatible? Don't quote me on that.

**If making changes via that KDM Theme Manager you mentioned, keep in mind that you likely need to do the force-reload command to actually see any difference.**


On the topic of configuring kdm, it works a bit weirdish. [FONT="Courier New"]/etc/kde3/kdm/kdmrc[/FONT] is the configuration file, with options concerning the whole X session. Obviously, this includes the login screen, so there's a proper Greeting section in there, with tags like the USETHEME= and THEME= ones we talked about earlier. HOWEVER, Kubuntu doesn't come with its "own" Kubuntu kdmrc, but rather with a file that overrides kdmrc settings, which would be the [FONT="Courier New"]/etc/default/kdm.d/20_kubuntu_default_settings[/FONT] file. If you use an application to change login manager settings, there's a chance that it modifies the kdmrc file, over which [FONT="Courier New"]20_kubuntu_default_settings[/FONT] take precedence. This, at least, is the case with the built-in Login Manager app under System Settings -> Advanced.

By design decision, upon start of KDM it reads [FONT="Courier New"]/etc/kde3/kdm/kdmrc[/FONT] and [FONT="Courier New"]backgroundrc[/FONT] (in the same folder). Then it considers their content to see if they're *unmodified* (kdmrc's THEME set to *@@@ToBeReplacedByDesktopBase@@@* and backgroundrc's WALLPAPER set to *default_blue.jpg*). If they are, it proceeds to import files from [FONT="Courier New"]/etc/default/kdm.d/[/FONT] and use their settings to override those found in the real kdmrc and backgroundrc files. If you use the Login Manager and change the background, it won't import the Kubuntu default settings and you lose your themed login (background no longer default_blue.jpg). Likewise, if you use another app that can manually set a theme, upon doing so, it won't import the Kubuntu defaults, and you lose your Kubuntu background (theme no longer @@@ToBeReplacedByDesktopBase@@@).

This isn't a big deal if you have apps with which to take care of it. Using only the default ones, though, there is no graphical interface to pick themes; the Login Manager under System Settings can change background and modify greeter text strings ("Welcome to <servername>, plrx login ktx"), along with some other non-theme related settings.

Better put, it isn't a big deal if you know what's *happening*. I just stumbled upon the Login Manager when exploring KDE's configurability and thought "..the hell, that's not the login background I have, *ker-change*". I went as far to reinstall to get it back.

I don't know how the KDM Theme Manager works. If it changes kdmrc and backgroundrc manually, be prepared for some unexpected behavior.

---

### Post by vvvladut on 2008-06-01
I can't really say I understood much of what you said there...but you do seem to know KDE inside and out. All I gather is that KDM Theme Manager might cause some unexpected behaviour...in my case that behaviour is that it doesn't seem to do anything at all. Oh well, I don't really need a "theme", as long as that other applet works, and is much more useful.

I'm going to mark it as solved, but since we opened this discussion, there is something else regarding the login macager that is bothering me: I remember I had a virtual machine running PC BSD with KDE 3.5 and right after I typed my username and password it would show some sort of progress bar, only instead of a bar there were cute icons which were being highlighted one after the other, along with some messages like "Loading desktop" "Loading network". I also saw this on a friend's computer running openSUSE so I hope it's not BDS related. I thought it was cute in a geeky kind of way, so I was wondering if you knew how to install that? Thanks.

---

### Post by Zorael on 2008-06-01
That's the KDE splash (ksplash).

Install the **ksplash** and optionally the **ksplash-engine-moodin** packages. I'm not sure what the latter does but its description seems promising.
```
$ apt-cache search ksplash
ksplash-engine-moodin - fading splash screen engine for KDE
ksplash - the KDE splash screen
```
Pop up System Settings, then pick Splash Screen.

---

### Post by Zorael on 2008-06-01
While we're talking KDM and login appearance, this is how to change the pre-logged in backgrounds. Since I only have one user on this machine I changed them to the same pic. Made things smooth, no flashing backgrounds between login steps. Make backups of mentioned files first.

[list=1][*]Save wallpaper somewhere public. The default location is in [FONT="Courier New"]/usr/share/wallpapers/[/FONT].
[*]Modify the WALLPAPER= line in [FONT="Courier New"]/etc/default/kdm.d/20_kubuntu_default_settings[/FONT] to point to it. For instance, my line;
```
WALLPAPER="**/usr/share/wallpapers/Emotion/1280x1024.jpg**"
```
To my knowledge, it should scale it to fit the screen, so picking a low resolution version may be inadvisable.
[*]Modify your theme .xml file in [FONT="Courier New"]/usr/share/apps/kdm/themes/*<theme name>*[/FONT] to also point toward it. The line you want to alter is this one:
```
        <item type="pixmap" >
                <normal file="**/usr/share/wallpapers/Emotion/1280x1024.jpg**" />
                <pos width="100%" x="0" y="0" height="100%" />
```
[*]Change your own user's wallpaper to the same pic, through whatever GUI interface you're used to.
[*]Either:
[list][*]Reboot, or...
[*]...log out, Ctrl+Alt+F1 to get to textual interface, log in, restart kdm from there.
```
$ sudo /etc/init.d/kdm force-reload
```[/list]
[*]All done, rejoice.[/list]

---

### Post by vvvladut on 2008-06-01
Woohoo - **ksplash** rules! :) I love the geeky output messages such as: "Setting up interprocess communication" or "Pre-compiling binary hypervisors for entropy generator configuration" (OK I made the last one up, but it would be cool to be able to set uo your own texts:)

As for pre-logged in background, I'm not sure what you mean: I can change the login screen background, and the only screen I see before that is the black one with kubuntu written in blue and the blue progress bar - but I think that looks pretty cool and I don't want to change it.

---

### Post by Zorael on 2008-06-01
You could make your own splash, I guess. Perhaps you can change the strings there. [http://docs.kde.org/kde3/en/kdebase/ksplashml/themes.html](http://docs.kde.org/kde3/en/kdebase/ksplashml/themes.html)

There are three "backgrounds", sort of. Listed in order of appearance:
[list=1][*]The **usplash** (not ksplash), which is displayed upon boot. The Kubuntu text with the loading bar. This is *before* the graphical interface (X) has been loaded.
[img]http://cactusdigital.net/wp-content/uploads/usplash_kubuntu.png[/img]


[*]The default background of X, displayed before a themed login or during a non-themed login, as well as after the login but before your personal wallpaper has been loaded. Defined in backgroundrc.
[img]http://files.ruphy.org/2007/11/vladstudio1.jpg[/img]
(Not the default in Hardy but you get the idea. Any random wallpaper.)


[*]The background during a themed login, defined in the theme's .xml file
[img]http://upload.wikimedia.org/wikipedia/commons/thumb/1/10/Kubuntu_8.04_login_screen.png/350px-Kubuntu_8.04_login_screen.png[/img]


[*]Your desktop wallpaper, displayed after having logged in. Defined in your own user settings, so varies between environments (KDE, Gnome, Xfce, etc.)
[img]http://deviceguru.com/files/kubuntu804-default-desktop-sm.jpg[/img][/list]
Suffice it to say that if these aren't the same (for instance, if you change your login theme, leave the X background to Kubuntu's default, and set your desktop wallpaper to something else), there'll be some furious wallpaper-changing going on.

As described in the earlier post, changing these entails toiling in configuration files, so it's obviously not something Joe User would do. I just thought I'd list it if you wanted to try it out.

---

### Post by vvvladut on 2008-06-02
I see, thank you for the explanation. I do see the usplash, the login manager background and of course, the desktop wallpaper, but there is no X default background. After the usplash progress bar reaches the end, the screen goes black, then the "working" cursor appears briefly and then the login screen appears in all its glory. I changed the background of the login screen to match the desktop wallpaper and the transition seems seamless. 

So now I see a total of one progress bar screen (usplash) and then my desktop wallpaper, with the login window and then the actual desktop. I like the usplash as it is and all the rest is easily configurable now. Life is good.

Thank you for your help, you seem one of the few people in this forum who knows KDE and loves to share knowledge. I am absolutely in love with KDE (3.5 much more than 4), and I prefer any of them to Gnome or any other desktop environment.

---

### Post by Zorael on 2008-06-02
Not at all, most welcome.

Please tag the thread as solved under Thread Tools though. Makes it easier to parse the thread list. :>

---

