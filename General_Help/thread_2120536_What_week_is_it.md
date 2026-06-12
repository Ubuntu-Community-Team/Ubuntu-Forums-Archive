---
title: "What week is it?"
date: 2013-02-26
forum: General Help
---

### Post by c901906 on 2013-02-26
When I click on the date (“Tue Feb 26, 4:00PM”) the calender pops up and displays March 26 week 13.

TIA!


Linux office 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 01:50:30 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
GNOME Shell 3.6.2

---

### Post by Habitual on 2013-02-26
What's the question?

---

### Post by Yellow Pasque on 2013-02-26
It might help if you told us what desktop you're using (Unity?)...

---

### Post by c901906 on 2013-02-27
> **Habitual said:**
> What's the question?

Why is it wrong?

---

### Post by c901906 on 2013-02-27
> **Temüjin said:**
> It might help if you told us what desktop you're using (Unity?)...


From the original post: GNOME Shell 3.6.2

---

### Post by csad on 2013-02-27
Actually, you should be able to get the right time and date for your timezone automatically over the internet sync option in: applications-->system-->time and date

This should also help: [https://help.ubuntu.com/12.04/serverguide/NTP.html](https://help.ubuntu.com/12.04/serverguide/NTP.html)

---

### Post by c901906 on 2013-02-27
> **csad said:**
> Actually, you should be able to get the right time and date for your timezone automatically over the internet sync option in: applications-->system-->time and date

This should also help: [https://help.ubuntu.com/12.04/serverguide/NTP.html](https://help.ubuntu.com/12.04/serverguide/NTP.html)

Thanks for your help. I think it's just broken.

[[img]http://s1.postimage.org/5oynbfl3f/Screenshot_from_2013_02_27_11_38_16.jpg[/img]](http://postimage.org/image/5oynbfl3f/)

I'm guessing that it will probably fix itself in the next couple of days (No Feb 29).

---

### Post by csad on 2013-02-27
I honestly don't get why you're having a problem. If you go to the Applications Menu and open up "Time and Date" under "System", you should be able to not only change the timezone, but change the date as you wish. 

I don't see how it could be broken, but if you think so, just go to synaptics and reinstall it.

---

### Post by Impavidus on 2013-02-27
The point is that it's 27 February, as indicated by the top line in the screen shot, but the calendar opens at the page for March.

I haven't used that calendar for a while. If you click on the small left arrow next to the month, it returns to the present month. Does the highlighted day stay on the 27th or does it disappear? And if you then close and reopen the calendar, it opens again at March?

---

### Post by c901906 on 2013-02-27
> **csad said:**
> I honestly don't get why you're having a problem. 

Me neither!

Changing the date does not help. It's correctly maintained by ntp. Just the widget is broken. Look at the picture that I posted. The date is correct. The calendar is wrong.

---

### Post by c901906 on 2013-02-27
> **Impavidus said:**
> The point is that it's 27 February, as indicated by the top line in the screen shot, but the calendar opens at the page for March.


Setting the month with the calendar left/right arrows will appear to work. Closing and then reopening the calendar will then fail again.

I'm guessing it's faulty leap year code.

---

### Post by c901906 on 2013-03-01
I thought it would fix itself. Oh-well.

[IMG][[img]http://s2.postimage.org/k8ilm8gnp/Screenshot_from_2013_03_01_06_56_58.jpg[/img]](http://postimage.org/image/k8ilm8gnp/)[/IMG]

---

