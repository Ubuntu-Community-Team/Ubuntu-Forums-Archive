---
title: "Adding Startup program to KDE??"
date: 2007-06-03
forum: General Help
---

### Post by ghandi69_ on 2007-06-03
I'm guessing there is no GUI method for adding a startup program to KDE (in my case... Katapult)...

I'm guessing there is a .Startup file somewhere.. but I cannot find it.  

Any help would be appreciated...

Thanks

---

### Post by SoggyCornflake on 2007-06-03
> **ghandi69_ said:**
> I'm guessing there is no GUI method for adding a startup program to KDE (in my case... Katapult)...

I'm guessing there is a .Startup file somewhere.. but I cannot find it.  

Any help would be appreciated...

Thanks

Try viewing your hidden folders.  There should be one called **kde**.  Inside it there's a folder called **Autostart.**    (/home/*YourUserName*/**.kde/Autostart**  <--- The **.** is very important.  It tells the system that you're looking for a hidden folder)
Make a link to the program you want (ie katapult).  You can do this by dragging an icon of the application into the directory and selecting the link option

The next time you log in, it should be started as you log in.

---

### Post by ghandi69_ on 2007-06-04
Worked like a charm, thanks for the help.

---

