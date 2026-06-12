---
title: "VirtualBox Question"
date: 2012-10-16
forum: General Help
---

### Post by cearlp on 2012-10-16
When trying to run VBOX I get the message that VT-x/AMD-V needs to be enabled in the BIOS, How is this done?

---

### Post by PowerBarry43 on 2012-10-16
Hi Clearlp

This is done by rebooting your computer and entering the BIOS setup by pressing a key during boot. Probably DEL key or an F key. Then find the option marked Visualization or something of that ilk (will vary depending on your BIOS so I can't offer much help on finding it I'm afraid), enable it save and exit with the F10 key and you should be good to go!

Barry

---

### Post by Cheesemill on 2012-10-16
That all depends on your BIOS.

Take a look at the instruction manual for your computer/motherboard for more details.
Both your motherboard and CPU have to support this feature for you to be able to enable it.

---

### Post by lukeiamyourfather on 2012-10-16
If your machine doesn't have hardware accelerated virtualization you can disable the feature in VirtualBox, but if you have it and can enable it in the BIOS the virtual machines will run ***_way_*** faster.

---

### Post by cearlp on 2012-10-16
Thanks All,
My BIOS did have Virtualization disabled, which I enabled.

---

