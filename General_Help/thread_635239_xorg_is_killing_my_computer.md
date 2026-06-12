---
title: "xorg is killing my computer"
date: 2007-12-08
forum: General Help
---

### Post by tisa on 2007-12-08
hi,
At last, after 3 posts i've seen what is killing my cpu.i don't know why when i scroll the cpu goes to 92% of use. most of this use is done by the xorg. the thing is that actually i'm using a P4 at 2.4MHz, 512 MB of ram and an ati as a graphic card. i've already installed the ati drivers. So the question is: may be the drivers badly installed?not enought RAM?
thx

---

### Post by ajgreeny on 2007-12-08
Most likely the graphics driver.  Try using the OS ati driver instead and see if it all comes back to normal.

---

### Post by tisa on 2007-12-08
ok, i found the problem, the driver was disabled.But now i have another problem. I enabled it, and now the screen goes well, but compiz now doesn't work. when i try to enable the visual effects to extra, it tells me that:The Composite extenison is not avaliable. what's happening?
thx for your time

---

### Post by ajgreeny on 2007-12-08
I think you need xgl or something added for the fglrx to work with compiz.

---

### Post by danwood76 on 2007-12-08
you need to install the latest ati driver from their website to be able to use compiz.

a good guide is here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
you will need to follow the manual method.

it will be compiz and your driver making your CPU go full wack.
if updating the driver doesnt help you'll have to live without desktop effects.

regards,
Danny

---

### Post by pointone on 2007-12-09
I'd recommend using Xgl over the latest ATI driver. I found the latest driver was choppy.

```
sudo apt-get install xserver-xgl
```

---

