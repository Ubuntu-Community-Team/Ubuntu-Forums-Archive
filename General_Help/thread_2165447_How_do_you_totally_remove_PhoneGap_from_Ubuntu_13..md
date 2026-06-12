---
title: "How do you totally remove PhoneGap from Ubuntu 13.04?"
date: 2013-08-05
forum: General Help
---

### Post by tyronebissell on 2013-08-05
Hi,

I have a PhoneGap installation that I want to completely remove from Ubuntu 13.04. I have searched for answers but I find very little in the way of removing PhoneGap.
Does anyone know how to remove it?

---

### Post by ian-weisser on 2013-08-05
How, exactly, did you install it?

---

### Post by tyronebissell on 2013-08-06
I installed it by using the following command:
$ sudo npm install -g phonegap

---

### Post by Cheesemill on 2013-08-06
Try this...
```
sudo npm uninstall phonegap
```

---

### Post by ian-weisser on 2013-08-06
This Stackoverflow question seems to address your need to uninstall npm modules:
[http://stackoverflow.com/questions/13066532/how-to-uninstall-npm-modules-in-node-js](http://stackoverflow.com/questions/13066532/how-to-uninstall-npm-modules-in-node-js)

---

### Post by ananthmadhavan6 on 2014-01-02
sudo npm uninstall -g phonegap

This worked for me.

---

### Post by taysonandrey on 2014-01-10
I still need some help.

Phonegap was installed and working to create projects, I wasn´t able just to build project locally.
Then I decided to install Cordova, but didn´t uninstall Phonegap first.
Cordova commands ("cordova ....") didn´t work, so I tried "sudo npm uninstall -g cordova" and "sudo npm -g phonegap".
Cordova was uninstalled successfully, but phonegap displayed an error and still working.

I wanna get rid of everything before isntalling Cordova again.
How can I solve this please?

---

