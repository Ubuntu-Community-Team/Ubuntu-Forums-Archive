---
title: "Streaming TV Channels not working"
date: 2016-01-27
forum: General Help
---

### Post by Tracey_Burr on 2016-01-27
Hi

I am trying to stream wwenetwork channel site. I am using both Chromium (as we have chromecast to our tv) and Firefox and getting the same result. It told me to go to Abode flash and update.  
So I made sure that the pepperflash was installed.  I have installed vlc, I have installed mplayer

what else do do.

I am running 
xubuntu 15.10
fresh install yesterday.

thanks

---

### Post by ajgreeny on 2016-01-27
You do not need the pepperflashplugin package installed any more; you can use flash version 20.0.0.267 in chromium by installing adobe-flashplugin from the canonical-partner repos.

The same flash version will also work fine in Firefox if you also install the freshplayerplugin from the ppa at [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

I have been to the wwwenetwork website to check it out and the Tour flash video works fine on my system with flash 20.0.0.267, but I am not going to register in order to try the site properly.

---

### Post by Tracey_Burr on 2016-01-27
Thank you so much for this information... I copied and pasted that into a terminal... please tell me what I do now??

many thanks

---

### Post by ajgreeny on 2016-01-27
Copied and pasted what?

You need to go to the weblink I gave you in a browser and follow the instructions there to add that ppa repository.
However, to save you the time doing that, just open a terminal and copy the following and run the command.
```
sudo add-apt-repository ppa:nilarimogard/webupd8
```
Now open software centre (or synaptic if you use it), refresh the repos and install freshplayerplugin.  For this to work you do need to have adobe-flashplugin installed, so ensure you have enabled the partner repos in software-sources aand then install the adobe-flashplugin package.

---

### Post by Tracey_Burr on 2016-01-27
thanks for that.... 
still not working......

will keep persisting

---

### Post by deadflowr on 2016-01-28
You might need to to install hal.
Looking at the wwe antiquated system requirements page,
It uses DRM.
If anything can possibly get the DRM support needed for it, it would be hal.

Though this deals with getting hal to use for hulu, it's a good reference on how to install it
[http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up](http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up)

here's the direct link to the ppa:
[https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)

This would only work with Firefox, as chrome/chromium do not have Adobe Protected Content/DRM playable support on linux.

Of course it's all a crapshoot...
But most likely your best bet.

---

### Post by Tracey_Burr on 2016-01-28
nope.....neither have worked...

---

### Post by ajgreeny on 2016-01-28
Have you tried Google-chrome instead of chromium?

There are some proprietary streaming sites that work with Chrome but not chromium so it could be worth trying.

---

