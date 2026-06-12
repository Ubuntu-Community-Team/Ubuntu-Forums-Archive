---
title: "Help with icon location"
date: 2012-12-01
forum: General Help
---

### Post by Matt12334 on 2012-12-01
I'm looking for the directory of a specific icon in the gnome shell (red circle with slash through it). My python IDE seems to be the only application that uses it, so I want to replace that icon with a new icon (which I already downloaded). Any help is very appreciated!

---

### Post by Frogs Hair on 2012-12-01
I find the Python icons in usr/share/applications. Other locations include usr/share/pixmaps and usr/share/icons.

What you are seeing indicates there is no icon for that application. I see no entry for it in the main menu which is the any easy way to change icons.

---

### Post by Cheesemill on 2012-12-01
As Frogs Hair mentioned that icon is the 'image missing' icon which is shown when there isn't a specific image for your application. It can be found at /usr/share/icons/Humanity/status/*/image-missing.svg (obviously change Humanity if you are using a different theme).

The correct way to go about solving your problem would be to create the appropriate .desktop file for your application so that it points to an existing icon.

What is the name of your Python IDE, how did you install it and how is it launched?

---

### Post by Matt12334 on 2012-12-01
> **Frogs Hair said:**
> I find the Python icons in usr/share/applications. Other locations include usr/share/pixmaps and usr/share/icons.

What you are seeing indicates there is no icon for that application. I see no entry for it in the main menu which is the any easy way to change icons.

Thanks for responding. If I attached the screenshot properly, you should see the lower icon that is a black rectangle with a crossed-out circle.  It appears to be an issue with IDLE in both Unity and Gnome, and I found the icon to replace for Unity.  However, I've been unable to fine the icon that I've described, even after searching through all of those folders.

---

### Post by Matt12334 on 2012-12-01
> **Cheesemill said:**
> As Frogs Hair mentioned that icon is the 'image missing' icon which is shown when there isn't a specific image for your application. It can be found at /usr/share/icons/Humanity/status/*/image-missing.svg (obviously change Humanity if you are using a different theme).

The correct way to go about solving your problem would be to create the appropriate .desktop file for your application so that it points to an existing icon.

What is the name of your Python IDE, how did you install it and how is it launched?

I'm using IDLE, but I have the Ubuntu Mono Dark icon set, so I'm going to check that folder soon.
Also, the blue/yellow icon is the icon for the application, and it creates an entirely new icon every time I launch it, which is pretty unusual. I installed it thought the software center, and it has always acted this way, which gets quite frustrating.

---

