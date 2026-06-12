---
title: "Help needed: Nikon Coolpix l14"
date: 2008-01-13
forum: General Help
---

### Post by eighthate on 2008-01-13
Hi my girlfriend recently recieved a Nikon Coolpix L14 digital camera, and is presently using ubuntu Linux 6.10, the problem is Linux is not even seeing the camera so she cant import any pictures from her camera to her computer..

What solutions are available?

Thanks.

---

### Post by yabbadabbadont on 2008-01-13
In the camera's settings menu, see if you can switch the interface to use "USB Mass Storage" mode (if it isn't already).  Then plug it in and it should be automounted as a new USB drive.  Also, I think that there is an existing udev rules bug in 6.10 relating to cameras in PTP mode.  You might want to search launchpad as I remember there being a simple solution that involved editing one of the udev rules files.

---

### Post by eighthate on 2008-01-13
I found out that she is using linux 6.06 think if i upgrade to 7.10 tha would help?

---

### Post by yabbadabbadont on 2008-01-13
The definitive answer is.... maybe.  :D

I think that Dapper Drake (6.06) also suffered from the udev rules bug.  Again, search launch pad.  Either way, switching the camera interface to "USB Mass Storage" mode should allow it to be mounted and, at least, be browsed like any other external USB drive.

---

### Post by eighthate on 2008-01-14
The camera doesnt even have that option :(

---

### Post by wolfen69 on 2008-01-14
try the 7.10 live cd to see if it works. download gthumbs and use the import feature. should work.

---

### Post by Subban on 2008-01-14
I have a couple of Nikon Coolpix cameras and both do have the setting to change between PTP and USB mass storage, in one it is right under the "USB" main menu item and can't be missed, in the other camera it is hidden slightly (rather oddly) under "Interface".

After a quick hunt on the Nikon site (in the FAQ)  it seems that camera should work as either PTP or Mass Storage, I would think there is a setting someplace but I can't find an online manual to disseminate and check for certainty myself.

Edit: Found a comment on a forum about Nikon Tech Support saying the camera only has PTP mode, I guess that trumps what their own FAQ says sadly about it doing Mass Storage mode, unless of course the tech support person was incorrect (wouldn't be first ;))

---

### Post by brommage on 2008-05-14
> **Subban said:**
> Found a comment on a forum about Nikon Tech Support saying the camera only has PTP mode, I guess that trumps what their own FAQ says sadly about it doing Mass Storage mode, unless of course the tech support person was incorrect

I have a Nikon Cooplpix L12, and I have that option. Under the menu setup> interface>usb (choose either PTP or Mass storage).

---

