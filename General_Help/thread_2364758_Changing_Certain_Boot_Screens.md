---
title: "Changing Certain Boot Screens"
date: 2017-06-27
forum: General Help
---

### Post by SBTlauien on 2017-06-27
These are the screens I see when I boot my system...

0. Black screen that says "Surface" in white text
---> 1. A completely purple/pinkish screen <---
2. Large text boot processes
3. Small text Boot processes(This must be after the graphics card kicks in)
---> 4. Default login screen with purple background and Ubuntu sound(This screen only lasts for about one second) <---
5. Login screen with custom background

I'd like to change the second screen that is completely purple/pinkish to a completely black screen and I'd like to change the fifth screen that shows the default login screen to my custom login screen with my custom background.

Thanks in advance.

---

### Post by CatKiller on 2017-06-27
The bootup splash process is controlled by something called Plymouth. You can either customise Plymouth, which may or may not be complicated (I've never tried) or you can remove the splash option from your GRUB config.

The login screen is called a greeter. You can customise it with lightdm-gtk-greeter-settings. The default Ubuntu greeter theme, unity-greeter, is less customisable than other LightDM greeter themes.

---

### Post by SBTlauien on 2017-06-28
> **CatKiller said:**
> The bootup splash process is controlled by something called Plymouth. You can either customise Plymouth, which may or may not be complicated (I've never tried) or you can remove the splash option from your GRUB config.

The login screen is called a greeter. You can customise it with lightdm-gtk-greeter-settings. The default Ubuntu greeter theme, unity-greeter, is less customisable than other LightDM greeter themes.

I don't believe the first screen that I'm talking about would be modified by Plymouth(which I have edited in the past).  I believe this screen belongs to the bootloader but I could be wrong.

The login screen has already been edited(see thread below) but it still shows the default login for about one second before changing.  I want to remove this slight "glitch".

[https://ubuntuforums.org/showthread.php?t=2364676](https://ubuntuforums.org/showthread.php?t=2364676)

---

### Post by again? on 2017-06-28
Don't know what release you're on but according to my notes this used to work for a purple flash before the greeter.
[COLOR="#FF0000"]Edit[/COLOR]: Just looked at your link. You can use the **same file** you created in that thread.
```
sudoedit /usr/share/glib-2.0/schemas/**10_unity_greeter.gschema.override**
```

Add the following lines. If the file is not empty just add the 2nd line to the end of the file.
Sets it to black.
```
[com.canonical.unity-greeter]
background-color = "#000000"
```
Save and close then update settings with
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

### Post by SBTlauien on 2017-06-28
> **guber2 said:**
> Don't know what release you're on but according to my notes this used to work for a purple flash before the greeter.
[COLOR=#FF0000]Edit[/COLOR]: Just looked at your link. You can use the **same file** you created in that thread.
```
sudoedit /usr/share/glib-2.0/schemas/**10_unity_greeter.gschema.override**
```

Add the following lines. If the file is not empty just add the 2nd line to the end of the file.
Sets it to black.
```
[com.canonical.unity-greeter]
background-color = "#000000"
```
Save and close then update settings with
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

This kind of fixed the fifth part(the login).  It still shows a login screen but now with a black background rather than that purple/pink background, and then a second later it shows my regular background.  It's like a small twitch it has and it's on all of my systems.

I looked and I have already tried editing "/usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.script" and changed two color attributes, but I still get that pink/purple screen that appears directly after my first screen that says "Surface".  It's one of the very first screens during the boot process.

---

### Post by CatKiller on 2017-06-28
> **SBTlauien said:**
> I looked and I have already tried editing "/usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.script" and changed two color attributes, but I still get that pink/purple screen that appears directly after my first screen that says "Surface".  It's one of the very first screens during the boot process.

That sounds like the theming of the GRUB menu, then. If you display the GRUB menu you'll probably find that it's the same colour. GRUB is very themable, but it's not something I've ever tried.

Note that we're using GRUB2 now when you're looking up how to change GRUB themes, and don't forget that you'll need to run update-grub for any changes to GRUB to take effect.

---

### Post by SBTlauien on 2017-06-28
Alright I got it fixed.  It was just the .grub file in the Plymouth directory.

Thanks!

---

