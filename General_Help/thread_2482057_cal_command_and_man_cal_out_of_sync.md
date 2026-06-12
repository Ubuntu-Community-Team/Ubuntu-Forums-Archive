---
title: "cal command and man cal out of sync"
date: 2022-12-17
forum: General Help
---

### Post by Skaperen on 2022-12-17
many options in "*man cal*" do not work in "*cal*".  is this an "*ubuntu*" issue or "*xubuntu*"?  does "*cal -e*" work for you?

---

### Post by TheFu on 2022-12-17
```
$ ncal -e 
04/17/2022

$ ncal -e 2023
04/09/2023

```

Only ncal supports the -e option according the my local manpages.
What am I missing?

```

SYNOPSIS
     cal [-31jy] [-A number] [-B number] [-d yyyy-mm] [[month] year]
     cal [-31j] [-A number] [-B number] [-d yyyy-mm] -m month [year]
     ncal [-C] [-31jy] [-A number] [-B number] [-d yyyy-mm] [[month] year]
     ncal [-C] [-31j] [-A number] [-B number] [-d yyyy-mm] -m month [year]
     ncal [-31bhjJpwySM] [-A number] [-B number] [-H yyyy-mm-dd] [-d yyyy-mm]
         [-s country_code] [[month] year]
    ** ncal [-31bhJeoSM] [-A number] [-B number] [-d yyyy-mm] [year]**

```
I've 'bold'ed the only like with the -e option.

Hopefully, you weren't using web-based manpages. Those are never the same version we have installed on our systems.

---

### Post by Skaperen on 2022-12-18
my bad.  out of habit i have always jumped my look down to the more detailed option description.  that has worked fine for me for years.  that was my error skipping over the [FONT=courier new]SYNOPSIS[/FONT].  so now and the future i need to re-look when the quick-look method runs into problems.  thank you for pointing this out without the games i often get on another web site (to remain unnamed).

i was using the [FONT=courier new]man[/FONT] command in a bash shell with a [FONT=courier new]PATH[/FONT] that got me to [FONT=courier new]/bin/man[/FONT] which really is [FONT=courier new]/usr/bin/man[/FONT] via the [FONT=courier new]/bin[/FONT] -> [FONT=courier new]usr/bin[/FONT] symlink that 20.04 gave me.

---

### Post by TheFu on 2022-12-19
Actually, my initial thought was the same as yours.  Then I looked more closely.  The manpage really needs to differentiate, in the details, which command the option that aren't shared with both work.

I'd never heard of ncal. Seems to have some options I could use, so thanks for asking the question. I learned more too!

---

