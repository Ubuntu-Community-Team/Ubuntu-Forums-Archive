---
title: "Consequence of mismatched UUID for swap when imaging Linux systems?"
date: 2014-06-21
forum: General Help
---

### Post by Roasted on 2014-06-21
I'm imaging some Linux systems on Xubuntu 14.04 using FOG. I created a master image on the smallest size hard drive I deal with, uploaded it, and deploy that to the other systems. The size of the HDD in the target systems varies quite a bit, so I use GParted to expand it.

I noticed as I booted up one of the imaged systems that for a split second there was an error about a UUID. I checked and the UUID for the EXT4 partition matches, but the UUID for swap vs what's in /etc/fstab does not match. I do not notice any other problems with the system, however. It just seems to work and function fine.

So curious me ended up here wondering if anybody can chime in as to what 'could' go wrong with this, or if perhaps there's a way to set up the imaging process to better accommodate this?

---

### Post by sudodus on 2014-06-21
I don't know FOG. But imaging a whole drive with Clonezilla and dd will re-create the UUIDs too, so the entry in fstab should match the UUID of the swap partition.

Is this a single problem (only with one of the cloned systems) or will all of the cloned systems? Could it be a copying error (maybe caused by a failing drive)?

---

### Post by Roasted on 2014-06-21
I checked all drives before I started imaging them and pulled out the ones that were failing or had bad sectors. Then I popped these drives in a spare tower I have and deployed them one at a time. My goal was to get them imaged so I can later drop them each into a desktop to hand out. This is a little home project and I don't have a world of space to daisy chain 15 desktops.

On each imaged system, the UUID for EXT4 / is fine, but it's different on each and every single system with the swap partition. I too used Clonezilla Live before, which is brilliant, but I got sick of answering a bunch of questions at startup to pull the image over SSH. Perhaps I can look into automating that. Clonezilla Server is unappealing to me given I've tried and failed to get it running a dozen times before. It looks crazy involved while FOG 'just works'. That said there's no denying CZ Live is amazing, given its capabilities from a flash drive without need for a server.

I'll have to duplicate efforts with CZ Live in the *same* method I used with FOG, just to see what it does. I don't recall seeing a UUID error, but it was SO quick before, it's possible I could have missed it.

---

### Post by oldfred on 2014-06-21
You can just edit fstab with the new UUID, if you have swap. Or create swap and then add UUID to fstab.

       sudo blkid -c /dev/null -o list

 gksudo gedit /etc/fstab

---

### Post by Roasted on 2014-06-21
Yeah - I'm aware I can change it manually. The point of this is to be as automatic as possible. That's why FOG looked so much nicer than Clonezilla Live since CZ Live asks you a bunch of questions during setup, whereas with FOG a lot of those questions are answered as part of the entire process.

I did pull an image (the same image**) from my server over SSH, and the UUID for swap matched. Clearly CZ Live is doing something FOG isn't. Given that FOG is largely meant for Windows deployment, eh okay fine, but there's a Linux option in the image field for a reason...

** When I set up the image, I took the same source, backed it up via Clonezilla to my server, then backed it up to my little FOG server. So it's the same image, but not the same image. i.e. I'm not taking a CZ image and restoring it with FOG, or the other way around. It's just the same install was used twice to back up via CZ and FOG in separate instances so I could tinker with both solutions.

I looked into automating Clonezilla Live, and it sounds like it's possible. I'm a little frustrated at the lack of documentation, though. I feel like it gives bits and pieces but doesn't give you any real meat. For example:

[http://clonezilla.org/related-articles/012_Automated_USB_thumb_drive_using_Custom/Automated_USB_thumb_drive_using_Custom.html](http://clonezilla.org/related-articles/012_Automated_USB_thumb_drive_using_Custom/Automated_USB_thumb_drive_using_Custom.html)

This article, which is the best I've found, is rather vague as it is, but not only that it assumes you are doing one drive to another and using NTFS. I'm a little unsure as to how I would populate the SSH settings/authentication portion of this... 

On one hand, it's probably a non-issue, given I can blaze through the CZ imaging process just based on memory of keypresses, but it'd be nice to drop it in place and just let it GO and do its thing. Couple that with the fact I am wildly curious and, well, here I am. :P

---

