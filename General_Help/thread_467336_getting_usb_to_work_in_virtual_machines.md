---
title: "getting usb to work in virtual machines"
date: 2007-06-07
forum: General Help
---

### Post by Frankie88 on 2007-06-07
My usb does not work in Virtual machines (windows 2000 professional) can any body help me? I use ubuntu.

I do not have a clue about computers :p

---

### Post by dagrump on 2007-06-07
Well, the first thing everyone needs to know is what virtual machine are you using?

---

### Post by borahshadow on 2007-06-07
also what device are you trying to connect to the virtual machine

---

### Post by guitarguy on 2008-03-30
I have the same problem. I have set up Virtualbox in my Ubuntu 7.10, and have Windows XP installed on a 70gig virtualHD. I went to these sites:
[http://www.arsgeek.com/?p=2776]("http://www.arsgeek.com/?p=2776")[URL="http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html"]
http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html[/URL]
I now get my USB Hard Drive to show up in my Virtualbox setting; but it is unavailable.
I guess I have to unmount it in Ubuntu? I am working on it but need some help.

Also I am wondering if I will be able to access the MIDI on my M-audio 24/96 soundcard PCI.

Thanks, guitarguy

---

### Post by 50words on 2008-03-30
If you want to get USB working in VirtualBox, you need to install the non-open-source edition from here: [http://tinyurl.com/2wtuc6](http://tinyurl.com/2wtuc6)

If you are using another virtualization product, this will not be the answer, obviously.

If you "know nothing about computers," you might find virtualization a bit difficult. Virtualbox makes it relatively easy, but you need to be comfortable working with your computer, at least.

---

### Post by guitarguy on 2008-03-30
I'm not an uber-geek, but this is my 2nd time around at trying to avoid a dualboot situation.
I did download the non-free version of Virtualbox and have got XP running on it.
I have used gedit to modify     [COLOR="Blue"]/etc/init.d/mountdevsubfs.sh[/COLOR] 
and                                      /[COLOR="Blue"]etc/udev/rules.d/40-permissions.rules[/COLOR]    as per [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=653853&highlight=VBoxManage]("http://ubuntuforums.org/showthread.php?t=653853&highlight=VBoxManage")
[COLOR="Black"] But I still get a[/COLOR] [COLOR="Blue"]Current state: Unavailalble[/COLOR] [COLOR="Black"]when I run [/COLOR][/COLOR][COLOR="Blue"]VBoxmanage list usbhost.[/COLOR]
I'm trying to hook up a 200G External USB HD and an HP Deskjet F300 printer/scanner. They both work in Ubuntu.

I did download and install Ubuntu Studio which has a modified kernel 2.6.22-14-rt.
It is a realtime kernel adapted for music production.I don't know if that is effecting the situation. All the files to edit seem to be the same as in the forums.

Hopefully I'll be able to get the USB straightened out.... but the soundcard issues (MIDI)
have got me more worried. I really don't want to have to dual boot. Any help would be appreciated.

---

### Post by theZoid on 2008-04-09
> **guitarguy said:**
> I'm not an uber-geek, but this is my 2nd time around at trying to avoid a dualboot situation.
I did download the non-free version of Virtualbox and have got XP running on it.
I have used gedit to modify     [COLOR="Blue"]/etc/init.d/mountdevsubfs.sh[/COLOR] 
and                                      /[COLOR="Blue"]etc/udev/rules.d/40-permissions.rules[/COLOR]    as per [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=653853&highlight=VBoxManage]("http://ubuntuforums.org/showthread.php?t=653853&highlight=VBoxManage")
[COLOR="Black"] But I still get a[/COLOR] [COLOR="Blue"]Current state: Unavailalble[/COLOR] [COLOR="Black"]when I run [/COLOR][/COLOR][COLOR="Blue"]VBoxmanage list usbhost.[/COLOR]
I'm trying to hook up a 200G External USB HD and an HP Deskjet F300 printer/scanner. They both work in Ubuntu.

I did download and install Ubuntu Studio which has a modified kernel 2.6.22-14-rt.
It is a realtime kernel adapted for music production.I don't know if that is effecting the situation. All the files to edit seem to be the same as in the forums.

Hopefully I'll be able to get the USB straightened out.... but the soundcard issues (MIDI)
have got me more worried. I really don't want to have to dual boot. Any help would be appreciated.

Guitar guy....have you created usbusers and added yourself to it, then log out and back in?

---

