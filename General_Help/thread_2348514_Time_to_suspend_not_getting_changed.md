---
title: "Time to suspend not getting changed"
date: 2017-01-04
forum: General Help
---

### Post by ssreddy555 on 2017-01-04
During inactivity, the time to go to suspend mode is not getting changed when changes are applied in the power settings or/and brightness settings in Ubuntu 16.04 LTS.

Can somebody please suggest a way out?

I have changed the times in the power manager as well. This simply reflected the changed times in the power settings but not actually applied.

I tried this when the laptop is connected to AC mains. 

I saw this problem reported & confirmed in the Bugs section as early as 11.04 but could not find a solution.

Thanks in advance.

---

### Post by #&amp;thj^% on 2017-01-04
systemd has a timer system that can be used to invoke systemd services similarly to cron. The OnCalendar option of timers can be used to trigger a timer at certain times according to a calendar event rule.
Suspend

In my case, I wanted to have my Desktop to suspend itself every day at 3 AM (I&#8217;m usually in bed by this time). To do this, I created a
```
/etc/systemd/system/auto-suspend.timer
```
Added this to it
```

[Unit]
Description=Automatically suspend on a schedule

[Timer]
OnCalendar=*-*-* 03:00:00

[Install]
WantedBy=timers.target
```

By default, a timer will invoke a service by the same name when triggered, so I created a text file
```
/etc/systemd/system/auto-suspend.service
```

Then I added this:
```
[Unit]
Description=Suspend

[Service]
Type=oneshot
ExecStart=/usr/bin/systemctl suspend
```

The service simply runs the systemd command to suspend the computer. I imagine there might be a better way to do it, but this way works fine.
Resume

Another handy feature of systemd timers is the ability to wake the system when triggered, with the WakeSystem option. I wanted my Desktop to resume at 6:30 PM, around the time I usually get home, so I created a text file: 
```
/etc/systemd/system/auto-resume.timer
```

And added this to it.
```

[Unit]
Description=Automatically resume on a schedule

[Timer]
OnCalendar=*-*-* 18:30:00
WakeSystem=true

[Install]
WantedBy=timers.target
```
Note: The time works on a 24 Hour Clock...IE 3:00AM=03:00:00 and 6:30PM=18:30:00 
This should do it, but the timer still wants to invoke a service, so I created a "no-op in" 
```
/etc/systemd/system/auto-resume.service
```

And Added this to it:

```
[Unit]
Description=Does nothing

[Service]
Type=oneshot
ExecStart=/bin/true
```

Once again,** there is likely a better way to achieve this**, but I am no systemd expert.

---

### Post by ssreddy555 on 2017-01-05
Thank u for giving an elaborate reply.

Feel I haven't made myself clear.

Please see the screenshot & the enclosed settings in the red rectangle.

I changed the settings to suspend during inactivity to what are shown here. But they are not getting applied in actuality. 
whatever be the values here, the time to suspend settings are remaining the same as the default values. I want to change them to the values set here.
I want to know how.

---

### Post by #&amp;thj^% on 2017-01-05
> **ssreddy555 said:**
> Thank u for giving an elaborate reply.

Feel I haven't made myself clear.

Please see the screenshot & the enclosed settings in the red rectangle.

I changed the settings to suspend during inactivity to what are shown here. But they are not getting applied in actuality. 
whatever be the values here, the time to suspend settings are remaining the same as the default values. I want to change them to the values set here.
I want to know how.

I understood the original post clear enough...and just offered another method...as it affects me also.
Just my way of handling it and sharing is all.:D
My thoughts (and maybe mine alone) on this is in "systemd" not correctly handling our preferences.
And as I said earlier "there is likely a better way to achieve this"
Regards

---

### Post by #&amp;thj^% on 2017-01-05
Well I think I found a better solution for this...using **"dconf editor"**
Navigate to "org/gnome/settings-daemon/plugins/power"...and in the right hand side you will see the options there for "sleep-inactive-ac-timeout" and "sleep-inactive-battery-timeout"


Note this:
> The amount of time in seconds the computer on AC power needs to be inactive before it goes to sleep. A value of 0 means never.
Hope it works for you also.;)

---

### Post by ssreddy555 on 2017-01-06
I have already tried this method without avail.

The changes we make here are simply reflected in the Power settings but they are not taking effect.

---

