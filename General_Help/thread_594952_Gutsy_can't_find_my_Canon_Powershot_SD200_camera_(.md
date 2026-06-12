---
title: "Gutsy can't find my Canon Powershot SD200 camera (w/error msg)"
date: 2007-10-28
forum: General Help
---

### Post by ticopelp on 2007-10-28
Hi there.

I have a Canon Powershot SD200 that worked fine under Feisty, and would import photos without a problem. Ever since updating to Gutsy, however, I can't seem to get it to work. I get this error:

> Camera not ready, multiple 'Identify camera' requests failed: OS error in camera communication

I tried other applications, such as Digikam, and no luck there either. 

I searched around the forum to try to find some answers -- the closest I got was someone recommending "downgrading" to an earlier version of libgphoto, but I don't know how to do that. 

Any ideas?

Thanks.

---

### Post by stomponthis on 2007-10-29
What app do you currently use?
I have a Canon Powershot G5 and it works with gtkam, but its not very flash.
I have VirtualBox with XP for things like my camera.  set up a share drive and it works good for downloading photos.  Just another option if things don't get better!

---

### Post by Selcal on 2007-10-29
I was attempting the same with a Camcorder and Kino.  I found that Linux USB isn't quite ready for USB.2.  I do know that a lot of newer periferals only work with USB2.  The solution i found was to install a PCI firewire card and hook it up via firewire.  It worked like a charm.

I don't know if it helps, but if you can swing firewire give it a shot.

---

### Post by broseman on 2007-11-01
Exactly the same problem here with the same camera...

Do you have any news on this?

---

### Post by ticopelp on 2007-11-01
> **broseman said:**
> Exactly the same problem here with the same camera...

Do you have any news on this?

Unfortunately, no. 

To answer some of the other questions in this forum, I use gThumb to import my pictures -- and, again, it always worked fine in Feisty. 

I don't know whether it's the new libraries, my upgrade, or what broke this functionality, but I may end up just going back to Feisty, quite honestly, until this gets cleared up. I managed a workaround by syncing my photos on my Feisty-running laptop and just moving them over to my main PC. Annoying, but I don't know what else to do.

---

### Post by timcredible on 2007-11-01
is gutsy mounting the camera as an external hard drive?  check the desktop to see if a new icon appears when you plug in your camera.  if not, then it's probably the files that match the vendor ID and model ID to a device type are missing your camera's info.  i had to modify one of those files to get feisty to recognize my fuji s5200, but gutsy has all the cameras in my family in it's files (four fujis, 5 kodaks) and digikam detects all of them correctly.  your other option is to just buy a card reader and put the memory card in it and read the files off of it just like a flash drive.  that option works all the time.

---

### Post by kweinert on 2007-11-01
I have a somewhat similar problem: Canon 350D. I don't get an error message, everything just hangs. It used be (under feisty) that I could plug in the camera and an explorer popped up and worked fine.

Now all that happens is the application hangs. gtkam, gphoto2, it doesn't matter.

I have reason to believe that it's a USB problem as usbview gives me errors and lsusb also hangs.

Should I start a different thread for this one?

All the people that suggest other ways of reading the images (like accessing the card) are, in a way, missing the point. It just **worked** prior to the upgrade. Since hardware hasn't changed and it no longer works, then it's some sort of Gutsy problem and I'll be glad to file a bug (or add info to an existing one) if I can find what bug to refer to.

Thanks.

---

### Post by frainbart on 2007-12-27
I have the same problem with the same camera. It was working fine under Feisty and now I cannot import photos from the camera in Gutsy.

---

### Post by bhall430 on 2007-12-30
I'm having the same trouble with my canon, I didn't even get vmware to identify the USB device!

---

### Post by ticopelp on 2007-12-31
Hope is faint, but a bump of sorts...

Does anyone know how to roll back the libgphoto drivers so I can get my camera to work?

---

