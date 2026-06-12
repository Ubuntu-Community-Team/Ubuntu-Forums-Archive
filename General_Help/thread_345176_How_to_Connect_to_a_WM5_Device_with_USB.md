---
title: "How to Connect to a WM5 Device with USB"
date: 2007-01-23
forum: General Help
---

### Post by edmondt on 2007-01-23
For Feisty Users:

* After upgrading to Feisty my rndis no longer works when I connect my device I get ipaq instead of rndis so I used [this guide ]("http://ubuntuforums.org/showthread.php?t=311158") to compile the latest kernel (2.6.22)

Remember to patch your kernel:

```

cd /usr/src/linux
wget http://synce.svn.sourceforge.net/svnroot/synce/trunk/patches/linux-2.6.22-rndis_host-wm5.patch
patch -p1 < linux-2.6.22-rndis_host-wm5.patch

```

This patch is optional which may increase performance on desktops as discussed on [the guide ]("http://ubuntuforums.org/showthread.php?t=311158"):

```

wget http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.22.1.bz2
bzcat patch-2.6.22-1.bz2 |patch -p1

```

make xconfig

You would get a window will lots of options about the kernel, remember to select your processor type etc for better performance.

If you have nvidia card:
Under "Processor type and features" turn "Paravirtualization Support" OFF


[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29) - Reminds us to enable these options:
CONFIG_USB_USBNET=y
CONFIG_USB_NET_CDCETHER=y
CONFIG_USB_NET_RNDIS_HOST=y

Search for "ipaq" and disable it, its for older pocket pc like WM 2002, 2003...

Follow the instruction on [this guide ]("http://ubuntuforums.org/showthread.php?t=311158") to finish compiling the kernel and install...

Reboot and reinstalled nvidia or ati drivers using a program called [envy]("http://www.albertomilone.com/nvidia_scripts1.html") (works for both nvidia and ati cards).

... Hope it works for you too... Follow the rest of the guide...

The purpose of this guide is to allow newer WM5 devices like HTC Wizard, Prophet to connect to Ubuntu Edgy 6.10 and be able to share files, install stuff. This guide will take about one hour to complete, depending on your skills etc.


First, let's install synce-trayicon. It won't work yet, but when we're done, it will give you a tray icon like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=37842&stc=1&d=1184099855[/IMG]

When you connect your device, you should see this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=37841&stc=1&d=1184099855[/IMG]

```

wget http://kuci.org/~teddy/ubuntu/synce-software-manager_0.9.0-2_i386.deb
wget http://kuci.org/~teddy/ubuntu/synce-trayicon_0.9.0-2_i386.deb

sudo dpkg -i synce-software-manager_0.9.0-2_i386.deb
sudo dpkg -i synce-trayicon_0.9.0-2_i386.deb

sudo ln -si /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2

```

Now the tray icon should be installed, and we need to put it in the startup; so goto System, Preference, Sessions, Startup Programs, Add New:

```

synce-trayicon

```

Now let's find out the device you have:

unplug your device and run this command:

```

ls /dev > /tmp/before

```

now plug in your device and run this:

```

ls /dev > /tmp/after
diff /tmp/before /tmp/after

```

If you see something like ttyUSB0, then you should go here:

[http://ubuntuforums.org/showthread.php?t=136257](http://ubuntuforums.org/showthread.php?t=136257)

Otherwise

```

sudo lshw -businfo | grep usb

```


I have a Prophet and before connecting my device it gives me:

```

usb@1        usb1       bus            UHCI Host Controller
usb@2        usb2       bus            UHCI Host Controller
usb@2:2                 bus            Logitech BT Mini-Receiver
usb@2:2.2               input          Logitech BT Mini-Receiver
usb@2:2.3               input          Logitech BT Mini-Receiver
usb@3        usb3       bus            UHCI Host Controller
usb@4        usb4       bus            EHCI Host Controller

```

After connecting my device and run the same code again it gives me:
```

usb@1        usb1       bus            UHCI Host Controller
usb@1:2                 generic        Generic RNDIS
usb@2        usb2       bus            UHCI Host Controller
usb@2:2                 bus            Logitech BT Mini-Receiver
usb@2:2.2               input          Logitech BT Mini-Receiver
usb@2:2.3               input          Logitech BT Mini-Receiver
usb@3        usb3       bus            UHCI Host Controller
usb@4        usb4       bus            EHCI Host Controller

```

So I have a Generic RNDIS... I would need compile some stuff to get the rndis driver:

```

sudo apt-get install libglib2.0-dev libusb-dev build-essential autoconf automake1.9 libtool libgnet-dev libhal-dev libhal-storage-dev libdbus-glib-1-dev subversion linux-headers-`uname -r` python-dbus

```

Now let's grab some stuff driver using terminal command, do this:

```

cd
svn checkout https://synce.svn.sourceforge.net/svnroot/synce/trunk/libsynce
svn checkout https://synce.svn.sourceforge.net/svnroot/synce/trunk/librapi2
svn checkout https://synce.svn.sourceforge.net/svnroot/synce/trunk/odccm
svn checkout https://synce.svn.sourceforge.net/svnroot/synce/trunk/synce-gnome

```

Compile libsynce, enter the commands line by line:

```

cd libsynce/
./bootstrap
./configure --enable-desktop-integration
make
sudo make install
cd ..

```

If you get any errors in ./configure, then search for the missing library, say you're missing gcc, then search like this:

```

apt-cache search packagename

```
or:
```

apt-cache search packagename | grep packagename

```

then install any missing packages:

```

sudo apt-get install packagename

```


Next:

```

echo "/usr/local/lib" | sudo tee -a /etc/ld.so.conf
sudo ldconfig
cd librapi2/
./bootstrap
./configure
make
sudo make install
cd ..

```

Compile odccm:

```

cd odccm/
autoreconf -i
./configure
make
sudo make install
sudo cp data/dbus/odccm.conf /etc/dbus-1/system.d/
cd ..

```

Next the usb driver: you should find out which driver will work by going to:

[http://www.synce.org/index.php/Windows_Mobile_2005_HCL](http://www.synce.org/index.php/Windows_Mobile_2005_HCL)

I have a Prophet (Dopod 818 Pro) usb-rndis should work, but usb-rndis-lite is the newer driver and that's what I will be using:

```

svn co https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
cd ..

```

If you need the usb-rndis-ng, do this:

```

sudo apt-get install libhal-dev libhal-storage-dev
svn co https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-ng
cd usb-rndis-ng/
./autogen.sh
./configure --enable-hal
make
sudo make install
cd ..

```


If it all works out, unplug and plug in your device, then do this:

```

sudo dhclient3 rndis0

```

And I got:

DHCPREQUEST on rndis0 to 255.255.255.255 port 67
DHCPACK from 169.254.2.1
bound to 169.254.2.2 -- renewal in 1267550 seconds.

I got an ip, great! now test out odccm by entering this:

```

sudo odccm -f

```


then enter:

```

pls

```

It should list your directory on your pocket pc.

If it doesn't work, or you have firestarter installed, do this:

```

sudo chmod u+w /etc/firestarter/user-pre
gksudo gedit /etc/firestarter/user-pre

```

Add this to the file:

```

$IPT -A INPUT -i rndis0 -j ACCEPT
$IPT -A OUTPUT -o rndis0 -j ACCEPT

```

Save and exit. Then:

```

sudo chmod u-w /etc/firestarter/user-pre

```

...and it should work. For a list of commands, goto:

[http://www.synce.org/index.php/SynCE_Tools](http://www.synce.org/index.php/SynCE_Tools)


So we have a connection, but we still need to make this useful, we need to install synce-gnome, which displays a bubble when your device is connected and disconnected, and you can also execute commands etc...


```

svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/oleavr-files/synce-gnome
cd synce-gnome/src
python test.py

```

Now when you unplug your device, you should see a bubble saying device disconected, plug it in and it will say device connected. This will be useful later on...

We want enable browsing via nautilus, so we need to do this:

```

sudo apt-get install librapi2 librapi2-dev librapi2-tools librra0 librra0-dev librra0-tools libsynce0 libsynce0-dev synce-dccm synce-serial libgnomevfs2-dev gcc-3.3

```

then:

```

cd /usr/lib
sudo ln -s libsynce.so.0.0.0 libsynce.so
sudo ln -s librapi.so.2.0.0 librapi.so

```

then to compile:

```

cd ~
export CC=/usr/bin/gcc-3.3
svn co https://svn.sourceforge.net/svnroot/synce/trunk/gnomevfs
cd gnomevfs/
./bootstrap
./configure
make
sudo make install

```

```

ls /usr/bin/gcc-*
export CC=/usr/bin/gcc-4.1
sudo gedit /etc/gnome-vfs-2.0/modules/default-modules.conf

```

Add this at the end of the file:

```

synce: libsyncevfs

```

Save and exit. You should then be able to browse your files by entering 
```

synce:///

```

Don't worry if it doesn't work now, it should be good after a restart when we finish the rest; we need to automatically start odccm:

```

gksudo gedit /etc/init.d/odccm

```

Copy and paste this in:
```

#! /bin/sh
# /etc/init.d/odccm
#
# Script d'initiation du daemon odccm
# http://www.synce.org

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin

test -x /usr/local/sbin/odccm || exit 0

. /lib/lsb/init-functions

case "$1" in
  start)
    log_daemon_msg "Starting odccm service"
    if start-stop-daemon --start --exec /usr/local/sbin/odccm ; then
        log_end_msg 1
        exit 1
    fi
    log_end_msg 0
  ;;
  stop)
    log_daemon_msg "Stopping odccm service"
    start-stop-daemon --stop --exec /usr/local/sbin/odccm ;
    log_end_msg 0
  ;;
  restart)
    $0 stop
    sleep 2
    $0 start
  ;;
    *)
    log_action_msg "Usage: /etc/init.d/odccm {start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

then:
```

sudo chmod +x /etc/init.d/odccmsudo
update-rc.d odccm defaults

```


Next we copy that synce-gnome to:

```

cd
sudo cp synce-gnome /usr/src/
sudo chown -R root.root /usr/src/synce-gnome

```

Put this in the System, Preference, Session, Startup Programs, add:

```

python /usr/share/synce-gnome/src/test.py

```

Next we modify test.py:

```

gksudo gedit /usr/share/synce-gnome/src/test.py

```

Clear everything and paste this in:

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import dbus
import dbus.glib
import gtk
import os

class TestApp:
    def __init__(self):
        self.devices = {}

        bus = dbus.SystemBus()
        self.bus = bus
        proxy_obj = bus.get_object("org.synce.odccm", "/org/synce/odccm/DeviceManager")
        mgr = dbus.Interface(proxy_obj, "org.synce.odccm.DeviceManager")

        mgr.connect_to_signal("DeviceConnected", self.device_connected_cb)
        mgr.connect_to_signal("DeviceDisconnected", self.device_disconnected_cb)

        session_bus = dbus.SessionBus()
        notif_obj = session_bus.get_object("org.freedesktop.Notifications", "/org/freedesktop/Notifications")
        self.notify_iface = dbus.Interface(notif_obj, "org.freedesktop.Notifications")

        for obj_path in mgr.GetConnectedDevices():
            self._add_device(obj_path, False)
        
    def device_connected_cb(self, obj_path):
        self._add_device(obj_path, True)

    def device_disconnected_cb(self, obj_path):
        if obj_path in self.devices:
            device = self.devices[obj_path]
            self.notify_iface.Notify("SynCE", 0, "", "PDA disconnected", "'%s' just disconnected." % device.name, [], {}, 3000)
            del self.devices[obj_path]
            p = os.popen('killall synce-trayicon')

    def _add_device(self, obj_path, just_connected):
        device = CeDevice(self.bus, obj_path)
        self.devices[obj_path] = device

        if just_connected:
            p = os.popen('killall synce-trayicon')
            self.notify_iface.Notify("SynCE", 0, "", "PDA connected", "A %s %s '%s' just connected." % \
                (device.model_name, device.platform_name, device.name), [], {}, 3000)


ODCCM_DEVICE_PASSWORD_FLAG_SET     = 1
ODCCM_DEVICE_PASSWORD_FLAG_PROVIDE = 2

class CeDevice:
    def __init__(self, bus, obj_path):
        self.obj_path = obj_path
        dev_obj = bus.get_object("org.synce.odccm", obj_path)
        dev = dbus.Interface(dev_obj, "org.synce.odccm.Device")
        self.name = dev.GetName()
        self.platform_name = dev.GetPlatformName()
        self.model_name = dev.GetModelName()
        self.dev_iface = dev
        
        dev.connect_to_signal("PasswordFlagsChanged", self.password_flags_changed_cb)
        
        self._print_debug()
        
        self._password_flags_changed()

    def _print_debug(self):
        dev = self.dev_iface
        print "Created CeDevice with obj_path=\"%s\"" % self.obj_path
        print "  GetIpAddress:", dev.GetIpAddress()
        print "  GetGuid:", dev.GetGuid()
        print "  GetOsVersion:", dev.GetOsVersion()
        print "  GetName:", dev.GetName()
        print "  GetVersion:", dev.GetVersion()
        print "  GetCpuType:", dev.GetCpuType()
        print "  GetCurrentPartnerId:", dev.GetCurrentPartnerId()
        print "  GetId:", dev.GetId()
        print "  GetPlatformName:", dev.GetPlatformName()
        print "  GetModelName:", dev.GetModelName()
        print "  GetPasswordFlags:", dev.GetPasswordFlags()

    def password_flags_changed_cb(self, added, removed):
        print "password_flags_changed_cb: added=0x%08x removed=0x%08x" % (added, removed)
        self._password_flags_changed()

    def _password_flags_changed(self):
        flags = self.dev_iface.GetPasswordFlags()

        if flags & ODCCM_DEVICE_PASSWORD_FLAG_PROVIDE:
            authenticated = False
            while not authenticated:
                dlg = EntryDialog(None, "Password required",
                                  "The PDA '%s' is password-protected.  Enter password:" % self.name,
                                  True)
                if dlg.run() == gtk.RESPONSE_ACCEPT:
                    authenticated = self.dev_iface.ProvidePassword(dlg.get_text())
                dlg.destroy()


class EntryDialog(gtk.Dialog):
    def __init__(self, parent, title, text, password=False):
        gtk.Dialog.__init__(self, title, parent,
                            gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT,
                            (gtk.STOCK_OK, gtk.RESPONSE_ACCEPT,
                             gtk.STOCK_CANCEL, gtk.RESPONSE_REJECT))

        label = gtk.Label(text)
        label.set_alignment(0.0, 0.5)
        self.vbox.pack_start(label, False)
        self._label = label

        entry = gtk.Entry()
        entry.set_visibility(not password)
        self.vbox.pack_start(entry, False, True, 5)
        self._entry = entry

        self.show_all()

    def get_text(self):
        return self._entry.get_text()


TestApp()
gtk.main()

```

Save and exit... Now you're ready to reboot!

Note:
- You need to plug and unplug your device after you login for the tray icon to light up


Now to sync with Evolution or Kontact, there is 3 options:

1. Use the SyncEngine - [http://www.synce.org/index.php/SyncEngine](http://www.synce.org/index.php/SyncEngine)
2. sync with Scheduleworld and Evolution using the syncevolution engine.
3. sync with a local Funambol server installed locally no internet connection required.

No matter which option you pick, there is going to be some work envolved :)

1. Please follow the guide: [http://www.synce.org/index.php/SyncEngine](http://www.synce.org/index.php/SyncEngine) to get SynEngine going...

2. If you have wifi or a unlimited gprs connection, Scheduleworld is a free service and might be a good way to go, since you can sync anywhere on the go and supports google, google calendar, evolution etc.

I will complete this how to at a later time... Please follow this guide if you plan to sync with ScheduleWorld

[http://www.sjoerdmulder.nl/wordpress/?p=4](http://www.sjoerdmulder.nl/wordpress/?p=4)


I hope someday, all this will be built in to ubuntu so that connect and sync with a pocket pc is easy. Please help by sending feedback and suggestions.

More Reading:

[http://www.lvivier.info/SynceFS/](http://www.lvivier.info/SynceFS/) - an application allowing to mount pocketPC like a remote filesystem (deb for ubuntu available).

---

### Post by subtex on 2007-02-03
Man is that a lot of work!

I think I'll wait until this is more plug and play...

;) 

Ubuntu has spoiled me.  I expect stuff to just sort of work now.

---

### Post by darrengoddard on 2007-02-14
thanks fr all the hard work put in.  i got this far...

[B]I got an ip, great! now test out odccm by entering this:

Code:

sudo odccm -f
[/B]
and then terminal just seemed to stop.  and i'm not sure what to do.  any help would be greatly appreciated.

regards
darren

---

### Post by dzul1983 on 2007-02-15
having the same problem here.. device is HTC Tytn (Hermes)

---

### Post by edmondt on 2007-02-19
Try it with just "sudo odccm" and then type "pls" and see if you have a directory listing...

If it works then skip "odccm -f", it is only used for testing...

---

### Post by wormie_dk on 2007-02-22
When I get to :
```
sudo dhclient3 rndis0
```

This command fails. dmsg might shed some light on the matter but I am not sure:
```

[17182098.320000] usb 4-6.4: new full speed USB device using ehci_hcd and address 12
[17182098.420000] usb 4-6.4: configuration #1 chosen from 1 choice
[17182098.504000] rndis_host 4-6.4:1.0: RNDIS_MSG_QUERY(0x01010101) failed, -110
[17182098.504000] rndis_host: probe of 4-6.4:1.0 failed with error -110

```

Do you have any idea how to proceed next?

Thanks

David

---

### Post by darrengoddard on 2007-02-23
so near and yet...

thanks for the info/advice with odccm -f. 

managed to move on and received the following message

darren@desktop:~$ sudo cp synce-gnome /usr/src/
cp: omitting directory `synce-gnome'

and then i ground to a halt.

would really appreciate your support.

regards
darren

---

### Post by darrengoddard on 2007-02-23
also (really not splitting hairs but it caught me out for a while) i think this is a typo...

should

sudo chmod +x /etc/init.d/odccmsudo
update-rc.d odccm defaults


actually say

sudo chmod +x /etc/init.d/odccm
sudo update-rc.d odccm defaults


smile
darren

---

### Post by beow on 2007-03-04
> **wormie_dk said:**
> When I get to :
```
sudo dhclient3 rndis0
```

This command fails. dmsg might shed some light on the matter but I am not sure:
```

[17182098.320000] usb 4-6.4: new full speed USB device using ehci_hcd and address 12
[17182098.420000] usb 4-6.4: configuration #1 chosen from 1 choice
[17182098.504000] rndis_host 4-6.4:1.0: RNDIS_MSG_QUERY(0x01010101) failed, -110
[17182098.504000] rndis_host: probe of 4-6.4:1.0 failed with error -110

```

Do you have any idea how to proceed next?

Thanks

David

I also got this RNDIS_MSG_QUERY(0x01010101) failed from dmesg. First time I inserted the plug I didn't get that message and also got a device (I think) rndis0. But now it halts by the rndis_host stage as above all times I plug in and out the plug. Is it possible to remove the "configuration #1" that was not present at the first attempt? How? 

Anyone?

---

### Post by Haitao on 2007-03-06
Hi!

Thanks a lot for the long post and detailed process. 

There is a typo starting from the section:
> Next we copy that synce-gnome to:

You probably need to edit your post and amend it as people will follow it blindly and it won't work.

The cp command should have -R in order to copy the sub-directories as well and there is a problem as you copy those files to /usr/src/... but then all the other commands and copy and paste are based on /usr/share/... instead. So the startup script won't work, the edit of test.py won't work and so on.

Now I almost got everything "working" except that pls gives me:
```
** (process:6368): WARNING **: No devices connected to odccm
pls: Unable to initialize RAPI: An unspecified failure has occurred

```

but dmesg see the device with the rndis driver (though I can't access [www.synce.org](www.synce.org) from China, I have a Dopod 838 and assumed the rndis-lite would work too).

Any idea about what could be wrong?

Thanks

---

### Post by minirx7 on 2007-03-12
I got everything to work for my HTC S620 - Excalibur.

I rebooted, and I am able to browse using the file manager, however for some reason, i am able to delete things but I cannot copy things to my phone.

It keeps saying an error messages.  Do you know what this is?

EXCELLENT GUIDE BY THE WAY!

EDIT.  I can copy things from phone to the computer, but not copy things from computer to the phone!

---

### Post by kizmat on 2007-03-12
I've the same problem with minirx7 (dopod c720w), having problems copying files to it. Seems to me like its a path problem. Any ideas anyone?

Also, it'll be great if internet surfing can be enabled, great work!

---

### Post by minirx7 on 2007-03-12
Really weird.. I am not quite sure how it can be a path problem if we can still see and delete files as well as copy files from the device.

---

### Post by kizmat on 2007-03-13
this is just my guess. I'm currently using pcp to copy my files over.

---

### Post by azidrane on 2007-03-21
> **edmondt said:**
> Try it with just "sudo odccm" and then type "pls" and see if you have a directory listing...

If it works then skip "odccm -f", it is only used for testing...

neither one of these want to work. when i run:

```
dmesg | grep "rndis[0-9]: register" | grep "rndis_host" | tail -1
```

I receive this:

```
[17277571.676000] rndis0: register 'rndis_host' at usb-0000:00:02.0-9, RNDIS device, 80:00:60:0f:e8:00

```

which i think tells me its connected.

Yet, when I run "sudo odccm" then "pls" i get:

```
** (process:16456): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'

```

The "WARNING **: No devices connected to odccm" is what confuses me.

I've tried to use "sudo odccm -f" but i get nothing at all out of that.

any clues anyone?

---

### Post by ombra32 on 2007-03-23
> **edmondt said:**
> ```

wget http://kuci.org/~teddy/ubuntu/synce-software-manager_0.9.0-2_i386.deb
wget http://kuci.org/~teddy/ubuntu/synce-trayicon_0.9.0-2_i386.deb

sudo dpkg -i synce-software-manager_0.9.0-2_i386.deb
sudo dpkg -i synce-trayicon_0.9.0-2_i386.deb

sudo ln -si /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2

```

Hello..I'm a x64 Ubuntu user..and I can't do this step (the first.. :( )....
What can I do to obviate to this? thanks..

---

### Post by sbrinkmann on 2007-04-11
I've got the HTC TyTN / Hermes Smartphone in germany it's called T-Mobile MDA Vario 2.

```
sbrinkmann@blackhawk:~$ sudo odccm
sbrinkmann@blackhawk:~$ pls

** (process:14336): WARNING **: Failed to get a connection: Not authenticated, you need to call ProvidePassword with the correct password.
pls: Could not find configuration at path '(Default)'
```

What should i do to authenticate the MDA withe my Laptop. Which setting should I do to get i connection between the MDA and my Laptop.

Thanks for help.

---

### Post by luxerama on 2007-04-28
> **azidrane said:**
> neither one of these want to work. when i run:

```
dmesg | grep "rndis[0-9]: register" | grep "rndis_host" | tail -1
```

I receive this:

```
[17277571.676000] rndis0: register 'rndis_host' at usb-0000:00:02.0-9, RNDIS device, 80:00:60:0f:e8:00

```

which i think tells me its connected.

Yet, when I run "sudo odccm" then "pls" i get:

```
** (process:16456): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'

```

The "WARNING **: No devices connected to odccm" is what confuses me.

I've tried to use "sudo odccm -f" but i get nothing at all out of that.

any clues anyone?

Ive got the exact same problem, no idea why though....
One other thing (I dont know whether its related) is that the synCE tray icon doesnt change ie. pick up a connected device. Ive got a T-Mobile MDA Vario II (HTC TyTN).

EDIT:
I just ignored that problem and ploughed on, and most some features actually work. what doesnt work is the nautilus bit, but i think the promblem seems to be with nautilus the error is:
```

nautilus: symbol lookup error: /usr/lib/gnome-vfs-2.0/modules/libsyncevfs.so: undefined symbol: synce_log_use_syslog

```
anyone any idea how to solve this? Anyways thanks for the great howto...

---

### Post by Corubia on 2007-04-30
Hi. first off nice looking guide.  Easiest one to read/follow so far.

My problem.  I get this far:

```
sudo odccm -f
```

or

```
sudo odccm
```

Then I get:

```
** ERROR **: Failed to get bus name: Connection ":1.19" is not allowed to own the service "org.synce.odccm" due to security policies in the configuration file
aborting...
Aborted (core dumped)
```

(Side Note: I don't know if this means anything, however, every time odccm is executed the numer in the "" increses.  ie: ":1.19", ":1.20", ":1.21" etc...)

I'm using feisty and I have a Dell Axim x51v. I'm trying to use the rndis-lite.  I would like to be able to sync with kontact, but I can use gnome apps in a pinch :)

Thank alot and again, great looking guide.  Your time is soo welcomed and appreciated.

Corubia

---

### Post by eatadonut on 2007-05-09
try editing /etc/dbus-1/system.d/NetworkManager.conf

Add this line to the section that says ```
<policy user="root">
```

```
<allow own="org.synce.odccm"/>
```

---

### Post by tinolupin on 2007-05-16
I have follow the guide.. With synce-tools (pls ... ) I can write to my wm5 TYTN but with nautilus (synce:///) I can read and delete but I can't write.. Anyone can help me??

---

### Post by tinolupin on 2007-05-21
i have found the solution, i must add this patch to gnomevfs plug-in:

```
diff -Nur synce-gnomevfs-0.10.0.svn20070511.orig/src/libsyncevfs.c synce-gnomevfs-0.10.0.svn20070511/src/libsyncevfs.c

--- synce-gnomevfs-0.10.0.svn20070511.orig/src/libsyncevfs.c	2007-05-05 16:24:38.000000000 +0100

+++ synce-gnomevfs-0.10.0.svn20070511/src/libsyncevfs.c	2007-05-11 14:45:39.000000000 +0100

@@ -374,9 +374,9 @@

   g_free(location);

   wstr_free_string(wide_path);

 

-	*(method_handle_return) = GUINT_TO_POINTER(handle);

+  *(method_handle_return) = GUINT_TO_POINTER(handle);

 

-  if((handle == INVALID_HANDLE_VALUE) || (synce_open_mode & GENERIC_WRITE))

+  if(handle == INVALID_HANDLE_VALUE)

     result = gnome_vfs_result_from_rapi();

   else

     result = GNOME_VFS_OK;

```

now i can read, write and delete on my tytn!!

---

### Post by MauroKTM on 2007-05-31
I'm  able to connect and get a IP address but when i try to get pls this is the answer:

pls: Unable to initialize RAPI: An unspecified failure has occurred

any idea?

---

### Post by codedmin on 2007-06-02
Hyy

I do all the 1s post steps, but when i do > sudo dhclient3 rndis0

i get the follow error
> 
sudo dhclient3 rndis0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
rndis0: ERROR while getting interface flags: No such device
rndis0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

And yes i have the phone connected and it isn't in stanby

I have on Htv TyTn with windows mobile 6

I anyone can help... i would like :D

Thanks

---

### Post by codedmin on 2007-06-03
I forgot say, but svns repos are wrong

Now they are
> 
cd
svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/libsynce](https://synce.svn.sourceforge.net/svnroot/synce/trunk/libsynce)
svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/librapi2](https://synce.svn.sourceforge.net/svnroot/synce/trunk/librapi2)
svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/odccm](https://synce.svn.sourceforge.net/svnroot/synce/trunk/odccm)


---

### Post by Kari_Juhani on 2007-06-05
hello .. can anyone help me ?? Trying to install HTC TyTn to Ubntu 7.04

I get this error message ..

it's in this part of installation :

---------
Code:

echo "/usr/local/lib" | sudo tee -a /etc/ld.so.conf
sudo ldconfig
cd librapi2/
./bootstrap
./configure
make
sudo make install
cd ..

--------

when i do "./configure", i get this :

checking for pyrexc... pyrexc
checking for headers required to compile python extensions... not found
configure: error: Building python bindings requested, but can't build them

it had also error in "pyrexc", but i installed pyrex and that was it...   these others i cant find : python is version 2.5 atm.


Another studip (?) question...  when i check with "USB viewer", i have 1 ECHI and 4 UHCI controllers. Seems that UCHI is USB 1.1 and ECHI 2.0 .. HTC is USB 2.0 ??  does this matter ?

I changed HTC to that cable wich was on ECHI, but i changed a Card reader back to ECHI and HTC back to UHCI.


Please .. anyone ?
Kari

---

### Post by bsdgal on 2007-06-06
Kari,

I get the exact same error. Where you able to work through this problem? Any suggestions anyone?

Thanks,

Jeanne

checking for a Python interpreter with version >= 2.2... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for pyrexc... no
checking for headers required to compile python extensions... not found
configure: error: Building python bindings requested, but can't build them

---

### Post by bsdgal on 2007-06-06
Don't know how I missed this:

[http://ubuntuforums.org/archive/index.php/t-436861.html](http://ubuntuforums.org/archive/index.php/t-436861.html)

sudo apt-get install python-dev

---

### Post by garlicsalt2 on 2007-06-07
```
** (process:16456): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'

```

I had this problem, as well. I was puzzled at first, but after awhile, I had the crazy idea to disable my device pin/password. After that, I can access my device just fine. Go figure...

Hope this works for other people too.

Also, for this problem:

```

** ERROR **: Failed to get bus name: Connection ":1.19" is not allowed to own the service "org.synce.odccm" due to security policies in the configuration file
aborting...
Aborted (core dumped)

```

I had this problem at first, but then realized that I missed a step ( I was following a different guide, but this step is what solved this problem for me)

```

cd odccm
cp data/dbus/odccm.conf /etc/dbus-1/system.d/

```

Note: I was logged in as root when I did this, so you may need to prefix the cp command with sudo.

---

### Post by Kari_Juhani on 2007-06-07
> **Kari_Juhani said:**
> hello .. can anyone help me ?? Trying to install HTC TyTn to Ubntu 7.04

I get this error message ..

it's in this part of installation :

---------
Code:

echo "/usr/local/lib" | sudo tee -a /etc/ld.so.conf
sudo ldconfig
cd librapi2/
./bootstrap
./configure
make
sudo make install
cd ..

--------

when i do "./configure", i get this :

checking for pyrexc... pyrexc
checking for headers required to compile python extensions... not found
configure: error: Building python bindings requested, but can't build them

it had also error in "pyrexc", but i installed pyrex and that was it...   these others i cant find : python is version 2.5 atm.


Another studip (?) question...  when i check with "USB viewer", i have 1 ECHI and 4 UHCI controllers. Seems that UCHI is USB 1.1 and ECHI 2.0 .. HTC is USB 2.0 ??  does this matter ?

I changed HTC to that cable wich was on ECHI, but i changed a Card reader back to ECHI and HTC back to UHCI.


Please .. anyone ?
Kari



this was solved , thanks to BSDGAL ...  

and i did get an ip-adress to htc for 10 seconds. 
Now next problem..  with this rate i'll have this solved just before WM6 update  arrivees to my HTC :)

Kari

---

### Post by Kari_Juhani on 2007-06-07
rndis - install give me this...  

kari@amd64-desktop:~/synce-usb-rndis-lite-0.10.0$ sudo ./clean.sh
removed `/lib/modules/2.6.20-16-generic/extra/usbnet.ko'
removed `/lib/modules/2.6.20-16-generic/extra/cdc_ether.ko'
removed `/lib/modules/2.6.20-16-generic/extra/rndis_host.ko'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/kari/synce-usb-rndis-lite-0.10.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 3 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules
kari@amd64-desktop:~/synce-usb-rndis-lite-0.10.0$ 


See this :

Instructions for kernels >= 2.6.21

As of version 2.6.21, the Linux kernel has most of the required support built in, and thus doesn't require the usb-rndis-lite driver. However, you still need to apply a patch to the kernel source for it to work.

For kernel version 2.6.21:

 cd /usr/src/linux
 wget [http://synce.svn.sourceforge.net/svnroot/synce/trunk/patches/linux-2.6.21-rndis_host-wm5.patch](http://synce.svn.sourceforge.net/svnroot/synce/trunk/patches/linux-2.6.21-rndis_host-wm5.patch)
 patch -p1 < linux-2.6.21-rndis_host-wm5.patch

For kernel version 2.6.22:

 cd /usr/src/linux
 wget [http://synce.svn.sourceforge.net/svnroot/synce/trunk/patches/linux-2.6.22-rndis_host-wm5.patch](http://synce.svn.sourceforge.net/svnroot/synce/trunk/patches/linux-2.6.22-rndis_host-wm5.patch)
 patch -p1 < linux-2.6.22-rndis_host-wm5.patch

You need the following options in your kernel config:

 CONFIG_USB_USBNET=y
 CONFIG_USB_NET_CDCETHER=y
 CONFIG_USB_NET_RNDIS_HOST=y

Compiling them as modules should also work. Finally, build and install your kernel as usual. 

i have no clue how to patch it.....  ????

Kari

---

### Post by Kari_Juhani on 2007-06-07
I think i must have some problem with USB - drivers .. can anyone say anything..

This is what i get, when i run  "cat /proc/bus/usb/devices"

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#= 11 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0bb4 ProdID=0b04 Rev= 0.00
S:  Manufacturer=HTC
S:  Product=Generic RNDIS
S:  SerialNumber= XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX  < -( i changed that one myself )
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=usbfs
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=usbfs
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
kari@amd64-desktop:~$ 


I have IP for my HTC, and i can see contens with "pls" .. but no sync.

Hell ..  i can browse HTC with Nautilus, but no sync

Synce-trayicon says : not connected. 



Kari

---

### Post by Kari_Juhani on 2007-06-07
???

Weird .. and Multisync crashes when it tryes to get info from first plug-in

Kari

---

### Post by Bittermormon on 2007-06-22
***Noob warning here***

When I type 
```
cd
svn co https://synce.svn.sourceforge.net/sv...trunk/libsynce
```
I get the following:
```
svn: PROPFIND request failed on '/sv...trunk/libsynce'
svn: PROPFIND of '/sv...trunk/libsynce': 405 Method Not Allowed (https://synce.svn.sourceforge.net)
```

can someone tell me whats up?

---

### Post by calemus on 2007-06-28
edmont much much props brother you are amazing. I truly apreciate the phenominal sight of people being so cooperative

---

### Post by bradleesargent on 2007-07-05
I think you have to right click on the link and select "copy link location" and then type:
svn co 
followed by shift-control-v to copy the link location into the terminal window and press enter.

This worked for me.

---

### Post by Bittermormon on 2007-07-05
thanks, I'll try it again and see what happens

---

### Post by karlhm76 on 2007-07-20
This all worked really really well and smooth.  - well as far as recompiling the kernel anyway. Now I have the problem with my restricted drivers. I have an atheros chipset, you see, and I require the madwifi driver, plus I require other things such as the nvidia restricted module etc etc.

how do I recompile those so they are the same as my linux headers?

Now I am putting off rebooting :-)

---

### Post by laredo7mm on 2007-07-20
Thanks for the great how to, I have just about everything working except for the GnomeVFS.  When I type in synce:/// in the "run application" window I get an error saying:

```
Couldn't display "synce:///".
The attempt to log in failed
```

If I type in synce:/// in the command line I get the following error:

```
bash: synce:///: No such file or directory
```

The pop up notification works, and when I type pls in the terminal, I see my ppc's files.

Any help would be greatly appreciated.  Thanks.

---

### Post by karlhm76 on 2007-07-23
Hi everyone, I overcame my problem with restricted drivers, but something doesn't seem right.

I get to step 

> sudo lshw -businfo | grep usb


I have a Prophet and before connecting my device it gives me:

Code:

usb@1        usb1       bus            UHCI Host Controller
usb@2        usb2       bus            UHCI Host Controller
usb@2:2                 bus            Logitech BT Mini-Receiver
usb@2:2.2               input          Logitech BT Mini-Receiver
usb@2:2.3               input          Logitech BT Mini-Receiver
usb@3        usb3       bus            UHCI Host Controller
usb@4        usb4       bus            EHCI Host Controller

After connecting my device and run the same code again it gives me:
Code:

usb@1        usb1       bus            UHCI Host Controller
usb@1:2                 generic        Generic RNDIS
usb@2        usb2       bus            UHCI Host Controller
usb@2:2                 bus            Logitech BT Mini-Receiver
usb@2:2.2               input          Logitech BT Mini-Receiver
usb@2:2.3               input          Logitech BT Mini-Receiver
usb@3        usb3       bus            UHCI Host Controller
usb@4        usb4       bus            EHCI Host Controller

So I have a Generic RNDIS... I would need compile some stuff to get the rndis driver:

And I see that instead of generic RNDIS, I have a Palm Treo.. (its a 750 running WM5) installed on usb@2:3.

Which is great! I can see it connected!
And I have installed odccm and synce and all that.

But which driver do I use if any? I have read on the net that for kernels > 2.6.21 RNDIS is not required.

Can anyone verify that? and if RNDIS is not required, how the hell do I connect to my PPC without it?

By the way. When I connect the PPC to my ubuntu box, the connection gets detected as a network connection and it comes up in my network manager list of available connections. If I choose it, it seems to connect!

but I can't do anything more than that.

Help?

---

### Post by garlicsalt2 on 2007-07-23
> **karlhm76 said:**
> Hi everyone, I overcame my problem with restricted drivers, but something doesn't seem right.

I get to step 



And I see that instead of generic RNDIS, I have a Palm Treo.. (its a 750 running WM5) installed on usb@2:3.

Which is great! I can see it connected!
And I have installed odccm and synce and all that.

But which driver do I use if any? I have read on the net that for kernels > 2.6.21 RNDIS is not required.

Can anyone verify that? and if RNDIS is not required, how the hell do I connect to my PPC without it?

By the way. When I connect the PPC to my ubuntu box, the connection gets detected as a network connection and it comes up in my network manager list of available connections. If I choose it, it seems to connect!

but I can't do anything more than that.

Help?

Actually, I believe that for kernels greater than 2.6.21, you don't need a separate driver for RNDIS, as support is built into the kernel. However, I don't think that the stock Ubuntu kernels have made it to 2.6.21 as of yet, so this wouldn't likely apply to most users. 

As for having a Network Connection show up, yes, that is normal.

Remember that odccm must be run as user root. However, if it is detecting the network interface at all, I think that it is safe to say that the kernel drivers are being loaded. If you want to be absolutely certain, go to a command prompt or favorite terminal program, and type ```
lsmod|grep "rndis_host"
```. This command shouldn't produce any output after a fresh reboot, before you plug in your device. However, after you plug-in your Treo, you should see something like:
```

rndis_host              8192  0
cdc_ether               7424  1 rndis_host
usbnet                 19848  2 rndis_host,cdc_ether
usbcore               134408  5 rndis_host,cdc_ether,usbnet,ohci_hcd

```

The numbers I listed above may vary, since I have compiled my kernel drivers from source, using a newer version of the code, but I expect that everything else would be the same.

To see if your phone is being recognized, go again to a command prompt, and type: ```
pls
``` If all is well, then you should see the contents of your \My Documents folder in your main device memory.

---

### Post by karlhm76 on 2007-07-24
Awesome garlicsalt2 thanks for your help!

Yes, I am running kernel 2.6.22.1 which is the latest stable kernel as of this writing. I followed this guide and ended up with it, but it doesn't matter because it works much nicer and I was able to compile it for K7 :-)

anyway, I'm getting some problems which looks like corruption with the file listings in nautilus, but I may try recompiling synce and all that because I recently recompiled the kernel.

the trayicon seems to work somewhat though.

Thanks again.

---

### Post by daemon73 on 2007-08-02
Hello!

for the first time I was able to get it all working ... dist: feisty with kernel 2.6.20-16-generic ... I can't believe it :)

Thank you!

---

### Post by karlhm76 on 2007-08-13
> **garlicsalt2 said:**
> ```
** (process:16456): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'

```

I had this problem, as well. I was puzzled at first, but after awhile, I had the crazy idea to disable my device pin/password. After that, I can access my device just fine. Go figure...



I got this message on my Palm Treo 750, I didn't have a device password set, but odccm just wasn't picking it up. I found the cause, it was a setting on the PPC called "USB to PC" in connection settings. I had unticked "enable advanced network functionality" for some reason. As soon as I ticked it again, everything worked.

I don't know what the equivalent setting is for other PPCs.

One symptom was when I connected my device, Network Manager didn't try and connect to it.

However I could see the device using 
sudo lshw -businfo | grep usb

Maybe this will help someone.

---

### Post by cyber_bushi on 2007-08-19
Hi fellows,

I'm not a py-guru so maybe one could help me out on this part:
```

hot33331@x20:~/temp/sync-engine$ ./sync-engine 
Traceback (most recent call last):
  File "./sync-engine", line 39, in <module>
    from SyncEngine.kernel import SyncEngine
  File "/home/hot33331/temp/sync-engine/SyncEngine/kernel.py", line 24, in <module>
    import rrasyncmanager
  File "/home/hot33331/temp/sync-engine/SyncEngine/rrasyncmanager.py", line 24, in <module>
    from partnerships import Partnership
  File "/home/hot33331/temp/sync-engine/SyncEngine/partnerships.py", line 27, in <module>
    import formatapi
  File "/home/hot33331/temp/sync-engine/SyncEngine/formatapi.py", line 21, in <module>
    import formats
  File "/home/hot33331/temp/sync-engine/SyncEngine/formats/__init__.py", line 21, in <module>
    import parser
  File "/home/hot33331/temp/sync-engine/SyncEngine/formats/parser.py", line 28, in <module>
    import conversions
  File "/home/hot33331/temp/sync-engine/SyncEngine/formats/conversions.py", line 25, in <module>
    import pyrtfcomp
ImportError: librtfcomp.so.0: cannot open shared object file: No such file or directory

```
It occures when I wanna start my sync-engine. I already do have connection to my pda to the file-system. 
Best regards,

cb

---

### Post by cyber_bushi on 2007-08-20
Well I figured that 
```
ImportError: librtfcomp.so.0: cannot open shared object file: No such file or directory
```

would be the interesting part of the output and that the lib would be missing. Then again, the lib exists and I even added her to the PYTHONPATH environment variable. Any suggestions? PLEASE? I'm sooooo close to the goal - file system access to the pda is already established, better than it was with my ipaq. So pleeeeeeeeaaaaaseee if you got any clue at all... write! Would love to being able to finally sync again!
Thanks in advance,

cb

---

### Post by AhronZombi on 2007-08-26
i cannot seem to get rndis-lite to see my t-mobile dash / htc excalibur it just sees this when i plug it in
```
[ 4592.648000] usb 1-2: new full speed USB device using ohci_hcd and address 10
[ 4592.876000] PM: Adding info for usb:1-2
[ 4592.876000] PM: Adding info for No Bus:usbdev1.10_ep00
[ 4592.876000] usb 1-2: configuration #1 chosen from 1 choice
[ 4592.880000] PM: Adding info for usb:1-2:1.0
[ 4592.880000] PM: Adding info for No Bus:usbdev1.10_ep81
[ 4592.880000] PM: Adding info for No Bus:usbdev1.10_ep02
[ 4592.880000] PM: Adding info for No Bus:usbdev1.10
```

please assist me if you can

---

### Post by kjaggu on 2007-08-30
Way too much coding.... 

Waiting for Plug and Play. Hoping to get it soon for non-techies like me. Also wanted to know, if i can transfer files to and from WM5 devices using Ubuntu or Kubuntu??

---

### Post by jvalenzuela on 2007-08-30
> **laredo7mm said:**
> Thanks for the great how to, I have just about everything working except for the GnomeVFS.  When I type in synce:/// in the "run application" window I get an error saying:

```
Couldn't display "synce:///".
The attempt to log in failed
```

If I type in synce:/// in the command line I get the following error:

```
bash: synce:///: No such file or directory
```

The pop up notification works, and when I type pls in the terminal, I see my ppc's files.

Any help would be greatly appreciated.  Thanks.

> **Bittermormon said:**
> ***Noob warning here***

When I type 
```
cd
svn co https://synce.svn.sourceforge.net/sv...trunk/libsynce
```
I get the following:
```
svn: PROPFIND request failed on '/sv...trunk/libsynce'
svn: PROPFIND of '/sv...trunk/libsynce': 405 Method Not Allowed (https://synce.svn.sourceforge.net)
```

can someone tell me whats up?

First at all, thanks for this greate how-to and all other posts. That's a great job!

Added to all things comments on this thread, I've added some little things to let this USB syncro work.

synce:/// error: In my case, the make install send the libsyncevfs.so file to the /usr/local/lib/gnome-vfs-2.0/modules/ directory, after try with LD_LIBRARY_PATH without sucess I did:

cd /usr/lib/gnome-vfs-2.0/modules
sudo ln -s /usr/local/lib/gnome-vfs-2.0/modules/libsyncevfs.so libsyncevfs.so

And runs...

Second thing -> When install, all runs well (except multisync) but after first reboot the WM5 doesn't connect (rndis OK, dhcp OK but not pls, pstatus and other) with the error:
pls: Could not find configuration at path '(Default)'

I've must to change this on wm5 device (sorry mi PPC is in spanish :-)

Inicio->Programas->ActiveSync->Menú->Conexiones... and there activate the option "Sincronizar todos los PC utilizando esta conexión" -> USB
(Something like: Syncronize all PC using this connection -> USB)

Now, I'm trying to resolve the multisync crash when try to syncronize -> Perhaps because I'm using the Universe paquets for feisty and not compiled directly? ... I don't now.

---

### Post by cyber_bushi on 2007-09-02
got a little bit further, still an error occurs:
```

pywbxml.c: In function '__pyx_f_7pywbxml_wbxml2xml':
pywbxml.c:176: error: 'WBXML_LANG_AIRSYNC' undeclared (first use in this function)
pywbxml.c:176: error: (Each undeclared identifier is reported only once
pywbxml.c:176: error: for each function it appears in.)
pywbxml.c: In function '__pyx_f_7pywbxml_xml2wbxml':
pywbxml.c:292: error: 'WBXMLGenWBXMLParams' has no member named 'produce_anonymous'

```
any clues?

best regards,

cb

---

### Post by jvalenzuela on 2007-09-03
Well continuing my last post. I remove all the standard Feisty packets related with opensync and multisync (doesn't run with Wm5) and recreate using [www.synce.org](www.synce.org) recomendations. Add these to the /etc/apt/source.list and try...

deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main
deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main

evo2-sync runs without any problem but unfortunately I have a Broken pipe error with synce-plugin (both of them the first coming from opensync and the one compilated for me using the synce recomendations... I suppose is some kind of bug on the 0.22 versión. I must to review).

Someone has this plug-in installed and running? If so, I will appreciate a lot a few lines with your experience.

---

### Post by jekkil on 2007-10-01
Hi,
I have a WM5 gsm (Samsung I600).
I suceed to connect and see the content of the gsm with pls and odccm.
But I would like to use the gsm as modem for UMTS/HSDPA networks. I have installed RNDIS, but failed to get to internet.
I get the default internet address 169.254.2.2, but when I try so start "Internet connection sharing" on the gsm, it keeps blocking saying "verifying the usb connection"

Anyone has an idea to solve this ?

Jekkil

---

### Post by happybrick on 2007-10-20
New to linux so go easy on me ;)

I fall at the first hurdle:

```
$ patch -p1 < linux-2.6.22-rndis_host-wm5.patch
```

> can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-2.6.22-rc3-orig/drivers/net/usb/rndis_host.c 2007-05-25 22:55:14.000000000 -0400
|+++ linux-2.6.22-rc3/drivers/net/usb/rndis_host.c      2007-05-27 17:06:16.000000000 -0400
--------------------------

I have two foldes in /usr/src:
linux-headers-2.6.22-14 
 linux-headers-2.6.22-14-generic

I've tried patching in both of them (wasn't sure which to use) but both give me the same error.

Can anyone help?

---

### Post by Jc2k on 2007-10-21
Just a few thoughts from a SynCE hacker.

[http://www.synce.org/index.php/Windows_Mobile_2005_HCL]("http://www.synce.org/index.php/Windows_Mobile_2005_HCL")

Don't rely on this. Use of usb-rndis-lite is preferred in all cases, and if it doesn't work we need to know so we can fix it.

In Ubuntu, i strongly suggest against recompiling the kernel just for usb-rndis-lite. It just isn't needed! Instead do this:

> svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install

The SVN driver has the added bonus of letting you access the internet via your WM6 phone. There are no difficult patching steps to get wrong either.

The best people to help you with SynCE are the SynCE team, so i look forward to seeing you in [IRC]("http://www.synce.org/index.php/IRC") or the [mailing list]("https://lists.sourceforge.net/lists/listinfo/synce-users").

---

### Post by recrem on 2007-10-21
Thanks for these instructions Jc2k!

My problem is that when executing the first instruction I get a fail error stating that the certificate can't be trusted even though I tell it to accept the certificate.  How can I rectify this?  I'm new to Linux but remember it has something to do with adding the certificates in the Synaptic Package Manager but can't find advice on this at the SynCE Wiki site...

Here is a copy of my terminal screen...

dan@dans-laptop:~$ svn co [https://synce.svn.sourceforge.net/sv...usb-rndis-lite](https://synce.svn.sourceforge.net/sv...usb-rndis-lite)
Error validating server certificate for 'https://synce.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/sv...usb-rndis-lite'
svn: PROPFIND of '/sv...usb-rndis-lite': 405 Method Not Allowed ([https://synce.svn.sourceforge.net](https://synce.svn.sourceforge.net))

---

### Post by chrishutt on 2007-10-25
I Just had the same problem - fortunately really simple.

I'm guessing that like me you just copied the commands and pasted into your terminal? Problem is the link for the files to checkout has been truncated where is says sv..usb-rndis-lite and should read :

svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/)

That should get the files you're after.

---

### Post by chrishutt on 2007-10-25
OK, it's just truncated my text as well.

why don't you click the link and copy it from your browser address bar and add svn co to the front in terminal. That's what I did.

---

### Post by chrishutt on 2007-10-25
This is the line "svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/"

(without speech marks)

---

### Post by recrem on 2007-10-25
Thanks for that Chris!  I'll be trying that as soon as I get home from work this evening...

---

### Post by jvalenzuela on 2007-10-30
Thanks Jc2k, I've really used this.

From the last post I've update to Gutsy (my Dell D630 now with Compiz looks great :-) and I've updated the WM5 config with some easy paths to this general work.

1) I've install usb-rndis-lite using Jc2k instructions.
2) I've blacklisted the ipaq module (don't use this module when the WM5 is connected)
3) I've added [http://jonnylamb.com/debian](http://jonnylamb.com/debian) ./ (source and binary). This repository has the 0.10 versión for synce programs (odccm, synce-gnome-vfs, librapi2, etc.) so no make is necesary.
4) Install synce-trayicon and synce-softwaremanager (using .deb packets for the first post here).
5) Create /etc/init.d/odccm and related links (same first post here expect that using odccm from jonnylamb repository the binaries are in /usr/sbin) and autostart session with synce-gnome.
6) Create firestarter rules for rndis0 interface.
7) RUN.

pls, nautilus and the rest is running. The next step is update the WM5 using rndis connection (for now no traffic throw the PC is running)

---

### Post by XioNoX on 2007-11-01
Aaaaarrrggg

I still can't make it working :/


1) I've install usb-rndis-lite using Jc2k instructions.
2) I've blacklisted the ipaq module
3) I've added [http://jonnylamb.com/debian](http://jonnylamb.com/debian) ./  (and install many packages)
4) Install synce-trayicon and synce-softwaremanager (using .deb packets for the first post here).
   but :
$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory

And rebooted.
But when I plugged my device in, and do a dmesg,
[ 1330.432000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 1330.628000] usb 2-1: configuration #1 chosen from 1 choice
[ 1330.736000] rndis_host 2-1:1.0: RNDIS_MSG_QUERY(0x01010101) failed, -110
[ 1330.736000] rndis_host: probe of 2-1:1.0 failed with error -110
and it is all...

please, help :)
XioNoX

answer : [https://sourceforge.net/forum/forum.php?thread_id=1802535&forum_id=96106](https://sourceforge.net/forum/forum.php?thread_id=1802535&forum_id=96106)

---

### Post by toneman77 on 2007-11-10
> **XioNoX said:**
> Aaaaarrrggg
...
4) Install synce-trayicon and synce-softwaremanager (using .deb packets for the first post here).
   but :
$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
...

answer : [https://sourceforge.net/forum/forum.php?thread_id=1802535&forum_id=96106](https://sourceforge.net/forum/forum.php?thread_id=1802535&forum_id=96106)

> **edmondt said:**
> 
```
sudo ln -si /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2
```

should do the trick

---

### Post by Jc2k on 2007-11-14
It makes me sick when I see new Ubuntu users having to recompile their kernels!! Just do this, and it'll fix the -110 errors too.

```
sudo apt-get install linux-headers-generic build-essential subversion
svn co http://synce.svn.sf.net/svnroot/synce/trunk/usb-rndis-lite
make
sudo ./clean.sh
sudo make install
```

If you have any more errors /please/ come to the synce mailing list or irc...

---

### Post by Jc2k on 2007-11-19
Gutsy users:

You need these repositories... Add them to your /etc/sources.list however you normally do it.
```
deb http://ppa.launchpad.net/synce/ubuntu gutsy main
deb-src http://ppa.launchpad.net/synce/ubuntu gutsy main
```

Then install odccm and some support libraries
```
sudo apt-get update
sudo apt-get install odccm python-rapi2 python-rra python-rtfcomp libwbxml2-dev synce-gnomevfs subversion build-essential linux-kernel-headers
```

The following will install the driver you need to connect your device:
```
svn co http://synce.svn.sf.net/svnroot/synce/trunk/usb-rndis-lite/
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```

Now start odccm and connect your device:
```
sudo odccm -f
```

If you want to sync your device, you are up to here in the wiki instructions now.
[http://www.synce.org/index.php/SyncEngine#pywbxml](http://www.synce.org/index.php/SyncEngine#pywbxml)

There is more to follow. Note that this method will mean you get a transparent upgrade to 0.11 when it is released...

---

### Post by saulalbert on 2007-12-07
Hi Jc2k - thanks for the useful how-to, I also felt a bit sick contemplating recompiling my kernel!

I have been trying to compile usb-rndis-lite but I'm having some issues:

```
[noi]% make                                                                                   ~/Desktop/usb-rndis-lite 9:53
make -C /lib/modules/2.6.22-14-386/build SUBDIRS=/home/saul/Desktop/usb-rndis-lite modules
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory. Stop.
make: *** [default] Error 2
```

I think it's a problem in the Makefile - which points at KDIR := /lib/modules/$(shell uname -r)/build

I don't have a  /lib/modules/2.6.22-14-386/build directory - I have the following:

```
[noi]% ls                                                                                   /lib/modules/2.6.22-14-386 9:56
initrd  madwifi        modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap    modules.symbols  ubuntu
kernel  modules.alias  modules.dep     modules.inputmap     modules.ofmap      modules.seriomap  modules.usbmap   volatile
```

I'm running Gutsy,

I hope that's useful. Any ideas?

Cheers,

Saul.

---

### Post by michellez on 2008-02-09
I'm stuck...

```
wget http://kuci.org/~teddy/ubuntu/synce-software-manager_0.9.0-2_i386.deb
wget http://kuci.org/~teddy/ubuntu/synce-trayicon_0.9.0-2_i386.deb
```

These give me a 404 not found error :( Where can I find these now?

Cheers,
Shell

---

### Post by foxy123 on 2008-02-18
I wonder if I can connect my GPS sat nav using this method. Apparently is runs on WM5 and I only need to access files on it. I've got MyGuide 3100.

---

### Post by zikace on 2008-03-07
If you have this ```
 make: *** [default] Error 2 
```
You must install the headers : ```
sudo apt-get install linux-headers-$(uname -r)
```
Try it, it should work then.

---

### Post by djbon2112 on 2008-03-12
I'm trying what Jc2k said (and followed [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) to the letter) but my Q isn't connecting. I get this:

```
joshua@joshua-laptop:~$ pls

** (process:26855): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'
```

I don't even know what I've done or haven't done here anymore.

---

### Post by Dr. Felger on 2008-03-14
This thread is really helpful and is getting me closer.  

After completing the above steps, starting 'odccm -f' and plugging in my O2 Windows Mobile Device, I am getting this error:

** (odccm:25587): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

It keeps printing this message until I hit Ctrl+C.  Has anyone seen this?

Here is another strange thing.  I am using a verizon air card 595 with gnome-ppp.  When I plug in my WM device, Ubuntu tries to use it as the network connection.  I can't go back to the ppp connection until I tell it to reconnect.  

Any ideas?  I am using the latest Hardy Heron version, btw.  Thanks.

---

### Post by Eric B on 2008-04-04
I can browse my device just fine, but it is not picked up as an RNDIS device until I enable Internet Sharing. Internet Sharing somehow mysteriously worked once, but never has again. I even checked my IP to verify it was indeed using my device to connect to the internet.

Here I plug in my device. If I run synce-serial-start, I can browse it move files, etc.
```
[ 5584.312000] usb 2-2: new full speed USB device using uhci_hcd and address 10
[ 5584.504000] usb 2-2: configuration #1 chosen from 1 choice
[ 5584.508000] ipaq 2-2:1.0: PocketPC PDA converter detected
[ 5584.512000] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
[ 5596.100000] usb 2-2: USB disconnect, address 10
[ 5596.100000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 5596.100000] ipaq 2-2:1.0: device disconnected
```

Here I enable Internet Sharing.
```
[ 5597.600000] usb 2-2: new full speed USB device using uhci_hcd and address 11
[ 5597.796000] usb 2-2: configuration #1 chosen from 1 choice
[ 5599.436000] rndis0: register 'rndis_host' at usb-0000:00:1d.1-2, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
```

I switch to eth2 which is what it shows up as, and I get nothing. I was told to add 
```
auto rndis0 
iface rndis0 inet dhcp
```
to /etc/network/interfaces, however it is always detected as eth2 and never rndis0.

Any help would be appreciated. Thank you.

---

### Post by beefcurry on 2008-04-19
I am trying to do the same thing, after following the steps here [http://www.synce.org/moin/SynceWithUbuntu]("http://www.synce.org/moin/SynceWithUbuntu")

I still can't detect my HTC Hermes (Dopod 838pro branded) with the pls step. Anyone have any insights?

---

### Post by azizzle on 2008-06-05
All I would like to do is be able to add files to my device, i.e. cabs, pics and ringtones or movies. I do not need to sync for emails or calendar events. How do I do this?? I don't want to go through the trouble of installing synce if I don't have to. 

Everytime I connect my pda the network tries to pick it up, i guess as a modem. How do I stop this from happening.

---

### Post by fhteagle on 2008-06-13
I need a bit of assistance repairing my usb-rndis setup. Either during a kernel update to 2.6.24-18-generic, or attempting to get synce working to actually sync and not just Internet Share, I took a very functional usb-rndis module set and broke it. 

what I know:

with usb-rndis-lite (version 3488 ) make'd and installed per jc2k directions (has worked well in the past), no module-assistant package installed, no synce packages installed:

- with no device plugged in, ifconfig shows no rndis0 or eth2

- with device plugged in, internet sharing not started (same result for two freshly restarted winmo 6 devices):

dmesg: 
[ 4715.449232] usb 2-2: new full speed USB device using uhci_hcd and address 10
[ 4715.614294] usb 2-2: configuration #1 chosen from 1 choice
[ 4717.419363] rndis0: register 'rndis_host' at usb-0000:00:1d.1-2, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
[ 4717.422295] udev: renamed network interface rndis0 to eth2

ifconfig:
eth2      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:8050  Metric:1
          RX packets:6 errors:5 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:363 (363.0 B)  TX bytes:732 (732.0 B)

dhclient eth2 returns:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth2/80:00:60:0f:e8:00
Sending on   LPF/eth2/80:00:60:0f:e8:00
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.102 on eth2 to 255.255.255.255 port 67
DHCPACK of 169.254.2.2 from 169.254.2.1
bound to 169.254.2.2 -- renewal in 1071327 seconds.

dhclient.leases last entry:
lease {
  interface "eth2";
  fixed-address 169.254.2.2;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 2592000;
  option dhcp-message-type 5;
  option domain-name-servers 208.67.220.220,65.111.181.232;
  option dhcp-server-identifier 169.254.2.1;
  option dhcp-renewal-time 1296000;
  option dhcp-rebinding-time 2268000;
  renew 4 2008/6/26 13:11:28;
  rebind 4 2008/7/10 09:36:01;
  expire 1 2008/7/14 03:36:01;
}

- device removal with internet sharing off:

dmesg:
[ 5163.801559] usb 2-2: USB disconnect, address 10
[ 5163.803610] eth2: unregister 'rndis_host' usb-0000:00:1d.1-2, RNDIS device (SynCE patched)


- device attached with internet sharing started (and yes internet sharing reports "connected"):

dmesg:
[ 5250.906481] usb 2-2: new full speed USB device using uhci_hcd and address 11
[ 5251.074479] usb 2-2: configuration #1 chosen from 1 choice
[ 5252.820646] rndis0: register 'rndis_host' at usb-0000:00:1d.1-2, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
[ 5252.823453] udev: renamed network interface rndis0 to eth2

dhclient:
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth2/80:00:60:0f:e8:00
Sending on   LPF/eth2/80:00:60:0f:e8:00
Sending on   Socket/fallback
DHCPREQUEST of 169.254.2.2 on eth2 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.102 from 192.168.0.1
DHCPREQUEST of 192.168.0.102 on eth2 to 255.255.255.255 port 67
DHCPACK of 192.168.0.102 from 192.168.0.1
bound to 192.168.0.102 -- renewal in 127477 seconds.

lease {
  interface "eth2";
  fixed-address 192.168.0.102;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 259200;
  option routers 192.168.0.1;
  option dhcp-message-type 5;
  option domain-name-servers 208.67.220.220,65.111.181.232,192.168.0.1;
  option dhcp-server-identifier 192.168.0.1;
  option dhcp-renewal-time 129600;
  option dhcp-rebinding-time 194400;
  option netbios-node-type 4;
  renew 0 2008/6/15 15:07:37;
  rebind 1 2008/6/16 09:43:00;
  expire 2 2008/6/17 03:43:00;
}

yet ifconfig still reports:
ifconfig:
eth2      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet addr:169.254.2.2  Bcast:169.254.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:8050  Metric:1
          RX packets:7 errors:5 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:640 (640.0 B)  TX bytes:15364 (15.0 KB)

- reboot of computer, adding/removing module-assistant package of usb-rndis, starting internet sharing before first connect to a freshly booted laptop, etc. do not change the results above

So, the things that jump out at me:

- the dmesg line about udev renaming rndis0 to eth2 (I do not remember seeing that before I tried the module-assistant package installed rndis modules or synce packages)
- the successful dhcp lease of a "valid" internet sharing ip
- network manager / ifconfig fail to see the new dhcp config

so yeah, what would cause the above symptoms? 

let me know if you need outputs of anything else / config files, etc...

thanks!

---

### Post by fhteagle on 2008-06-15
First off thanks to jc2k for replying in irc...

Problem _apparently_ solved. It seems that I had not actually removed package "odccm", despite asking synaptic to remove it. Now that odccm is actually gone, the dhcp is behaving as expected again.

Next question is can someone point me to a recommended set of steps to get synce working with evolution _without_ breaking usb-rndis's ability to run Internet Sharing sessions?

Thanks!

---

