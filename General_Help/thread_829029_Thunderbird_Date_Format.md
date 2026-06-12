---
title: "Thunderbird Date Format"
date: 2008-06-14
forum: General Help
---

### Post by nostra16 on 2008-06-14
Hello,

I'm having problems choosing the date format for the "Default" date in Thunderbird.

I first followed  [this  UbuntuForums post]("http://ubuntuforums.org/showthread.php?t=113018&highlight=gnome+date+format") to set my Custom time format to "Day Name DD Month Name YYYY, HH:MM (24-hour)" (with a %A %d %B %Y, %H:%M value), and later [this MozzilaZine guide]("http://kb.mozillazine.org/Date_display_format") to change the date format in my Thunderbird panel.

The custom time setting work at least for the clock on the upper panel (witch respects my settings), but the 3rd format for Thunderbird mail dates (mails arrived longer than a week ago) does not. 

My key for "Default" is set to user_pref("mail.ui.display.dateformat.default", 2); , but my dates are still in MM/DD/YYYY, HH:MM (in 12-hour format).

Don't know a lot about this but it seems to me that Thunderbird is not picking up my custom defined time format, and sticking to the by default set format of MM/DD/YYYY HH:MM (12-hour).

If that is the cause of my problems, how can I change the default system date format?

If I'm not specific enough please let me now and I'll add in further details.

Thanks for reading me!

nostra16

---

### Post by yogm2k on 2009-03-30
> **nostra16 said:**
> Hello,

I'm having problems choosing the date format for the "Default" date in Thunderbird.

I first followed  [this  UbuntuForums post]("http://ubuntuforums.org/showthread.php?t=113018&highlight=gnome+date+format") to set my Custom time format to "Day Name DD Month Name YYYY, HH:MM (24-hour)" (with a %A %d %B %Y, %H:%M value), and later [this MozzilaZine guide]("http://kb.mozillazine.org/Date_display_format") to change the date format in my Thunderbird panel.

The custom time setting work at least for the clock on the upper panel (witch respects my settings), but the 3rd format for Thunderbird mail dates (mails arrived longer than a week ago) does not. 

My key for "Default" is set to user_pref("mail.ui.display.dateformat.default", 2); , but my dates are still in MM/DD/YYYY, HH:MM (in 12-hour format).

Don't know a lot about this but it seems to me that Thunderbird is not picking up my custom defined time format, and sticking to the by default set format of MM/DD/YYYY HH:MM (12-hour).

If that is the cause of my problems, how can I change the default system date format?

If I'm not specific enough please let me now and I'll add in further details.

Thanks for reading me!

nostra16

Even I am getting the same problem; installed add-on also but it didn't work out!!

---

### Post by Antares784 on 2010-08-18
I, too, am having this issue. I've already changed the system date/time format, but Thunderbird insists on sticking to the MM/DD/YYYY format for the date, and this is driving me nuts.

(I have a special situation here where the profile for Thunderbird is stored on a different partition that can be accessed by both Windows 7 and Ubuntu, but I figure that shouldn't make a difference).

Help?

---

### Post by hena on 2010-10-27
See the following

[http://lildude.co.uk/howto-customise-thunderbird-date-format](http://lildude.co.uk/howto-customise-thunderbird-date-format)

---

