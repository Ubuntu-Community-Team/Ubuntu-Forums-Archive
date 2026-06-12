---
title: "Making SeaMonkey default browser in KDE"
date: 2007-08-16
forum: General Help
---

### Post by Old *ix Geek on 2007-08-16
I'm sure I'm missing something really obvious, but I'm stumped.  How do I set SeaMonkey as my default browser in KDE?

Let me clarify: When I installed SeaMonkey, I **definitely** selected its choice to make it my default browser.  However, when I select links from certain applications, Konqueror fires up.  For example, I installed Google Desktop last night, and whenever I do anything in it [such as "Show Home Page" on its right-click menu], it loads in Konqueror.

I've searched ALL of the options in SeaMonkey's preferences but couldn't find a "make SeaMonkey my default browser" choice.  I've searched about:config looking for anything that resembled "default browser" but found nothing.

When I tried ```
sudo update-alternatives --config x-www-browser
``` it had three choices: Firefox, Konqueror, and Epiphany, with Konqueror set as default.  Since SeaMonkey wasn't LISTED, I couldn't select it.

Any ideas?  Again, I'm using KDE so please avoid Gnome solutions.  Thanks!

---

### Post by Old *ix Geek on 2007-08-17
No ideas, eh?  ](*,)

---

### Post by HermanAB on 2007-08-17
Uhh, you have to set that in KDE, since it is a function of the calling application, not the target  application.

---

### Post by FluffyBunny on 2007-08-23
I did the same thing just the other day. In kopete any link that was sent to me would open in Konqueror so I went and changed it.

Go into system settings, go into default applications
in default applications there is a web browser on the list, 
in that option you can specify which browser you want by command

Hope this helps if you didn't already figure it out
Fluffy Bunny

---

