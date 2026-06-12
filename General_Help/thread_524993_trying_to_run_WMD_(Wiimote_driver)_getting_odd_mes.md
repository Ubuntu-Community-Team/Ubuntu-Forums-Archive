---
title: "trying to run WMD (Wiimote driver) getting odd message."
date: 2007-08-13
forum: General Help
---

### Post by billdotson on 2007-08-13
I am getting the following message when I try to run WMD.py:

bill@bill-desktop:~/Desktop/wmd-0.1.2$ sudo python WMD.py
Traceback (most recent call last):
  File "WMD.py", line 45, in <module>
    wmd = WMD()
  File "WMD.py", line 29, in __init__
    ev = EVDispatcher( cf )  # In a way this is the core of the program. It dispatches events between each module
  File "/home/bill/Desktop/wmd-0.1.2/wmd/EVDispatcher.py", line 19, in __init__
    self.xlib = EventBridge_PyXlib( self, cf )
  File "/home/bill/Desktop/wmd-0.1.2/wmd/EventBridges/PyXlib.py", line 16, in __init__
    self.d = display.Display( ENV_DISPLAY )
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 124, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/var/lib/python-support/python2.5/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots

I downloaded wmd again and extracted it agian just to make sure and it yesterday and it worked.  I don't think I have changed anything.  I reinstalled     

    *  bluetooth (for bluez, at least in Ubuntu 7.04)
    * python-bluez
    * python-xlib
    * python-pygame
    * python-osd
    * python-matplotlib
    * python-numpy
    * python-numpy-ext 
 
And I am still getting it.  Any ideas on what is going on?

and still nothing.

---

### Post by marrvel on 2007-08-16
Hi Bill,

I´m getting the same message did you manage to fix this in the end?

Cheers

---

### Post by marrvel on 2007-08-16
I found the answer, I hadn`t patched python xlib, try this it worked for me:

Open your /usr/lib/python<version>/site-packages/Xlib/protocol/display.py file, then change line 530 from:

```
recv = self.socket.recv(2048)
```

to

```
recv = self.socket.recv(4096)
```

python version is currently 2.5 (08/07)

I got this from here:
[http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html]("http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html")

Thanks ozar

---

### Post by billdotson on 2007-08-18
yep, that works.  Great job.  However in Feisty display.py is at this location: /usr/share/python-support/python-xlib/Xlib/protocol or at least it was for me.
Thanks man.

---

### Post by jdfreshwater on 2007-08-20
I still had problems with getting WMD running, I had much more success with cwiid, which seems to work much the same way, with less hassel.

---

### Post by JamesA on 2007-08-22
im getting:

```
OSError: [Errno 2] No such file or directory: '/dev/input/uinput'

```

if i locate 'uinput' i get

```

/home/james/wii/wmd-0.1.2/wmd/EventBridges/uinputKeymap.py
/home/james/wii/wmd-0.1.2/wmd/EventBridges/uinput.py
/home/james/wii/wmd-0.1.2/wmd/EventBridges/uinput.pyc
/home/james/wii/wmd-0.1.2/wmd/EventBridges/uinputKeymap.pyc
/home/james/wii/cwiid-0.5.03/wminput/uinput.c
/home/james/wii/cwiid-0.5.03/wminput/uinput.d
/home/james/wii/cwiid-0.5.03/wminput/uinput.o
/home/james/wii/wmd-trunk/wmd/EventBridges/uinputKeymap.py
/home/james/wii/wmd-trunk/wmd/EventBridges/uinput.py
/home/james/wii/wmd-trunk/wmd/EventBridges/.uinputKeymap.py.swp
/home/james/wii/wmd-trunk/wmd/EventBridges/.uinput.py.swp
/home/james/wii/wmd-trunk/wmd/EventBridges/uinput.pyc
/home/james/wii/wmd-trunk/wmd/EventBridges/uinputKeymap.pyc
/lib/modules/2.6.17-10-generic/kernel/drivers/input/misc/uinput.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/input/misc/uinput.ko
/usr/include/linux/uinput.h
/usr/src/linux-2.6.21.5/drivers/input/misc/uinput.c
/usr/src/linux-2.6.21.5/include/linux/uinput.h

```

any ideas?

---

### Post by JamesA on 2007-08-22
found a solution for 

```
OSError: [Errno 2] No such file or directory: '/dev/input/uinput'
```

install a program called 'mouseemu' and that should sort the problem. How i found this was i simply searched synaptic for 'uinput' and that came up. Being 4:04am i thought '**** it', installed it, now WMD seems to work.


Either way, WMD , its C altrenative Cwiid and  of course libwiimote-0.4 all seem to be very temperamental, and are only really fit for the machines they where built on. All the wiki how-to information even on their own sites are complete garbage. i've a sneaky suspicion somone has been deleting entrys. Especially on the WMD's page where the page keeps saying things like "edit the following file - instructions on what to edit above", and there is nothing above..

I had to find a 3rd party site for Cwiild to actually get instructions on how to install the thing, you'd think it would be in the readme file. And libwiimote... it keeps extracting itself to a directory neither application is looking for.

So unless you are a sad ******* like me, that spent a good two days trying to get this working, almost destroying your OS uninstalling python2.4 (not compatible with WMD), and almost punching your own face in with fustration, then i suggest stay away from this untill alternative, more developed projects arise.

---

### Post by sefs on 2007-08-22
Why would you want to run Weapons of Mass Destruction?

---

### Post by billdotson on 2007-08-23
actually, did you do sudo modprobe uinput , that usually fixes errors related to uinput...

---

### Post by jdfreshwater on 2007-10-15
[http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote]("http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote")
This should fix the problem of having to redo modprobe uinput after a reboot.
> 
Make sure that the uinput module is loaded on system startup and your mythtv user has read access to the created device /dev/input/uinput. I added the following lines to /etc/rc.local

 modprobe uinput
 chmod a+r /dev/input/uinput

---

