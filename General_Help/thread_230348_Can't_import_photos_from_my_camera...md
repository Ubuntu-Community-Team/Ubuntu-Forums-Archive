---
title: "Can't import photos from my camera.."
date: 2006-08-05
forum: General Help
---

### Post by eighthate on 2006-08-05
My camera: canon rebel.
 i tried importing photos from my cam using gtumb and xsane but it doesnt works, on xsane it says no device available and on gtumb it says canon_usb_get_dirents: canon_usb_long_dialogue failed to fetch direntries, returned -114...

EDIT: I also tried the programs digikam and f-spot, they crashed.

Some1 help me please.
anyone can help?

---

### Post by njzillest on 2006-08-06
what do you mean by from your cam?

do you mean a memory device (ie: flash drive, memory card) or via direct connection using USB and Camera? 


Your problem description is very vague

---

### Post by CliveP on 2006-08-06
No idea if this will help, but I couldn't read the images from my new Sony DSC-H2 under Ubuntu 6.06.  I found a workaround by forcing the camera to use PTP mode instead of automatically detecting the type of USB connection.  Hope that's useful.

---

### Post by z-vet on 2006-08-06
There are many devices (especially digital cameras) that are not yet supported. It means you need to use cardreader instead of trying to get photos from your cam directly. Worked for me...

---

### Post by noof on 2006-08-07
> **eighthate said:**
> My camera: canon rebel.
 i tried importing photos from my cam using gtumb and xsane but it doesnt works, on xsane it says no device available and on gtumb it says canon_usb_get_dirents: canon_usb_long_dialogue failed to fetch direntries, returned -114...

EDIT: I also tried the programs digikam and f-spot, they crashed.

Some1 help me please.
anyone can help?

try using gtkam (it's in the universe repos)

---

### Post by shaikhaman on 2006-08-27
CliveP Thanks !!!

I also have a Sony DSC-H2 and could not import it to my Ubuntu 6.06. And selecting PTP mode got the trick and could import easily autometically after plugin to pc and also from F-Spot !!

Ubuntu forum is great !!!!

---

### Post by soze on 2006-08-27
If you have a card reader, you might want to try my freeware program [URL="http://www.alanlight.com/dim/Dim.htm"]DIM: Digital Image Mover
[/URL]

---

