---
title: "Plymouth unable to update spash screen"
date: 2016-04-29
forum: General Help
---

### Post by bholu_taksh on 2016-04-29
Hi,
I recently discovered plymouth and was figuring out how to work with it. Initially the GUI didn't start. Some searching helped and I got it running. Now I had tried installing themes (not much left in synaptic) and tried some themes. I then uninstalled one of them and restarted system to check. Now when I'm trying to install and set other theme, the update-initramfs isn't working.

The output for ```
sudo update-alternatives --config default.plymouth
``` is as below -

```

There are 6 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   150       auto mode
  1            /lib/plymouth/themes/orange                                               100       manual mode
  2            /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth                 100       manual mode
  3            /usr/share/plymouth/themes/spinner/spinner.plymouth                       70        manual mode
  4            /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo-scale-2.plymouth       99        manual mode
  5            /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       manual mode
* 6            /usr/share/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   150       manual mode

Press <enter> to keep the current choice
[*], or type selection number: 

```

If I select any of them, and then update using 
```
sudo update-initramfs -u
```

I get following output -

```

update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
W: plymouth module (/usr/lib/x86_64-linux-gnu/plymouth//.so) missing, skipping that theme.

```

I tried searching over internet but couldn't find any solution to this. Currently my boot screen isn't showing anything during boot-up other than default colour background (purple). While shutting down, it displays Ubuntu Studio in text form (I had tried setup Ubuntu Studio screen and it did worked). Please help me out to set a theme for my system. I'm using Ubuntu 16.04 with plymouth version 0.9.2.

---

### Post by mickee384 on 2016-05-04
I get exactly the same response!

---

### Post by draekko on 2016-05-14
I fixed it on my end by editing /usr/lib/x86_64-linux-gnu/plymouth/plymouth-populate-initrd

i changed a line near the end from

inst ${PLYMOUTH_PLUGIN_PATH}/renderers/frame-buffer.so $INITRDDIR

to

inst ${PLYMOUTH_PLUGIN_PATH}/renderers/frame-buffer.so $INITRDDIR
inst ${PLYMOUTH_PLUGIN_PATH}/script.so $INITRDDIR

then running 

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all

fixed it.

Note my original custom theme was in /lib/plymouth/themes i made a new one in /usr/share/plymouth/themes where all the other themes were. Don't think that was the problem but just in case fyi :)

Also note you will still get the nagging warning but it installs the seemingly missing script.so per the changes above.

---

### Post by mickee384 on 2016-06-02
I will give that a try! Merci!

---

### Post by mickee384 on 2016-06-12
I do not have x86_64-linux-gnu/plymouth/plymouth-populate-initrd - I assume as I have a e32 bit machine. Is there a similar file for that? I cannot find one.

---

### Post by mattlach on 2016-06-18
> **draekko said:**
> I fixed it on my end by editing /usr/lib/x86_64-linux-gnu/plymouth/plymouth-populate-initrd

i changed a line near the end from

inst ${PLYMOUTH_PLUGIN_PATH}/renderers/frame-buffer.so $INITRDDIR

to

inst ${PLYMOUTH_PLUGIN_PATH}/renderers/frame-buffer.so $INITRDDIR
inst ${PLYMOUTH_PLUGIN_PATH}/script.so $INITRDDIR

then running 

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all

fixed it.

Note my original custom theme was in /lib/plymouth/themes i made a new one in /usr/share/plymouth/themes where all the other themes were. Don't think that was the problem but just in case fyi :)

Also note you will still get the nagging warning but it installs the seemingly missing script.so per the changes above.

Hmm.

I made the changes you recommend above, but I still only get the default Ubuntu 16.04 text logo, no matter what I do.

What is interesting is that the default Ubuntu Text logo is located in /usr/share/plymouth/themes, but when I run "update-alternatives --config default.plymouth" it only lists themes located in /lib/plymouth/themes to choose from.

I copied my custom theme from /lib/plymouth/themes to /usr/share/plymouth/themes, and strangely enough that made the library error message go away, but upon reboot after running initramfs it still only shows the default Ubuntu Text logo...

---

### Post by mattlach on 2016-06-18
> **mattlach said:**
> Hmm.

I made the changes you recommend above, but I still only get the default Ubuntu 16.04 text logo, no matter what I do.

What is interesting is that the default Ubuntu Text logo is located in /usr/share/plymouth/themes, but when I run "update-alternatives --config default.plymouth" it only lists themes located in /lib/plymouth/themes to choose from.

I copied my custom theme from /lib/plymouth/themes to /usr/share/plymouth/themes, and strangely enough that made the library error message go away, but upon reboot after running initramfs it still only shows the default Ubuntu Text logo...

Wow.

This time I even decided to - as a hack - replace the text.plymouth of the default Ubuntu text logo (this is on Ubuntu Server btw) with a copy of my custom plymouth file and even then when I run run update-initramfs and reboot, I STILL get the default ubuntu text splash on boot.

Something is rather messed up here.,

---

### Post by mattlach on 2016-06-18
> **mattlach said:**
> Wow.

This time I even decided to - as a hack - replace the text.plymouth of the default Ubuntu text logo (this is on Ubuntu Server btw) with a copy of my custom plymouth file and even then when I run run update-initramfs and reboot, I STILL get the default ubuntu text splash on boot.

Something is rather messed up here.,

Well,  I took a look in /etc/alternatives:

```
# ls -l |grep .plymouth
lrwxrwxrwx 1 root root  49 Jun 18 14:10 default.plymouth -> /lib/plymouth/themes/kodi-logo/kodi-logo.plymouth
lrwxrwxrwx 1 root root  59 Jun 18 14:36 text.plymouth -> /usr/share/plymouth/themes/ubuntu-text/ubuntu-text.plymouth
```

My kodi-logo plymouth theme is correctly referenced there as default.plymouth.

It seems like the system completely refuses to use it though, and instead just uses the ubuntu-text.plymouth reference, which results in the default Ubuntu text splash.

As an experiment, I tried replacing /usr/share/plymouth/themes/ubuntu-text/ubuntu-text.plymouth with a symlink to my kodi-logo.plymouth file, but that didnt work at all.   It just reverted to no plymouth splash at all.

I guess it is safe to say that plymouth-label and it's implementation in alternatives is completely broken in Ubuntu 16.04

I'm going to revert all my hacks for now and check if there is a bug filed against the plymouth-label package.

---

### Post by bholu_taksh on 2016-07-25
Finally fixed it! Thanks a lot draekko!!

---

### Post by mickee384 on 2016-07-31
as of today the startup Plymouth is still butchered. Strange though, when rebooting/shutting down, Plymouth shows fine there?

---

### Post by mickee384 on 2016-09-11
This is not solved.

---

### Post by demented_demigod on 2016-10-14
I found that the plymouth theme I was trying to use was hardcoded to use the old path ```
/lib/plymouth/themes/
``` instead of ```
/usr/share/plymouth/themes
``` I'm using 16.10, but the same should be the case in 16.04.

I edited this out and the theme started working. It didn't make the warning message go away ```
plymouth module (/usr/lib/x86_64-linux-gnu/plymouth//.so) missing, skipping that theme.
```

You can find all the files with this hardcoded path in your plymouth theme by running the command ```
grep -Ri -e "/lib/plymouth" /usr/share/plymouth/themes/<path-to-your-plymouth-theme>
```

edit the files with your favourite editor or something fancier like sed

Once you have done this the theme can be installed using the following:
```
 sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/<path-to-your-plymouth-theme>/<your-plymouth-file>.plymouth 100
sudo update-alternatives --config default.plymouth
### you'll be asked to choose your default theme by number here ###
sudo update-alternatives --config default.plymouth
```

now you can reboot and enjoy the glory of your new plymouth theme

---

### Post by Woulouf on 2017-02-13
Hi everybody

i got the same issue with plymouth custom theme.

I tried draekko's tip but it didn't work for me

Then i read this : [http://www.routereflector.com/2016/11/plymouth-module-missing-on-ubuntu/](http://www.routereflector.com/2016/11/plymouth-module-missing-on-ubuntu/)

and it says

> Theme folder and theme filename must be the same,[...]

My folder filename was typed with uppercase letters but not the theme filename. I put lowercase letters everywhere and it was done. No error after a sudo update-initramfs -u

Hope it'll help !

---

### Post by tuxedojoe on 2017-08-20
Thank you Woulouf! That did it for me! Now Tux can finally create havoc without any warnings. Try him out as your boot logo here: [https://tux4ubuntu.blogspot.com](https://tux4ubuntu.blogspot.com)

---

