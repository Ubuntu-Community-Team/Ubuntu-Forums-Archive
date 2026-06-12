---
title: "WebCam and Scanner"
date: 2007-05-04
forum: General Help
---

### Post by Dave Otter on 2007-05-04
Have got Ubuntu 6.06 running OK except for my Webcam and Scanner-neither of which seem to be detected by the relevant  program.

   Any ideas appreciated.

                        Thanks

---

### Post by Thingymebob on 2007-05-04
I'm assuming these are both usb, please post the output of lsusb so we at least know what you've got.

open a terminal : 
        Applications > Accessories > Terminal
and type 
        lsusb
highlight the output with your mouse then press ctrl+shift+c to copy the text to the clipboard

Visit the sane site to see if your scanner is supported [http://www.sane-project.org/]("http://www.sane-project.org/")
and a howto here: [http://howtos.linux.com/howtos/Scanner-HOWTO/index.shtml]("http://howtos.linux.com/howtos/Scanner-HOWTO/index.shtml")

This is probably the best place to start for your webcam [http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml]("http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml")

---

### Post by Dave Otter on 2007-05-05
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 004 Device 004: ID 0c45:62bb Microdia
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
otter@otter-desktop:~$
  This is what came on following your instructions
              now what?

   Apologies for delay

---

### Post by Thingymebob on 2007-05-05
Good News! You scanner is listed on the sane site as having good support using the gt68 backend. This is assuming it has been correctly identified as many cheap scanners such as mustek use this chipset and 05d8:4002 is apparently the default product id for the GT6801 chipset

This is what you need to do:

You need a firmware file for your scanner, it will be on your windows installation disk somewhere and will be named ???fw.usb. Copy it to your desktop
if your scanner is actually an artec ultima 2000 it will be ePlus2k.usb

If you can't find it most can be downloaded from the gt68xx backend homepage
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/) if you still can't find it, shout, I'll let you know how to get it out of the windows driver disk.

 and put it in /usr/share/sane/gt68xx
in a terminal type:
```
sudo mv ~/Desktop/??fw.usb /usr/share/sane/gt68xx/??fw.usb
```You will be asked for a password, it is your login password.
??fw.usb being the name of te firmware file.
Don't forget Linux is case sensitive

Now you need to edit gt68xx.conf:
in a terminal type:
```
sudo gedit /etc/sane.d/gt68xx.conf
```

look through the file and uncomment the lines relating to your scanner (remove the # from the start of the line)
e.g if you do have the Artec Ultima 2000, change the lines:
```
# Artec Ultima 2000:
#override "artec-ultima-2000" 
#firmware "ePlus2k.usb"

TO:

 Artec Ultima 2000:
override "artec-ultima-2000" 
firmware "ePlus2k.usb"
```make sure the firmware matches what you have actually put in gt68xx folder
if the firmware line doesn't exist, add it. 

save the file and close it

now type 
**scanimage -L**
in the terminal to see if sane has correctly identified your scanner, if it does type 
**scanimage -vT** to test it, hpoefully all will pass. You should now be able to scan.

I can't test this as I don't have this scanner but it should work

Reading Material:
[http://www.sane-project.org/man/sane-gt68xx.5.html]("http://www.sane-project.org/man/sane-gt68xx.5.html")
[http://www.sane-project.org/]("http://www.sane-project.org/")

**Webcam**
Still Looking (not looking so good)

---

### Post by Dave Otter on 2007-05-06
get as far as being asked for my password- then Everything freezes-cannot type in my password

---

### Post by Thingymebob on 2007-05-06
type in your password and hit return, Nothing will happen as you are typing ( the cursor will sit at the start of the line blinking but appear to do nothing)

---

### Post by Dave Otter on 2007-05-06
just says incoddect password-but it isn't



     Will give up on this one for now--but many thanks for your input

---

