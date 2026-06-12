---
title: "history command with timestamp"
date: 2013-08-01
forum: General Help
---

### Post by vladoboss-gmail on 2013-08-01
I want to enable timestamp to history command. I tried different values with export HISTTIMEFORMAT but it only display timestamps change from when "export HISTTIMEFORMAT" was executed, and not the real time in history when command was executed. Example:
```
489  2013-08-01 19:46:14 &#1083;&#1089;
  490  2013-08-01 19:46:14 ls
  491  2013-08-01 19:46:14 cd Picasa/
  492  2013-08-01 19:46:14 ls
  493  2013-08-01 19:46:14 cd Collages/
  494  2013-08-01 19:46:14 ls
  495  2013-08-01 19:46:14 ls -lh
  496  2013-08-01 19:46:14 cd
  497  2013-08-01 19:46:14 ssh
  498  2013-08-01 19:46:21 ping google.com
  499  2013-08-01 19:46:28 ping 4.2.2.1
  500  2013-08-01 19:57:38 man history
  501  2013-08-01 20:06:18 less .bash_history 
  502  2013-08-01 20:07:57 export HISTTIMEFORMAT='%F %T '
  503  2013-08-01 20:08:00 history 
  504  2013-08-01 20:22:33 export HISTTIMEFORMAT="%h/%d - %H:%M:%S "
  505  2013-08-01 20:22:37 history 
  506  2013-08-01 20:48:01 export HISTTIMEFORMAT='%F %T '
  507  2013-08-01 20:48:05 history 
```
You can see that date&time is the same 2013-08-01 19:46:14 before HISTTIMEFORMAT was executed and after that it display in correct date/time. Is any option to display the history logs recursively in real time?

---

### Post by papibe on 2013-08-01
Hi vladoboss-gmail.

AFAIK it is not "retroactive" in Bash. If you take a look at the file ~/.bash_history, timestamps are only recorded when HISTTIMEFORMAT is set.

Regards.

---

### Post by vladoboss-gmail on 2013-08-01
Unfortunately you're right. Thanks

---

