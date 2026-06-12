---
title: "24hr digital clock to a 12hr format"
date: 2016-04-13
forum: General Help
---

### Post by swedeman2 on 2016-04-13
Aloha,

   I just loaded Lubuntu 15.10 on my laptop and would like to change the 24hr digital clock to a 12hr format. Everything else is running fine. Got tired of microsoft trying to force me to upgrade to Windows 10.

---

### Post by deadflowr on 2016-04-13
You mean the clock in the top panel?

If so, click on it, and at the bottom should be an entry for *Time and Date Settings*.
Open and there should be a tab for clock.
In this section you should be able to toggle/select 12hr or 24hr, which ever you prefer.

---

### Post by swedeman2 on 2016-04-13
When I right click and select "Digital clock" settings, a widow pops up with a window box for Clock Format with a "%R" and another window box for Tooltip Format with a "%A %x" in it. No radio buttons.
My task bar is at the bottom like windows (default). the speaker / battery / wifi / time / shut down icons on the bottom right.

---

### Post by deadflowr on 2016-04-13
Ha, my mistake.
I missed the L in Lubuntu.

I'm adding the lubuntu prefix to the title of this thread for you.
(it should let lubuntu users find it easier)

Nevermind my earlier post, it has nothing to do with lubuntu.

---

### Post by sisco311 on 2016-04-13
"%R" means 24 hour format.  Replace it with "%r" which means 12 hour format. For a complete list of a format options you can check out the man page of the `date' terminal command:```
man date
```

If you aren't comfortable with the terminal, then you can check out the online version of the manual page: [http://manpages.ubuntu.com/manpages/raring/man1/date.1.html](http://manpages.ubuntu.com/manpages/raring/man1/date.1.html)

---

### Post by swedeman2 on 2016-04-13
Thanks Sisco311, that worked great. Going to have to learn the new xterminal codes. Kinda like the old DOS of windows. 
I really like the Lubuntu OS. Once I get comfortable with it, it's goodbye Windows.........

Thanks everyone for your input. I was surprised on how fast the response was.

---

