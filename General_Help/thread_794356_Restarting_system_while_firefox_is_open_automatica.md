---
title: "Restarting system while firefox is open automatically saves the session."
date: 2008-05-14
forum: General Help
---

### Post by Double D on 2008-05-14
Up to date 8.04 and 3 beta 5

Firefox automatically saves my session when i restart ubuntu and firefox is still open

is there a way to disable or fix this? im pretty sure in not in the preferences

---

### Post by Monicker on 2008-05-14
Take a look here:
[http://kb.mozillazine.org/Session_Restore]("http://kb.mozillazine.org/Session_Restore")

---

### Post by Double D on 2008-05-14
nope, answer isnt there

it may be an issue with firefox regarding a restart as a crash, which would make this happen

can someone else try this and see if it happens to them too?

---

### Post by talz13 on 2008-05-14
> **Double D said:**
> nope, answer isnt there

it may be an issue with firefox regarding a restart as a crash, which would make this happen

can someone else try this and see if it happens to them too?

You tried:
> Disable

To disable the crash recovery feature, set browser.sessionstore.resume_from_crash to false:

    * Type about:config in the Location Bar
    * Press Enter
    * Find browser.sessionstore.resume_from_crash
    * Double click to set it to false 

To completely disable all session saving behavior, including the recording of session information, set browser.sessionstore.enabled to false:

    * Type about:config in the Location Bar
    * Press Enter
    * Find browser.sessionstore.enabled
    * Double click to set it to false

I know that firefox restores sessions in the same manner that you describe even in windows, if you leave firefox open when you shutdown/reboot.

---

### Post by Monicker on 2008-05-14
> **Double D said:**
> nope, answer isnt there

it may be an issue with firefox regarding a restart as a crash, which would make this happen

can someone else try this and see if it happens to them too?

The instructions work fine for me.  What exactly did you try from that page?

---

### Post by Double D on 2008-05-14
well i still want my sessions to restore after a crash, but not after i intentionally restart!

---

### Post by talz13 on 2008-05-14
> **Double D said:**
> well i still want my sessions to restore after a crash, but not after i intentionally restart!

I think the main problem there is that it just can't tell if it's a crash or the OS purposefully pulls the plug on the app.  Since I've seen the same "problem" across windows, linux, and maybe mac, I don't know if there's a good solution... :(

---

### Post by Double D on 2008-05-14
> **talz13 said:**
> I think the main problem there is that it just can't tell if it's a crash or the OS purposefully pulls the plug on the app.  Since I've seen the same "problem" across windows, linux, and maybe mac, I don't know if there's a good solution... :(

yeah thats what i was thinking, i just tried it again but this time it asked me whether i wanted to restore or not, instead of automatically restoring it. hopefully the final version of 3 will fix this problem

---

### Post by cdenley on 2008-05-14
If you leave windows open when you logout, the process has to be killed or it will crash when it's X session ends. If you kill the process, then firefox can't clean up after itself. I guess if you don't want to close firefox properly, a workaround would be adding these two lines to the end of "/etc/gdm/PostSession/Default" before the "exit 0".
```

killall -w firefox
rm ~/.mozilla/firefox/*.default/sessionstore.*

```
This would delete the stored session when you logout or shutdown, but still doesn't close firefox properly.

---

