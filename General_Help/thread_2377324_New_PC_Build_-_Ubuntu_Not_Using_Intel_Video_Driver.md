---
title: "New PC Build - Ubuntu Not Using Intel Video Driver"
date: 2017-11-11
forum: General Help
---

### Post by Rich_S on 2017-11-11
Just built a new PC yesterday.
  8700K 32 GB RAM 1 TB Samsung 960 Evo
  Still waiting on my 1080 Ti to come in, but put everything together and installed Ubuntu 16.04 on it.


  It's crawling.  Like 486 slow.  Windows take forever to render,  there's a huge lag when typing.  Etc.  I'm 99% sure it's a video card  issue.


  Installed Intel Graphics Update Tool.  Added OIBAF repos.  Updated all packages.  Still running ridiculously slow.


  Under Additional Drivers it says it's running the proprietary  microcode for Intel CPUs but nothing about video drivers.

Reinstalled, then installed 17.10 and now running 17.04.  Same issue every time.

lspci says "VGA compatible controller: Intel Corporation Device 3e92"  Shouldn't it say Intel 915 or HD630 or something?


  Any ideas?

---

### Post by Rich_S on 2017-11-11
Think I may have found something.  
If I run:

  env | egrep 'INTEL|GL|MESA'
  I get:
  LIBGL_ALWAYS_SOFTWARE=1
  Where is this getting set and how do I fix it?

---

### Post by Rich_S on 2017-11-11
That wasn't it.  Unset the env variable, problem remains.

---

### Post by mc4man on 2017-11-11
Maybe take a look here,
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

---

### Post by Rich_S on 2017-11-12
> **mc4man said:**
> Maybe take a look here,
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

Yep.

Here is the solution for anyone that wants to run Ubuntu on CoffeeLake integrated graphics:
  Make sure you're running Ubuntu 17.10 and everything is updated.

  _Install the latest video drivers:_

  ```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update

``` 

 _Update the kernel parameter.  I used Grub Customizer to do it:_

  ```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt update 
sudo apt install grub-customizer 

```  

Launch grub customizer, go to the General tab, and enter *i915.alpha_support=1* under Kernel Parameters.

  Reboot.

---

### Post by luifergreco on 2017-12-11
> **Rich_S said:**
> Yep.

Here is the solution for anyone that wants to run Ubuntu on CoffeeLake integrated graphics:
  Make sure you're running Ubuntu 17.10 and everything is updated.

  _Install the latest video drivers:_

  ```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update

``` 

 _Update the kernel parameter.  I used Grub Customizer to do it:_

  ```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt update 
sudo apt install grub-customizer 

```  

Launch grub customizer, go to the General tab, and enter *i915.alpha_support=1* under Kernel Parameters.

  Reboot.

I had the same issue, this worked. Thanks!!!

---

### Post by jostle on 2018-02-12
Thanks for the pointers.
My problem was that the only resolution available was 1024x768.

I didn't add the oibaf repository and have successfully got 4K output by just editing /etc/default/grub, changing the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash *i915.alpha_support=1*"

Then run 'sudo update-grub'
and reboot.

BTW
Should there be a 'sudo apt-get install <something>' or 'sudo apt-get upgrade' in the Install latest video drivers section?

---

### Post by Jacajack on 2018-03-21
I can relate to the very same problem with my i7-8700k.
I updated the graphics drivers from the PPA mentioned above and added the *i915.alpha_support=1 *kernel boot option and now everything works fine.

Thanks!

---

### Post by ruffieux on 2018-03-31
> **jostle said:**
> Thanks for the pointers.
My problem was that the only resolution available was 1024x768.

I didn't add the oibaf repository and have successfully got 4K output by just editing /etc/default/grub, changing the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash *i915.alpha_support=1*"

Then run 'sudo update-grub'
and reboot.

BTW
Should there be a 'sudo apt-get install <something>' or 'sudo apt-get upgrade' in the Install latest video drivers section?


Thank you very much. This solved my problem too!

---

### Post by tony-sleeckx on 2018-04-17
Yes! Using the PPA _and_ the grub switch solved my issues of the monitor not being detected, the display settings not being available, and the sound not working through HDMI. Using 8th Gen i3-8100 on Asus Prime B360-Plus mobo. Using only the grub switch hung the pc during boot.

Thank you very much.

---

### Post by mtro2 on 2018-04-21
Guys, Help please, I've got a new PC for work, but have the same issue like you had: only one resolution 1024x768 and no one setted drivers for VGA compatible controller.
Does your method of resolving work only in Ubuntu 17.10? because I have 14.04 and it didn't help me :(
System:
Ubuntu 14.04
Proc: Intel i3-8100 CPU @3.60x4

---

### Post by wildmanne39 on 2018-04-21
Welcome to the forum mtro2, please start your own thread instead of posting in an old solved thread! You can link to this one if you believe it will be helpful.

Thanks

---

