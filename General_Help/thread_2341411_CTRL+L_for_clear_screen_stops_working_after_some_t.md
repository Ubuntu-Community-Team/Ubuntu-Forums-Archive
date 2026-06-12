---
title: "CTRL+L for clear screen stops working after some time"
date: 2016-10-27
forum: General Help
---

### Post by gojira2016 on 2016-10-27
I am working a lot with bash, ssh, GNU screen, in xfce4-terminal 0.6.3.
I  often use the key combination CTRL+L to clear the screen and get the prompt to the top of the terminal.
Recently,  the key combination CTRL+L simply stops working. During a session, it  suddenly has no effect anymore. Even in newly openend xfce4 terminals  during the same session. I have to restart my entire Xubuntu to get it  to work again.
This is driving me crazy.
I am not able to  figure out what exactly the source of the problem is: bash, ssh, GNU  screen, Xfce, Xubuntu, or a combination of those.
If anyone has encountered such a problem, and knows of a way to fix it, I'd love to read it. Thank you.
Versions used:
Xubuntu 16.04
xfce 4.12
xfce4-terminal 0.6.3

---

### Post by vasa1 on 2016-10-28
Does the workaround in [http://unix.stackexchange.com/questions/141228/control-l-not-clearing-screen](http://unix.stackexchange.com/questions/141228/control-l-not-clearing-screen) (for OSX) work?

```
bind -x '"\C-l": clear'
```

Two more links that may be of relevance:
[ctrl-l no longer works in bash]("https://ubuntuforums.org/archive/index.php/t-1074878.html")
and
[URL="http://unix.stackexchange.com/questions/132804/why-ctrll-in-terminal-wont-clear-screen-like-cls-in-powershell"]Why CTRL+L in Terminal won't clear screen like cls in Powershell
[/URL]

---

### Post by gojira2016 on 2016-10-28
Thank you. I read these threads, they do provide explanations of CTRL+L behavior and workarounds, but my question was more *why* CTRL-L, seemingly without a reason, stops working and how to prevent that. The workarounds are a good way of getting the bash cleared, but they are just that: workarounds. How can I repair the *original* behavior, without having to reboot the entire Xubuntu?

---

### Post by billwho on 2016-10-28
Does typing [FONT=lucida sans unicode]**clear**[/FONT] work?

---

### Post by gojira2016 on 2016-10-28
Yes, works, even after CTRL-L stopped working!

---

### Post by billwho on 2016-10-28
Does **ctrl-c** work?
Does **ctrl-d** exit terminal?

---

### Post by gojira2016 on 2016-11-08
Only now I can continue with this, I was on a holiday.

> **billwho said:**
> Does **ctrl-c** work?
Does **ctrl-d** exit terminal?

Yes and yes. I could now test it, when this happens, ctrl-c and ctrl-d work, but ctrl-l does not work.

---

### Post by kingneutron on 2016-12-02
--If this is still an issue, have you tried replacing the keyboard? Could be dirt in the key or something. Also, have you tried the other Ctrl key?

---

