---
title: "CPU Frequency Scaling Control in Kubuntu?"
date: 2012-11-04
forum: General Help
---

### Post by jlacroix on 2012-11-04
I have laptop that was previously using Arch, but now uses Kubuntu. In Arch, I had to install cpufrequtils to get CPU frequency scaling to work. However, in Kubuntu CPU frequency scaling works out of the box, and I'm not sure how considering it doesn't appear that cpufrequtils is even installed. So, what is it using to make this work, and how to I configure it?

My main question is how can I configure Kubuntu to use the conservative governor if I so chose to do so?

I Googled this and I found mention of the cpufreq-set command, but when I try to run that I just get a message that cpufrequtils is not installed. So somehow the developers made frequency scaling work without that being installed.

---

### Post by Linuxisfast on 2012-11-05
Its done at kernel level now, just install the cpufreq plasma to control it.

---

### Post by jlacroix on 2012-11-05
> **Linuxisfast said:**
> Its done at kernel level now, just install the cpufreq plasma to control it.
Thank you. I decided that I want to make the default conservative. I found the following link that describes how to do it:
[http://askubuntu.com/questions/149271/how-to-change-default-scaling-governor-back-to-ondemand](http://askubuntu.com/questions/149271/how-to-change-default-scaling-governor-back-to-ondemand)

But the file it says to edit:
/etc/default/cpufrequtils
Does not exist, even after installing cpufrequtils.

How do I change the default governor in Kubuntu? There has to be some sort of file I can edit...

---

### Post by Doug S on 2012-11-05
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2072951") post #5 by pq...q.

---

### Post by Linuxisfast on 2012-11-05
> **jlacroix said:**
> Thank you. I decided that I want to make the default conservative. I found the following link that describes how to do it:
[http://askubuntu.com/questions/149271/how-to-change-default-scaling-governor-back-to-ondemand](http://askubuntu.com/questions/149271/how-to-change-default-scaling-governor-back-to-ondemand)

But the file it says to edit:
/etc/default/cpufrequtils
Does not exist, even after installing cpufrequtils.

How do I change the default governor in Kubuntu? There has to be some sort of file I can edit...
Install Jupiter from its ppa and its the easiest and most effective way to do it.

---

### Post by jlacroix on 2012-11-05
> **Linuxisfast said:**
> Install Jupiter from its ppa and its the easiest and most effective way to do it.
That appears to be a GTK application if I'm not mistaken.

---

### Post by jlacroix on 2012-11-06
Apparently, there are no decent Qt/KDE tools for this purpose. I ended up just writing a simple BASH script that does it, so I marked this as solved.

```
#!/bin/bash
# init

##### SHOW INITIAL MENU #####
while :
do
clear
echo "***************************************"
echo "* Choose CPU Scaling Governor:        *"
echo "***************************************"
echo "* [1] On Demand                       *"
echo "* [2] Conservative                    *"
echo "* [3] Powersave                       *"
echo "* [4] Performance                     *"
echo "* [Q] Exit                            *"
echo "***************************************"
echo -n "Enter your menu choice: "
read choice
case $choice in
##### END SHOW INITIAL MENU #####


##### (1) ACTIVATE "ON DEMAND" GOVERNOR #####
1) sudo cpufreq-set -r -g ondemand ;;
##### END ACTIVATE "ON DEMAND" GOVERNOR #####


##### (2) ACTIVATE "CONSERVATIVE" GOVERNOR #####
2) sudo cpufreq-set -r -g conservative ;;
##### END ACTIVATE "CONSERVATIVE" GOVERNOR #####


##### (3) ACTIVATE "POWERSAVE" GOVERNOR #####
3) sudo cpufreq-set -r -g powersave ;; 
##### END ACTIVATE "POWERSAVE" GOVERNOR #####


##### (4) ACTIVATE "PERFORMANCE" GOVERNOR #####
4) sudo cpufreq-set -r -g performance ;;
##### END ACTIVATE "PEFORMANCE" GOVERNOR #####


##### (Q) EXIT THE PROGRAM #####
q|Q) exit 0;;
##### END EXIT THE PROGRAM #####


##### INVALID OPTION #####
*) echo "Oopps!!! You didn't choose a valid option.";
echo "Press Enter to continue. . ." ; read ;;
##### END INVALID OPTION #####

esac
done

##### END INVALID OPTION #####

esac
done

```

---

### Post by hydrian on 2012-11-28
In 12.04, you can install indicator-cpufreq.  It isn't pretty, but it does provide a usable GUI interface for CPUFreq.  Here is how you use it.  Nothing special really. 

```

#> sudo aptitude install indicator-cpufreq

```

You can use the KDE 'Autostart' GUI management application so indicator-cpufreq is started at login.  You can also do it via the CLI too. 
```

#> cd ~/.config/autostart
#> ln -s /usr/bin/indicator-cpufreq

```

Then re-login. It will show up in the system tray as a program without an icon.  Right click on the system tray icon and you can select the governor or specific clock speed. 

This is proven in Kubuntu 12.04 with KDE 4.9.2 (Backports).

---

### Post by jlacroix on 2012-11-28
> **hydrian said:**
> In 12.04, you can install indicator-cpufreq.  It isn't pretty, but it does provide a usable GUI interface for CPUFreq.  Here is how you use it.  Nothing special really. 

```

#> sudo aptitude install indicator-cpufreq

```

You can use the KDE 'Autostart' GUI management application so indicator-cpufreq is started at login.  You can also do it via the CLI too. 
```

#> cd ~/.config/autostart
#> ln -s /usr/bin/indicator-cpufreq

```

Then re-login. It will show up in the system tray as a program without an icon.  Right click on the system tray icon and you can select the governor or specific clock speed. 

This is proven in Kubuntu 12.04 with KDE 4.9.2 (Backports).
Thank you, that is very useful. I solved it a different way, however.

First, I made it so that the cpufreq-set command doesn't ask for password (I configured sudo to not need a password for it).

Second, I made a bash script for each, gov_powersave, gov_conservative, gov_ondemand, etc and saved them in /usr/local/bin.

Finally, I went into the KDE power settings and for each category (plugged in, on battery, low power, etc) I set it to run one of the above commands accordingly. This way, I don't have to actually worry about running a script each time or selecting anything.

I am thinking about setting up a machine with Ubuntu so I can play around with Unity, so I'll need to figure out how to automate the running of those scripts in a similar way.

On a somewhat related note, I had an incident where Kubuntu didn't sleep even though I closed the lid, and it almost roasted in my bag. So I had to write another script to enforce the sleep settings since I can't trust KDE's anymore.

---

