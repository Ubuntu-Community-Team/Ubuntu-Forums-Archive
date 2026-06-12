---
title: "Suspend hook not working in Xubuntu 15.04"
date: 2015-07-01
forum: General Help
---

### Post by The Trickster on 2015-07-01
I've been using [this suspend hook]("http://askubuntu.com/questions/152403/how-do-i-make-changes-to-proc-acpi-wakeup-permanent?answertab=votes#tab-top") with Ubuntu & Kubuntu since the days of 12.10, however when I did a clean install of Xubuntu 15.04 yesterday, I noticed it suddenly not working. I've created a file: ```
/usr/lib/pm-utils/sleep.d/45fixusbwakeup
``` copied the script into it, and made it executable with: ```
sudo chmod +x /usr/lib/pm-utils/sleep.d/45fixusbwakeup
``` as I always did before. I'm not an expert, and this hook has always been working from me, so I don't have a clue what could be wrong now.

What I basically need is that these 3 commands execute every time before computer is going to sleep, or at every startup:

```
sudo -s
echo USB0 > /proc/acpi/wakeup
echo USB2 > /proc/acpi/wakeup
```

I would also like to note that when I suspend via terminal command:

```
sudo pm-suspend
```

Script works flawlessly, it's only not working via traditional shutdown--->suspend button in Xubuntu, so I guess this is something Xubuntu-related. I guess it actually suspends via:

```
xfce4-session-logout --suspend
```

And that's creating the problem.

---

### Post by Toz on 2015-07-01
Most probably because xfce4-session will use systemd-sleep on a systemd system (not pm-suspend). systemd-sleep hooks should be put in /lib/systemd/system-sleep using the following template:
```
#!/bin/sh
case $1/$2 in
  pre/*)
    echo "Going to $2..."
    ;;
  post/*)
    echo "Waking up from $2..."
    ;;
esac

```
...and made executable. One other caveat with systemd is that the scripts in this directory are run concurrently, not sequentially based on name (as is the case with pm-utils).

---

### Post by The Trickster on 2015-07-01
I've tried by simply copying this script to /lib/systemd/system-sleep and it won't work. Is there a way to change default suspend command to pm-suspend?

---

### Post by Toz on 2015-07-01
> I've tried by simply copying this script to /lib/systemd/system-sleep and it won't work.
Try the script like this. Make sure its executable. Works on my 15.04 system:
```
#!/bin/sh
case $1/$2 in
  pre/*)
    echo USB0 > /proc/acpi/wakeup
    echo USB2 > /proc/acpi/wakeup
    ;;
  post/*)
    ;;
esac
```
>  Is there a way to change default suspend command to pm-suspend? 
I don't know. I'll have a look. [Here](https://bugzilla.xfce.org/show_bug.cgi?id=9952) is the bug report and [commit]("http://git.xfce.org/xfce/xfce4-session/commit/?id=0bc5eb603a3ab4af930fac70e03cfe7aa63a399e") that changed things.

---

### Post by The Trickster on 2015-07-02
> **Toz said:**
> Try the script like this. Make sure its executable. Works on my 15.04 system:
```
#!/bin/sh
case $1/$2 in
  pre/*)
    echo USB0 > /proc/acpi/wakeup
    echo USB2 > /proc/acpi/wakeup
    ;;
  post/*)
    ;;
esac
```

Again, pm-suspend works, log out--->suspend won't :(

edit: It won't work even in Kubuntu 15.04, they obviously changed something.

---

### Post by Toz on 2015-07-02
Can you try this version of the script (it includes debugging info):
```
#!/bin/sh
case $1/$2 in
  pre/*)
    echo "Entering sleep..." >  /tmp/sleep.log
    echo "Entering sleep"
    cat /proc/acpi/wakeup >> /tmp/sleep.log
    echo USB0 > /proc/acpi/wakeup
    echo USB2 > /proc/acpi/wakeup
    echo "After setting values..."  >> /tmp/sleep.log
    cat /proc/acpi/wakeup >> /tmp/sleep.log
    ;;
  post/*)
    echo "Awaking from sleep..." >>  /tmp/sleep.log
    echo "Waking up"
    cat /proc/acpi/wakeup >> /tmp/sleep.log
    ;;
esac
```
...and after a suspend/resume cycle using xfce4-session, post back the contents of /tmp/sleep.log.

And can you also post back the results of:
```
ls -l  /lib/systemd/system-sleep/45fixusbwakeup
```
...and one more time:
```
cat /proc/acpi/wakeup
```

EDIT: And one more item: the results of:
```
sudo journalctl -b -u systemd-suspend
```

---

### Post by The Trickster on 2015-07-02
It works now, man! I don't know how but it started working. Thank you for your time, really!

---

### Post by Toz on 2015-07-03
> **The Trickster said:**
> It works now, man! I don't know how but it started working. Thank you for your time, really!

Glad to hear. Can you mark this thread "Solved" using the Thread Tools link above?

---

