---
title: "Applications become unusable icons on the panel"
date: 2019-10-09
forum: General Help
---

### Post by bjngchn on 2019-10-09
I click on Chrome icon or audacity icon, or something similar.
 Program runs but it is outside my control. It goes to  the panel possibly after jumping a few times, 
and clicking on doesn't help. Closing it  directly may not be possible either. 
Only thing I can do is to use command line to kill  these processes..

What can be the reason?
Any quick fixes?
Anything I can try, which may help, without doing harm?

---

### Post by uRock on 2019-10-09
Please tell us what version ubuntu and which DE you're using.

---

### Post by bjngchn on 2019-10-09
Kubuntu 14.04  Not sure what you mean by which DE but I think it is KDE.  Now system settings doesn;t work either.  Shortly before this I disabled kwallet in system settings, and this might have disabled chromium.  And now I can;t go back to run system settings, because system setting is getting PANELized. as well.

---

### Post by bjngchn on 2019-10-09
Now system settings works. Chromium still doesn't work. System settings started to work after disabling baloo.  Maybe just a coincidence.

---

### Post by deadflowr on 2019-10-09
Kubuntu 14.04 is out of support.
Please install a supported release.
Might solve all issues...

(Currently 16.04, 18.04, and 19.04 are supported, with 19.10 on it's way soon)

---

### Post by cruzer001 on 2019-10-09
> **deadflowr said:**
> Kubuntu 14.04 is out of support.
Please install a supported release.
Might solve all issues...

(Currently 16.04, 18.04, and 19.04 are supported, with 19.10 on it's way soon)
From where do you get this information?  Kubuntu 16.04 is no longer supported.

[https://kubuntu.org/news/trusty-14-04-lts-end-of-life-and-end-of-kubuntu-support-for-xenial-16-04-lts/](https://kubuntu.org/news/trusty-14-04-lts-end-of-life-and-end-of-kubuntu-support-for-xenial-16-04-lts/)

---

### Post by uRock on 2019-10-09
> **bjngchn said:**
> Kubuntu 14.04  Not sure what you mean by which DE but I think it is KDE.  Now system settings doesn;t work either.  Shortly before this I disabled kwallet in system settings, and this might have disabled chromium.  And now I can;t go back to run system settings, because system setting is getting PANELized. as well.

> **bjngchn said:**
> Now system settings works. Chromium still doesn't work. System settings started to work after disabling baloo.  Maybe just a coincidence.

Are you able to re-enable kwallet? If you have your system set to log you in automatically, then it is possible kwallet is being called by the apps that aren't opening properly. You can also try to launch one of the apps that is not currently working by using the terminal to launch. Launching via terminal will show you any errors the application is putting out.

---

### Post by uRock on 2019-10-09
Though 14.04 is EOL, 16.04 will still get updates for core softwares, such as the kernel and other packages used by the primary Ubuntu install. The best bet would be to back up data and complete a fresh install of 18.04.

---

### Post by deadflowr on 2019-10-10
> **cruzer001 said:**
> From where do you get this information?  Kubuntu 16.04 is no longer supported.

[https://kubuntu.org/news/trusty-14-04-lts-end-of-life-and-end-of-kubuntu-support-for-xenial-16-04-lts/](https://kubuntu.org/news/trusty-14-04-lts-end-of-life-and-end-of-kubuntu-support-for-xenial-16-04-lts/)

duh, yep.
My bad.
I was thinking they were still doing 5 years for some reason with 16.04.
Though I still say it's better than having 14.04.

---

### Post by bjngchn on 2019-10-10
Bringing kwallet to its default didn't help........  Sometimes I see "profile error " on the  Chromium task icon, when I try to run Chromium.  This is a user related thing.  Easiest solution might be creating a new user. ................... Yes, I would buy a good laptop and install  18 , but there are no good laptops anymore. I bought a bad laptop and installed 18, and don't want to use it.  All new laptops  have unremovable embedded battery, or they have poor specs, like 250 GB memory., core3 processor.  I would buy 10 more of my  current laptop if I can find it.  Hopefully  people will force computer industry into  making good laptops with removable batteries.  I contact ASUS and ask them if they have any of these old laptops with 1TB memory, and removable battery. They just ignore. I wonder why they have a web site then., if it is nonfunctional.

---

### Post by bjngchn on 2019-10-10
RESOLVED.
Let me say how it was fixed.  While searching internet I found this:
[https://ubuntuforums.org/showthread.php?t=2247343](https://ubuntuforums.org/showthread.php?t=2247343)

and applied a command there:
sudo apt-get install --reinstall nautilus-share


(is this command safe?)
And still most applications went to the panel instead of running on the desktop correctly, 
but since desktop 
effects were not disabled yet I was able to see that before going to the panel, these programs  
"appeared " on the left part of the screen, which I suspected was representing computer's own monitor, while
I was only able to see things on the external monitor.
Then I was able to run system settings after a few attempts correctly,  disabled computer's
own monitor, and only allowed the external monitor, so everything appears on this external monitor. 

kmix was fixed also.

An ancient problem about this user: Audacity didn't play sounds, and it was fixed as a side effect.

---

### Post by uRock on 2019-10-10
I'm glad you were able to get that figured out. We didn't know about the primary monitor not being operable.

---

### Post by deadflowr on 2019-10-10
If your problems seem fixed, [please mark this thread a solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

