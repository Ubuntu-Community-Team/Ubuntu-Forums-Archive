---
title: "Need Basic help on few things."
date: 2013-01-08
forum: General Help
---

### Post by matrunner on 2013-01-08
Hi

I am new here. I need some help.

1) I change my brightness of laptop in ubuntu. But wen restart it goes back to orig state full brightness. How to keep it to state i keep so that i need not have to change each time. There is also no option like save the setting.

2) Can i use Open office and remove libre office ?

3) If i have linux installer downloaded directly how can i instal thru that directly.

4) How do i clear wat has been used already or say i use ccleaner to clear all my documents, last used details everything in windows. is there any like that in here, coz wen ever i open browser it remem all pass and misc details.

5) suggest some best softwares i can use - FREE
      Video player, Music player, Full office suite, Mail client, Any good to have softwares.

---

### Post by tgalati4 on 2013-01-08
I rarely boot my laptops.  I just put them to sleep (suspend-to-RAM) and they maintain the brightness when they wake.  When the machine boots, typically it will use the brightless level set in the BIOS.  The machine that I am on now (Dell 600m) has a screen brightness setting for AC and Battery in BIOS and it will boot to that every time.  You can add a script to set screen brightness when you first boot, or you can set it in display properties and it should remain whatever you set it to.

Not sure about Open Office, or if things break when you remove LibreOffice.  What functionality are you missing in LibreOffice?

I don't understand question 3.  You can use a Windows-based installer, a USB Flash Drive installer (unetbootin) or you can burn a DVD and boot from the DVD and then install while running from the DVD.

Depending on your browser, some of those settings are stored on the web.  Do you want to set up a dual-boot system?  Windows and Ubuntu with a choice at boot time which system to go into?

On question 5:  The Ubuntu DVD has the best software already packaged as part of the installation.  If there is something that you are not happy with, then you would need a more specific question.  For instance if the video player is not working for you, then you can request alternatives or you can search the package repositories:

Open a terminal:

```
apt-cache search video player
```

There are lots to choose from.

---

### Post by Dreamer Fithp Apprentice on 2013-01-08
> **matrunner said:**
> Can i use Open office and remove libre office ?
Yes. Just install OO and start using it. If it works ok for you, then uninstall Libre if you have no use for it.

> **matrunner said:**
> If i have linux installer downloaded directly how can i instal thru that directly.I assume you mean an installer for Open Office intended for a linux system. If it is an archive, extract it (IMPORTANT: Do this on a native linux file system such as ext3, NOT on a FAT or NTFS) and look for an installer script inside. You may have to right click on it, select properties and mark it executable on the permissions tab. Run the script, either from a graphical file manager (typically by double clicking it and pressing the "run" or "execute" or something like that button) or by typing in a terminal emulator "sudo path-to/installerscriptname" and pushing enter, making the appropriate substitutions. If it is a something.deb file, just double click it or run it from the command line the same way you would a script. Again, you may have to mark it executable first.

> **matrunner said:**
>  How do i clear wat has been used already or say i use ccleaner to clear all my documents, last used details everything in windows. is there any like that in here, coz wen ever i open browser it remem all pass and misc details.
The program you want is "bleach bit". 

> **matrunner said:**
> suggest some best softwares i can use - FREE
      Video player, Music player, Full office suite, Mail client, Any good to have softwares.vlc for video. I use it to play sound files too but you might want to look at some others if you want to do stuff more complicated than just play a sound file. Anarok (sp?) has a good rep. Open Office for an office suite. Mail client, dunno, never used one.

---

### Post by ScottDeagan on 2013-01-08
> **matrunner said:**
> 
1) I change my brightness of laptop in ubuntu. But wen restart it goes back to orig state full brightness. How to keep it to state i keep so that i need not have to change each time. There is also no option like save the setting.


I too suffered from the brightness problem. The brightness can be changed from the command line using:

```

sudo su -c "echo 45 > /sys/class/backlight/acpi_video0/brightness"

```

Just replace the '45' with a value that suits you. My laptop has a maximum brightness of 95. The maximum brightness can be obtained using:

```

cat /sys/class/backlight/acpi_video0/max_brightness

```

To hardcode brightness settings for startup, create a file named **75-backlight.rules** in directory **/etc/udev/rules.d/**, and then add the following contents to this file:

```

ACTION=="add", KERNEL=="acpi_video0", SUBSYSTEM=="backlight", SUBSYSTEMS=="pci", ATTR{brightness}="45"

```

Just remember to change the "45" to a brightness setting the suits you.

---

### Post by ScottDeagan on 2013-01-08
> **Dreamer Fithp Apprentice said:**
> ...Mail client...

In regards to a mail client, I would strongly recommend Thunderbird, especially if you use Gmail. I use Thunderbird with the Zindus, Calendar and Lightning extensions. Works great for me.  The only minor gripe I have is the grid seems too "squashed up" for my liking, making my inbox look awful on a 2560 x 1440 monitor. If you do decide to use Thunderbird and you want the lines in the inbox spaced out a little more, you can use the theme I have attached. To install it, you have to:

1. cd ~/.thunderbird
2. ls -l (you should see a directory that's something like: efddxzxn.default)
3. cd efddxzxn.default (replace _**efddxzxn**_.default with whatever you have).
4. mkdir chrome
5. Extract userChrome.css from the attached file into the newly created 'chrome' directory.
6. Restart Thunderbird.

The attached userChrome.css will simply space things out a bit more. which (to me) looks far better than the squishy default. If you don't like it, simply delete userChrome.css.

---

