---
title: "Unmounting Error with Jump Drive"
date: 2008-04-25
forum: General Help
---

### Post by spacefreak86 on 2008-04-25
Not too much of a problem, but I wasn't sure where to put this. Anyway, while trying out Kubuntu Hardy, I got the following message while clicking the "safely remove" on the jump drive:

Error: kio_media_mounthelper

The device was successfully unmounted, but could not be ejected.

Anyone know a reason for this one?

---

### Post by HunterThomson on 2008-04-25
I had the same error with the beta I was running before I switched back to 7.10. It is not a problem though. Your computer can not eject the USB drive:popcorn:

---

### Post by roderick on 2008-04-26
it's cosmetic only. the error message window should probably be suppressed, but otherwise no harm.

---

### Post by spacefreak86 on 2008-04-26
I didn't think so, as you said, a USB jump drive can't be ejected. Is there a way for future version to detect what type of drive it is before spitting out with "cannot be ejected?" That seems to be more of something for a CD drive, not a USB connection.

---

### Post by roderick on 2008-04-26
HAL rules can be written to handle the events passed to the systems notification infrastructure.

I would guess you could write a specific .fdi for HAL to ignore the USB. Not sure how generic it could be written.

Jump onto the HAL lists and find out from them.

---

### Post by spacefreak86 on 2008-04-26
The what rules?

---

### Post by roderick on 2008-04-26
HAL - [http://en.wikipedia.org/wiki/HAL_(software](http://en.wikipedia.org/wiki/HAL_(software))

It's a core part of the linux hardware detection. Have a look at the wikipedia site for details and a link to various other info.

---

### Post by doorknob60 on 2008-04-28
Personally, I'd love to see this fixed, because it happens every time i choose Safely Remove on a Flash Drive, Memory Card, etc on my parents laptop, and whenever they do it, they think something's horribly wrong with their computer and bug me about it (it's running Kubuntu Hardy).

---

### Post by qpieus on 2008-04-28
This is a bug in the eject package that has apparently been fixed on fedora:

[https://bugzilla.redhat.com/show_bug.cgi?id=437362](https://bugzilla.redhat.com/show_bug.cgi?id=437362)

I looked at ubuntu launchpad and did not see any bug reports submitted for this in ubuntu. Anyone feel like submitting this bug to launchpad? I'm super busy right now with work and won't be able to submit this myself for a while.

---

### Post by spacefreak86 on 2008-04-29
Tell me how and I'll do it.

---

### Post by qpieus on 2008-05-02
> **spacefreak86 said:**
> Tell me how and I'll do it.
Thanks.

I had some time today so I just filed the bug report.

[https://bugs.launchpad.net/ubuntu/+source/eject/+bug/225946](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/225946)

Here's some info on how bugs in ubuntu are reported and tracked.
Ubuntu uses Launchpad for bug reporting/tracking:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

You'll see a button near the top labeled "report a bug". You will need to register to be able to report a bug.

Once you're in you write a short description of the problem and then they give you directions on supplying the package name and version, what happens, and what you expect to happen. It's pretty simple. The only thing I'm not sure about is whether or not I gave them the info they'll need to track down the bug. I did submit the link to the red hat bug tracker that describes the problem too. That report had some technical stuff I didn't understand but the folks at Launchpad will know what it means :)

---

### Post by tutwabee on 2008-05-12
> **roderick said:**
> it's cosmetic only. the error message window should probably be suppressed, but otherwise no harm.

Are you sure about this?  Now that I get this error message every time I safely remove a usb device my iPod screen no longer displays the "OK to Disconnect" message after I safely remove it.  Is there some extra message that may be sent to usb devices upon eject being run?

Edit: I just ran eject /dev/sdb1 to eject my iPod after it was already unmounted by hal and it is now displaying the "OK to Disconnect" screen.  I think there is more to it than just a physical eject.

---

### Post by doorknob60 on 2008-05-12
> **tutwabee said:**
> Are you sure about this?  Now that I get this error message every time I safely remove a usb device my iPod screen no longer displays the "OK to Disconnect" message after I safely remove it.  Is there some extra message that may be sent to usb devices upon eject being run?

Edit: I just ran eject /dev/sdb1 to eject my iPod after it was already unmounted by hal and it is now displaying the "OK to Disconnect" screen.  I think there is more to it than just a physical eject.

Same with my iPod, didn't try ejecting form terminal though.

---

### Post by jamlc on 2008-05-18
Hi all, anyone found a solution to this problem? I agree that there has got to be some problem, because the device (a cell phone) used to tell me the cable could be removed back on Gutsy. Now it only does it when I do sudo eject from command line. 

Thanks

---

### Post by qpieus on 2008-05-22
Here's another bug report for the same problem. The report has some workarounds:

[https://bugs.launchpad.net/ubuntu/+bug/217550](https://bugs.launchpad.net/ubuntu/+bug/217550)

---

### Post by qpieus on 2008-06-11
Here's another bug report with a patched kdeeject file. The file replaces the original in /usr/bin. This patched worked fine for me.

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/222041/comments/21](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/222041/comments/21)

The following bug report has a patch that also gets rid of the error, but the device icon stays on the desktop, which you may not like. 

[https://bugs.launchpad.net/ubuntu/+bug/217550/comments/16](https://bugs.launchpad.net/ubuntu/+bug/217550/comments/16)

The patched kdeeject file I used gets rid of the error message and also removes the device icon after the device is "safely removed".

---

