---
title: "[SOLVED] Laptop Brightness Won't Stay 100%"
date: 2008-05-29
forum: General Help
---

### Post by jlacroix on 2008-05-29
I am using Ubuntu on a laptop, an Acer Aspire, and the brightness is driving me nuts. Here is a typical experience:

First, my laptop boots and the brightness is very dim. That's fine, it's at the boot screen so no need for brightness there.

Then, I log into the desktop (either KDE or Gnome) and the system automatically brightens up my screen. So far, so good.

If I start any game (like an NES emulator, MAME, or any of the full screen Linux games) Ubuntu dims the screen to its lowest setting. I never asked it to!

So, while I play my game, I just manually turn up the brightness using the shortcut keys. Gnome reports my brightness is 100%, even though it's not. Even though it shows the brightness at 100%, it still lets me brighten up my screen.

Then, while still playing the game, if the screen changes, Ubuntu automatically dims up my screen again. Especially with Mednafen, an NES emulator, even without playing it full screen. This creates an endless tug-o-war, I brighten up my screen, Ubuntu dims it about two seconds later. Repeat, repeat, repeat.

My laptop is plugged in to AC while this is happening. I'd completely understand Ubuntu dimming my screen if I'm running on battery, and I'm not, my battery is charging, the battery light is solid and I'm getting a steady power current.

What I'd prefer is to have the screen all the way bright if running on AC, and then dim if running on battery.

Again, this happens with KDE and Gnome, and I didn't have this problem with 7.10, only 8.04.

Basically, the only time the brightness stays all the way up is if I'm at the desktop doing file management or web browsing, I only have this problem when playing any game, fullscreen or not.

Also, adding the brightness applet to the panel doesn't help.

---

### Post by jlacroix on 2008-05-30
Anyone?

---

### Post by doorman on 2008-05-30
Hy!

I had the same problem on a 7.10 box, and the solution was to tur off acpi.

Steps to do it:

1) Open up a sudo editor
      - if you use gnome, press Alt+F2, then type gksu gedit
      - if you prefer a terminal editor, sudo vi, sudo joe, sudo nano, etc...
2) Open the file /boot/menu.lst
3) Find the line that says "default" and remember the number written there (let's call it X)
     - usually it "default 0"
4) Scroll down till the end of the file. You'll find a list there of images to choose from on boot. Now, find the Xth entry (each entry has 4 or 5 lines)
5) Append "acpi=off" at the end of the kernel line (usually the third one)
6) Save the file and reboot

Of course, you can add the acpi=off line to each kernel entry if you do not boot always the same image

---

### Post by jlacroix on 2008-05-30
Will that effect standby, hibernate, and making it use less power when on battery? I don't want to lose all the mobility features. Thank you.

---

### Post by doorman on 2008-06-01
i must admit i'm not sure :(

you'll still be able to hibernate and put it on stand by, but i really don't know what happens when the battery goes out ( my guess is that the laptop switches off without warning, but not sure about that )... You should try it to see :)

---

### Post by sdennie on 2008-06-01
Disabling ACPI may be overkill.  This fix isn't specific to your problem but, it may help: [http://ubuntuforums.org/showpost.php?p=5009164&postcount=3](http://ubuntuforums.org/showpost.php?p=5009164&postcount=3)

---

### Post by jlacroix on 2008-06-02
Thanks guys. Turning off ACPI wouldn't be a good tactic for me, other people use the laptop and they don't pay attention to the battery icon like I do unless a message pops up.

Not only that, but this worked as expected in Ubuntu Gutsy with ACPI enabled, I got the battery notifications and the screen wouldn't turn dim whenever I launched an OpenGL application, so the solution isn't ACPI, it seems to me to be a regression in Hardy.

---

### Post by sdennie on 2008-06-02
jlacroix: Did you try the possible fix I linked to?

---

### Post by jlacroix on 2008-06-02
> **vor said:**
> jlacroix: Did you try the possible fix I linked to?

Not yet, but I will the next available opportunity. I'm not on the laptop right now but I'll try that when I get on it next.

Does blacklisting the video have any side effects?

---

### Post by sdennie on 2008-06-02
I have no idea but, it's very easy to unblacklist it if it doesn't fix your problem.

---

### Post by jlacroix on 2008-06-02
That seems to have fixed it. I'll only know after a little while of usage (I only had time to try it for like five minutes and a single opengl app) but I'm pretty sure that did it. Thanks!

---

