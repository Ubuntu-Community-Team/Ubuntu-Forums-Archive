---
title: "Custom date/time format for clock applet"
date: 2008-05-03
forum: General Help
---

### Post by raykroeker on 2008-05-03
Within 7.04 (Feisty Fawn) I was able to set a custom format for my clock applet using gconf-editor.  Within current release (8.04; Hardy Heron) the value for the key (/schemas/apps/clock_applet/prefs/custom_format) is a schema that cannot be modfied from within the editor.

  Can anyone help me change the format; even if not from within the gconf-editor, any way to set a specific format for the clock applet would be appreciated.

---

### Post by SQuark on 2008-06-01
That's because you're not supposed to edit the schemas.

The key you're looking for is /apps/panel/applets/applet_?/prefs/custom_format

Don't forget to change /apps/panel/applets/applet_?/prefs/format to custom.

---

### Post by CameO73 on 2008-06-01
Thanks! Didn't know this was possible.

Some more info for those interested:

[LIST]
[*]time format parameters: [http://php.net/strftime](http://php.net/strftime)
[*]I found the custom_format and format keys in **/apps/panel/applets/clock_screen0/prefs**
[*]example: **wk.%V | %a %d-%b-%Y %H:%M** -- will display time as **wk.22 | Sun 01-Jun-2008 12:18**
[/LIST]

---

### Post by noynac on 2008-06-02
Thanks for the thread. I've wanted to change the panel clock format but didn't know this could be done.

I also wanted to change the date format in nautilus. The configuration editor does have a date_format setting, but it only accepts three specific options. Anyone know how to change this?

---

### Post by bjorn_johansson on 2008-12-21
Hi, I followed the instructions in this thread and they worked for me. The date format is now "Sunday 2008-12-21 09:15" in the applet on the top right corner of the esktop
but when I cright click and select "copy Date" i still get 
"Sunday, December 21 2008"

Where can I change this?

---

### Post by geazzy on 2011-05-17
> **CameO73 said:**
> %a %d-%b-%Y %H:%M
[/LIST]

thanks it's work for me in  ubuntu natty :)

---

### Post by poisonborz on 2011-10-08
it's important to note that you must run gconf-editor **without sudo**, otherwise the desired values above will not appear.

---

### Post by davidmaxwaterman on 2011-10-21
> **bjorn_johansson said:**
> Hi, I followed the instructions in this thread and they worked for me. The date format is now "Sunday 2008-12-21 09:15" in the applet on the top right corner of the esktop
but when I cright click and select "copy Date" i still get 
"Sunday, December 21 2008"

Where can I change this?

I wonder if you managed to find a way to copy the date as it is displayed, rather than some other format. The current behaviour seems an aweful lot like a bug to me...

---

### Post by dcstar on 2011-10-22
> **davidmaxwaterman said:**
> I wonder if you managed to find a way to copy the date as it is displayed, rather than some other format. The current behaviour seems an awful lot like a bug to me...

Display formats are just that, underlying formats are most likely set in the LOCALE definitions for the system.

A "Copy" is probably the underlying data which is then displayed using the LOCALE defined format.

---

### Post by davidmaxwaterman on 2011-10-22
> **dcstar said:**
> Display formats are just that, underlying formats are most likely set in the LOCALE definitions for the system.

A "Copy" is probably the underlying data which is then displayed using the LOCALE defined format.

i agree. it is very likely that it makes sense technically, but it almost certainly is not what the user wants.

---

