---
title: "Issues with Beryl"
date: 2006-10-26
forum: General Help
---

### Post by ThrobbingBrain66 on 2006-10-26
Hey guys.  So a couple weeks back, I installed compiz for the first time and am very happy with it.  I was playing around and installed Beryl this morning and am having some issues.  I have an Intel card and used this guide to install:

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

Once I get everything installed, I log out and back in again, type beryl-manager in the terminal and everything is great.  So then I add beryl-manager to my startup list.  However, when I restart my computer after this Beryl begins to load and then my window borders start to flicker.  The only thing that fixes this is to right-click the beryl icon in the notification and close it...then everything is fine and Beryl works.  Anyone have experience with this?  Thanks for the help.

btw, I'm using Edgy and Compiz works flawlessly, if that makes any difference.

---

### Post by tronica on 2006-10-26
i've heard this happening to alot of people, i would search the beryl forums

[http://forum.beryl-project.org]("http://forum.beryl-project.org")

---

### Post by orb9220 on 2006-10-26
You might try changing the startup. And give beryl a low number than gnome-manger. This issue seemed to go away having beryl load before gnome.

Go to sessions>current sessions tab and change order. My beryl is 39 now and all my gnome stuff is in 40's-50's.

---

### Post by Perfect Storm on 2006-10-26
Another way - Set in beryl Manager to use Metacity before you logout and when you log in go back and switch beryl on. I know it seems a bit annoying my way, but it's one of the solution.

---

### Post by ThrobbingBrain66 on 2006-10-26
thanks, ill give that a try

---

### Post by ThrobbingBrain66 on 2006-10-26
> **orb9220 said:**
> You might try changing the startup. And give beryl a low number than gnome-manger. This issue seemed to go away having beryl load before gnome.

Go to sessions>current sessions tab and change order. My beryl is 39 now and all my gnome stuff is in 40's-50's.

Here is an odd problem.  I tried setting beryl to 39 as you suggested however, the change never stays permanent.  as soon as i log back in, it changes back to 50.

---

### Post by ThrobbingBrain66 on 2006-10-26
> **Artificial Intelligence said:**
> Another way - Set in beryl Manager to use Metacity before you logout and when you log in go back and switch beryl on. I know it seems a bit annoying my way, but it's one of the solution.

thanks for the suggestion.  that does seem to be a slight hassle though.  if that's the case, ill just go back to compiz until beryl has had some time to mature.

---

### Post by ThrobbingBrain66 on 2006-10-26
seems i was able to fix this by adding 
```
emerald --replace
```
to the startp programs along with beryl-manager.

i guess id still like to know why my changes to startup priority won't save.

thanks for all the help

---

### Post by BdON003 on 2006-10-29
> **orb9220 said:**
> You might try changing the startup. And give beryl a low number than gnome-manger. This issue seemed to go away having beryl load before gnome.

Go to sessions>current sessions tab and change order. My beryl is 39 now and all my gnome stuff is in 40's-50's.
Thanks, that worked great for me

---

### Post by ronmarley1 on 2006-10-29
> **ThrobbingBrain66 said:**
> seems i was able to fix this by adding 
```
emerald --replace
```
to the startp programs along with beryl-manager.

i guess id still like to know why my changes to startup priority won't save.

thanks for all the help
This fix worked for me, however, I do not need to add the --replace modifier.  Additionally, with the latest SVN of beryl, this issue is fixed.

---

