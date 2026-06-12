---
title: "hp pavilion a705w wont install"
date: 2008-03-06
forum: General Help
---

### Post by Cibico99 on 2008-03-06
Hello, I have an Hp Pavilion A705w. I am trying to install ubuntu on it, it boots the cd and then i go to launch or install, it loads the kernel and then on the next loading screen it freezes after about 3 little sections. Please help

---

### Post by m.musashi on 2008-03-06
I've had this problem (or similar) before. In my experience HPs have issues with ACPI. Try adding acpi=off to the boot line. I forget the key to allow you to edit but I think it's one of the F keys.

---

### Post by Cibico99 on 2008-03-06
Yea its F6, but what do i put in? "acpi=off" but without the quotes right?

---

### Post by m.musashi on 2008-03-06
Yes. If it's F6 it should open up a boot line with a bunch of stuff. Move to the end and add

acpi=off

no quotes or anything and then press enter. It may help but no guarantee.

---

### Post by Cibico99 on 2008-03-06
is it acpi=off or acpi-off, equals or no equals

---

### Post by m.musashi on 2008-03-06
Oops. Sorry. Typo. It's an equal sign.

---

### Post by Cibico99 on 2008-03-06
nope it still does the same thing, just stops after 3 bars

---

### Post by m.musashi on 2008-03-06
I'm not sure the exact command but you can also add

nolapic

I think that's it. Try both. You can also try the graphic safe mode. The reason it won't boot is usually some hardware incompatibility. You have to figure out what it is and then try and get it to ignore it.

---

### Post by Cibico99 on 2008-03-06
so what is it, "nolapic acpi=off"?

---

### Post by m.musashi on 2008-03-06
I think so. It's been a while. You can add multiple options. Just put a space between each one.

---

### Post by Cibico99 on 2008-03-06
okay here is the exact line of code, can u tell me what it should be and thanks for all this help
file=/cdrom/preseed/ubuntu.seed boot=casper initrd-/casper/initrd.gz quiet splash --
that is the exact line for the Start or install ubuntu option, if you could repost the exact line of what it should be that would be great thanks

---

### Post by m.musashi on 2008-03-06
I don't have a live CD running but based on your line just add the nolapic etc like this

file=/cdrom/preseed/ubuntu.seed boot=casper initrd-/casper/initrd.gz quiet splash nolapic acpi=off --

I don't know what the -- is for at the end but I'd leave it.

---

### Post by Cibico99 on 2008-03-08
Yea i tried that and that didnt work, i dont know whats goin on

---

