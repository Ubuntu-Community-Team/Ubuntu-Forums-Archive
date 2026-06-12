---
title: "Firefox won't open"
date: 2005-09-08
forum: General Help
---

### Post by muka on 2005-09-08
Well I have updated FF today, and after it installed, when trying to run it, walla it won't run.

Did notice during install some message about something not installing, but lost it.

Anyone any clues please. 

Much thanks

---

### Post by swamytk on 2005-09-08
You have not mentioned about how you updated?

Uninstalled exiting one? used apt-get (synaptic) to update? or used tar from mozilla site? do you remember the error message? let me have more details? 

What ever be, ensure that you are installing as root.

---

### Post by wellery on 2005-09-08
also try running it from the terminal by going:

Applications->systemTools->terminal

and typing

```
firefox
``` 

and see if there are any errors.

---

### Post by muka on 2005-09-08
Thanks for all that.

I did try to install it via apt-get in terminal window, and the sudo there asks for my user password.

So how do I install via root ?
Can also install via Synatic, and again, how do I run that via root ?

I'll give the apt-get another go and see what message happen.

Otherwise any other advice ?

Cheers

---

### Post by rafakl on 2005-09-08
Same thing happened to me.

It is because when you upgraded, apt-get installed firefox 1.0.6 but you had open the old firefox and then the install failed.

What i did was:

1) reboot ubuntu (there was happening some strange things in Synaptic after the upgrade, like showing different description of packages, and with the reboot it was solved).

2) search in synaptic for mozoilla-firefox package, left click it and click in "mark for reinstallation", then click in "apply". If it doesnt work, then mark it for removal, then click on apply.

3) search again for mozilla-firefox package, left click it but now select "mark for installation", click on apply, and wait for synaptic to install firefox.

After that, you can start using your upgraded firefox!!!

 :-)

---

