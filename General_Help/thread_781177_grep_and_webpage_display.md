---
title: "grep and webpage display"
date: 2008-05-04
forum: General Help
---

### Post by meg23 on 2008-05-04
I was wondering if it is possible to use the grep command to find a 

field in a terminal based web page and display it. If this is 

possible, what kind of script would I need?

---

### Post by Monicker on 2008-05-04
Not quite sure what you mean.  Lynx has optioons to display the content and source of a web site to standard output.  You could parse that.  Are you talking about a specific form field?

---

### Post by meg23 on 2008-05-04
Here is the problem in a nutshell. I need to get sunset times from 

[www.myzmanim.com.I](www.myzmanim.com.I) want to schedule a script in crontab to display 

the sunset time in the terminal. I figured it would be possible to 

use something like the grep command to search the page and cut out 

everything else in eLinks (or lynx), just displaying sunset.

---

### Post by Monicker on 2008-05-04
> **meg23 said:**
> Here is the problem in a nutshell. I need to get sunset times from 

[www.myzmanim.com.I](www.myzmanim.com.I) want to schedule a script in crontab to display 

the sunset time in the terminal. I figured it would be possible to 

use something like the grep command to search the page and cut out 

everything else in eLinks (or lynx), just displaying sunset.

Interesting. You have to specify a location.  And the source for the results pages is pretty messy.  :)


This worked for me:

```
lynx -dump http://www.myzmanim.com/day.aspx?vars=US62215|grep "At sea level"|awk '{print $6}'|tail -1
```

I just picked a random US zip code for the vars variable.  If they change the layout of the page sufficiently in the future, the above line won't work.  It could just be put in a bash script.

---

### Post by frenchn00b on 2008-05-04
> **meg23 said:**
> I was wondering if it is possible to use the grep command to find a 

field in a terminal based web page and display it. If this is 

possible, what kind of script would I need?

```
elinks url > page.htm ; less page.htm   # press /word2search
```
or 
```
elinks url > page.htm ; cat page.htm | grep word2search   # press /word2search
```

---

### Post by meg23 on 2008-05-04
Thanks, those suggestions worked perfectly.

---

