---
title: "Tricky ps/2 to usb mouse problem"
date: 2007-09-16
forum: General Help
---

### Post by md_lasalle on 2007-09-16
Hello all

I'm currently setting up my KVM switch between my macbook pro running ubuntu 6.10(kde) and another computer.

The problem is, the KVM switch works only with PS/2 ports, while the macbook pro only has usb ports.

Solution : i bought an adapter that takes 2 ps/2 ports and converts them to only 1 usb male.

My keyboard seems to work, but not the mouse. I have booted into Mac Os X to test, and the mouse is working there.

Is there some trick i have to tell ubuntu so that my mouse can be recognized by the OS ?

Thanks for any input.

---

### Post by leonidas666 on 2007-09-16
I have a similar device (keyboard and mouse PS/2 -> USB),  and for me it works without installing any driver / making any explicit setting (ubuntu 7.04). I believe this device is implementing some kind of USB standard (like USB Mass storage), so that no extra driver should be necessary.
Maybe your KVM is creating the problem? Does it work if you plug in mouse and keyboard straight away, without the kvm?
Maybe you have a problem in your xorg.conf file? (i did not make any changes in my file, and for me it works, though).

---

### Post by md_lasalle on 2007-09-16
thanks for the reply.

well if i plug my stuff directly, yes it works.

I dont know if it changes anything, but my mouse is usb, i connect it to the kvm with a usb to ps2 adaptor, then with the kvm end, i convert ps/2 to usb ( man what a senseless setup lol )

and it works on my macOsX as stated above so my guess is the problem is software.

Do you have any idea what should be in my xorg.conf file to make it work ?

Thanks

---

### Post by leonidas666 on 2007-09-17
> **md_lasalle said:**
> 
I dont know if it changes anything, but my mouse is usb, i connect it to the kvm with a usb to ps2 adaptor, then with the kvm end, i convert ps/2 to usb ( man what a senseless setup lol )

I ran into a similar problem some time ago, i wanted to use a ps/2 mouse at the COM -Port (don't ask me why :) ). I wanted to use a ps/2 to serial adapter which i had lying around, but then i found out that these kind of adapters are just electrical connections, and the controller in the mouse has to take care of whether it is sending data according to USB,Ps/2 or Com Protocoll. So in short, the adaptor will work if you bought it together with the mouse, but if you take the adapter from one mouse and want to use it with another mouse it might not work. However, in your case, since the mouse is working without the KVM switch (did you use the adapter when you were testing it in OS X?) this is probably not the problem. 

Maybe the KVM-Switch is somehow creating the problem? Did you try disconnecting the KVM and only connecting the KWM once the computer has booted?

I cannot help you more with the xorg.conf, but if you enter "xorg.conf mouse" in google i'm sure you'll find lots of information.

---

### Post by md_lasalle on 2007-09-17
yeah i had the exact same kvm setup while testing in OS X, but thanks for the tips, I'll look into xorg.conf mouse configs deeper.

---

