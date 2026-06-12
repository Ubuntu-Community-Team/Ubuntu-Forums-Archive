---
title: "How to get DPMS working again"
date: 2013-06-18
forum: General Help
---

### Post by defaria on 2013-06-18
DPMS (the ability to put my monitors in power saving mode) used to work for a long time. But lately it seems to turn off at random. I've been trying to trace down what is causing this but I can't seem to find it.

I have two monitors on my desktop and usually after xscreensaver runs for a while it puts the screens to sleep. But I often wake in the middle of the night seeing the xscreensaver screensavers running taking up energy and CPU on my desktop. 

As I said I run xscreensaver and under the Advanced tab Display Power Management I have Power Manager Enabled, Standby After 5 minutes, Suspend After 10 minutes and Off After 20 minutes as well as Quick Power-off in Blank Only Mode. I've had Brightness & Lock set to Turn screen off when inactive for 5 minutes and Lock after 10 minutes. Thinking that perhaps Brightness & Lock settings were stepping on xscreensaver setting I turned those off. But it didn't help.

Like I said, this used to work, without issue, but started not working lately (since updating to 13.04). I even have a cronjob running ever 15 minutes that executes a script using xset dpms 600 1200 1800 as well as capturing the current DPMS settings using xset q both before and after the xset dpms command.

There seems to be something setting DPMS's standby times as I see stuff like:

```

$ grep Standby /tmp/debug.log
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 0    Suspend: 0    Off: 0
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 600    Suspend: 1200    Off: 1800
  Standby: 600    Suspend: 1200    Off: 1800
...

```

I see now that my script sets this to 600 1200 1800 whereas apparently xscreensaver is setting this to 300 600 1200. I will change my script to use 300 600 1200. But who is setting it to 0 0 0?!? This setting to 0 0 0 occurs several times. Who's doing that?

I'm gonna set xscreensaver to 300 600 1200, my script to 300 600 1200 and Brightness & Lock to Turn screen off when inactive for 5 minutes and Lock screen after 10 minutes and see if this gets any better but anybody who knows more about this feel free to comment.

---

### Post by defaria on 2013-07-02
So, nobody's got an answer? Great!

---

### Post by pqwoerituytrueiwoq on 2013-07-02
[FONT=courier new]xset dpms[/FONT] should turn it on [FONT=courier new]xset -dpms[/FONT] should turn it off
[FONT=courier new]xset -q | grep  'DPMS is'[/FONT] will tell you the current state

---

### Post by defaria on 2013-08-21
The issue is not really dpms on or off, it's the settings of standby suspend and off that seems to be the problem. Even if it is that dpms is turned off, who's turning it off?!?

---

### Post by defaria on 2013-08-21
I just performed another test. Given:

```
Earth:cat /usr/local/bin/setdpms.sh 
#/bin/bash
logfile=/tmp/debug.log
#logfile=/dev/null

export DISPLAY=:0
echo $(date)                                >> $logfile
echo "Current DPMS Settings"                >> $logfile
xset q | grep -e DPMS -e Standby -e Monitor >> $logfile 2>&1
xset dpms 300 600 1200                      >> $logfile 2>&1
echo "Status: $?"                           >> $logfile
echo "DPMS now set to"                      >> $logfile
xset q | grep -e DPMS -e Standby -e Monitor >> $logfile 2>&1
echo "------------------------------------" >> $logfile

```

Cronned ever 15 minutes I get:

```
Earth:grep "DPMS is" debug.log
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
  DPMS is Enabled
Earth:

```

So DPMS is never disabled. However:

```

Earth:grep "Standby" debug.log
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 0    Suspend: 0    Off: 0
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 0    Suspend: 0    Off: 0
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 0    Suspend: 0    Off: 0
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 0    Suspend: 0    Off: 0
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
  Standby: 600    Suspend: 600    Off: 600
  Standby: 300    Suspend: 600    Off: 1200
Earth:

```

Somebody's periodically setting Standby, Suspend and Off to zero.

---

