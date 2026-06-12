---
title: "Top panel clock date wrong"
date: 2013-06-05
forum: General Help
---

### Post by Dave_L on 2013-06-05
Ubuntu 12.04.2

The system clock is correct.

But the date at the top of the clock in the top panel often lags behind the actual date.

In the attached screen shot, which was made at 2013-05-31 08:52:16, the date at the top is "Thursday, May 30", while the correct day of the month (Friday, May 31) is highlighted in the month display below.

The dates usually get "in synch" later in the day.

Is there something I can do to fix the date at the top?

---

### Post by papibe on 2013-06-05
Hi Dave_L.

First I would make sure your:
```
System Settings -> Time & Date
```
Are set to get the time "Automatically from the Internet" instead of "Manually".

Then, my guess would be that there is some config file on your home directory that got somehow owned by root or other. To test this theory you could run this command:
```
sudo find ~/ -not -path ~/.gvfs -and -not \( -user yourusername -and -group yourusername \) -exec ls -ld '{}' \;
```
You will be able to see which files are not owned by you. In that the case, the easiest way to change them back to you would be:
```
sudo chown -R  yourusername:yourusername  ~
```
(replace 'yourusername' with your actual local username).

Hope it helps. Let us know how it went.
Regards.

---

### Post by Dave_L on 2013-06-05
"Automatically from the Internet" is the current setting.

There are no files in the home directory owned by root.

Logging out and in again fixes the date. The problem is that it's not getting refreshed automatically, or at least not frequently enough.  In 10.04, this problem did not occur.

---

### Post by papibe on 2013-06-05
I corrected the 'find' command, you should replace 'yourusername' by your actual username (sorry about that).

Usually the time zone is obtained from the router (or DHCP server). Have you check that your router is well setup?

Another case could be that your BIOS clock is not correct. Furthermore, your CMOS battery may be dying. The typical sign of the last case is that your computer is out of time/date when it is turned on after a certain time of being off.

Regards.

---

### Post by Dave_L on 2013-06-05
papibe:

I made the necessary changes to the "find" command.

I'm not sure that you understood my original post.  **The system date/time is correct.**  There is no problem with the BIOS clock or the time zone. The "date" command has the correct output.

The only problem is with the clock widget in the top panel. It indicates the date in two places, and they're inconsistent. The screen shot in the original post illustrates that.

---

### Post by papibe on 2013-06-05
I apologize for the misunderstanding.

It looks like this [Bug #1124482]("https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1124482") (look at the screenshot attached).

It would be nice if you can add yourself to the affecting people (on the top), and drop a line or two in the comments.

Regards.

---

### Post by Dave_L on 2013-06-06
Thanks. That bug looks like the same as what I'm experiencing. I've added myself as affected by it.

---

