---
title: "nautilus usb window switch"
date: 2016-07-20
forum: General Help
---

### Post by gleedadswell on 2016-07-20
This is a very minor issue which I am, nonetheless, finding somewhat annoying.  Under Ubuntu 16.04 when I insert a usb thumb drive it launches a window of nautilus displaying the contents of the thumb drive, as it should.  However, it doesn't seem to "think" of this as a window of nautilus because if I already have a nautilus window open I can't switch between the two windows using ALT+`.  This seems to be new in 16.04.  Somehow the nautilus window pointing at the thumb drive is "special" and functions as if it is a window of a different application.  Is this the expected behaviour, and is there some setting of nautilus, perhaps, which I can set so that a nautilus window displaying contents of a thumb drive will be treated just like any other nautilus window?

By the way, I am otherwise finding 16.04 to be very good.  The laptop I'm using it on seems to be performing much better under 16.04 than it did under 14.04 (quicker, seems not to heat up as much, much longer battery life).

Cheers!

---

### Post by mc4man on 2016-07-20
forget this nonsense(the forum, not you..

---

### Post by mc4man on 2016-07-20
This is the result of a long standing bug involving the trash & what happened when a nautilus window from external volume was minimized. In the case of volumes it appeared to min to the Files icon but actually went to the volume's icon (- if that icon was pinned to unity launcher.

So now all volumes other than your current Os one are controlled by their launcher icon & minimize to that icon. Notice the pips on these icons when open. So in the case of the alt switcher you'll need to use the arrow keys to go to open volumes.

Also note that now these other volumes don't need to be pinned to the launcher to control. Once open an icon will appear for however long the volume window is open.

---

### Post by him610 on 2016-07-20
> I can't switch between the two windows using ALT+

You may want to try *Alt+Tab*, it works for me.

---

