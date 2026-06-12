---
title: "Problem with hotkeys"
date: 2007-12-11
forum: General Help
---

### Post by lukpeta on 2007-12-11
Hi,
I have Ubuntu 7.10 wiht all updates with internet installed in my laptop (Aristo Prestige 1600). I download drivers to my Radeon X 1600 from [www.ati.com](www.ati.com) (32 bit).

I have problem with hotkeys - it's doesn work (wifi, contrast, brightness) ((

What i must to do, if i want reduce brightness??

with this hotkeys i found solution to music hotkeys - i click right mouse button on speaker, and i select preference and PCM - and it's work!!


Sorry for my english.

Please help me.

North

---

### Post by blazercist on 2007-12-11
MainMenu > System > Preferences > Keyboard

Select the "Layouts" tab.  Choose generic 105 key.

It should work.

---

### Post by lukpeta on 2007-12-11
i have: Generic 105-key (Intl) PC but it's not working :(

---

### Post by blazercist on 2007-12-11
then you need to check your laptop's documentation and find the correct keyboard layout, thats your problem.  Your laptop prolly has some weird layout.

---

### Post by lukpeta on 2007-12-11
but in windows i haven't got any problems :/ hmmm... maybe in console i can do it??

---

### Post by DagMan on 2007-12-11
you can try the brightness applet by right clicking on the panel and adding it.  It may not work.

These problems are usually caused because there isn't yet a module available yet for the laptop to access those functions in Linux, or it's not set up properly and is trying to controll the functions but it is not doing it properly.  The latter happens because there's a lot of differant laptops to account for and where the interface to these things shows up is often in a differant place from one computer to the next, and the logic used to find them isn't perfect.

You can have a look through the files and directorys in /proc/acpi and see if you find anything in there regarding the LCD.  On mine it's located at /proc/acpi/video/VGA/LCDD/brightness but I would expect yours to be differant.
you can read files in there using for example ```
cat /proc/acpi/video/VGA/LCDD/brightness
```
And if you do find one that looks like it accepts values to change the brightness, try to use a value as follows, and a value of 7 for example which for me is half bright.
```
sudo su root -c "echo 7 > /proc/acpi/video/VGA/LCDD/brightness"
```

If you find that there is a file somewhere under /proc/acpi that controlls brightness, then you can go the next step at looking at how to fix it and by hopefully binding it to the normal keys as well.  If you don't find a file like that then you are probably out of luck unless there's a module for your laptop that can be installed.

---

### Post by bean1975 on 2007-12-11
```
sudo su root -c "echo 7 > /proc/acpi/video/VGA/LCDD/brightness"
```

OMG OMG OMG this works on Panasonic CF-Y5 under Gutsy since I upped to Gutsy I was unable to control brightness thank you thank you thank you! Here is my version of /etc/acpi/panabright.sh:
```

#!/bin/sh
# check power state
BRIGHTNESS=$(( `grep current /proc/acpi/video/GFX0/LCD1/brightness|cut -c10-` ))
if [ "x$1" = "xdown" ]; then
   BRIGHTNESS=$(( $BRIGHTNESS - 5 ))
   if [ $BRIGHTNESS -gt 0 ]; then
     echo $BRIGHTNESS > /proc/acpi/video/GFX0/LCD1/brightness
   fi
elif [ "x$1" = "xup" ]; then
   BRIGHTNESS=$(( $BRIGHTNESS + 5 ))
   if [ $BRIGHTNESS -lt 100 ]; then
     echo $BRIGHTNESS > /proc/acpi/video/GFX0/LCD1/brightness
   fi
else
   echo >&2 Unknown argument $1
fi

```

---

### Post by lukpeta on 2007-12-12
i clear my /etc/acpi/panabright.sh file, and i write this code:
#!/bin/sh

# default span value

SPAN=1

# check power state

BRIGHTNESS=$(( `grep current /proc/acpi/video/GFX0/LCD1/brightness|cut -c10-` ))
if [ "x$1" = "xdown" ]; then
   BRIGHTNESS=$(( $BRIGHTNESS - 5 ))
   if [ $BRIGHTNESS -gt 0 ]; then
     echo $BRIGHTNESS > /proc/acpi/video/GFX0/LCD1/brightness
   fi
elif [ "x$1" = "xup" ]; then
   BRIGHTNESS=$(( $BRIGHTNESS + 5 ))
   if [ $BRIGHTNESS -lt 100 ]; then
     echo $BRIGHTNESS > /proc/acpi/video/GFX0/LCD1/brightness
   fi
else
   echo >&2 Unknown argument $1
fi               <- its all my panabright file

and i restart my computer and i try fn+F6/F7 and fn+left/right but it;s don't work :((

this command sudo su root -c "echo 7 > /proc/acpi/video/VGA/LCDD/brightness" give me message: sudo su root -c "echo 7 > /proc/acpi/video/VGA/LCDD/brightness"

brightness applet - don't work :(

my /proc/acpi/video/VGA/LCDD/brightness file is clear...


please help me, i'm begginer in linux...

BIG THX for your help :)))

---

### Post by bean1975 on 2007-12-12
What's the contents of /proc/acpi/video/VGA/LCDD/brightness ? And why VGA/ why not GFX0/ ? You sure looking at the right directory?

---

### Post by lukpeta on 2007-12-12
/proc/acpi/video/VGA0/LCD - i have this path... my brightness fiole is clear.... 

i haven't this: GFX0

---

### Post by alamir on 2008-02-19
Download this:[http://www.da-cha.jp/files/pcc-acpi-0.9.tar.bz2](http://www.da-cha.jp/files/pcc-acpi-0.9.tar.bz2)
and this: [http://www.da-cha.jp/files/hotkey-handler-1.4.tar.gz](http://www.da-cha.jp/files/hotkey-handler-1.4.tar.gz)
[http://www.da-cha.jp/files/ac-power-handler-1.0.tar.gz](http://www.da-cha.jp/files/ac-power-handler-1.0.tar.gz)
[http://www.da-cha.jp/files/pcc-acpi-0.8.1.all.patch](http://www.da-cha.jp/files/pcc-acpi-0.8.1.all.patch)
[http://www.da-cha.jp/files/acpi_video-2.6.8.1.patch.txt](http://www.da-cha.jp/files/acpi_video-2.6.8.1.patch.txt)
Downlaod this then....[http://www.da-cha.jp/letsnote#Downloads](http://www.da-cha.jp/letsnote#Downloads)

 Run the following command:

    patch -p1 < location_of_patch

Now make menuconfig or use your favourite method of kernel configuration.
Kernel configuration

   1. Go under "Code maturity level options" and enable "Prompt for development and/or incomplete code/drivers". Then exit this menu.
   2. Go under "Power Management Options (ACPI, APM)" and enable "Power Management support".
   3. If you want suspend-to-disk (hibernate) to work, enable "Software Suspend"
   4. Enter the "ACPI (Advanced Configuration and Power Interface) Support" menu.
   5. Enable "ACPI support"
   6. Select "AC Adapter" as a built-in
   7. Select all other ACPI options you want
   8. Select "Panasonic Laptop Extras" as a built-in

Exit menuconfig (or your favourite configuration utility) and build and install the kernel.
Setting up acpid

To configure acpid for using the new Hotkey driver, you will need to download the "Hotkey Handler" package (listed under downloads). Untar this file in /etc/acpi (or your distribution's acpid configuration location).

If you want acpid to reduce the screen brightness when on battery power, you should also download the "AC Power Handler" package (listed under downloads) Untar this file in /etc/acpi (or your distribution's acpid configuration location).

If you plan not to use GUI for volume and mute(hotkeys or Gnome), please edit hotkey.pl to change $config values as "mute_mode" = 0 or 1 and "mixer_mode" = 0. In default, these are set to 2 that mean volume and mute is set by GUI utility.
Setting up hotkeys or Gnome shortcut keys

download new hotkeys utility which support Panasonic. If you use Debian GNU/Linux, you only download deb package. Not so, you may download source package and compile. It is easy to compile. $ ./configure $ make $ make install thats all.

To configure hotkeys for using the hotkey driver, you will need to download the "pcc.def" file(listed under downloads). Make directory $HOME/.hotkeys and copy this file. After you launch hotkeys -t pcc , you may show overlay gui by pushing Fn+F1,F2, Fn+F4, Fn+F5, Fn+F6 hotkeys.

---

