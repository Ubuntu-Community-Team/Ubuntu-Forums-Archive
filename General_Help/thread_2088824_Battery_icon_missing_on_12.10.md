---
title: "Battery icon missing on 12.10"
date: 2012-11-27
forum: General Help
---

### Post by Shaun_Yute on 2012-11-27
Hello all, I seem to be having this issue as well along with the time/date display. I am currently on battery power but there is no battery icon. Any assistance is greatly appreciated. I am using Ubuntu 12.10.

---

### Post by howefield on 2012-11-27
Post moved to its own thread and title changed to reflect question.

---

### Post by Shaun_Yute on 2012-11-27
Attached is a screen shot of what I am seeing. It is missing the battery power and time/date. When I go into System Settings I don't have the option for time/date anymore and when I click on power it closes System Settings.

---

### Post by howefield on 2012-11-27
Do you have the package indicator-datetime installed ?

---

### Post by Shaun_Yute on 2012-11-27
Do they often uninstall themselves? As of yesterday I had the battery and date/time icons. Now I have neither of them. Which command should I use to verify? Sorry kind of a beginner.

---

### Post by LuisGMarine on 2012-11-27
> **Shaun_Yute said:**
> Do they often uninstall themselves? As of yesterday I had the battery and date/time icons. Now I have neither of them. Which command should I use to verify? Sorry kind of a beginner.

Open up a terminal window, ( CTRL + ALT + T )

Type in the following code, and then post back the answer.  
```
apt-cache policy indicator-datetime
```

... if all is well it should look something like this :

```
indicator-datetime:
  Installed: 12.10.2-0ubuntu3
  Candidate: 12.10.2-0ubuntu3
  Version table:
 *** 12.10.2-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Shaun_Yute on 2012-11-27
Looks like it is no longer installed.

indicator-datetime:
  Installed: (none)
  Candidate: 0.3.94-0ubuntu4
  Version table:
     12.10.2-0ubuntu3 0
        100 /var/lib/dpkg/status
     0.3.94-0ubuntu4 0
        500 [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

I have a feeling this has something to do with my updates. Every time I start System Updater it tells me I need to perform a partial upgrade to install the updates. I perform it and it says it completes but I get the same pop up stating I need to perform a partial upgrade.

---

### Post by LuisGMarine on 2012-11-27
Here is something that I came accross, try these commands and let me know if they fix your problem.

First run this command:

```
sudo apt-get install indicator-power
```

if the package is already installed, then try to re-install it by running these commands.

```
sudo apt-get purge indicator-power
```

```
sudo apt-get install indicator-power
```

---

### Post by LuisGMarine on 2012-11-27
> **Shaun_Yute said:**
> Looks like it is no longer installed.

indicator-datetime:
  Installed: (none)
  Candidate: 0.3.94-0ubuntu4
  Version table:
     12.10.2-0ubuntu3 0
        100 /var/lib/dpkg/status
     0.3.94-0ubuntu4 0
        500 [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

I have a feeling this has something to do with my updates. Every time I start System Updater it tells me I need to perform a partial upgrade to install the updates. I perform it and it says it completes but I get the same pop up stating I need to perform a partial upgrade.

ok that's fine!  just go ahead and type this into the terminal then to install it:

```
sudo apt-get install indicator-datetime
```

Do this first and then if it doesn't work, try what I posted in my previous reply. :lolflag:

---

### Post by Shaun_Yute on 2012-11-27
Awesome, that worked. I installed both indicator-power and datetime. Now I just have to figure out what is going on with my updates to see why it is asking me to perform a partial upgrade each time.

---

### Post by LuisGMarine on 2012-11-27
So you got the icon battery back?  If so can you please mark the thread as solved.  The partial upgrade might have to go own its own thread.

---

