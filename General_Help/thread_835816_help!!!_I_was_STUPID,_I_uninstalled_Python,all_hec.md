---
title: "help!!! I was STUPID, I uninstalled Python,all heck broke loose"
date: 2008-06-20
forum: General Help
---

### Post by rbpember on 2008-06-20
I was having problems with python (another story) and thought I would reinstall it using the synaptic package manager. That didn't work, so I tried uninstalling it in order to reinstall it.

********* NEVER EVER DO THIS!!!!!!! **********************
I have learned the hard way that Python is an integral part
of Linux, or at least Ubuntu.

Once I did the "apply" I could see I was in trouble and saved
the output about all the packages being removed. Of course I had
lost the synaptic package manager, and just about all the other
Ubuntu bells and whistles, so I needed to to use apt-get. (I 'm using my officemate's Windows laptop to send this message.) I started with the ubuntu dekstop package (sudo apt-get install ...) which was the first package removed, but this did not complete because so many other packages were missing.

Is there any hope of reinstalling the packages in the proper
order, or am I just doomed to do a reinstall?

The small bit of good news is that my file system is intact, I'm still on the network, and I can run "startx" to start X -- no window manager, however. 

In closing--HELP!!!

---

### Post by Happy_Man on 2008-06-20
*chuckles* Well, everyone has their newb moments, right? Mine was trying to manually compile KDE. Worst hellhole I ever threw myself into (at the time). 

To fix this (at least somewhat): You have the saved output of Synaptic, right? Well, if you know what parts of Python you removed, you can just add them back. Most of the GUI portion of any Linux system is built off of Python nowadays, but then, Linux has plenty of ways to get around without a single window of any kind whatsoever. 

```
sudo apt-get install lynx
``` That installs a text-based web browser. It's not pretty, but it works, renders HTML enough to read it, and gets the job done. That way you can let your officemate work. :p

If for some reason reinstalling everything one by one doesn't work, then the easiest option is to reinstall. See the link in my sig about a separate /home partition so you can set one up when/if you have to reinstall so that the next time you don't have to sacrifice your data.

In closing: be happy you're not as bad off as the poor guy who uninstalled all his kernels and then wondered why his computer wasn't booting up. ;)

---

### Post by shae on 2008-06-20
After booting into command line, try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by VMC on 2008-06-20
This was kind of a funny topic on so many levels :)
We've all been there in some form or other. Ironically, I was wondering eralier today which language was more useful Python or Ruby. Now I know! I was looking for a good GUI interface. So I tried installing Tk. I didn't work well with Perl, so I uninstalled it. 

I would think that there should be some warning if Python is so useful. I didn't know Python is what drove Synaptic. Would Aptitude work in this scenario. Someone has suggested to use that. I have played around with it but it's confusing. I tried installing Tk using Aptitude but couldn't get it to go.

---

### Post by rbpember on 2008-06-21
One monkey randomly typing for hours can eventually fix an OS,
or, at least, Ubuntu.:rolleyes:

I finally got things fixed. 

It took repeated applications of

apt-get update
dpkg --configure -a

and 

sudo apt-get install ubuntu-desktop
sudo apt-get install xxxxxx

For the most part, these would all eventually fail with
errors related to dependent packages not being configured,
although at some point I was able to run twm after startx. 
Finally, I just  did

su -

and did

apt-get update
dpkg --configure -a

one more time, and gnome was back, the ubuntu dekstop was back,
and, most importantly (for me) the snaptic package manager was back.
I needed to restore a few more non-essential things via spm,
but I was back in business.

I'm not sure why the previous apt-get's/dpkg's failed, nor
why the last ones finally worked. I'm sure as heck not going to
experiment and find out why, though.

---

### Post by rbpember on 2008-06-21
Pardon my manners:

Thanks for all the suggestions. And thank you for not laughing
me off the face of the earth. It was extremely stupid of me
to delete Python... :oops:

---

