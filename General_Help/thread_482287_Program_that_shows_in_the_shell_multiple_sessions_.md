---
title: "Program that shows in the shell multiple sessions of other shell(like with tabs)"
date: 2007-06-23
forum: General Help
---

### Post by Garret88 on 2007-06-23
I found this screenshot:

[http://servut.us/Mozz/kuvat/screenie.png]("http://servut.us/Mozz/kuvat/screenie.png") 

How does this mate do?

I know screen but i think that it can't show also the tabs(and the possibility to create new sessions).

---

### Post by eggdeng on 2007-06-23
Not sure if I understand you right but you can open tabs in the terminal simply by going to the File menu, then New Tab.

---

### Post by Garret88 on 2007-06-23
> **eggdeng said:**
> Not sure if I understand you right but you can open tabs in the terminal simply by going to the File menu, then New Tab.

Ok i know this but you can do this with terminal like gnome-terminal or konsolle(of KDE). But i use urxvt(because i am on openbox).

In that screen you can see that tabs are inside the shell and not made with gnome-terminal or konsolle

---

### Post by wimac on 2007-06-23
I think he is using screen I use a simalar setup i have this in my .screenrc:

caption always "%?%F%{-b bc}%:%{-b bb}%?%C|%D|%M %d|%H%?%F%{+u wb}%? %L=%-Lw%45>%{+b by}%n%f* %t%{-}%+Lw%-0<" 

this puts a staus bar across the bottom you could use it to get ya started so you can modifiy it to do what you want.

---

