---
title: "Battery Notifications in xfce ...."
date: 2019-04-30
forum: General Help
---

### Post by Furycd001 on 2019-04-30
HI..

Running a minimal Xubuntu 16.04.06 install. Power manager will display a notification whenever my battery is low, but not when my battery is fully charged. How can I make power manager display a notification whenever my batter is fully charged ??

---

### Post by Autodave on 2019-04-30
Do you have an icon on the screen that shows the level of battery charge if you hover over the icon?

---

### Post by Furycd001 on 2019-04-30
I have the power manager plugin active in my panel. [Here's what it looks like whenever I hover the icon]("http://i.imgur.com/uUhf6T0.png") && [here's what it looks like whenever I click on the icon.]("http://i.imgur.com/ywG2Dui.png") I receive a notification whenever my battery is low, just not when it's 100% fully charged ....

---

### Post by #&amp;thj^% on 2019-04-30
Gosh i can't remember if Xenial had this or not, but:
```
apt search battery-monitor
```
If it's not there see: [https://github.com/maateen/battery-monitor](https://github.com/maateen/battery-monitor)

---

### Post by Furycd001 on 2019-04-30
> **1fallen said:**
> Gosh i can't remember if Xenial had this or not, but:
```
apt search battery-monitor
```
If it's not there see: [https://github.com/maateen/battery-monitor](https://github.com/maateen/battery-monitor)

Thanks for the reply and for the link :) Cannot find anything so I don't think it's included. My previous minimal xubuntu 16.04.06 install showed me a notification out of the box when my battery reached 100%. Don't actually remember installing anything extra just for the function....

---

### Post by Autodave on 2019-04-30
I am running 2 laptops on Xubuntu and neither one tells me when the battery is fully charged.  Both tell me when I get down to a certain threshold.

---

### Post by Furycd001 on 2019-04-30
> **jonny6 said:**
> Thanks for the reply and for the link :) Cannot find anything so I don't think it's included. My previous minimal xubuntu 16.04.06 install showed me a notification out of the box when my battery reached 100%. Don't actually remember installing anything extra just for the function....

Just after checking out that link that you provided. It's exactly what I'm looking for though it currently doesn't work with 16.04 :(

---

### Post by #&amp;thj^% on 2019-04-30
Can you show me this:
```
battery-monitor & disown

```

---

### Post by Furycd001 on 2019-04-30
> **Autodave said:**
> I am running 2 laptops on Xubuntu and neither one tells me when the battery is fully charged.  Both tell me when I get down to a certain threshold.

Thanks for the heads up :) I have memory problems so I could very easily be wrong about seeing notifications before. I'll probably end up having to create a script or something to accomplish this....

---

### Post by Furycd001 on 2019-04-30
> **1fallen said:**
> Can you show me this:
```
battery-monitor & disown

```

I installed through the ppa & can't get it to launch. Here's the output....

```
furycd001@Reviziis:~$ battery-monitor & disown
[1] 30202
furycd001@Reviziis:~$ battery-monitor: command not found

```

Here's the output I get whenever I try to launch it from a terminal....

```

** (run.py:27589): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-nS6BADGEU9: Connection refused
Traceback (most recent call last):
  File "/usr/share/battery-monitor/run.py", line 14, in <module>
    from AppIndicator import AppIndicator
  File "/usr/share/battery-monitor/AppIndicator.py", line 29
    TEST_MODE: bool
             ^
SyntaxError: invalid syntax

```

---

### Post by #&amp;thj^% on 2019-04-30
How did you install it?
For Ubuntu and its derivatives

Let&#8217;s install from PPA (currently supported: 14.04, **16.04, **16.10, 17.04 & 17.10):
```

sudo add-apt-repository ppa:maateen/battery-monitor -y

sudo apt-get update

sudo apt-get install battery-monitor -y
```

That&#8217;s all. Battery Monitor Stable is installed on your system

---

### Post by Furycd001 on 2019-04-30
> **1fallen said:**
> How did you install it?
For Ubuntu and its derivatives

Let&#8217;s install from PPA (currently supported: 14.04, **16.04, **16.10, 17.04 & 17.10):
```

sudo add-apt-repository ppa:maateen/battery-monitor -y

sudo apt-get update

sudo apt-get install battery-monitor -y
```

That&#8217;s all. Battery Monitor Stable is installed on your system

I just edited my previous reply & this is on the github page....
> 
Let's install from PPA (currently supported: 14.04, 17.10 & 18.04; _**we're struggling with Ubuntu 16.04 right now**_):


---

### Post by #&amp;thj^% on 2019-04-30
Yep seems they have their hands full ATM:
```
/usr/share/battery-monitor/run.py:29: PyGIDeprecationWarning: Since version 3.11, calling threads_init is no longer needed. See: https://wiki.gnome.org/PyGObject/Threading
  GObject.threads_init()
Config file is missing or not readable. Using default configurations.
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python3.7/threading.py", line 917, in _bootstrap_inner
    self.run()
  File "/usr/lib/python3.7/threading.py", line 865, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/share/battery-monitor/AppIndicator.py", line 80, in __run_daemon
    notification.show_specific_notifications(monitor)
  File "/usr/share/battery-monitor/Notification.py", line 112, in show_specific_notifications
    percentage = int(info["percentage"].replace("%", ""))
ValueError: invalid literal for int() with base 10: '96\nbattery 1: discharging'
```
My first quick hack results in this:
```
Exception ignored in: <function Notification.__del__ at 0x6e2e632769d8>
Traceback (most recent call last):
  File "/usr/share/battery-monitor/Notification.py", line 172, in __del__
    self.notifier.close()
gi.repository.GLib.Error: g-io-error-quark: Error calling StartServiceByName for org.freedesktop.Notifications: Timeout was reached (24)
```
If I can come up with a clean patch, I'll submit it.
Works well enough on 18.04 though.:(

---

### Post by Furycd001 on 2019-04-30
Thanks for the help & for the heads up :) I may just have to upgrade to 18.04....

---

### Post by #&amp;thj^% on 2019-04-30
Well for fun I just downloaded the "battery-monitor_0.6-bionic_all.deb"
Used gdebi-cli to install it and Boom Works.
Make sure these are installed first:
```
sudo apt-get install python3 python3-gi libnotify-dev acpi

```
It's been a while since I used 16.04 **so I'm not sure how this will pan out for you???**
```
lsb_release -a && apt policy battery-monitor
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco
battery-monitor:
  Installed: 0.6-beta-4-bionic
  Candidate: 0.6-beta-4-bionic
  Version table:
 *** 0.6-beta-4-bionic 100
        100 /var/lib/dpkg/status

```
And always beware of my suggestions>>> I'm an Adventurous Soul.:lolflag:

---

### Post by Furycd001 on 2019-05-01
Thank you for checking & for the heads up :) I just found [this battery notification]("https://github.com/hg8/battery-full-notification") on github & it happens to do the job I want perfectly. Thank you very much for all of the help that you provided. I'm going to mark this thread as solved now....

---

### Post by cmcanulty on 2019-05-06
I have the opposite problem with xubuntu. I have power manager set to notify me when battery gets to 10%. It never does just shuts down when battery drains.

---

