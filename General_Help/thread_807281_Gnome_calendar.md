---
title: "Gnome calendar"
date: 2008-05-25
forum: General Help
---

### Post by magnus0 on 2008-05-25
How can I change, what day does the week start with? In my country, it starts with Monday and it's really annoying to see that Sunday there all the time.

---

### Post by RATM_Owns on 2008-05-25
Look around in System->Administration->Time and Date

---

### Post by fragos on 2008-05-25
Evolution has a parameter for start day in calendar preferences. Mine is set to Monday and when viewing the calendar within evolution the view is Monday first. The date time display in the applet bar does always start with Sunday. The calendar data you are viewing is from the evolution data base. There is a small application called "dates" that also shares the evolution data base. It also starts views with Monday. I draged its icon to my applet bar for quick access.

---

### Post by niteshifter on 2008-05-25
Hi,

>  Look around in System->Administration->Time and Date

Ah, no, that's not what he wants. He wants to change the appearance of the calender that pops when one clicks the clock (Clock-applet) in the top right corner of a GNOME desktop. This question was asked yesterday in the Abs Beginner forum, and is still unresolved.

You can change the time / date by the method you describe, just not the format. Try it: Pick any European city and see the clock time display change. Now click on it - that @#$* calender still insists on the US display (elsewhere in the world the week starts with Monday). Restart or no restart - the popped calender insists on US formatting. After you see the time change in the display, open a terminal and give the "locale" command - if you're a US user everything still says en_US.UTF-8.

It gets more complicated than that: via gconf-editor one has means to specify the formatting of the Clock applet's display - but not the popped calender. And yes, Evolution will let you specify the start of your work week - but not the start day of the week itself. Try it - no joy.

It's an interesting problem - I've seen screenshots of a non-US format calender via the Clock applet, so I know it can be done. I'm thinking it's a locale setting issue ... but I'm very rusty on locale stuff.

I think he needs to do something (but not yet!) along the lines of an update-locale TIME=et_EE.<something> - that's where I'm stuck: on the country code needed and the char set. I also haven't worked out what side-effect if any this will cause. This line of thought is backed by some googling - it's solved in Slackware via proper locale setup.

---

### Post by Zlatan on 2008-12-23
> **magnus0 said:**
> How can I change, what day does the week start with? In my country, it starts with Monday and it's really annoying to see that Sunday there all the time.

[That]("http://onlyubuntu.blogspot.com/2008/05/howto-set-gnome-calendar-first-day-of.html") helped me:

---

### Post by artm on 2009-02-25
Gnome calendar applet adheres to your locale settings. In Ubuntu, you can assign locale components by editing the file /etc/defaults/locale. Here is what I've got there:

$ cat /etc/default/locale
LANG="en_US.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"

Which means: I want software messages in American, but time, paper size and units in British i.e. weeks starting with Mondays, A4, metric.

To see your current locale settings:

$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_GB.UTF-8
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT=en_GB.UTF-8
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by pmorch on 2009-02-25
Thanks, artm, works perfectly. And avoids messing with files that are overridden by apt-get upgrade later. Just grand.
):P

---

### Post by shlema on 2009-12-01
artm,

thank you very much, it works.

---

### Post by MacHaddock on 2011-03-30
if your swedish this might help

[http://comments.gmane.org/gmane.linux.debian.user.swedish/10109](http://comments.gmane.org/gmane.linux.debian.user.swedish/10109)

---

