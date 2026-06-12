---
title: "AT command alternative"
date: 2014-06-30
forum: General Help
---

### Post by emanmcdow on 2014-06-30
Hello everyone! I am looking for a command that allows me to schedule commands. I have looked at "at", but according to the internet it doesn't allow interactive commands. In my case I want steam to open at a specific time, so that it can start downloading. (Isp data limitations make it so that I have to download half of a game in one month and the other half in another. I want to start it at midnight of the beginning of the first day of July. Lol.) I can't get steam (or even gedit for that matter) to open using at. There are no error messages. Are there any good alternatives for the job I want done? Thanks guys!

---

### Post by oldos2er on 2014-06-30
[Crontab]("https://help.ubuntu.com/community/CronHowto").

---

### Post by emanmcdow on 2014-06-30
I don't think that's what I'm looking for.

---

### Post by steeldriver on 2014-06-30
What kind of interactive input does it need exactly (sorry not familiar with steam)? if it's simple prompt-response type stuff then you may be able to script it with 'expect' and - then schedule *that* via 'at' or 'crontab'

---

### Post by emanmcdow on 2014-06-30
> **steeldriver said:**
> What kind of interactive input does it need exactly (sorry not familiar with steam)? if it's simple prompt-response type stuff then you may be able to script it with 'expect' and - then schedule *that* via 'at' or 'crontab'

I just need a gui. When I want steam to open, I need to be able to see and use it. Steam will start downloading from it's queue as soon as it opens, I just need steam to open.

---

### Post by erind on 2014-06-30
> **emanmcdow said:**
> [...] I have looked at "at", but according to the internet it doesn't allow interactive commands. [...] 
I can't get steam (or even gedit for that matter) to open using at. There are no error messages. [...]

***at*** can very well be used with an interactive shell, (with the right syntax of course). Maybe you didn't set the *DISPLAY* variable (?). The following code works fine when run in a terminal:

```
 echo  "export DISPLAY=:0.0 ; gedit" | at 23:00
```

I haven't used Steam so can't comment on that.

---

### Post by oldos2er on 2014-07-01
> **emanmcdow said:**
> I don't think that's what I'm looking for.

If you desire a GUI app, see [https://help.ubuntu.com/community/CronHowto#GUI_Applications](https://help.ubuntu.com/community/CronHowto#GUI_Applications) which mentions a program called gnome-schedule.

---

