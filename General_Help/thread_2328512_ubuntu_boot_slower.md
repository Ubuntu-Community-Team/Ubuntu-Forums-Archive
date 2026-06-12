---
title: "ubuntu boot slower"
date: 2016-06-21
forum: General Help
---

### Post by kaky951357 on 2016-06-21
hello,
after I installed a Linux distro with Ubuntu I notice that Ubuntu are booting slower than when he was the only system on my laptop, and before displaying the Ubuntu logo, when booting it shows some code line saying that system have issues if necessary I can screen shot
how can i make ubuntu boot faster ?

---

### Post by ventrical on 2016-06-21
What current version of ubuntu are you using?

Regards..

---

### Post by Impavidus on 2016-06-22
If you put a second Linux system on your computer, then that second system may now be in control of the bootloader, which might be causing an issue. Which distro and version is the other Linux? Maybe you can update the configuration of the other Linux's bootloader. Or you can try moving control of the bootloader back to Ubuntu.

---

### Post by kaky951357 on 2016-06-22
hello,
thanks for help 
my current ubuntu version is 15.10 the other distro is kali linux 2.0 ,grub is controled by kali linux

---

### Post by ventrical on 2016-06-22
This could be a systemd issue. I am not sure if upgrading to 16.04 lts would help. Could you try to boot  from Grub using upstart and see if there is difference? If upstart not installed:

```

sudo apt-get install upstart

```

Could you send some hardware specs?

Regards..

---

### Post by kaky951357 on 2016-06-22
Hello,
i'm Afraid to upgrade my system because the last time i did it to 16.04 i had Some serious issues forced me to reinstall ubuntu, how can i boot from upstart? where i have to install upstart (ubuntu or kali)?
i have a asus X555LA i5 5200U Intel HD Graphics 5500 4GB RAM 500GB HDD

---

### Post by ventrical on 2016-06-22
> **kaky951357 said:**
> Hello,
i'm Afraid to upgrade my system because the last time i did it to 16.04 i had Some serious issues forced me to reinstall ubuntu, how can i boot from upstart? where i have to install upstart (ubuntu or kali)?
i have a asus X555LA i5 5200U Intel HD Graphics 5500 4GB RAM 500GB HDD

It should be in Grub options... ummm you are using 15.10 (wily werewolf) I am, pretty sure it had default systemd.

Here is how to check upstart version.

```

initctl --version

```

regards..

---

### Post by kaky951357 on 2016-06-22
hello,
upstart is already installed on my ubuntu system how can i boot from it in grub (what should i select on grub) ?? 
thanks for help

---

### Post by ventrical on 2016-06-22
> **kaky951357 said:**
> hello,
upstart is already installed on my ubuntu system how can i boot from it in grub (what should i select on grub) ?? 
thanks for help

It will say (upstart) if you have default systemd. But if the (upstart) is not there then it is booting into upstart by default and then this is not the problem.

regards..

---

### Post by ventrical on 2016-06-22
What ubuntu distro? What desktop did you install?

regards..

---

### Post by kaky951357 on 2016-06-23
hello,i successfully boot from upstart.
the option boot with upstart wasn't in grub belong to kali i hade to select "ubuntu avanced option" and then select "ubuntu (upstart)" , it was faster than the normal boot, how can i force ubuntu to always boot with upstart ?

---

### Post by kaky951357 on 2016-06-23
and using upstart it tell me something about disk, it that normal ?

---

### Post by ventrical on 2016-06-23
> **kaky951357 said:**
> and using upstart it tell me something about disk, it that normal ?

Often time there will be verbose script displaying the actions during bootup.  

Uh.. there is a way to boot to default (upstart) but I do not have info handy at the moment.

Wait.. and someone will reply.

Regards..

---

### Post by QDR06VV9 on 2016-06-23
Permanent switch back to upstart

Install the upstart-sysv package, 
```
sudo apt install upstart-sysv
```
which will remove ubuntu-standard and systemd-sysv (but should not remove anything else -- if it does, yell!), and run 
```
sudo update-initramfs -u 
```
After that, grub's "Advanced options" menu will have a corresponding "Ubuntu, with Linux ... (systemd)" entry where you can do an one-time boot with systemd.

If you want to switch back to systemd, install the systemd-sysv and ubuntu-standard packages.
And after do not forget to run again
```
sudo update-initramfs -u
```

---

### Post by kaky951357 on 2016-06-24
hello,
thanks i can boot from upstart by defaults 
have nice day

---

