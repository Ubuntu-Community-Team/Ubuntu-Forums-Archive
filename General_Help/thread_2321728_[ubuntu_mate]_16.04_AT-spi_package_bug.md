---
title: "[ubuntu_mate] 16.04 AT-spi package bug"
date: 2016-04-24
forum: General Help
---

### Post by alexpag on 2016-04-24
After installing ubuntu mate 16.04 I&#900;m facing this bug [https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/577113](https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/577113) , [http://www.linuxquestions.org/questions/linux-newbie-8/at-spi-registryd-desktop-4175490640/](http://www.linuxquestions.org/questions/linux-newbie-8/at-spi-registryd-desktop-4175490640/),  [http://ubuntuforums.org/showthread.php?t=1448923](http://ubuntuforums.org/showthread.php?t=1448923).  I removed orca and at-spi from the startup applications but the problem still exists. Any thoughts?

---

### Post by bapoumba on 2016-04-24
Do you have System > Prefs > Personal > Assistive Technologies disabled (unchecked) ?

---

### Post by alexpag on 2016-04-24
> **bapoumba said:**
> Do you have System > Prefs > Personal > Assistive Technologies disabled (unchecked) ?

Yes I have already done that it&#900;s unchecked.

---

### Post by bapoumba on 2016-04-24
Hmm :)
Edit : do you have a at-spi-registryd.desktop file somewhere ?

---

### Post by alexpag on 2016-04-24
> **bapoumba said:**
> Hmm :)
Edit : do you have a at-spi-registryd.desktop file somewhere ?

Where shall I search for this file?I&#900;m very disappointed because with all the previous versions (15.04, 15.10) I didn&#900;t have any kind of problems.:(

---

### Post by bapoumba on 2016-04-24
Not quite sure, your /home most probably. You can [B]locate at-spi-registryd.desktop
[/B]
Reading this [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/729827](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/729827), there is a demon, do you see anything when you run **top** in a terminal ? You can** killall <demon name>** or **kill9 <pid>** (which is less graceful to the system) and see if it works.
Have a look at post #18 of the bug report and see if the solution works for you. That simply renames the files, you can easily undo if needed.

---

### Post by alexpag on 2016-04-29
> **bapoumba said:**
> Not quite sure, your /home most probably. You can [B]locate at-spi-registryd.desktop
[/B]
Reading this [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/729827](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/729827), there is a demon, do you see anything when you run **top** in a terminal ? You can** killall <demon name>** or **kill9 <pid>** (which is less graceful to the system) and see if it works.
Have a look at post #18 of the bug report and see if the solution works for you. That simply renames the files, you can easily undo if needed.

I think that those two commands worked:

sudo mv /usr/lib/at-spi2-core/at-spi2-registryd /usr/lib/at-spi2-core/at-spi2-registryd.old

 and

 sudo mv /usr/lib/at-spi2-core/at-spi-bus-launcher /usr/lib/at-spi2-core/at-spi-bus-launcher.old

Thank you very much!:D

---

### Post by bapoumba on 2016-04-30
Glad to see you got it to work, and thanks for marking your thread as solved :)

---

### Post by Melodie on 2017-02-13
> **bapoumba said:**
> Glad to see you got it to work, and thanks for marking your thread as solved :)

Hello,

I didn't see any solution to this elsewhere on the web for the Ubuntu editions using systemd (starting Xenial). As Xenial uses fully systemd, wouldn't it be possible to create some service files that could be enabled and disabled? If so how?

You might wonder why do I ask if a simple "mv" can do the trick? Well if you wonder : what becomes of the trick when one day at-spi2-core is updated? Pointless mv, has to be done again… Don't you think?

Best regards,
Mélodie

---

