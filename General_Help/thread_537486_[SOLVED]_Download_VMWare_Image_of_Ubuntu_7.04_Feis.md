---
title: "[SOLVED] Download VMWare Image of Ubuntu 7.04 Feisty Fawn"
date: 2007-08-29
forum: General Help
---

### Post by JawsThemeSwimming428 on 2007-08-29
I'm looking for a pre-made VM of Ubuntu Feisty Fawn (GNOME) in English. On the Virtual Appliance Marketplace, the only GNOME VM's of Feisty are either server or in another language. Anyone know where I can get one?

---

### Post by apetresc on 2007-08-29
There seems to be one towards the bottom of this page: [http://www.thoughtpolice.co.uk/vmware/](http://www.thoughtpolice.co.uk/vmware/)

Hope this works :)

---

### Post by JawsThemeSwimming428 on 2007-08-30
Thanks, I did see that page before and the reason I didn't use it is because all of the images are server images. Is there a big difference between the regular Feisty install the Server install?

---

### Post by apetresc on 2007-08-30
> **JawsThemeSwimming428 said:**
> Thanks, I did see that page before and the reason I didn't use it is because all of the images are server images. Is there a big difference between the regular Feisty install the Server install?

Oh, sorry, I didn't realize those were server images. In any case, the only difference between a server install and a desktop install is that the desktop install has "ubuntu-desktop" package, which brings in a lot of other packages (making up the desktop) as dependencies. If you install the server version in a VM and simply type ```
sudo apt-get install ubuntu-desktop
``` then it will be exactly identical to a normal desktop install.

---

### Post by JawsThemeSwimming428 on 2007-08-30
Thanks very much! That is exactly what I needed to know!!

---

### Post by kieranmullen on 2007-08-30
Why doesnt ubuntu but vmware relases out and put them on the main page?

Are these the only vm releases that are available?

thank you

KieranMullen

---

### Post by rmclaug5 on 2007-09-03
Moved post    Sorry, I am new to this board and I couldn't find a way to delete this.

---

### Post by jamiepane on 2007-09-03
I'm running a Ubuntu 7.04 Virtual Machine off of Windows with VMware. I did it by following this walkthrough. I HIGHLY recommend you read.

[http://www.linux.com/articles/58176](http://www.linux.com/articles/58176)

Note: I assume you've downloaded VMPlayer from VMware. If not, do it!

---

### Post by JawsThemeSwimming428 on 2007-09-03
Thanks for the link...that is a good read. I have been trying out some other distros through VM and Ubuntu is still on the top. Linux Mint was pretty good and I am waiting to try Mepis and Sabayon. Any thoughts?

---

