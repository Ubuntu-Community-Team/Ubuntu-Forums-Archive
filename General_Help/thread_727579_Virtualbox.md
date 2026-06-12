---
title: "Virtualbox"
date: 2008-03-17
forum: General Help
---

### Post by jwkungfu on 2008-03-17
Hello,
I'm trying to start up Audacity using Virtualbox to run a Rode USB Podcaster microphone (as this microphone is not supported by Linux...
I've set up a virtual machine (XP M$ Windoze) and when I tried to run it an error message appeared....


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


As usual with error messages, this is of absolutely no help to ordinary folk...
Can somebody decipher it and suggest what I should do next?
Many many thanks in advance!!

jw.

---

### Post by wolfen69 on 2008-03-18
first go to system>admin>software sources and make sure everything is checked off. also check third party tab. close and reload.


then in terminal:
```
sudo dpkg --configure -a
```
then
```
sudo apt-get install -f
```
then
```
sudo /etc/init.d/vboxdrv start
```

may or may not help, but it can't hurt. i had this problem also, but can't remember how i fixed it.

---

### Post by cdaringe on 2008-03-18
I had a similair error previously.  I read around on forums with no one able to address it.  It seemed to be some sort of permissions problem.  Try running your virtual machine as root

```
gksudo virtualbox
```
see if it boots up

also (somone please correct me if im wrong), im not sure that virtual box (the free edition) supports USB.  you could read more about that on their website.  sorry to bum you out if its true :(

---

### Post by jwkungfu on 2008-03-18
> **wolfen69 said:**
> first go to system>admin>software sources and make sure everything is checked off. also check third party tab. close and reload.


then in terminal:
```
sudo dpkg --configure -a
```
then
```
sudo apt-get install -f
```
then
```
sudo /etc/init.d/vboxdrv start
```

may or may not help, but it can't hurt. i had this problem also, but can't remember how i fixed it.

Here is what I did in a terminal window...

john@john-laptop:~$ sudo dpkg --configure -a
john@john-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-imaging tk8.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
john@john-laptop:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                             [ OK 

Same error came up though.....???

---

### Post by jwkungfu on 2008-03-18
Hey!!!   :O)
Thanks for that!!
I think you are on to something there!!!
It started to run, but then it said fatal error because of the floppy drive....
Something I don't understand about this emulation lark (amongst almost everything else)... what are they talking about when they ask for the floppy drive???!!!
I click on and run the emulator, I tell it which mode I want it to emulate, I tell it what Application to run with.... what's with this other crap?
Sorry if I sound frustrated, it's because I am!!   ;o)

---

### Post by jwkungfu on 2008-03-18
I had a look on the VirtualBox web site and found this...

    * Virtual USB Controllers. VirtualBox implements a virtual USB controller and allows you to connect arbitrary USB devices to your virtual machines without having to install device specific drivers on the host. 

    * Remote Desktop Protocol. Unlike any other virtualization software, VirtualBox fully supports the standard Remote Desktop Protocol (RDP). A virtual machine can act as an RDP server, allowing you to "run" the virtual machine remotely on some thin client that merely displays the RDP data. 

    * USB over RDP. With this unique feature, a virtual machine that acts as an RDP server can still access arbitrary USB devices that are connected on the RDP client. This way, a powerful server machine can virtualize a lot of thin clients that merely need to display RDP data and have USB devices plugged in.

---

### Post by amd-64 on 2008-03-18
I remember having to add my user name to the vboxusers group. Before you start the VM, you can edit the machine properties and remove floppy drive if you wish.

---

### Post by Dr.Ninethousand on 2008-03-18
don't you just have to run and set up your virtual machine as root/sudo?

because that's how I solved these errors..

---

### Post by 3rdalbum on 2008-03-18
> **Dr.Ninethousand said:**
> don't you just have to run and set up your virtual machine as root/sudo?

because that's how I solved these errors..

That's one way to solve the error, but it's a really, really bad way. If an attacker compromised the virtual machine, and you're running Virtualbox as root, the attacker could likely get control over your host OS. Whereas if Virtualbox is running as an ordinary user, an attacker would only get the same permissions as that user.

You should go to System > Administration > Users And Groups and add your user account to the "vboxusers" group. Then log out and log back in again. It takes so little effort to do, so make sure you do it and stay safe :-)

---

### Post by markharding557 on 2008-03-18
> **jwkungfu said:**
> Hello,
I'm trying to start up Audacity using Virtualbox to run a Rode USB Podcaster microphone (as this microphone is not supported by Linux...
I've set up a virtual machine (XP M$ Windoze) and when I tried to run it an error message appeared....


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


As usual with error messages, this is of absolutely no help to ordinary folk...
Can somebody decipher it and suggest what I should do next?
Many many thanks in advance!!

jw.
deactivating nmi-watchdog by editing boot1st men should help did for me here is another post about it

> 
Hi, captlogic & all
I Have the same problem as yours (exactly)
the problem is : nmi_watchdog is activated, I'm searching the utility of it and how to set it off.

For the moment :
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ) see "linux hosts" and "debian/ubuntu ..."

after somme search :
[http://forums.gentoo.org/viewtopic-t...irtualbox.html](http://forums.gentoo.org/viewtopic-t...irtualbox.html)

I try it and come back

Edit :
and it works :

I have edited the /boot/grub/menu.lst : (and BACKUP it before)
add nmi_watchdog=0 at the end of kernel line

    kernel /vmlinuz-2.6.20-16-generic root=UUID=XXX ro quiet splash nmi_watchdog=0

reboot
re-install vbox (from deb package or sources)

Edit 2 : more information about NMI : [http://www.linux-tutorial.info/modul...ial&pageid=116](http://www.linux-tutorial.info/modul...ial&pageid=116)

---

### Post by wolfen69 on 2008-03-18
> im not sure that virtual box (the free edition) supports USB
it does support USB with a workaround:

gksudo gedit /etc/init.d/mountdevsubfs.sh

Once you&#8217;ve got that open in Gedit, type CTRL-F to search for a string. Search for &#8216;magic&#8217; (sans quotes).

That should bring you to this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount &#8211;rbind /dev/bus/usb /proc/bus/usb

All those pound signs are comments. Remove them from the last four lines so you end up with this:

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount &#8211;rbind /dev/bus/usb /proc/bus/usb

Save the file and exit Gedit. Round one goes to the user!

Now we&#8217;re going to create a group called usbusers. Go to System-> Administration-> Users and Groups. Type in your password and then click the Manage Groups button. From there click the Add Group button and name it usbusers. Check off your username below. Exit these windows and round two goes to us.

groups.png

Now we&#8217;ve got to change a file in udev. So, let&#8217;s gedit it and gedit over with. I&#8217;ll apologize for the bad jokes in a later post.

    gksu gedit /etc/udev/rules.d/40-permissions.rules

Again, CTRL-F to bring up the search dialog and search for &#8216;usbfs replacement&#8217; (again, sans quotes). Once you find it, you should be looking at this:

    USB devices (usbfs replacement)
    SUBSYSTEM==&#8221;usb_device&#8221;, MODE=&#8221;0664&#8243;

You&#8217;ll want to change it to this:

    # USB devices (usbfs replacement)
    SUBSYSTEM==&#8221;usb_device&#8221;, GROUP=&#8221;usbusers&#8221;, MODE=&#8221;0664&#8243;

Save your file and exit out of Gedit.

Now, the last bit of hackery which may or may not be required for you. It was for me. We&#8217;re going to add a mount to /etc/fstab for usb devices using usbfs.

    gksudo gedit /etc/fstab

At the bottom, add the following line:

    none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Save the file and exit Gedit. Phew! Now, the easiest way to get all of these changes working on your system is to restart it. So go ahead and do that and then I&#8217;ll see you back here in a few.

Back? Great. Time to plug in your USB device, whether it&#8217;s a thumb drive, an iPod or something else, plug it in and let Ubuntu detect it.

Now, we&#8217;re going to open up Virtualbox and make some changes to your XP machine BEFORE you start it up. So go to Applications-> System Tools-> Virtualbox and get it started up.

Highlight your XP machine (if it&#8217;s not the only instance of a virtual machine) and click the Settings button at the top of Virtualbox. You should now have a USB option on the left hand side of your settings. Click the add icon on the right hand side (see the pic below) and select the device from the list. In my example, it&#8217;s a 512MB memory key. Now click the Okay button.

vboxaddusb.png

Start up your virtual XP machine and you will see a notice pop up courtesy of Ubuntu about unsafe device removal. Nod your head sagely and let&#8217;s continue on. Once XP is up and running, it should automatically detect the new USB device, and do it&#8217;s best to install it. With my memory key, it was as simple as turning the virtual XP machine on and letting XP take care of it.

You may have to go to the Devices menu on your virtual machine (once it starts up) select USB Devices and then uncheck whatever it is you&#8217;re trying to mount.  Repeat the process, this time checking it off and it should mount if it didn&#8217;t automatically.

---

### Post by Dr.Ninethousand on 2008-03-18
> **3rdalbum said:**
> That's one way to solve the error, but it's a really, really bad way. If an attacker compromised the virtual machine, and you're running Virtualbox as root, the attacker could likely get control over your host OS. Whereas if Virtualbox is running as an ordinary user, an attacker would only get the same permissions as that user.

You should go to System > Administration > Users And Groups and add your user account to the "vboxusers" group. Then log out and log back in again. It takes so little effort to do, so make sure you do it and stay safe :-)

ha yeah..  I only played with it for a moment to go through the install process of TinyMe with a friend..  will do it this way in the future though..

---

