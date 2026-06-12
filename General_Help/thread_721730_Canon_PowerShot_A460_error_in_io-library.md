---
title: "Canon PowerShot A460 error in io-library"
date: 2008-03-11
forum: General Help
---

### Post by Superkoop on 2008-03-11
When I first plug in my camera, (Canon PowerShot A460) my camera is autodetected, and it asks me if I would like to import photos, so I press import photos. And then on the next import screen it shows me asking where I would like to put the pictures, and what type of camera it is, and all that. The type of camera I have selected is USB PTP class camera, and I have tried a lot of the other types of cameras (along with most of the Canon series listed). But at the bottom of that import window, it gives me the following error:

```
An error occurred in the io-library ('Could not find the requested device on the USB port'): Could not find USB device (class 0x6, subclass 0x1, protocol 0x1). Make sure this device is connected to the computer.
```

I have tried to import my pictures using other programs, but those programs don't even say there is a camera attached to the computer. 

And the only other info on this error I have found off of google was a bug from OpenSolaris, and that looks like a much different problem. [http://bugs.opensolaris.org/view_bug.do?bug_id=6536628](http://bugs.opensolaris.org/view_bug.do?bug_id=6536628)

I am using Gutsy 64bit, and when I had first installed Ubuntu I was able to import my photos without a hitch. Now I can't. 
Any help would be appreciated as I would like to be able to get my pictures on the computer.
Thanks.

---

### Post by Superkoop on 2008-03-13
*Bump*

---

### Post by Superkoop on 2008-03-14
*Bump*

---

### Post by Superkoop on 2008-03-15
Well I have figured out that this happened because I updated my kernel, 2.6.24-8-generic is the one I am using. But if I boot into my older kernel (2.6.22-6 I believe) I can get my pictures to import. 
I guess I'll upgrade to a newer kernel and see if my camera will work with that one. Worth a shot anyways. (I'd like to be able to import my pics w/o having to boot into an older kernel)

Edit: Kernel  2.6.24-12-generic gave me the same problem, perhaps it has something to do with me using a Hardy Kernel in Gutsy. And Gphoto (or whatever it is that imports the photos) isn't configured for the newer kernel. I guess I will wait until Hardy comes out, and see if it works with that. If not, I will post a bug report. 
Guess I'm stuck booting into an older kernel to import my pics for now.

---

