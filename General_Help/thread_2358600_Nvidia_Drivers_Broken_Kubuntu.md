---
title: "Nvidia Drivers Broken Kubuntu"
date: 2017-04-15
forum: General Help
---

### Post by Zerochilli on 2017-04-15
Hi,

I have installed Kubuntu 16.04 last night, Encrypted my hard drive, All went well. I then proceded to boot into it and it worked fine.

However I have a Nvidia GTX 1070 GPU, With Dual monitors, Kubuntu only recognized my primary monitor which is HDMI not my secondary one which is VGA.

So I installed:

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-367

and when I boot up the resolution is so big I can't enter my encryption phrase therefore I cannot boot into my OS anymore.

And I don't know what to do regarding dual monitor :(

Anyhelp would be appreciated Thanks. :P

---

### Post by Autodave on 2017-04-15
Not sure why you are using that driver: the newest version is 378.13 I believe. And, I just use the drivers available through *synaptic package manager.*

You will need to remove the current driver and install the newest.

---

### Post by Zerochilli on 2017-04-15
Thanks for your answer but how do I uninstall the nvidia drivers if I can't get past the encryption part. I cannot even boot into desktop ;(

---

### Post by Autodave on 2017-04-15
Sorry, can't help you there other than to suggest reinstalling. Maybe someone else has a better answer for you.

---

### Post by RobGoss on 2017-04-15
Hello and welcome, Try to boot in to **recovery mode **this might help you accomplish this task [https://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode](https://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode)

If you are successful you can then try removing the **nvidia-drivers ** please see this post for details [https://askubuntu.com/questions/865454/how-can-i-uninstall-specific-nvidia-drivers](https://askubuntu.com/questions/865454/how-can-i-uninstall-specific-nvidia-drivers)

---

### Post by i2000s2 on 2017-04-16
Once in the recovery mode (select Network), you should be able to run command lines. If not working, in the recovery mode option select run command as root (IIRC), and purge the NVidia driver:

```

apt-get purge nvidia*
rm /etc/X11/xorg.conf

```
Then reinstall the default one by 
```

ubuntu-drivers autoinstall
```
Pay attention to see if the driver installation has any error to build into the kernel module. 

Now restart into the normal mode to see if it works.
If not, I am not sure if your lightdm or gdm settings were broken. But it doesn't hurt to reconfigure it. In the TTY run:
```

sudo apt-get --reinstall install gdm
sudo dpkg-reconfigure lightdm
sudo service lightdm start

```

---

### Post by Zerochilli on 2017-04-16
Thanks for your replies.

 I have booted into recovery mode and tried to purge nvidia drivers from root shell and it says read only as the process is locked. So I am still unable to proceed.

---

### Post by RobGoss on 2017-04-16
Question? is there and particular reason why you would want your system **Encrypted**? just wondering

---

### Post by Zerochilli on 2017-04-16
Not particularly. Are you saying I should perhaps try it with out encrypting my drives?

---

### Post by RobGoss on 2017-04-16
If you don't need **encrypting** it may be best to do with out it because it will complicate thing down the road. I would stick is the normal installation and see how that works after all, this is a new installation so you don't have much to loose

---

### Post by Zerochilli on 2017-04-16
I have just installed Fresh ubuntu 16.04 no encryption, Below is a pic of my Driver manager should I use the nvidia driver to enable my 2nd VGA monitor to work or wuold it break it.

Cause my 2nd VGA monitor isn't being detected and is just a black screen atm


[http://i68.tinypic.com/2d8cgh.jpg](http://i68.tinypic.com/2d8cgh.jpg)

Help is appreciated.

Thanks :)

---

### Post by RobGoss on 2017-04-16
For future reference when posting images you can use the **paper clip** option using the **advance **tab to display your images

I would say yes use the first option and see if the proprietary work better

---

### Post by Zerochilli on 2017-04-16
Ok I have installed the Nvidia Driver and good news I am able to login.

Bad news is that my 2nd screen still is not being detected. Do you have any idea why it still wouldn't be there :(.

I am so close Thanks.

---

### Post by RobGoss on 2017-04-16
It might be a good idea to open a new thread for your dual monitor issue, it will get the attention needed to get things working. If this issue with the driver has been solved use the **thread tool** at the top of this post

---

### Post by i2000s2 on 2017-04-16
@zerochilli, I like your good news! Let's diagnose it a little bit. The goal is to make your second monitor work, right? Try running 
```


lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display
```This will tell us if the drivers are installed correctly and which driver you are using.I can have a try to use NVidia driver. If you use NVidia, run the following in your terminal```
dpkg -l nvidia-primecat /var/log/Xorg.0.log
```Post your result here. It will be helpful for us to find your problem.

---

