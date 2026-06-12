---
title: "Automatix2 GoogleEarth failed"
date: 2006-12-23
forum: General Help
---

### Post by rossnixon on 2006-12-23
Hi all, linux newbie here.

Installed Ubuntu CE 2.0 yesterday. (a minor tweak of 6.10)
Got some new stuff using Automatix2, but GoogleEarth failed, with the following message in the log file.

GoogleEarthLinux.bin' saved [2003]
/home/rossnixon/GoogleEarthLinux.bin: 1: Syntax error: redirection unexpected
Finished

I only got a small bin file - 2kb or 20kb or something.
What do I do now?

Thanks, Ross

---

### Post by iamhugeinjapan on 2006-12-23
I don't know why it failed by Google Earth is very easy to install by yourself.

Download it from the Google Earth site: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Then right click the GoogleEarthLinux.bin file and choose Properties. Then the Permissions tab. Check the box by 'Allow executing file as program'  (Google often neglects to do that)

Double click it and the Google Earth install should start.  I can't remember if it creates its own launcher icon afterwards or not but you can then start it by going Alt+F2 and putting in googleearth

Enjoy!

---

### Post by shane2peru on 2006-12-23
Are you sure it isn't a 20MB file?  Click on **Places** on your menu bar, then click on your username  find the file called GoogleEarthLinux.bin and right click on properties.  Find its size.  If it isn't 20MB, you didn't get the whole file.  You can download it[ here]("http://earth.google.com/download-earth.html")  Once you download it it is rather easy to install by hand.  In a terminal **Applications - Accessories - Terminal** you are going to want to type or paste: ```
./GoogleEarthLinux.bin
```  and it should install.  Use all the default settings.  You also may be able to double click this file and select terminal, and that may work too.  I primarily use the terminal.

Shane

---

### Post by rossnixon on 2006-12-23
Thanks for the advice.
The bin file was only 2kb each of the three times I tried, so now I'm getting it manually.
I'm guessing that there is an error in the Automatix2 script.

---

### Post by shane2peru on 2006-12-23
Just as a word of caution.  I would be careful of Automatix2.  It is nice and does set things up quickly sometimes, but I have read many posts of problems.  You can install many programs from **System - Administration - Synaptic Package Manager**  That is the way that Ubuntu was meant to be run.   Also a good guide to help you configure it is [here.]("http://easylinux.info/wiki/Ubuntu_Edgy")  Enjoy!

Shane

Ps, Google is not included in Synaptic though.

---

