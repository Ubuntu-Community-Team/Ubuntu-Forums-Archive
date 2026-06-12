---
title: "Thunderbird Callendar Dates Not Active. Curious if it's repairable?"
date: 2015-03-25
forum: General Help
---

### Post by 777funk on 2015-03-25
I'd love to get the callendar working. It works in Windows but anytime I login to Ubuntu, it's inactive. This is one of the important parts of my OS. Is there a way to bring it to life in Ubuntu? The saved callendars are there in my shared profile but no dates show and I can't add a new event. All works as it should in Windows.

---

### Post by TheFu on 2015-03-25
"Calendar"

Did you load the lightning plugin/addon [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning) and point it at a compatible CalDAV or DAV server?  Proprietary protocols may not be supported.

---

### Post by ajgreeny on 2015-03-25
Do you see the calendar but it is empty, or do you not see it at all? It's not clear from your description. 

Do you have the repository version of **xul-ext-lightning** or the **lightning** add-on direct from mozilla add-ons?  I found the former to be better and it is updated automatically along with TB when that is updated.

---

### Post by 777funk on 2015-03-25
I do have the add-on from Mozilla. It's buggy even in Windows sometimes but it's REALLY buggy (for me anyways) in Ubuntu. And I do see the Calendar but can't do anything (read or write). The saved callendar names are there but no content in the calendar's cells. It's all there in Windows.

Picture Attached. 


[B]EDIT: I just added it through the terminal:
sudo apt-get install xul-ext-lightning

and I don't see anything different. Is this in Thunderbird or a standalone?[/B]

EDIT Again: HA! Wow... I uninstalled from the Add-Ons Menu and now it works! The above apt-get install must not have taken because the add-on style install was getting in the way.

---

### Post by ajgreeny on 2015-03-26
If this is now solved, which I believe is what you are saying, please mark as such from the Thread Tools menu at the top.

I had this same problem a long time ago with the add-on from mozilla, which was solved in my case the same way as yours seems to have been.  The repository version seems to be better matched to Ubuntu's version of TB from the repos, so that is how I have been running it for many years now.

---

### Post by 777funk on 2015-04-08
It's now working in Ubuntu (which was more important) but once I installed it through > apt-get and uninstalled it through Mozilla Thunderbird > Add-Ons now it doesn't exist in Windows.

I wish there was a good way to have it work in both OS's. But for now I will not worry about Windows. So... not quite solved, but it's close enough that if no further development happens, I'm fine for the immediate.

---

