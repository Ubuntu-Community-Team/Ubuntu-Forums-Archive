---
title: "Clock Misbehavin"
date: 2013-12-10
forum: General Help
---

### Post by mayagrafix on 2013-12-10
The digital clock on the menu-bar is showing the UTC time and not local. I already went to all settings >>> Time & Date panel and set the right location, but to no avail. The menu-bar clock insist on showing UTC time (the minutes are ok, but the hours are way ahead).

I've also been having some problem with the Language Keyboard selection on the same menu-bar, have to choose again the correct Language for the keyboard layout every time I start the machine, even though it is correctly highlighted on the menu. 

Me thinks probably some bug in 13.04 which will eventually get fixed, but the time thing does bother me.

THANKS FOR UR HELP.

---

### Post by drmrgd on 2013-12-10
Are you by chance dual booting with Windows?  There is a somewhat old issue that I ran into myself before (although I think my issue was the converse of what you describe), where the system would insist on using UTC time instead of local time.  Have a look at this page, and go down to the section 'Multiple Boot Systems Time Conflicts' and see if this makes any sense:

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

If you're not dual booting, then it's probably something else, but I don't have any immediate ideas other than some of the other Troubleshooting bits at the bottom of the page.

---

### Post by ian-weisser on 2013-12-11
Open a terminal and show us the output of these three commands:
```
date
date -u
timedatectl
```

---

### Post by mayagrafix on 2013-12-11
mayagrafix@Inspiron-620ss:~$ date
Wed Dec 11 13:26:45 CST 2013

mayagrafix@Inspiron-620ss:~$ date -u
Wed Dec 11 19:26:57 UTC 2013

mayagrafix@Inspiron-620ss:~$ timedatectl
      Local time: Wed 2013-12-11 13:27:17 CST
      Universal time: Wed 2013-12-11 19:27:17 UTC
      Timezone: America/Merida (CST, -0600)
      NTP enabled: yes
      NTP synchronized: no
      RTC in local TZ: no
      DST active: no
 Last DST change: DST ended at
                  Sun 2013-10-27 01:59:59 CDT
                  Sun 2013-10-27 01:00:00 CST
 Next DST change: DST begins (the clock jumps one hour forward) at
                  Sun 2014-04-06 01:59:59 CST
                  Sun 2014-04-06 03:00:00 CDT

---

### Post by mayagrafix on 2013-12-11
Update: AS OF THIS MORNING TIME +DATE MENU IN OPERATING SYSTEM IS WORKING AOK.

So far so good today, the local time displays correctly on the menu-bar as does the date (orange highlight box would stick to previous date on calendar, although would display correctly  on top of calendar menu) but it is working good today, all by itself.

Guess Ill keep an eye on it for now and report back if same problem re occurs.

---

### Post by ian-weisser on 2013-12-11
> **mayagrafix said:**
> 
      NTP enabled: yes
[COLOR=#ff0000]       NTP synchronized: no[/COLOR]
      

If your NTP is working properly, that should usually say "yes"

---

### Post by mayagrafix on 2013-12-12
[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/calendarmenubar_zps0ee886b5.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/calendarmenubar_zps0ee886b5.png.html)

If u look closely, although date is correct on top of menu, in the numbers area of calendar OS does not update to correct position (in this case should be Thu 12, not Wed 11).

> If your NTP is working properly, that should usually say "yes" 
were do I adjust NTP?

Thanx for ur help.

---

### Post by ian-weisser on 2013-12-12
> **mayagrafix said:**
> were do I adjust NTP?

Sorry I don't know about the Unity calendar, I do know a bit about NTP.

Check your NTP drift file. Great explanation at [https://pthree.org/2013/10/13/ntp-drift-file/](https://pthree.org/2013/10/13/ntp-drift-file/)

Check your NTP config /etc/ntp.config to ensure you are checking valid, reachable NTP servers.
If you have any questions about the NTP config, show us the file.

You can also use the *ntpdate* command to immediately synchronize your clock. See the ntpdate manpage for important usage information,

---

### Post by mayagrafix on 2013-12-13
This forum is great! The problem seems to have fix itself just by posting here. More power to you guys :>)

---

### Post by drmrgd on 2013-12-13
> **mayagrafix said:**
> This forum is great! The problem seems to have fix itself just by posting here. More power to you guys :>)

HA!  That's good because when you posted that Unity calendar picture, I think some of my neurons misfired and died.  Couldn't figure for the life of my why a resource that I was pretty sure basically pulled information from the same location would have totally different output within itself.  Quite a strange problem!

---

