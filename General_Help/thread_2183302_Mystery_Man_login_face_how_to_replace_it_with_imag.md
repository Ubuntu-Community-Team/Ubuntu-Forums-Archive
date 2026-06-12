---
title: "Mystery Man login face: how to replace it with image icon ?"
date: 2013-10-24
forum: General Help
---

### Post by Coder88 on 2013-10-24
When I log out of my desktop xubuntu 13.10 I am presented with the login manager that shows my username and a faceless 'mystery man' icon that is just a faceless white head and shoulders silhouette against a background. That looks very tacky and I would like to replace that aesthetically poor image with something more graphically pleasing. can anybody help me figure out where that image is in my filesystem so I can find it and replace it as root with another image?

---

### Post by CatKiller on 2013-10-24
You could randomly replace system files... or you could just assign an image for your account like a sensible person. Historically that was done by putting an image as ~/.face, but Gnome ignores that in favour of using the User Accounts settings. I have no idea how Xfce handles it, but it's likely to be similar.

---

### Post by coldraven on 2013-10-24
Although I'm running Ubuntu I thought haha! that must be easy, I'll just go to user accounts. Wrong!
So now the wait for some genius to come along and put us out of our misery :(

---

### Post by Coder88 on 2013-10-24
> **CatKiller said:**
> You could randomly replace system files... or you could just assign an image for your account like a sensible person. Historically that was done by putting an image as ~/.face, but Gnome ignores that in favour of using the User Accounts settings. I have no idea how Xfce handles it, but it's likely to be similar.


Well the problem is there is no configuration GUI utility in xubuntu (nor apparently in Ubuntu) to simply "assign an image for your account like a sensible person." Nothing in the user accounts settings GUI to assign a face image.  ~/.face would be a hidden file, but what type-- that is not an image file, so what would one put in .face?

---

### Post by jerome1232 on 2013-10-24
It really is that easy in

Ubuntu, Cog -> System Settings -> User Accounts -> next to your name in the right hand pane click the tile there, browse for a picture etc...


Xubuntu, I'm not sure.... the users and groups utility doesn't seem to allow it.


edit: My Xubuntu is on a system that has Ubuntu installed as well, so that user and groups utility *may* not be part of a default Xubuntu install.

---

### Post by Coder88 on 2013-10-24
> **jerome1232 said:**
> It really is that easy in...
Xubuntu, System Menu -> System Settings, -> Users and Groups - click the tile next to your name, browse for a picture etc...

It would be that easy if there was a tile next to my name in the Users/Groups config panel; but there is not.

> **jerome1232 said:**
> edit: My Xubuntu is on a system that has Ubuntu installed as well, so that user and groups utility *may* not be part of a default Xubuntu install.

There is a user/groups utility in xubuntu, but not with any faces/picture icon to click and change. What I am wondering is where the heck is that mystery man crappy looking default faces icon-- if I can find it I can just replace it with something easier on the eyes.

---

### Post by jerome1232 on 2013-10-24
You caught me before an edit, the Xubuntu interface looks very similar to Ubuntu's but when I tried to click the spot where the tile is in Ubuntu's users account tool, nothing. Supposedly you can place a 92x72 png in ~/.faces but there really ought to be a gui way to accomplish this...

---

### Post by Dennis N on 2013-10-24
The Lubuntu icon in the greeter can be changed, but so far I've never seen a way to change it in Xubuntu. I will be interested in Samuel_Peters solution!

---

### Post by Toz on 2013-10-24
Yes, for Xubuntu 13.10, put an image in your home directory called **.face** or **.face.icon**. The size of the image doesn't seem to matter. Xfce will eventually have a profile editor, I believe there is one in git, but it doesn't appear to have made it into the 13.10 release.

You can test it without logging out by running:
```
lightdm --test-mode
```
...in a terminal window (Note: the package **xserver-xephyr** needs to be installed).

[[img]http://en.zimagez.com/miniature/lightdm.png[/img]](http://en.zimagez.com/zimage/lightdm.php)

---

### Post by Coder88 on 2013-10-24
> **Samuel_Peters said:**
> I managed to do it but I forgot. I'll have a look tomorrow!

That would be awesome. Please do come back here and share the solution if you remember.

I recall I had to choose between GDM and LGDM (light GDM) when installing xubuntu, I chose LGDM. I just installed GDM and again had that choice, I chose GDM. But it is the same issue, exact same mystery man face that I can not change in any Users and Groups settings, etc. (no difference).  geesh, then I logout and see that mystery man login screen and I go away for an hour and come back and it is gone, instead a giant wallpaper and giant digital clock with the time and no clue how to get back to the login-- turns out i had to scroll my mouse wheel to get back to the login; wtf are the programmers thinking on this sort of sheeeet, geesh, make it freaking simple, i mean ANY keypress should have removed that screensaver instead of requiring a mousewheel scroll. That is the thing about Linux, it is always some weird sheeeet like this or that, and hey I am a geek of many decades. If linux is to get more mainstream I think the developers of the distros and GUIs need to bring NON-geeks on board for testing of what is intuitive or not, what is needed, etc.

---

### Post by CatKiller on 2013-10-24
That's because that's the default image for a user that hasn't specified their face. It'll be the same whichever login manager you use. That's why the icon used is a user without a face.

You haven't said that you've assigned a ~/.face, so I'm assuming you haven't. It will need to be readable by the LightDM (or GDM if you're using that now) user, which probably means Execute for Others on ~ and Read for Others on ~.face.

There's an alternative method of configuration detailed [here]("https://wiki.archlinux.org/index.php/LightDM#Changing_your_avatar").

---

### Post by Dennis N on 2013-10-24
Thanks guys. I used the Account service method and it works. I made a 96x96 PNG version of my avatar and used that for the logo. I followed the instructions on the Arch Wiki link in CatKiller's post. 

Comments:

My logo is just named avatar.png and it works fine (no .face or .face.icon was necessary). 

I needed to include the name the image file in the **Icon=** statement in **/var/lib/AccountsService/users/<username>** or it didn't work. That is, in my case:

**Icon=/var/lib/AccountsService/icons/dn/avatar.png**

I did this in Xubuntu 13.04, not 13.10, so it works there too.

Added:

In Lubuntu 13.10 and in 13.04: also worked by adding login image to home folder and naming it **.face** -- Much easier!

---

