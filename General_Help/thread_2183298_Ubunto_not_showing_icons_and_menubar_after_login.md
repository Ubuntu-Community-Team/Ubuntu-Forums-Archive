---
title: "Ubunto not showing icons and menubar after login"
date: 2013-10-24
forum: General Help
---

### Post by HierisIngo on 2013-10-24
[COLOR=#333333][FONT=UbuntuRegular]Hello,[/FONT]

[FONT=UbuntuRegular]I did install Ubuntu 13.10 on my old PC. Everything went fine except for when I login into my account there is no menubar, no icon bar, just only my wallpaper (in the loginscreen the menubar is available) . I can do thing like creating a new folder and even access settings (so I did setup my internet connection) and I can access the log thingy (forget how to call it) by pressing ctrl+alt+F1, but I can't do anything else with it. I had this same issue also when I did try to Install Ubuntu in the past (that was version 12.Idontknowanymore). I did spend this many hours searching how to fix this on the internet, but without any succes.[/FONT]
[FONT=UbuntuRegular]My computer isn't really super, I think it has about 1GB RAM, and the original OS is Windows XP (I did pick the 32Bit version of Ubuntu).[/FONT]
[FONT=UbuntuRegular]Does anyone knows how I can fix this problem and start using Ubuntu? Thanks[/FONT]
[FONT=UbuntuRegular]Sincerely, Ingo[/FONT]
[/COLOR]

---

### Post by philinux on 2013-10-24
Try this.

open a terminal ctrl + alt + t and then type in nautilus and hit return

Now press ctrl h to show the hidden files.

Navigate to the folder .config and delete the folder compiz-1

close nautilus and then in the terminal type in gnome-session-quit and logout then log back in.

---

### Post by alan tam on 2013-10-24
This something to do with your graphic card support. 
You may restart your PC at grub loader, instead of login in as usual, you safe boot your pc to low graphic mode.
Once you get into the low graphic mode, you should see menubar and icons. Go to the user accounts in setting. Create a new user with admin rights.
reboot your pc and login with the new user name you created in the low graphic mode. you should have a full functioning desktop screen.
Thought this is not the best method but it works for me when i have the same problem.

---

### Post by HierisIngo on 2013-10-24
> **philinux said:**
> Try this.

open a terminal ctrl + alt + t and then type in nautilus and hit return

Now press ctrl h to show the hidden files.

Navigate to the folder .config and delete the folder compiz-1

close nautilus and then in the terminal type in gnome-session-quit and logout then log back in.
Thanks for the answer. But it doesn't work... :(

> **alan tam said:**
> This something to do with your graphic card support. 
You may restart your PC at grub loader, instead of login in as usual, you safe boot your pc to low graphic mode.
Once you get into the low graphic mode, you should see menubar and icons. Go to the user accounts in setting. Create a new user with admin rights.
reboot your pc and login with the new user name you created in the low graphic mode. you should have a full functioning desktop screen.
Thought this is not the best method but it works for me when i have the same problem.
Thanks for the answer. But how exactly do I do that? I mean booting in low graphics mode? I'm new in Linux and stuff, I did try some things, but my problem still isn't solved. I did boot in recovery mode with failsafeX graphics, but when I do it I get "The system is running in low-graphics mode" error and the rest of the screen is completely black.
Thanks.

(Quick note; I forgot to say in the post that the menubar is available in the login screen, but when I login it disappear leaving only my wallpaper left and I few files I put there)

---

### Post by philinux on 2013-10-24
Lets just check if the unity plugin is active.

ctrl alt t

and then use this.

```
setsid unity
```

The screen will flicker flash etc just leave it to settle down. Report back after.

---

### Post by HierisIngo on 2013-10-24
> **philinux said:**
> Lets just check if the unity plugin is active.

ctrl alt t

and then use this.

```
setsid unity
```

The screen will flicker flash etc just leave it to settle down. Report back after.
Alright thanks, I did get this:

```
hierisingo@ubuntu:~$ setsid unityhierisingo@ubuntu:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.


compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.


compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Stopping plugin: session
compiz (core) - Info: Unloading plugin: session
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Unloading plugin: resize
compiz (core) - Info: Stopping plugin: workarounds
compiz (core) - Info: Unloading plugin: workarounds
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Unloading plugin: place
compiz (core) - Info: Stopping plugin: snap
compiz (core) - Info: Unloading plugin: snap
compiz (core) - Info: Stopping plugin: regex
compiz (core) - Info: Unloading plugin: regex
compiz (core) - Info: Stopping plugin: mousepoll
compiz (core) - Info: Unloading plugin: mousepoll
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Unloading plugin: imgpng
compiz (core) - Info: Stopping plugin: gnomecompat
compiz (core) - Info: Unloading plugin: gnomecompat
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Unloading plugin: move
compiz (core) - Info: Stopping plugin: vpswitch
compiz (core) - Info: Unloading plugin: vpswitch
compiz (core) - Info: Stopping plugin: commands
compiz (core) - Info: Unloading plugin: commands
compiz (core) - Info: Stopping plugin: decor
compiz (core) - Info: Unloading plugin: decor
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Unloading plugin: compiztoolbox
compiz (core) - Info: Stopping plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Stopping plugin: ccp
compiz (core) - Info: Unloading plugin: ccp
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core



```

---

### Post by Samuel_Peters on 2013-10-24
Try wiping linux from your hardrive including any backup partitions and reinstall it. Just remember to backup your files on a cd-ROM first though.

---

### Post by TheReverend403 on 2013-10-24
Yeah, I'm having this exact same problem. The menu and icons ARE there, I can click them and the menus work, they are just invisible like so:

[IMG]http://i.revthefox.co.uk/MGM1O[/IMG]

---

### Post by HierisIngo on 2013-10-24
> **Samuel_Peters said:**
> Try wiping linux from your hardrive including any backup partitions and reinstall it. Just remember to backup your files on a cd-ROM first though.
Thanks for you're sugestion, but I think I have reinstalled Ubuntu like 10 times before, and it's everytime the same story... :(

> **TheReverend403 said:**
> Yeah, I'm having this exact same problem. The menu and icons ARE there, I can click them and the menus work, they are just invisible like so:

[IMG]http://i.revthefox.co.uk/MGM1O[/IMG]
Yep, it's an super frustrating problem.

---

### Post by TheReverend403 on 2013-10-24
OK, it seems to work fine under Linux 3.8.0-32-generic

nfi why...

---

### Post by HierisIngo on 2013-10-26
I type this from Xubuntu, and it works! ^_^
Xubuntu is just as good as Ubuntu, maybe even better for my PC because is lighter.

Thanks for the help everyone, but it&#347; not needed anymore.

---

