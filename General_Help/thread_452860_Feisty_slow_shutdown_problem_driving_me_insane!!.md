---
title: "Feisty slow shutdown problem driving me insane!!"
date: 2007-05-23
forum: General Help
---

### Post by feister on 2007-05-23
Ok, here is the deal. Everything was working out-of-the-box initially. I started installing a few apps and got even wireless got to work. Then gave it a shot....enter Beryl...etc.etc... but out of the clear blue sky my shutdown button doesn't work (click on it and nothing happens) repeat it a few more then desktop freezes. Another problem, seems related, is that whenever I  *gksudo gedit* on the terminal the the file never opens for the next....like 5 minutes?? same thing when it shuts down....you have to wait 5 or so minutes (i found out by WAITING  ). Shall I ditch gnome? 

HELP!!!!

---

### Post by rax_m on 2007-05-24
Have you tried checking what may be using up your resources by running "top" from a terminal?

Also are you running Beryl or anything else? 

Could it be you've installed some services that start up and make the machine take ages to shutdown?

On a side note.. I've moved to XFCE and found it to be faster and a bit more stable (with Beryl) at a very slight loss of desktop functionality.

---

### Post by feister on 2007-05-24
Thank you for help

> **rax_m said:**
> Have you tried checking what may be using up your resources by running "top" from a terminal?



Yes, actually this is the first thing I did. I have a few apps,like Amarok etc.., that I don't think were affecting my resources, but I  terminated them anyway and tried to see the difference but It still takes 5min to shutdown. I had to do it from the terminal using shutdown -r now command, which seems to work (with some weird flash image during restarting)
> 

Also are you running Beryl or anything else? 



Beryl, I did installed Beryl to play around with cool 3D stuff and show off my FF 7.04 Ubuntu desktop to my roommates and try,for 1000 time, to persuade them join freedom from  WinDOZ. Beryl actually worked but with lots of googling for my ATI to get it going. and If you ask me the exact steps how I got it to work, I confess that I have no clue right now. Soooooooo I thought I should remove it since this stuff happened after installing apps. But still that doesn't seem to solve my damn 5min wait for the shutdown button to actually bring the shutdown/suspend..etc menu. Oh btw its not just shutdown, when I want to edit something using gedit as a root it takes 5min to actually open. but when i use just gedit without gksudo it works right away. came to think of it, could it be some issue with root? 

> 

Could it be you've installed some services that start up and make the machine take ages to shutdown?

On a side note.. I've moved to XFCE and found it to be faster and a bit more stable (with Beryl) at a very slight loss of desktop functionality.

I haven't tried XFCE but I changed desktop from gnome to kde and still the problem is there, but it actually gave me a chance to try out kde ;). 

what gives?

---

