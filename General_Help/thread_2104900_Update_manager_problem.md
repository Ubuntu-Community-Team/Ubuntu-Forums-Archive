---
title: "Update manager problem"
date: 2013-01-14
forum: General Help
---

### Post by Zirts on 2013-01-14
Hi,

When I open up my update manager or do a sudo apt-get update in terminal, it starts do download a lot of data instead of just checking for what needs to be downloaded.

I mean like 100mb's of data downloaded when i start it up and then when it's all done I get the screen atlast where it shows that I need this and this package downloded. So if I install them and everything is up-to date and I start the update manager again the same thing starts over again.

This does not seem normal at all, downloading should happen when I press to update not check for them..

What can be wrong here?

---

### Post by d4m1r on 2013-01-14
What version of Ubuntu are you running? What kind of internet connection do you have?

If it is 10.10 as you profile suggests, might be downloading a new version of Ubuntu because yours is no longer supported?

---

### Post by ibjsb4 on 2013-01-14
Update does just what it says, updates your package manager.  At the end of your terminal update if you with to install you must ..

```
sudo apt-get upgrade
```

Then it gets installed.

---

### Post by Zirts on 2013-01-15
Well my connection is 1Mbit/s so it kinda bothers me if it does this all the time. And it's 12.10 Ubuntu.

---

### Post by mcduck on 2013-01-15
How would the system know what needs to be updated, if not by downloading the up-to-date information about available package versions from the repositories? ;)

---

### Post by Zirts on 2013-01-24
Okay, so when I am having two computers next to eachother now and one is downloading huge amounts of data with ```
sudo apt-get update
``` and the other is not it is normal? 

The last one just checks what is there to download and then it's done, like it is supposed to be.

---

