---
title: "Can adobe be set as default pdf reader?"
date: 2013-11-20
forum: General Help
---

### Post by huxley2 on 2013-11-20
Hi, everybody

I have adobe reader IX installed but I can't directly open any pdf files with it. When I right click a pdf > open with > show other applications, adobe isn't listed as an option.

I can open adobe reader and go into File > open... and select a pdf but it's getting annoying. At the moment pdf default reader is the ubuntu Document Reader programme which is o.k for quick reads but for study I need adobe reader. 

Does anyone know how I can set adobe as default?

Thanks

---

### Post by ccmiller12 on 2013-11-20
What version of Ubuntu are you using, and what platforms (Lubtunu, Kubuntu, ect..). If it is Ubuntu, open system settings, in the activities view, then go to system info. There you can select Default applications. See this link for more options: [http://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/](http://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/)

---

### Post by david98 on 2013-11-20
System settings default application's select it there

opps did not see previous post sorry):P

---

### Post by huxley2 on 2013-11-21
I'm using ubuntu 13.10. I tried sorting it via system settings but there wasn't an option for opening pdf files, the only options were for > Web, Mail, Calendar, Music,Video and photo's

---

### Post by philinux on 2013-11-21
To set any default.

Right click on file, properties, open with, choose app click set as default button.

---

### Post by huxley2 on 2013-11-21
Problem solved.

I removed it in terminal with:
```
sudo apt-get remove acroread
```

Then re-installed acroread and adobe was automatically set as default pdf reader

---

