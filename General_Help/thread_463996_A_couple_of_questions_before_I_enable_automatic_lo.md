---
title: "A couple of questions before I enable automatic login"
date: 2007-06-04
forum: General Help
---

### Post by navneeth on 2007-06-04
I'm the only user on the computer, so I actually don't need a login window every time I start Ubuntu. But there have been instances in the past where Ubuntu would crash, and I had to go to the failsafe mode. Now, if I enable automatic login, would I be able to enter the failsafe mode by any other means, if for some reason normal Ubuntu would not boot?  

Thanks.

---

### Post by rich.bradshaw on 2007-06-04
When you get to grub, you can quickly press e to edit what you are booting, and change what you want there.

So, yes you can rescue it!

You can alwyas boot from the live-cd if you have problems and fix it that way anyway.

---

### Post by viciouslime on 2007-06-04
> **rich.bradshaw said:**
> When you get to grub, you can quickly press e to edit what you are booting, and change what you want there.

So, yes you can rescue it!

You can alwyas boot from the live-cd if you have problems and fix it that way anyway.

You don't actually need to edit anything. Recovery mode will always be an option, unless you purposely remove it. Automatic login just prevents the login screen from showing, not grub or anything else. :)

---

### Post by navneeth on 2007-06-04
Thanks for the replies. :)

> **rich.bradshaw said:**
> When you get to grub, you can quickly press e to edit what you are booting, and change what you want there.

So, yes you can rescue it!

You can alwyas boot from the live-cd if you have problems and fix it that way anyway.

I have never tried to edit the grub at start-up. I'll look it up. 

And I'm an 'Alternate Installer CD'-guy. That's because the LiveCD was just too slow. But only a few days ago I added more RAM, which should solve that problem, and also the rare crash. 

So goodbye Login screen. :)

---

### Post by reclusivemonkey on 2007-06-04
Do you mean an automatic GDM login? If anything goes wrong, you can always use ALT+F1-F6 to get any of the six terminals "underneath" X to do what you need to do.

---

