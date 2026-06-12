---
title: "Different theme for administrative tasks?"
date: 2006-11-07
forum: General Help
---

### Post by urukrama on 2006-11-07
Why is it that every administrative task I perform uses a different theme than my standard one?

Whether I do a sudo gedit xyz, or use Synaptic, or gksudo nautilus/thunar, etc it always uses an ugly gray/blue skin, instead of my standard MurrinaEalm theme.

Is there a way to undo this, and have one theme throughout? It is quite useful to have a different theme for administrative tasks, just to remind me I can mess up my system, but the default theme that is given is a bit too ugly for my tastes.

---

### Post by autocrosser on 2006-11-07
That is a interesting question--The answer is that Admin tasks (run with gksudo or sudo) uses the root user settings--to have a system-wide theme, you would need to start with the root user--setting "his" theme & then making your theme the same.

Root user account is not "active" by default in Ubuntu (unlike some other distros)--so the root account uses a "default" setting--I have used Linux for many years & activate root almost as soon as I install--there are several good Wiki pages on root & how to activate the account---but Ubuntu's stand is that the system is "less" secure with the account active---In practice, if you use that account sparingly, you have no problems (I.E.--NO Internet access--watch VERY carefully what you do--etc).

I DO NOT advocate enabling root account UNLESS you know what you are doing & are willing to accept the results (you can nuke your install VERY easily in root)

---

### Post by CatKiller on 2006-11-07
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

Certainly no reason to enable the root account to log in with.

---

### Post by urukrama on 2006-11-07
Thanks Catkiller. That worked fine.

---

### Post by janbockaert on 2006-11-18
And it helped me too. The forums are amazing. Thanks Catkiller.

---

### Post by temcat on 2006-11-18
The trick described here works for administrative applications, but doesn't work for GDM for some reason. GDM dialogs use the default Edgy theme which I want to get rid of but don't know how.

---

### Post by CatKiller on 2006-11-18
GDM themes are distinct from icon themes and window manager themes. They can be changed with the tool at System -> Administration -> Login Window.

---

### Post by temcat on 2006-11-18
> **CatKiller said:**
> GDM themes are distinct from icon themes and window manager themes. They can be changed with the tool at System -> Administration -> Login Window.

No, I didn't mean GDM themes :-) I meant GTK+ theme that GDM is using for its dialogs. I can't find an option to change the GTK+ theme in System -> Administration -> Login Window.

---

### Post by Wijsneus on 2007-04-10
> **CatKiller said:**
> ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

Certainly no reason to enable the root account to log in with.

Thanks - this worked brilliantly.

---

### Post by Jabran Asghar on 2007-04-21
Hi, 

Well, I want to do it the other way round, i.e. I want that when I run any applications using gksudo etc, those root applications should have a different theme than that of my default theme. Anybody knows how to do this?

I sudo nautilus sometimes, and it will be a lot useful to be able to visually identify root nautilus windows through a different theme.

Thanks for any hints.

Jabran

---

