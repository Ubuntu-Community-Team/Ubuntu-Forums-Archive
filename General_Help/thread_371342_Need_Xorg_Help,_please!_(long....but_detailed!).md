---
title: "Need Xorg Help, please! (long....but detailed!)"
date: 2007-02-26
forum: General Help
---

### Post by Innova on 2007-02-26
I got Ubuntu 6.10 installed over the weekend, but Xorg is not working.  I have an nvidia 6800GS and Princeton Graphics LCD1700.

After the installation, when I first rebooted, the splash screen displayed fine, but when gdm started up, I saw red, green and blue flashing colors.  I then started fooling around with the xorg.conf file, but could never get it working.  I finally found this page:  [https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration), which had a lot of information.

The first thing I tried was to re-run the sudo dpkg-reconfigure xserver-xorg command.

Then I tried to start up Xorg and I got an error, none of the screens were valid:

[http://utopiaprogramming.com/xorg/Xorg.0.log.failed.to.start.no.valid.screens](http://utopiaprogramming.com/xorg/Xorg.0.log.failed.to.start.no.valid.screens)

I noticed the framebuffer error so I reran the reconfigure xserver command, and answered "no" to using the hardware framebuffer.    I also found my documentation for my monitor and added horizontal and vertical sync numbers.  Now, xorg starts, but my monitor says that the signal is out of range.  Here is the log:

[http://utopiaprogramming.com/xorg/Xorg.1.log.out.of.range](http://utopiaprogramming.com/xorg/Xorg.1.log.out.of.range)

Here is the xorg.conf for that configuration:

[http://utopiaprogramming.com/xorg/xorg.conf](http://utopiaprogramming.com/xorg/xorg.conf)


Here are the specs of my monitor:  [http://utopiaprogramming.com/xorg/lcd1700Specs.html](http://utopiaprogramming.com/xorg/lcd1700Specs.html)

Here is the output of lspci -n:  [http://utopiaprogramming.com/xorg/lspci.out](http://utopiaprogramming.com/xorg/lspci.out)

The discover command given on the above help page, didn't work (command not found):  [http://utopiaprogramming.com/xorg/discover.out](http://utopiaprogramming.com/xorg/discover.out)

There are some other logs and xorg.conf files that I tried with no luck here:  [http://utopiaprogramming.com/xorg/](http://utopiaprogramming.com/xorg/)

I have been working on this problem for three days now, and really would like to get on to the next problem!  Any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2007-02-26
I think your problem is best solved by installing the nvidia driver.

The easiest way I know is with the envy script :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From CLI:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

Follow the instrctions on the Envy site ....

Configure your monitor:

GUI = In a terminal enter (with X running):

```
nvidia-settings
```

---

### Post by Innova on 2007-02-27
Thanks!  That did it.  I needed to do a bit of digging to get envy to run, but once the nvidia drivers were installed X started perfectly.

---

