---
title: "Where is the installed application?"
date: 2013-01-09
forum: General Help
---

### Post by ruwan2 on 2013-01-09
Hi,
I install a TI DSP software. After the installation, I do not know where it is now. I have searched it at "Dash Home", it does not show up. In the installation, it does not ask me where to store the application. Could you help me on finding the installed software?

The second question is about the GUI file folder display. I do not find a menu control to the display format, such as small icon, detail etc. 

Thanks.

---

### Post by adityamagadi on 2013-01-09
check under /bin

---

### Post by JRV on 2013-01-09
Use the which command to locate the program:
Example:
```

which firefox

```
returns "/usr/bin/firefox".

---

### Post by jerome1232 on 2013-01-09
How did you install this software?

As for the second question, open nautilus (that's your file browser) hover your mouse over the top panel towards the left side of your screen, the menu items will appear, select view, you can find the items you want there.

---

### Post by amahi on 2013-01-09
hi

[COLOR="DarkOrange"]first question[/COLOR] : (whereis command)
example:
```
whereis firefox
```

( The whereis command is used to locate the binary, the source code and the online manual page for any specified program )

more:
[http://linux.about.com/library/cmd/blcmdl1_whereis.htm]("http://linux.about.com/library/cmd/blcmdl1_whereis.htm")


[COLOR="SeaGreen"]second question[/COLOR]:

go to home folder and in menu:
Edit>Preferences

changes the size(65% is good  )  :)

---

### Post by grahammechanical on 2013-01-09
I tried to find out what you meant by this

>  TI DSP software.

I ended up here

[http://www.ti.com/lsds/ti/tools-software/linux.page]("http://www.ti.com/lsds/ti/tools-software/linux.page")

Did you download one of these files? Please explain the installation process that you followed.

Regards.

---

