---
title: "Startup problem"
date: 2015-02-11
forum: General Help
---

### Post by Rui_Garcia on 2015-02-11
Greetings,
So I recently installed kicad on lubuntu, there are a few cvpcb libraries missing, but my main problem is when I turn on my computer, after putting the password it shows a warning telling me of the missing libraries and  cvpcb is running. The desktop environment doesn't show up until I kill cvpcb.
I dont understand much about linux but I took a look to the autostart programs folder and I dont see Cvpcv there.

Thank you,
Rui

---

### Post by v3.xx on 2015-02-11
I just installed kicad to lubuntu 14.04 (I assume you are running the same).  System boots and program runs without issue.  Nothing about missing libraries or cvpcb.

How did you install it?

Open it using the terminal and look for errors.
```
kicad
```

---

### Post by Rui_Garcia on 2015-02-12
I used the helper script to install kicad.
I forgot to say that now I dont have any problems with the missing libraries and no errors when opening it using the terminal.
My problem is that Cvpcb runs automatically when I startup de computer and creates a new project called essai.pro.The desktop enviroment doesn't show up until closing cvpcb, all menus and files, cant open terminal before closing cvpcb.

I used bootchart to see when cvpcb was running and tried to remove with update-rc.d but it's still the same.

[IMG]http://i62.tinypic.com/2yzeyb7.png[/IMG]

[IMG]http://i61.tinypic.com/1zz5h8y.png[/IMG]

---

### Post by v3.xx on 2015-02-12
> I used the helper script to install kicad.
What helper script?  All I did to install kicad was use one command.
```
sudo apt-get install kicad
```
Which I would think yields the same results as using the software center.

Maybe reinstalling kicad would do some good.
```
sudo apt-get install --reinstall kicad
```
Also please post:
```
apt-cache policy kicad
```

And check this button for posting pictures :)
[ATTACH=CONFIG]259934[/ATTACH]

---

