---
title: "I deleted my wireless driver"
date: 2008-03-28
forum: General Help
---

### Post by gameryoshi600 on 2008-03-28
Okay. So here is what happened.

I find a guide to get wireless on my Ubuntu Feisty Fawn...

Now, this guide tells me to delete my wireless driver and install a new one. Now I realize, this is for a Dell laptop and now my wireless is all gone.

I have a compaq Presario V6000. I need a wireless driver for this if their is one.

Thanks to anyone who bothers to help me, the n00b. Thanks guys!

---

### Post by ibuclaw on 2008-03-28
Confirm that this is your Laptop
[http://www.trustedreviews.com/notebooks/review/2006/09/29/HP-Compaq-Presario-V6000/p3]("http://www.trustedreviews.com/notebooks/review/2006/09/29/HP-Compaq-Presario-V6000/p3")

If so, we're looking for the Broadcom Wireless Drivers.

Specifically [**bcm43xx-fwcutter**.]("http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter")

Where did you get your Tutorial from, may I ask?
Deleting drivers sounds like a bit extreme.

If you used deb files, packages would of been automatically updated.
Else, the command **rmmod** to temporary disable the driver should of been the required action.

Regards
Iain

---

### Post by ibuclaw on 2008-03-28
Here is a tutorial that you show perhaps follow.

[http://ubuntuforums.org/showthread.php?t=458164]("http://ubuntuforums.org/showthread.php?t=458164")

If you are getting difficulty in setting up your wireless, then comment on what sort of problems you were having before you removed it.

We can help you through this :)

Regards
Iain

---

### Post by gameryoshi600 on 2008-05-02
uh yeah i did delete the wireless driver. but now i recovered my system then got hardy its all perfect
thanks to you anyways

---

