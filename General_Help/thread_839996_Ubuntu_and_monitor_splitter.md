---
title: "Ubuntu and monitor splitter"
date: 2008-06-24
forum: General Help
---

### Post by gdp77 on 2008-06-24
Hi.

I recently innstalled Ubuntu 8.04 at a friend's system. He has a 19" LG TFT monitor and a Nvidia 7900GTX video card, so I also installed the latest nvidia drivers (using envy). Everything worked great.

The problem is that my friend owns 2 systems (2 towers), so he uses a monitor switch (noname brand) in order to be able to work with his 2 systems, using 1 monitor. So, whenever we connect the monitor directly to the ubuntu box, the monitor is being recognized and works like a charm (1280x1024 @ 60Hz). Whenever we connect the monitor through the switch, the monitor is being recognized as CRT  640x480 and there is no way (through nvidia-settings) &#964;&#959; change resolution. 

Can I manualy edit xorg.conf in order to force 1280x1024 @ 60Hz, even though we use the monitor switch? What kind of setting do I need to make?

---

### Post by ryanhaigh on 2008-06-26
Im still using gutsy and I know that things have changed considerably with regard to X in hardy but you may find this tutorial on using xrandr useful. It allows you change your display configuration dynamically from the commandline. It works with my nvidia 8600 card.

[http://www.phoronix.com/scan.php?page=article&item=927&num=1](http://www.phoronix.com/scan.php?page=article&item=927&num=1)

I remember in previous releases if there where multiple modes eg 1280x1024 800x600 then removing all the modes other than what you used would force the right resolutions. Not sure if this would work with Hardy and new X though.

---

### Post by gdp77 on 2008-06-26
I will give it a try when I visit my friend's house. 

Since I only need 1280x1024 @ 60Hz isn't there only a line I could add to xorg.conf and be done with it? That way I could tell my friend what to do over the phone. 

Thanks in advance

---

### Post by ryanhaigh on 2008-06-26
You could get your friend to email you a copy of their xorg.conf file and have a look, there are many sites that can give you info on what you would need but as I said I'm not really sure this would work as new X tries hard to configure itself.

If you plug the monitor into the computer directly, using sudo nvidia-settings and write the configuration to xorg.conf then edit that file to remove any unwanted modes you might be able to force the resolution you want.

---

### Post by gdp77 on 2008-06-27
I have tried that. It appears that there is no change in the xorg.conf when i connect directly the monitor. Somehow the system each time triew to recognize the monitor and configures itself. That's why I need to find a way to force the 1280x1024 res.

---

### Post by ryanhaigh on 2008-06-27
The new X in hardy will autoconfigure the resolution based on EEID info from the monitor but there won't be any change in xorg.conf unless you explicitly tell nvidia-settings to write the config. After that you MAY be able to remove the other options forcing the correct res.

---

