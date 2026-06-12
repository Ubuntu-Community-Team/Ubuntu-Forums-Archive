---
title: "xfce4-genmon-plugin colored text/bars"
date: 2012-10-17
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-17
[http://goodies.xfce.org/projects/panel-plugins/xfce4-genmon-plugin#recent_releases](http://goodies.xfce.org/projects/panel-plugins/xfce4-genmon-plugin#recent_releases)
> Introduces new markup for colored and styled textwhere can i find this markup?
i would like to apply color to my script's bar
```
#!/bin/bash
GPU=`nvidia-smi | head -9 | tail -1 | sed 's/[^0-9 ]//g' | awk '{print $2"% "$3"MB "$4"MB"}'`
USE=`echo $GPU | awk '{print $1}'`
MEM=`echo $GPU | awk '{print $2" of "$3" used"}'`
echo "<bar>$USE</bar><tool>Memory: $MEM</tool>"
```

---

### Post by papibe on 2012-10-18
Thread moved to **General Help**.

---

### Post by Toz on 2012-10-18
Have a look at the "New Features" section here: [https://github.com/dnschneid/xfce4-genmon-plugin]("https://github.com/dnschneid/xfce4-genmon-plugin"). It demonstrates xml coding to achieve this. Using this, I was able to change the colour of the man genmon text, but was unable to change anything in the tooltip.

---

### Post by pqwoerituytrueiwoq on 2012-10-19
can you post the code you used, the example xml code is not working for me...
running xubuntu 12.10

---

### Post by Toz on 2012-10-19
I was certain I did this with xml codes earlier, but I can't repeat it now. 

I _can_ change some things using Pango markups ([http://developer.gnome.org/pango/stable/PangoMarkupFormat.html]("http://developer.gnome.org/pango/stable/PangoMarkupFormat.html")) using a script like:
```
#!/bin/bash

echo "<txt><span weight=\"bold\" fgcolor=\"Red\">Test</span></txt><tool>Tester</tool>"

```

I'll see if I can get the xml markups to work again.

---

### Post by pqwoerituytrueiwoq on 2012-10-19
thanks, this will be nice for my sensor applets

---

