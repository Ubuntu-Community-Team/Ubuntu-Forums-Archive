---
title: "Problem with upstart?"
date: 2015-08-31
forum: General Help
---

### Post by rudeboy2 on 2015-08-31
Hi, I'm quite new to Ubuntu and Linux as a whole. My skill level is between beginner and intermediate.

I keep getting an error message on start up asking me to report an error with upstart.

Anybody know what this could be? I'll post a screenshot of the error message, if there is any other information you might need then let me know. I'm using the latest version of ubuntu on a Dell Latitude laptop. Processor is an intel quad core i5.

[IMG]http://imgur.com/Ean9SkX.jpg[/IMG]

---

### Post by QDR06VV9 on 2015-08-31
Hi rudeboy2 Welcome to the forums.:D
When you say latest release that tells me nothing.
Latest Releases are 14.04.3 && 15.04 && 15.10(Development)
Post back the output of in terminal
Just to be clear Open a terminal and paste the code below into the terminal
```
lsb_release -a
```
Highlight the results with your mouse cursor and then right click mouse and select copy or keyboard option control+shift+c
Paste that back here in you thread.
Then we can make a better choice in what to offer for help.
Kind Regards

---

### Post by grahammechanical on 2015-08-31
You say that you are using the latest version of Ubuntu. But that could be Ubuntu 15.04 or Ubuntu 14.04.3. Which is it?

Upstart is Canonical written software that is used as an init system. Ubuntu is built on Debian and Debian used Upstart until recently when it switched to a Redhat init system called SystemD. So, Ubuntu made the change to SystemD with the release of Ubuntu 15.04. If you are using 15.04 then your system should be loading with SystemD by default. And there should be a Upstart option in the Grub Advanced options for Ubuntu sub-menu.

I am not sure if SystemD was back ported to Ubuntu 14.04.3. The screenshot that you posted does not show the part of the error message that explains what the problem actually is. Your choices are:

1) to click Continue and report the problem
2) to uncheck the error box and click continue and carry on using Ubuntu.

Does this error message appear every time you restart? Does it appear again and again while you are using Ubuntu. If it appears once but does not stop you using Ubuntu normally, then, if it was me, I would not let it trouble me. I am using the development version of Ubuntu 15.10. We sometimes get error messages like that regarding one thing or another. They have never prevented me from using Ubuntu. When I report the error I am sometimes informed that the bug has already been reported.

If you decide to report the error then certain system logs will be collected and become part of the bug report. You will be asked to confirm the passing over of those logs as they may contain sensitive information. If you continue you will be taken to a bug report that may reveal more information about the problem. That is if you are not the first person to report this error.

Regards.

---

