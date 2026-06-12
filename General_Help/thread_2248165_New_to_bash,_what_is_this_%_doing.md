---
title: "New to bash, what is this %? doing?"
date: 2014-10-12
forum: General Help
---

### Post by sanctusmessor2 on 2014-10-12
This is part of a disk usage monitoring script
Specific line
```
[COLOR=#333333][FONT=Inconsolata]**if**[/FONT][/COLOR][COLOR=#333333][FONT=Inconsolata] [ [/FONT][/COLOR][COLOR=#008080][FONT=Inconsolata]${current_usage%?}[/FONT][/COLOR][COLOR=#333333][FONT=Inconsolata] -ge [/FONT][/COLOR][COLOR=#008080][FONT=Inconsolata]${max_usage%?}[/FONT][/COLOR][COLOR=#333333][FONT=Inconsolata] ];[/FONT][/COLOR]
```

I've used it with and without the %? and I know that the %? seems to make the **if** statement ignore the % for the sake of integer comparison but I don't know why...

Full script here: [http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/](http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/)
Specifically Version 1

---

### Post by Vaphell on 2014-10-13
*${var%pattern}* returns the value of $var with *pattern *trimmed off the right side (# does the same on the left). %is the operator here, followed by pattern.
? is just 'any character', so in this particular case **%?** removes the % sign from the usage value in order to compare the numbers.

---

