---
title: "Connecting a Nexus 7 to Kubuntu"
date: 2013-01-15
forum: General Help
---

### Post by Monsuco on 2013-01-15
I recently purchased a Google Nexus 7. I love it except I can't figure out how to sync with Kubuntu. The Nexus won't mount as mass storage so I have to use MTP. What's the best way to handle MTP on Kubuntu?

---

### Post by Jedwinjim on 2013-01-15
I use airdroid. Free app & it's just drag & drop in a web browser from there! Easy :)

---

### Post by Jedwinjim on 2013-01-15
although with all of my music uploaded to googleplay (space for 20,000 free songs) I just pin what I want to listen to when I'm at home/work. Films on dropbox, books on amazon kindle app, job done!

---

### Post by Monsuco on 2013-01-15
I knew there were alternatives, but at times I would rather just connect my Nexus to my laptop and have it work like it does on Windows.

---

### Post by mgw2008 on 2013-01-20
You need kio-mtp - there's a package installer available.

---

### Post by ljonesj on 2013-01-21
also make sure u have usb debugging mode on in the system settings of the nexus 7

---

### Post by SeijiSensei on 2013-01-21
I had trouble getting kio-mtp to work with my Samsung Galaxy S3 so I paid $1.40 to install [Wifi File Transfer Pro](https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en) on my phone.  That starts a web server on the phone that you can access with a browser and upload and download files.  It's nowhere near as nice has using the phone as a mass storage device, but it does work reliably.  The Pro version has no size limits on transfers and enables you to select multiple files/directories to upload. 

The reasoning for the decision to no longer support USB mass storage on ICS and later Android builds is [here](http://www.reddit.com/r/Android/comments/mg14z/whoa_whoa_ics_doesnt_support_usb_mass_storage/).  Apparently if your phone supports an external memory card you can use USM with that.  The Nexus doesn't have a memory card slot, though.

---

### Post by Jim Connachan on 2013-01-21
Try this it worked for me but watch when you go to /media/nexus7 the files take a good few minutes to work. You may also have to be root.

[http://forum.manjaro.org/index.php?topic=1672.0](http://forum.manjaro.org/index.php?topic=1672.0)

JC

---

