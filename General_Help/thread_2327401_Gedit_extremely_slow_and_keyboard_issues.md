---
title: "Gedit extremely slow and keyboard issues"
date: 2016-06-10
forum: General Help
---

### Post by leozinho29_eu on 2016-06-10
Hello

After I have tested Ubuntu MATE in a USB, I decided to install it. However, I did not wished to delete Lubuntu or install another operational system in another partition. So I have installed the mate-core package. It was already a Frankenbuntu with some Debian parts, but was running well and there were just minor bugs related to the volume controller. Mate is very good, the volume controller works correctly, uses some resources more, but there's still plenty of free memory. 

However, some issues have (re)appeared in Lubuntu.

First: gedit became very, very slow. Trying to write, paste, copy, select, everything. A new message appeared when opening it using the terminal:

```
(gedit:4507): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

This message do not appear and the performance is very good when running gedit as superuser. No other software was affected (at least I have seen none with similar problems).

Second: a annoying keyboard bug, which makes some character that I pressed to be ignored. This is clearly notable when trying to search files in folder. This bug was driving me crazy with Lubuntu 14.04. I upgraded the system to 16.04 and it disappeared. Now it is back. 

Looks like some configurations were changed due to mate-core installation. If I know which ones are the responsible for this, I could change them.

Thank you.

---

### Post by sudodus on 2016-06-10
I have problems with gedit in 16.04 LTS too. I have started using ***geany*** instead, and it is a very good alternative. Another alternative is ***pluma***, the MATE fork of gedit.

I don't know why you have a problem with the keyboard. I have only a simple suggestion how to fix it: Have you used the ***'language support'*** tool to make sure that the language support is consistent and up to date?

---

### Post by vasa1 on 2016-06-10
> **sudodus said:**
> I have problems with gedit in 16.04 LTS too. ...
What sort of problems? Is this with Lubuntu 16.04? I installed gedit using "--no-install-recommends" and I'm not facing any issues in Lubuntu's Openbox session. Launching gedit via the terminal doesn't throw up any messages.

---

### Post by sudodus on 2016-06-10
It is very slow (like it is causing swapping, but I have 4 GB RAM). It happens also when started from a terminal window in a Lubuntu session. (I have Xubuntu desktop and Lubuntu desktop installed. So gedit came with Xubuntu.)

I had no such problems with gedit before I installed this Xenial system.

---

### Post by leozinho29_eu on 2016-06-10
The keyboard issues were happening since Lubuntu 14.04. After I have installed the 16.04 version, the keyboard errors have stopped. Now, likely due to a configuration that was changed with the mate-core package, the keyboard is problematic again. The keyboard issue happens on both Mate and Lubuntu. When I was accessing the forums, a example of the error happened.

I wrote in the keyboard:
```
[www.ubuntufor]("http://www.ubuntufor")
```

And the result was:
```
wrwofwut.nuub
```

It makes no sense. Why would the "r" be between the "w"? Am I nuub? ;-;

About the gedit error, it is exclusive to Lubuntu. In mate the message do not appear and it is faster (still not as before).

My notebook is a Asus M2400N, it is old and it has pretty limited video capabilities. Maybe its limited capabilities are, in part, responsible for this errors.

---

### Post by sudodus on 2016-06-10
It is a known fact that mixing desktop systems in the same installed systems can cause problems. For example, I would not mix standard Ubuntu (with Unity) with any other desktop environent, but I have so far had rather good experiences of a mixed Xubuntu + Lubuntu system.

The reason for these problems is probably that both systems use the same configuration files, but want different content in them.

I would reinstall, maybe make two systems side by side, one with Lubuntu and one with MATE, or simply select the desktop environment that you like the best and stay with it, if there is not space enough for two systems.

---

### Post by leozinho29_eu on 2016-06-10
About the gedit issue: I removed it and installed Pluma. Pluma is fast as Leafpad, has a better interface (at least to me) and has the resources I want, thank you.

About removing one or another: I really wanted to keep both. I like the Windows XP face Lubuntu has (I made a green Start button with Tux in the place of the XP flag). However, new things are always welcome, and Mate is there for it.

It's like the computer throttles. The characters I write don't appear in the moment I pressed the keys, they appears in a burst and in a chaotic way. 

Is there a package that, if I reinstall, makes the configuration files to be reset to the Lubuntu ones?

Edit: 

About the filemanagers (Caja and PCManFM) ignoring the first letter pressed in a search: the first letter behaves as it was a dead key. After the first letter in the first search, all the other presses work fine.

I have noticed the mouse freezes for a second or two sometimes when waiting to appear the text I wrote. This is new to me.

---

### Post by sudodus on 2016-06-10
Probably there are people who know how to fix your problem (without reinstalling), but I'm sorry, I don't know how to do it.

---

### Post by mc4man on 2016-06-10
> **leozinho29_eu said:**
> 
First: gedit became very, very slow. Trying to write, paste, copy, select, everything. A new message appeared when opening it using the terminal:

```
(gedit:4507): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

This message do not appear and the performance is very good when running gedit as superuser.
That message typically only shows up when someone uses sudo gedit. Maybe check your $HOME directory to see if root owns any files.
From normal terminal prompt, there should be nothing returned that lists root for owner or group
 
```
ls -lA -R |grep root
```

---

### Post by leozinho29_eu on 2016-06-10
I was able to solve the issues.

To do this, I had to:
-Purge all the fcitx packages
-Install gir1.2-matekbd
-Reinstall the fcitx packages I removed before
-Configure the new fcitx installation to make the only addons activated to be Keyboard Layout, Fcitx Unicode Typing Support and Virtual Key Board. 

I don't know which step corrected it, but it was one of these. With fcitx removed performance was the same as before the bugs, but with limited keyboard support. fcitx hit the performance, but I don't know how.

Gedit is running as it was before, the keys are responding well and the mouse no longer freezes.

---

### Post by leozinho29_eu on 2016-06-10
> **mc4man said:**
> That message typically only shows up when someone uses sudo gedit. Maybe check your $HOME directory to see if root owns any files.
From normal terminal prompt, there should be nothing returned that lists root for owner or group
 
```
ls -lA -R |grep root
```

I checked it, and root owns some of the ffmpeg and Mesa 8.0.5 files in the source folders. I have to do a post only about the Mesa issues I am having :(

---

### Post by sudodus on 2016-06-10
Congratulations and thanks for sharing your solution :KS

---

