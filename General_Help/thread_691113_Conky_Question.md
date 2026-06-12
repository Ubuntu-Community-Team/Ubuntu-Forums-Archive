---
title: "Conky Question"
date: 2008-02-08
forum: General Help
---

### Post by uberlube on 2008-02-08
I have been using Conky for a week now and I recently found out that it can be edited to look  differently and show additional information. I found the script that I wanted from this site here:
[http://conky.sourceforge.net/screenshots.html]("http://conky.sourceforge.net/screenshots.html")
So I opened Kedit and pasted it into there and this is where I'm stuck, I don't know how to make it into an executable. I went into the preferences from there and clicked the box that says "make executable" but when I double click on it, it just reopens the file in Kedit. Do I have to add an .exe or something similar as in windows to make this launch or am I missing some other important step entiarely?

---

### Post by seventhc on 2008-02-08
well, you can just type **conky & exit** at the terminal
to run it or <alt-F2> type **conky**
, or do you want it to run at start up??

---

### Post by uberlube on 2008-02-08
i would like it to run at startup yes. i have conky working right now but the code that they give on that site is supposed to make it look different.

---

### Post by uberlube on 2008-02-08
i found out how to get it to work through IRC thanks anyway

---

### Post by kerry_s on 2008-02-08
check out this thread-> [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)
alot of good ideas, from many conky users. :)

---

### Post by seventhc on 2008-02-08
have a look here, tons of conkyrc's w/screenshots.
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+screenshots](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+screenshots)
to have it run at start up
open an editor and put this in
```
#!/bin/bash
sleep 30 && conky;

```save it as **.conky_start.sh**
the period makes it a hidden file
the 30 is how many seconds before it starts, you can change it to whatever you want, I just give it 30 so everything else is started before it.

then in a terminal
```

chmod +x conky_start.sh
chmod 755 conky_start.sh

```then navigate to you sessions (not sure if it's the same for kde) but for me
* System>Preferences>Sessions*
click add and put this in the command box
/home/your_user_name/.conky_start.sh

---

