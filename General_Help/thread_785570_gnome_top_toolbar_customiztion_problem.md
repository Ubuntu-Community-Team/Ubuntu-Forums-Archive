---
title: "gnome top toolbar customiztion problem"
date: 2008-05-07
forum: General Help
---

### Post by boxer1028 on 2008-05-07
I am a newbie to Ubuntu Hardy and I wanted to experiment with customizing my desktop. So, naturally the first thing I did was look for tutorials that would teach me how to do so. I found a specific tutorial on Softpedia that look thorough. I followed the steps and about half way through I came to a step that told the reader to delete the *gnome-panel* entry. I followed the steps and delete it and to my surprise the top and bottom tool bars disappeared. I have hunted all over the internet for documentation on how to reinstall the [I]gnome-panel[/I but I cant seem to find anything or even, do it on my own.

I have pasted the tutorial link below. Under the section titled 'Bonus Tweaks' tip number 3 is where i executed this step and the tool bars disappeared on me.

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

---

### Post by mano cazalet on 2008-05-07
first I would try to uncheck the "Automatically remember running applications when logging out" option and open terminal 
```
 killall gnome-panel
```

to see if that restarts the panels

---

### Post by boxer1028 on 2008-05-08
Nothing, The problem occurred when I deleted the gnome-panel under (sessions/current sessions) tab. 

I cant seem to get it back. Ive been working on this for two days. Can anyone help?

---

### Post by FuturePilot on 2008-05-08
Try unchecking the box that says to automatically remember running applications. I think the problem is you still have that checked and since gnome-panel isn't running, it's not starting up now.

---

### Post by boxer1028 on 2008-05-08
I have done that. I went to (session properties/session options) and I am sure I unchecked the box that says "Automatically remember running application when logging out". 

Under current sessions tab I deleted gnome-panel and it disappeared how can i get it back?

---

### Post by mano cazalet on 2008-05-08
and what happens if you try to start it from terminal:

gnome-panel

---

### Post by boxer1028 on 2008-05-08
Well, that was easy. All i did was open the terminal and typed 'gnome-panel'. 

Now that I fixed that, I would like to remove the bottom gnome-panel and put my opened windows on the top panel. Where can I start?

Thanks guys!

---

### Post by FuturePilot on 2008-05-08
Right click on the top panel and select Add to Panel. Then add the Window List applet.

---

