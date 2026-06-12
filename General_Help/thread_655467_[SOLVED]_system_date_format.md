---
title: "[SOLVED] system date format"
date: 2008-01-01
forum: General Help
---

### Post by MacDuff on 2008-01-01
I would like to change the way dates are displayed on my systems to Year Month Day rather than the current Day Month Year or Month Day Year,  both or which are commonly used here in Canada.

Reviewing other posts,  I found one that seemed to suggest that the environment location should be changed to a country that uses the year/month/day format.  I am concerned that something other than the date format may also be changed by such a strange work-around.

Is there a way to just enter a date format that will effect a global change on how dates are displayed without having to change my nationality?  :)

Thanks

---

### Post by dlegend on 2008-01-01
I found exactly what you are looking for via this post: [http://ubuntuforums.org/showpost.php?p=630735&postcount=3](http://ubuntuforums.org/showpost.php?p=630735&postcount=3)

> 
The time format should follow your locale. What language settings did you choose when installing? If I select English (US) for the session, i get the time format you want, but if I use my default Swedish i get weekday, date, month, hour.minute.

If you right-click, you do get to set some preferences like 12/24 hour time, but in keeping with the Gnome philosophy, you don't see everything there is to set up front, as opposed to KDE. (This is the subject of many a flame war, but let's not delve into that now...)

To be sure, you can set a custom date format, but you need to know about format strings according to the C library function strftime(). And to set it you need to use the Configuration Editor. From the menus: Applications - System Tools - Configuration Editor.

To just do what you asked for: In the Configuration Editor, navigate to /apps/panel/applets/clock_screen0/prefs. Set the key "custom_format" to
```

%a %b %e, %H.%M

```

, and "format" to
```

custom

```


Note the key "custom_format" will have to be changed according to your preferences. Play around with it until it fits your needs. 

For reference: [http://au2.php.net/strftime](http://au2.php.net/strftime)

The above link will give you the different variables that you can use in the custom time format.

**Edit: I think this might work for you:**

```

%Y %b %d, %H.%M

```

That should output 2008 Jan 1, 11:17 AM

or

```

%y %b %d, %H.%M

```

That should output 08 Jan 1, 11:17 AM

Let me know if it works!

---

### Post by MacDuff on 2008-01-01
Thank you digend!

I knew there had to be a way to do it BUT it would have taken me days to find a way of doing it without your help.  It seems to have worked.  File listings can now be sorted and viewed by year, month day. 

I don't know if it will adversely affect anything but I will find out in time.  If it does, the information you provided allows me to easily make additional changes.

Thank you so much for your help.

Mac

---

### Post by ~LoKe on 2008-01-01
Ohh, didn't really think you could do this (silly of me to think that something wasn't possible).  I'm not using Gnome anymore so I've got my own date applet.  This would have been useful a while ago.

---

