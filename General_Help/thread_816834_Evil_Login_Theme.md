---
title: "Evil Login Theme"
date: 2008-06-03
forum: General Help
---

### Post by MetalManiacMat on 2008-06-03
Just a few minutes ago I thought I would change my login theme, so I went and downloaded one from gnome-look, I think Its called nUbuntu. Anyway now I cannot login, when I reset all i get is a loading cursor with nothing to fill out (like username or password) can I revert to my old login screen using the terminal?

---

### Post by Bubba64 on 2008-06-03
> **MetalManiacMat said:**
> Just a few minutes ago I thought I would change my login theme, so I went and downloaded one from gnome-look, I think Its called nUbuntu. Anyway now I cannot login, when I reset all i get is a loading cursor with nothing to fill out (like username or password) can I revert to my old login screen using the terminal?

Is the choice box in the left corner, and have you tried safe gnome. I don't know f you installed this with the terminal you may be able to remove it that way be careful.

---

### Post by MetalManiacMat on 2008-06-03
and how would i go about using in safe mode? where i shoudl see th login screen its just black with a loading cursor.

---

### Post by Bubba64 on 2008-06-03
[QUOTE=MetalManiacMat;5104507]and how would i go about using in safe mode? where i shoudl see th login screen its just black with a loading cursor.[/QUOTE

I am sure I don't have the answer for you, but it sounded like you could bring up the terminal the safe mode is in the same drop down but I don't remember the login procedure for the safe mode. Have you tried to remove nUbuntu with the terminal. That is what I would try but I have nothing to lose on my computers, so that is why I say be careful.

---

### Post by MetalManiacMat on 2008-06-03
this is pretty much a fresh install so i have nothign important. but i would rather solve the problem. i have no clue on how to remove nUbuntu. I think changing my theme to the defualt Human Login Theme would be a better solution but i dont know how. anyone have any clue on this?

---

### Post by danwood76 on 2008-06-03
The login window config file is located:
/etc/gdm/gdm.conf
(I think)

So go to the terminal:
Ctrl+Alt+F1
Login and type:
```

sudo nano /etc/gdm/gdm.conf

```
Then use the nano search function and search for
```

GraphicalTheme

```
To get the default ubuntu one change it to:
```

GraphicalTheme=Human

```

---

### Post by MetalManiacMat on 2008-06-03
ill try it out in a couple of minutes, thank you

---

### Post by MetalManiacMat on 2008-06-03
it seems it was already set to human. could i edit a file to somehow skip the login screen and logon automatically?

---

### Post by danwood76 on 2008-06-03
Well here is an extract from a sample gdm.conf I found on the net:
```

# These two keys are for the themed greeter (gdmgreeter). Circles is the
# standard shipped theme. If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true. Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

```
This is the default ubuntu config for that part.
You should check that the GraphicalThemeDir is set.

You could try changing the theme to be one of the others like circles.

To do an auto login look for the section like this:
```

[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

```
and change the last two entries above like so:
```

AutomaticLoginEnable=true
AutomaticLogin=**USERNAME**

```
Obviosuly replacing with your username.

---

### Post by MetalManiacMat on 2008-06-03
thanks alot danwood76, but after alot of messing about i think it all due to a bad video driver. i ended up loggin in and compiz was not working (which was weird) then a notification popped up telling me my restricted driver was not in use. i enabled it and reset. but i am having the same problem. im not very good with driver issues so i think it would be much easier if i just reinstalled Ubuntu. Thanks alot for your help

---

### Post by daleus on 2008-06-03
when it gets to the black screen, push ctrl + alt + backspace, then ctrl + alt + f1 (or any of the f keys up to f7)

login into the CLI, and then once logged in do "startx" will allow you to login and will bypass the login screen (as you already logged in).

However, this won't help for bad drivers or anything.

---

### Post by MetalManiacMat on 2008-06-04
> **daleus said:**
> when it gets to the black screen, push ctrl + alt + backspace, then ctrl + alt + f1 (or any of the f keys up to f7)

login into the CLI, and then once logged in do "startx" will allow you to login and will bypass the login screen (as you already logged in).

However, this won't help for bad drivers or anything.

I'll have to remember that for "next time". In the end I ended up just reinstalling Ubuntu. Now all I have to do is install as 124 updates :S

---

### Post by gwenn on 2008-08-21
> **MetalManiacMat said:**
> Just a few minutes ago I thought I would change my login theme, so I went and downloaded one from gnome-look, I think Its called nUbuntu. Anyway now I cannot login, when I reset all i get is a loading cursor with nothing to fill out (like username or password) can I revert to my old login screen using the terminal?

I found now your post and and I suppose that is just too late for you but...
If you use the root terminal ,emacs,Ctrl-x Ctrl-f,open file 
/etc/gdm/gdm.conf,the you find 
GraphicalThemeRand=false,change
GraphicalThemeRand=true,and that must change the theme randomly in the directory.Obviously you must have copied the theme you want in this directory with cp -r(recursively).Then,whith a litle patience you can test 
if the theme you downloaded works and then you can fix it as a default theme.Mine runs randomly

---

