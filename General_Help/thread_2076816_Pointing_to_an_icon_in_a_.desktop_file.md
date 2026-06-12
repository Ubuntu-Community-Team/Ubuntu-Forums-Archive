---
title: "Pointing to an icon in a .desktop file?"
date: 2012-10-27
forum: General Help
---

### Post by kenmore on 2012-10-27
So I just installed Sublime Text 2 and I created a .desktop file so I can see it in the Gnome 3 Activies launcher, have a desktop icon, etc

But I can't get the icon to display properly.
In the Sublime Text 2 directory there is an Icon folder that contains some icons. In my .desktop file I like to one like this:
```
Icon=/usr/local/Sublime\ Text\ 2/Icon/128x128/sublime_text.png
```

But it doesn't work. I get a blank icon with only the name below it. I've never created a desktop file before so bare with me =D

Thanks.

Edit:Solved.... apparently.
So after Googling and Googling I came across an example and it had pretty much the same thing I had but without the backslashes. I thought you had to escape the spaces but apparently you don't =S
Now it's working.

---

