---
title: "Panel Clock Format?"
date: 2014-09-01
forum: General Help
---

### Post by 2CV67 on 2014-09-01
In System Settings > Language Support > Regional Formats, I have selected 'English (Ireland)' & I have clicked on 'Apply System-Wide'.

The example date on that window says Mon 01 Sep 2014 etc.

But my Panel Clock insists on giving me Mon Sep 1 2014 etc.

Now I admit this is not the end of the world, but it would be nice if I could find how to get Mon 1 Sep 2014.

Possible?

Thanks!

---

### Post by Dennis N on 2014-09-01
The panel clock may accept a custom format in its properties dialog.

Mon 01 Sep 10:45 AM
```
%a %d %b %I:%M %p
```

Mon 01 Sep 2014
```
%a %d %b %Y
```

For codes, look here under Date Format:

[http://www.computerhope.com/unix/udate.htm](http://www.computerhope.com/unix/udate.htm)

---

### Post by 2CV67 on 2014-09-01
> **Dennis N said:**
> The panel clock may accept a custom format in its properties dialog.

Yes...
Now if I could just find the properties dialog.  :oops:

---

### Post by 2CV67 on 2014-09-03
OK - found it!

I had to install dconf-tools (in Synapt).
Then open dconf Editor > com > canonical > indicator > datetime.
time-format > custom.
custom-time-format > "%a_%e_%b_%Y___%R__".

This gives me "Wed  3 Sep 2014   20:15  "
Personally, I find that much easier to read at a glance than the default "Wed Sep 3 2014 20:15".
But you don't have to agree!

"SOLVED" for me! :)

[I]EDIT: I have some double- & triple-spaces in my format, but the forum doesn't show them, so I show tham as underlines_.
There are no underlines in the real format.[/I]

---

