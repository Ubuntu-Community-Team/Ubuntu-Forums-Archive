---
title: "Select Networked files"
date: 2007-07-12
forum: General Help
---

### Post by twistedtwig on 2007-07-12
Hi,

I have a number of computers at home.  All my music is on my main (Ubuntu) server accessible via Samba (windows share).  When I try and view them through places, connect to server it is kind enough to give me a complete connection to the server share which is permanent. But if I am using gtkpod I don't have that share in my "places" list.  I have no idea how to access the shares to be able to copy the music across.

could someone tell me how I can do this please as I don't want to have to copy all the music I want to my desktop computer everytime I load my ipod.

Thanks

---

### Post by twistedtwig on 2007-07-13
to try and make that a little clearer.

I can connect to the samba share on the server with connect to server which places an icon on the desktop to easily get there.

When using some applications this link is available but with gtkpod it is not.  I can not figure out how I can access a samba share on another computer from here.

Is there a way to create a sym link to it, or have some sort of reference that means it would act like network places in windows.

thanks

---

### Post by twistedtwig on 2007-07-13
The way I resolved it was to mount the drive rather than use connect to server.

the "insecure" way of doing so is like this

//192.168.10.1/media /media/bMountPoint smbfs auto,username=abc,password=123,uid=1000,mask=000,user 0 0

A good guide to it is here:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

