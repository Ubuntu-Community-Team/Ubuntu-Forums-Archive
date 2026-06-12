---
title: "How to diagnose total freeze after forced shutdown?"
date: 2015-11-16
forum: General Help
---

### Post by chrisandrew87 on 2015-11-16
Hi!


A few days ago my notebook started to completely freeze (screen, mouse and sound) and my only way out seems to be a forced shutdown via long press in the hardware button.

I am still not able to find nothing "insightful" after these two answer: [http://unix.stackexchange.com/questions/181067/how-to-read-dmesg-from-previous-session-dmesg-0](http://unix.stackexchange.com/questions/181067/how-to-read-dmesg-from-previous-session-dmesg-0) and [http://unix.stackexchange.com/questions/21963/where-do-i-find-messages-regarding-last-failed-linux-boot](http://unix.stackexchange.com/questions/21963/where-do-i-find-messages-regarding-last-failed-linux-boot) (but it can be simply due to my inexperience :D)


How can I diagnose this problem after booting up again? 


Also, any directions for what I should be looking for are appreciated.

Thank you in advance!

---

### Post by tgalati4 on 2015-11-16
Welcome to the forums.  What is the make and model of the notebook and how old?  Any cracks in the case?

```
dmesg | more
```

or

```
more /var/log/syslog
```

Software errors tend to be repeatable and leave some error messages.  Hardware errors tend to be random and leave misleading and multiple error messages.

Try booting without the battery (AC cord only) to rule out a failing battery.

---

### Post by tgalati4 on 2015-11-16
Welcome to the forums.  What is the make and model of the notebook and how old?  Any cracks in the case?

```
dmesg | more
```

or

```
more /var/log/syslog
```

Software errors tend to be repeatable and leave some error messages.  Hardware errors tend to be random and leave misleading and multiple error messages.

Try booting without the battery (AC cord only) to rule out a failing battery.

---

