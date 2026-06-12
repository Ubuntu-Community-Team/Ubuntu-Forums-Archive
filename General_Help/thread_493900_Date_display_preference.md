---
title: "Date display preference"
date: 2007-07-06
forum: General Help
---

### Post by kenmiles on 2007-07-06
Evolution shows my date as mm/dd/yyyy but I would like it the British way (dd/mm/yyyy.
Can anyone point me in the right direction to change this.
Thanks in advance,
Kenneth.

---

### Post by Ayuthia on 2007-07-06
**Oops!  You would think that I would have learned to read by now.  This information will change the date and time on the panel....**

The only place that I was able to find this was under the Configuration Editor.  To get there,  press Alt-F2 and the run gconf-editor.  From there you will need to get to the following:

/->apps->panel->clock_screen0->prefs

You will then see a list of options on the right.  You will need to change 'format' to custom and then go to custom_format.  Double click on custom_format and enter the string format that you would like to see.  The format options can be found at this link:

[http://www.die.net/doc/linux/man/man3/strftime.3.html](http://www.die.net/doc/linux/man/man3/strftime.3.html)

For example:
%d/%m/%Y %I:%M%P

would display:
06/07/2007 04:42pm

---

### Post by Ayuthia on 2007-07-06
It does not look like there is an option for this yet.  It was set as a future enhancement.  Here is what I found:
[http://bugzilla.gnome.org/show_bug.cgi?id=205137](http://bugzilla.gnome.org/show_bug.cgi?id=205137)

---

### Post by brickbat on 2007-08-18
Stuff like this is why Evolution is rubbish.  They think this is an added feature instead of a requirement.

---

