---
title: "Nvidia drivers causing too many headaches"
date: 2012-11-15
forum: General Help
---

### Post by tamccullough on 2012-11-15
Ok, I'm a little confused, and so maybe some of you can help me out.

I've installed 12.10 64 bit ubuntu on a multiboot machine.

AMD Phenom(tm) II X6 1090T Processor × 6 
16 GiB
GTX 460

 I am having problems with the nvidia drivers.  I first tried  the nvidia current drivers that are default with a new install and then I tried the  drivers found in the X Updates ppa and still with no success...

My resolution gets fudged and compiz doesn't appear to work.  Panels aren't displayed.

So I have had to use the default Nouveau driver just to work with 12.10.  Which is fine, but I am a graphics person that works heavily with blender and of course with Steam coming...

I also have 12.04 and Win 7 installed on the same system. No problems.

I have been using ubuntu for a while now, since 9.04 and I have never encountered any issues with nvidia drivers.

Is it nvidia or canonical?

Could I get some help, or maybe someone could direct me to an appropriate thread?

Cheers

---

### Post by Laiquendi on 2012-11-15
I have almost identical situation, only the processor is different (intel i5), the rest (including GTX460) is similiar. And I have dual boot too.
And no problems ever encountered...
So it may be some trash in your configuration, programs or the CPU. nVidia drivers are working great with this GPU.

---

### Post by tamccullough on 2012-11-15
Hmmm.

I'm not really sure what I am doing wrong then.

This was a clean vanilla install of 12.10.  ( same thing with another system in the house using an older cpu and a gtx285) both are having the same problems.

Now I am even more confused.

I wonder if I should disconnect the other drives and just run another clean install.

---

### Post by tamccullough on 2012-11-15
Could I have done something in my BIOS on both systems to have messed this up?

---

### Post by bogan on 2012-11-15
Hi!, **tamccullough**,

Several Posts report trouble with 12.10 installs due to the correct linux header files not being available for the nvidia driver to create the necessary kernal module.

Run the following; if it reports 'linux-headers-generic is already the latest version', then this is not the cause of your problem. ```
sudo apt-get update
sudo apt-get install linux-headers-generic
```If it installs the file, purge and re-install the nvidia driver. ```
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo reboot
``` Substitute for 'nvidia-current', "nvidia-experimental-304" or whatever package you want.

CHao!, **bogan**.

---

### Post by tamccullough on 2012-11-16
bogan!

You sir are an amazing person.

I was certain I would have to reinstall, and was about to do just that, but decided to hold off and see if somebody had a fix.

Glad I did.

Following your directions, both of my 12.10 installs are working with nvidia drivers now.

I am a happy man again.  No more howling at the moon.

Cheers!


This fix should be a little easier to sniff out...

fix for nvidia drivers not working properly with ubuntu 12.10 displaying poor resolution and no compiz

maybe that will help the next guy find this thread.


QUOTE=bogan;12356678]Hi!, **tamccullough**,

Several Posts report trouble with 12.10 installs due to the correct linux header files not being available for the nvidia driver to create the necessary kernal module.

Run the following; if it reports 'linux-headers-generic is already the latest version', then this is not the cause of your problem. ```
sudo apt-get update
sudo apt-get install linux-headers-generic
```If it installs the file, purge and re-install the nvidia driver. ```
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo reboot
``` Substitute for 'nvidia-current', "nvidia-experimental-304" or whatever package you want.

CHao!, **bogan**.[/QUOTE]

---

