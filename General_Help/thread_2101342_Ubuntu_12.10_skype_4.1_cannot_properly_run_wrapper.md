---
title: "Ubuntu 12.10 skype 4.1 cannot properly run wrapper"
date: 2013-01-04
forum: General Help
---

### Post by Chelidze on 2013-01-04
I installed downloaded skype from official website "Ubuntu 12.04 (multiarch)" and installed it. then I followed this steps Quit Skype if running

```
Uninstall Skype IF you installed it from the repositories.

Reboot

Choose your Skype version (32/64 Bit) to download and install it

Make sure you added the repository ppa:skype-wrapper/ppa

In terminal console, run

sudo add-apt-repository ppa:skype-wrapper/ppa
sudo apt-get update && sudo apt-get install skype-wrapper python-skype After that, run in terminal console

skype-wrapper Acknowledge the pop up authorization requests (don't forget to check the boxes to remember the selection)

Restart and done!

link to the original answer [http://askubuntu.com/a/123304/42591]("http://askubuntu.com/a/123304/42591")
```

 [IMG]http://i.imgur.com/GgIkh.jpg[/IMG]
but sadly non of the functions of skype weaper are functioning 

on the launcher skype start icon shows default menu when I right click on it 
is there a way to fix this thank you in advanced

---

### Post by dannyboy79 on 2013-01-04
for your launcher, you dragged and dropped the /usr/share/application/skype to your side bar correct?

---

### Post by Chelidze on 2013-01-04
> **dannyboy79 said:**
> for your launcher, you dragged and dropped the /usr/share/application/skype to your side bar correct?

thank you for the fast reply
no I have not dragged and dropped from this location 
when I entered the provided location I got two skype icons is there a difference ???

[IMG]http://i.imgur.com/Tuh4c.png[/IMG]
[COLOR="Magenta"]
Update [/COLOR]

I dragged and dropped this version ```
skype-wrapper
```
from this location
```
/usr/share/application/
```
as you specified and now it works like a charm 
thank you

---

### Post by dannyboy79 on 2013-01-04
no problem, glad I could help

---

### Post by Chelidze on 2013-01-04
> **dannyboy79 said:**
> no problem, glad I could help

Again Thank you very much

---

