---
title: "Roccat/CM Inferno Apps"
date: 2013-01-23
forum: General Help
---

### Post by Arkenbrien on 2013-01-23
Greetings!

I took the plunge and dual-booted my7 machine with Ubuntu, my new favorite operating system! :p I *really* like the workspaces. Blender + Gimp running at the same time maximized is going to be very helpful.

I have Roccat's Isku keyboard and CM's Storm Inferno mouse. I think the drivers were installed automatically, because all the buttons work (A little re-mapping for some of the shortcut keys via the settings>keyboard were required).

However, I cannot find out how to install or even find the GUI app. In windows, it showed a program that allowed you to program macros and such. In Ubuntu, I think I found the app in rar format for the Inferno, however, after unpacking it, I can't figure out what .exe to run and how to run them.  Nothing on the Roccat. 

Finding the GUI would be nice to have in Ubuntu, as I would like it to do stuff in Blender.

_____

One more unrelated quick question: Is it possible to use an android tablet as a drawing pad in Gimp?

_____

Thank you all in advanced.

EDIT: I just found out these instructions for the inferno GUI [here]("http://www.vitanuova.com/inferno/downloads.html"):

On *Linux systems with a Debian base*, such as Ubuntu, to compile the graphical version of the system     you will need the Debian packages *libxext-dev, libxpm-dev, and x11proto-xext-dev* installed.

What does this mean?

EDIT 2: Talk about finding everything you need after you spend 5 minutes creating a help topic about it....

[Roccat Drivers/Interface.]("http://sourceforge.net/projects/roccat/")

Now I have a new question: How do I execute .exe? And could any one of you take a look at the installation instructions for the Roccat and tell me what they are telling me to do?

---

### Post by Arkenbrien on 2013-01-23
I think this might be a bug, but when going into suspension or turning of the system, the computer still delivers power to the illuminated keyboard and mouse.

I still do not have any idea on what to do with the application files. Please help.

---

### Post by Arkenbrien on 2013-01-24
Well, no response. 

I personally was not able to find out how to start the installation process.

I was, however, able to find out that the CM Storm Inferno and Roccat Keyboards have internal memory of the profiles created. So for me, it is solved to an extent. All I have to do is restart my computer, boot to windows, edit the profile, then restart and boot to Ubuntu.  

If, however, anyone actually *wants* to help me deciphering this bit, they are more than welcome. 

```
* First make sure dependencies are met

  * You will need gcc and the development files for your actual kernel.
    Please mind that package names are distribution dependent. Names for Fedora
    and Ubuntu are showcased here:
    
    Fedora              Ubuntu

    kernel-devel        linux-headers

* Decide if you want to install manually or use DKMS

  * Manual installation

    * Determine your actual running kernel version.

      Run

      $ uname -r
  
      cd to the subdirectory of this package that suits your kernelversion best.

    * Configure modules

      If you just want to compile the modules for the devices you own you can edit
      the makefile and comment out the CONFIG_HID_ROCCAT_* lines you don't want to
      compile. You also can comment out the lines for modules that are already
      included in the actual kernel if you don't want to overwrite the original ones.
      But there might be newer versions included in this package that can save you a
      kernel update.
  
    * compile modules

      $ make
  
      If everything compiles ok you can install the modules with
  
      $ sudo make modules_install
  
      If you get errors you might miss some needed packages.

    * Make sure the modules can be loaded

      Issuing
  
      $ sudo modprobe roccat
  
      should not produce an error message.
  
      Some distros (e.g. the ones with buntu in their names) won't search the
      modules extra folder for the module dependency list unless forced.
      After module installation a
  
      $ sudo depmod -a
  
      should do the trick if the module can't be found by modprobe.

  * DKMS

    * Unpack to right dir
   
      To use DKMS this package has to reside in /usr/src
   
    * Execute
   
      $ dkms add -m kmod-roccat -v 0.7.1
      $ dkms build -m kmod-roccat -v 0.7.1
      $ dkms install -m kmod-roccat -v 0.7.1

* Make sure the modules are loaded when needed and generic driver keeps his hands off

  There exist multiple solutions to accomplish this, but different kernelversions
  support different ways.

  * For kernelversions from 2.6.28 upwards
  
    The device specific userland tool packages install udev rule files that make
    sure control is handed over from the generic to the specific driver. Also
    these rule files contain rules to change access rights of device files and
    sysfs attributes.

  * Fallback for kernelversions prior to 2.6.28
  
    Add the following lines to /etc/rc.local

    modprobe kone
    for x in `ls -1 /sys/bus/usb/drivers/usbhid/*/modalias` ; do
      grep -i v1e7dp2ced "$x" >/dev/null &&
      echo -n $x >/sys/bus/usb/drivers/usbhid/unbind &&
      echo -n $x >/sys/bus/usb/drivers/kone/bind
    done

    The settings are applied no the next reboot and are not applied if the
    device is replugged into a running system!

* Updating kernelincluded drivers

  If you use a kernel >= 2.6.35 some modules might be already be included and
  compiled. Hopefully your distribution has it compiled as module.
  
  To distinguish between kernel included and external modules they have different
  names. The kernel included device specific drivers have a hid_roccat_ prefix.
  
  To keep the old drivers from loading please copy the
  blacklist-roccat.conf file to /etc/modprobe.d
```

---

### Post by Arkenbrien on 2013-02-01
Well, after a while, I finally managed to get the Roccatgui working. It was a major learning experience. 

First off, I downloaded the wrong package. That took a little while to realize. This is the correct package: 

sourceforge.net/projects/roccat/files/roccat-tools/roccat-tools-0.15.0.tar.bz2/download

After extracting it in any folder, install/open the Synaptic Package Manager (you can find in in the Ubuntu Software Center, or type it in the Home Dash), then search and install the following packages (to install, simply check the box next to the items, then click Mark For Installation. After all the required items have been marked, click the apply button at the top):

cmake
gcc
libgtk2.0-dev
libnotify-dev
libcanberra-dev
libusb-1.0-0-dev
libunique-dev
libdbus-glib-1-dev
libgudev-1.0-dev

Change directories in the terminal ( $ cd /insert/directory), type the following commands:

$ mkdir build
$ cd build
$ cmake -DCMAKE_INSTALL_PREFIX="/usr" ..
$ make
$ sudo make install
$ sudo /sbin/ldconfig
$ sudo touch --no-create /usr/share/icons/hicolor

The  $ make and $ sudo make install commands take a little while.

Ensure that on the [ $ cmake -DCMAKE_INSTALL_PREFIX="/usr" .. ] command, you do not exchage the "/usr" for "/yourusername", and do not correct the spelling and insert "/user". This will mess up the directory and make it much harder on yourself. I fixed the spelling, and was unable to use the gui properly after installation. Also ensure that there are two periods at the end of that same command. 

It is possible to copy and paste the commands directly, lessening the chance for error.

In order to actually use the gui, execute the following:

$ sudo groupadd roccat
$ sudo usermod -a -G roccat $USER

Do not exchange the $USER for your user name.

Logout/login to apply the last two commands. Afterwards, to ensure that you are part of the roccat group, simply type in " group " in the terminal, and read the list. If roccat is in the list, you are part of that group.

Update the udev rules:

$ sudo udevadm control --reload-rules

After updating the rules, open dconf Editor from the home dash, which should be pre-installed. In the side bar, navigate as follows:

com > canonical > unity > panel

Within the value, add a comma after the last application name (if a fresh install, usually 'Update-notifier'), and add 'roccatgui' within the bracket. Do not eliminate the brackets. 

Then, open Startup Applications. Add a new startup program. The name is Roccatgui, and the command is roccatgui.

If you logout/login, it will show you an error, basically telling you that you do not have permission to access roccatgui, but the roccat icon should appear in the top panel, and be fully functional. It will require a full restart in order to eliminate the error message. To access the gui, right click on the icon, and from there navigate to the desired product.

____

I hope that will be helpful to any new user with a roccat peripheral. A big thank you Stefan.

Now unto the Inferno...

---

