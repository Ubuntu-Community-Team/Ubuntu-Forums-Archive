---
title: "LightScribe"
date: 2008-05-23
forum: General Help
---

### Post by Exsecrabilus on 2008-05-23
[http://lightscribe.com/downloadSection/linux/index.aspx](http://lightscribe.com/downloadSection/linux/index.aspx)

I don't get it, how do I install LightScribe?
Which packages do I use? There are like four.

---

### Post by igster on 2008-05-23
I don't have a LightScribe drive to test with but it looks like you start with the system software ([http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb)) then get the Simple Labeler ([http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb)).  Then, if you want, you can download their templates to make fancier labels.

Hope this helps.

---

### Post by reiki on 2008-05-24
That's correct. System Software first and then the Simple Labeler.

Simple Labeler is exactly that.... simple. You get text and some limited graphics.

If you want to print full coverage images onto your lightscribe media you'll want to also install 4L, but do that AFTER you get the System Software from lightscribe.com

4L is in the repositories for Hardy. Not sure about Gutsy or lower. 

To the best of my knowledge it doesn't put an icon in your Applications menu. You would start 4L from command line using "4L-gui" (without the quotes) or you may need to run it as "sudo 4L-gui". Once you get it to start and recognize your drive you can work on running it without having to be root and/or creating a launcher for it.

---

### Post by Jerry N on 2008-05-24
> **reiki said:**
> 

To the best of my knowledge it doesn't put an icon in your Applications menu. You would start 4L from command line using "4L-gui" (without the quotes) or you may need to run it as "sudo 4L-gui". Once you get it to start and recognize your drive you can work on running it without having to be root and/or creating a launcher for it.

Actually you can put an icon for 4L-gui on the desktop but it won't do any good!  "sudo 4L-gui" in a terminal is what works for me.  I use OpenOffice (or Powerpoint running under Crossover) to create a template for a CD and then save the template as a .jpg file.  From there, it can be imported into 4L-gui.  Major PIB compared to creating and burning the Lightscribe label in Windows using Nero.  Unfortunately, NeroLinux doesn't do Lightscribe.

Jerry

---

