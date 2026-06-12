---
title: "Upgraded kernel/driver, now screen is small."
date: 2013-03-05
forum: General Help
---

### Post by Heeter on 2013-03-05
Hi all,

I upgraded my kernel and nvidia driver using the xorg-edgers PPA, now my desktop is small and I have a thick black border around the desktop, and Unity is not working properly. I tried purging the kernel, but it is still doing this.

Is there a way I can fix this?

Thanks

Heeter

---

### Post by ubun_two on 2013-03-05
I just did the kernel update, and I had issue with my nvidia video card driver.  I updated it to nvidia-313, and it worked again.

---

### Post by Heeter on 2013-03-05
Hey, thanks for the reply

How did you get 313? I only see 310/304 in jockey?

Did you upgrade nvidia driver before the kernel?

Thanks

Heeter

---

### Post by ubun_two on 2013-03-05
I have it listed under "Additional Drivers" in Software Sources dialog.  I have the xorg-edgers PPA, but you seem to have that as well, so I am not sure what's different.  It seemed 310 worked for me, so you can try that if you can't find 313.

I updated nvidia driver after the kernel was updated.

---

### Post by Heeter on 2013-03-05
Well,

maybe if I can find a way to revert back to stock, I can try again, but install 313 first. I have 310 installed and it did this screen resolution problem with unity problem.

Thanks for your help so far, ubun_two

Heeter

---

### Post by Heeter on 2013-03-05
Update:

I pulled up the jockey additional driver interface, selected a generic nvidia driver, and installed and rebooted.

This did the trick

Thanks

Heeter

---

