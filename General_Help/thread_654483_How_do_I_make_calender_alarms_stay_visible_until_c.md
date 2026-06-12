---
title: "How do I make calender alarms stay visible until clicked?"
date: 2007-12-31
forum: General Help
---

### Post by Alco on 2007-12-31
Currently calendar alarm pop ups disappear automatically. I would prefer having to click a button on them to make sure I have seen them. I am used to having a choice of dismiss/snooze/ok to do that.

Thanks.

---

### Post by go_beep_yourself on 2007-12-31
Which program are you using to do that? Evolution? Kalarm? You could even use cron. Are you using Ubuntu as an alarm clock to wake yourself up in the morning?

---

### Post by Alco on 2008-01-02
I use Evolution to add calendar entries. The alarms or reminders it generates stay visible for 10s, then disappear. I would like to see them disappear only after I have clicked it.

---

### Post by aJayRoo on 2008-01-02
If you explicitly set an alarm/reminder (I don't remember what it is called) when you create an event then the alarm should appear in the middle of you screen and require you to press OK before it closes as well as producing the pop up in the corner. Note this is extra to the small reminder pop ups that disappear after a short time.

---

### Post by lubeck on 2008-01-24
Found this - hope others did  Worked !

The following change causes the old-style dialog box to pop up instead of placing the notification in the tray.  Run the following command and uncheck the notify_with_tray box:
Code:

gconf-editor /apps/evolution/calendar/notify/notify_with_tray

You probably have to kill evolution and evolution-alarm-notify and then restart evolution for this to take effect.

---

