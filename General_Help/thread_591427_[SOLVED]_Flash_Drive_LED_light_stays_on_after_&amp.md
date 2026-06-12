---
title: "[SOLVED] Flash Drive LED light stays on after &amp;quot;Unmount&amp;quot;"
date: 2007-10-25
forum: General Help
---

### Post by SnathaidMhor on 2007-10-25
Hi, If I just pull out my Mobile Mate 1 GB flashdrive it (obviously) gives me a message saying I need to "eject" it to avoid memory loss. I assume that in Ubuntu Gutsy "eject" is no longer present because I do not have that particular option, I have the option to "unmount" which is the same thing as eject.

After I "unmount" the flashdrive the led light stays on, however the Icon for the device disappears from the desktop and I do not get the "need to eject" message. 

My question is, even though the LED light stays on is my device being properly ejected or is it staying connected?

Thanks.

I am on a Dell1501 laptop, and like I mentioned before, using 7.10 Gutsy version of Ubuntu.

---

### Post by UK-Wobbie on 2007-10-25
> **SnathaidMhor said:**
> Hi, If I just pull out my Mobile Mate 1 GB flashdrive it (obviously) gives me a message saying I need to "eject" it to avoid memory loss. I assume that in Ubuntu Gutsy "eject" is no longer present because I do not have that particular option, I have the option to "unmount" which is the same thing as eject.

After I "unmount" the flashdrive the led light stays on, however the Icon for the device disappears from the desktop and I do not get the "need to eject" message. 

My question is, even though the LED light stays on is my device being properly ejected or is it staying connected?

Thanks.

I am on a Dell1501 laptop, and like I mentioned before, using 7.10 Gutsy version of Ubuntu.

Is the light flashing when unmounted? If the light is still flashing it means that the drive is still being used.
But i do not know what you mean on staying on.. Is the light on all the time when being used?

---

### Post by scohar70 on 2007-10-25
> **SnathaidMhor said:**
> My question is, even though the LED light stays on is my device being properly ejected or is it staying connected?

I have a flash drive reader and it does exactly the same thing.  You're fine as long as you do the unmount first before yanking the device out.  Once the icon disappears from your desktop, feel free to unplug!

---

### Post by mjziegle on 2007-10-25
Run a sync command and see what happens.  If the light continues flashing you're not properly removing the device.

---

### Post by chunderbunny on 2007-10-25
Short version: Yes, even though the light stays on it is safe to remove the drive after it has been unmounted. 


Long version: The problem here is that "unmount" and "eject" are not the same thing. "unmount" is a software-only operation that flushes the write buffer to the disk then disconnects the filesystem. "eject" performs the additional operation of telling the the hardware that the device is no longer in use. 

Normally "eject" is only needed for CD drives, where the tray will eject when the drive is told that the disk is no longer needed. But on USB sticks with a light, the light does not indicate whether the disk is mounted, it records whether it has been *told* that the disk is mounted or not. Since the "unmount" command does not communicate with hardware the disk is unmounted but is never told, so the light stays on.

---

### Post by SnathaidMhor on 2007-10-25
Ahhh... thank you all for your help.

It doesn't blink after I unmount it. And like I said I do not get the pop up window saying I did the wrong thing, so you all are right and it is definitely unmounted.

Thanks again!!!:)

---

