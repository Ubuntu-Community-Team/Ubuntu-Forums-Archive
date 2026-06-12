---
title: "Firefox not displaying pages"
date: 2012-12-23
forum: General Help
---

### Post by Dusenberg on 2012-12-23
Firefox: 17.0.1+build1-0ubuntu0.11.10.1
Ubuntu 11.10
Kernel: Linux 3.0.0-28-generic-pae (i686)

I've had no problems on my laptop for ages.....
but now I have major problem with Firefox as it suddenly won't display text in any website correctly.   One day it was ok then next it wasn't. I can't think of anything I was doing that could cause it.  I've had to install Chromium so I can continue to use the web. 

Screenshot attached of the typical corruption in firefox and what it looks like in Chromium.

I've used synaptic to completely remove firefox, then I've done sudo apt-get purge, then re-installed firefox, but still the same problem.

Also I now see there's a problem with Thunderbird v17.0 not displying html emails correctly. I've 'viewed source' of the email and all the text is there but similar corrupted display to firefox.

I can't find anything on google.

This is serious!  Anyone any ideas please??

---

### Post by carl4926 on 2012-12-23
Have you cleared all the cache etc..

---

### Post by Dusenberg on 2012-12-23
Thanks carl4926 - yes I've cleared cache, but no difference.

---

### Post by ajgreeny on 2012-12-23
Try starting FF in safe mode with the command ```
firefox --safe-mode
```which disables all your add-ons etc etc, to see if that helps.  If not start with a new profile by shutting down FF, renaming the hidden **~/.mozilla** folder in your home as a backup, then restarting FF.

If that works you will know there is a profile problem of some sort and can start adding back folders from your old profile to the new one, one by one.

---

### Post by Dusenberg on 2012-12-23
Thanks ajgreeny.  Tried both your suggestions but no difference.

I have now completely removed Firefox and installed an old version 7 through synaptic. Same problem!

This seems to be an HTML font rendering problem.  I'm wondering if something's screwed with fonts on my machine.  The fact that chromium will display the same pages correctly means it can find fonts and I've checked in LibreOffice and so can it.   

Anyone know where/how firefox looks for fonts?

---

### Post by ajgreeny on 2012-12-23
Go to the FF preferences Content tab and use the Advanced button in the fonts and colours section.  There you can try playing with settings as shown in my screeny to see if it helps.

---

### Post by IsaacJGL on 2012-12-23
The same thing happens to me on ubuntu 12.04, but after about 2 minutes, it displays the page. It's kind of weird...

---

### Post by carl4926 on 2012-12-23
I'm not seeing this problem and I have a whole rack of machines using Firefox across a wide spectrum of distros.
So far the main link I can see is Gecko

Test a new user login
And a Live CD of 12>

---

### Post by Dusenberg on 2012-12-24
Thanks everyone for your help. Problem solved. It was fonts, and it was my fault.

I had a whole lot of fonts in the ~./gimp-2.6/fonts folder and I'd decided last week they needed to be in the main fonts folders so all the apps could get at them.  As the std ubuntu fonts installer only seems to be for individual fonts, I followed some instructions I google'd and moved them as root into /usr/local/share/fonts.  Then I did a fc-cache -fv. 

I hadn't linked this to my Firefox/Thunderbird problems until yesterday. I found the permissons on all the fonts were set to r--, so as they were root owned firefox running under my uid couldn't read them.  Changed them all to rrr, and everything is back to normal!

Once again thanks.

---

