---
title: "return to Ubuntu desktop from Gnome desktop"
date: 2022-12-27
forum: General Help
---

### Post by Old Jimma on 2022-12-27
Hello Community:

I've been using the Ubuntu 22.04 desktop... and found a few Gnome tools that I like (like weather) and installed them, also. Among the things I installed was the gnome desktop.

However, at every boot, my computer booted into the Ubuntu 22.04 desktop. That was good and my preference.

... Then, on booting  a few days ago, I  noticed an option with radio buttons that offered the choice of booting into the Gnome desktop... so, I took it.


The Gnome desktop is ok, but more work than I wanted... and I want to return to the Ubuntu 22.04 desktop.

I've rebooted sever times... but it boots directly into the Gnome desktop.

How do I return to use the Ubuntu 22.04 desktop as my default option when booting?

Thanks,
OLD

---

### Post by tea for one on 2022-12-27
Are you referring to the session chosen at the log-in page?

---

### Post by Old Jimma on 2022-12-28
Hello Tea for One:

Yes. That's the button.

Currently, if I tap or click on that "gear" button, nothing happens: I don't get any response, and there are no choices offered to choose the desktop type (ubuntu, gnome, etc).

Thanks,
Old Jimma

---

### Post by #&amp;thj^% on 2022-12-28
> **Old Jimma said:**
> 

How do I return to use the Ubuntu 22.04 desktop as my default option when booting?

Thanks,
OLD

Happy Holiday older than old Jimma, have you just tried to run:
```
apt install --reinstall ubuntu-gnome-desktop
``` 
It should just force the ubuntu-gnome-desktop to reconfigure everything back to default.
If you still want to use the Gnome Offering I'm not going to be able to help you with that one. (I'm just not a Gnome fan these days)

---

### Post by Old Jimma on 2022-12-28
Hi 1Fallen:

Thank you for your reply. I appreciated it.

Tried > sudo apt install --reinstall ubuntu-gnome-desktop

and then reboot.

I couldn't get that little gear on the logon page to allow me to choose anything. .. and it just booted back into gnome.

Gnome is a nice idea, but there is alot that doesn't work as well as the Ubuntu desktop. 

Old

---

### Post by tea for one on 2022-12-28
You could reconfigure the gdm3 display manager/log in via the terminal:-
```
sudo dpkg-reconfigure gdm3
```
Then reboot.
Any improvement?

---

### Post by Old Jimma on 2022-12-29
HI tea:

thanks for your care, suggestions, and help. I am grateful for it.

I tried this... but to no avail.

I'm reinstalling Ubuntu 22.04 now... with no Gnome stuff. 

A reinstall doesn't take much time

I hope you'll have a great day!

Sincerey,
Old Jimma from the Old Country

---

### Post by #&amp;thj^% on 2022-12-29
> **Old Jimma said:**
> 

I couldn't get that little gear on the logon page to allow me to choose anything. .. and it just booted back into gnome.

Gnome is a nice idea, but there is alot that doesn't work as well as the Ubuntu desktop. 

Old


Jimma I had forgotten a bug I found early in the development cycle where you actually had to click in side the box for login name for any other desktop options would display.
See Attached photo

---

