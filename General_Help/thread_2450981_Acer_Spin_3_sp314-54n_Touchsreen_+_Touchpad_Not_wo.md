---
title: "Acer Spin 3 sp314-54n Touchsreen + Touchpad Not working in Kubuntu 20.04/Ubuntu 20.04"
date: 2020-09-24
forum: General Help
---

### Post by zdos123 on 2020-09-24
Hello,
I recently acquired an Acer Spin 3 SP314-54N, it is a great laptop however i'm rather a big fan of linux so very soon after i got it i installed ubuntu on here (my end goal was kubuntu but i had a usb with ubuntu laying around) after messing around with the storage mode, switching from intel RST to AHCI, it worked and booted up smooth, however neither my touchscreen or trackpad work. I managed to fix the trackpad by changing the trackpad mode from IC2 to PS2 however the touchscreen still doesn't work because from what i've looked up the touchscreen is reliant on IC2 (i think i'm not sure), someone with the bigger brother to my laptop, the spin 5 managed to fix it by entering in "i8042.nopnp=1 pci=nocrs", that might not be precisely it as i just read it off a scribbled note, they put it into the grub when they booted it up, inbetween "splash" and "_ _ _", which i can't find when i go to the grub menu and press e on the grub, i'm pretty stuck and it would be a bummer not being able to use the touchscreen.

Thanks,
Zdos123

p.s. i've tried different kernels my current one is the default Kubuntu kernel 5.4.0-42-generic

---

### Post by CelticWarrior on 2020-09-24
Welcome.

Additional kernel parameters are added to the same line where you find "quiet splash", with a space between each one.
If it works you can make permanent.

---

### Post by fungiblename on 2020-10-24
> **zdos123 said:**
> Hello,
I recently acquired an Acer Spin 3 SP314-54N, it is a great laptop however i'm rather a big fan of linux so very soon after i got it i installed ubuntu on here (my end goal was kubuntu but i had a usb with ubuntu laying around) after messing around with the storage mode, switching from intel RST to AHCI, it worked and booted up smooth, however neither my touchscreen or trackpad work. I managed to fix the trackpad by changing the trackpad mode from IC2 to PS2 however the touchscreen still doesn't work because from what i've looked up the touchscreen is reliant on IC2 (i think i'm not sure), someone with the bigger brother to my laptop, the spin 5 managed to fix it by entering in "i8042.nopnp=1 pci=nocrs", that might not be precisely it as i just read it off a scribbled note, they put it into the grub when they booted it up, inbetween "splash" and "_ _ _", which i can't find when i go to the grub menu and press e on the grub, i'm pretty stuck and it would be a bummer not being able to use the touchscreen.

Thanks,
Zdos123

p.s. i've tried different kernels my current one is the default Kubuntu kernel 5.4.0-42-generic

This worked for me on this model of a new Spin 3 (August 2020 manufacture date) on Kubuntu 20.04, thanks! The stylus buttons don't work, but the stylus and screen do.

If you want to make this stick between boots, edit your /etc/grub/default file to look something like this near the top: 


```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
#give yourself some time to manually edit grub parameters
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nopnp=1 pci=nocrs"
GRUB_CMDLINE_LINUX=""
```


Save the file, then run ```
sudo update-grub
```

---

### Post by jonesmeier on 2021-06-21
Hello,

thank you very much for posting this and "scribbling down" those driver settings zdos123, have my touchscreen now working on a newly acquired Acer Spin 3 SP314-54N

Cheers!

---

