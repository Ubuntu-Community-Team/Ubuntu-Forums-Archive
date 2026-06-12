---
title: "Swappiness Value"
date: 2015-11-27
forum: General Help
---

### Post by RobGoss on 2015-11-27
Hello everyone hope you guys had a great Thanksgiving, I have a question about changing the Swappiness value in order to speed my system up

I'm using Ubuntu 14.0.4 LTS . I opened up my terminal and added the following command, cat /proc/sys/vmv/swappiness

Then I tried editing the following file to make the changes gksu gedit /ect/sysctl.conf

The problem is when running this command the file comes up empty..

Thanks for any help with this

---

### Post by sammiev on 2015-11-27
I tried your command and it was blank.

Then in Terminal I used this.

```
cd /etc

gksu gedit sysctl.conf
```

which worked.

---

### Post by QDR06VV9 on 2015-11-27
> **sammiev said:**
> I tried your command and it was blank.

Then in Terminal I used this.

```
cd /etc

gksu gedit sysctl.conf
```

which worked.
+1 works here that way too sammiev
And for further info
[https://sites.google.com/site/easylinuxtipsproject/speed]("http://ubuntuforums.org/newreply.php?do=newreply&p=13397871")
Regards

---

### Post by deadflowr on 2015-11-27
/etc not /ect
fer what it's worth

---

### Post by RobGoss on 2015-11-27
> **deadflowr said:**
> /etc not /ect
fer what it's worth


Yep that worked, I was adding the command the way I found it there must have missed spelled something but **etc** worked. Thank you all for your time and help

---

