---
title: "creating an shortcut"
date: 2006-08-21
forum: General Help
---

### Post by Namtellum on 2006-08-21
Basicly my question here is how do I make a desktop shortcut that will automaticly run a game in wine using -opengl rather than going into the terminal and physically changing directories and typing 'wine blah.exe -opengl'. Thanks in advance!

---

### Post by Fass on 2006-08-21
Rightclick the desktop, choose to create launcher and enter the pertinent command to start the app with wine in the "Exec" field.

---

### Post by Namtellum on 2006-08-21
Still not getting it..
basicly heres what i need it to do
1. get into the directory where warcraft 3 is cd...    .wine/drive_c/Program files/Warcraft III
2. now that im in the directory...   wine war3.exe -opengl

I'm sure theres a much easier way to do this..forgive my newbieness :p

---

### Post by Fass on 2006-08-21
You can enter the command directly:
```
wine ~/.wine/drive_c/Program\ files/Warcraft\ III/war3.exe -opengl
```

I am assuming that .wine is in your users home directory. That's what the "~" stands for.

Now, if you want a short cut to it on you desktop, that's what you're gonna have to put in the "Exec" field in the "Create Launcher" dialogue which you access by right clicking your desktop and choosing "Create Launcher."

---

### Post by biffta on 2006-08-30
Is there an easy way to create shortcuts that are equilivent to:

cd Desktop
ln -s /usr/local/bin/ bin

That launcher thing has got 7-8 bloody fields in it! I just want to drag and drop like in windows/kde!


Thanks!

---

### Post by Anonii on 2006-08-30
> **biffta said:**
> Is there an easy way to create shortcuts that are equilivent to:

cd Desktop
ln -s /usr/local/bin/ bin

That launcher thing has got 7-8 bloody fields in it! I just want to drag and drop like in windows/kde!


Thanks!

You could do these 2 commands , one command with:

cd Desktop && ln -s /usr/local/bin/ bin

And adding this to the "Command" field. Then naming your launcher and selecting "Ok".
If its a terminal command like that, you have to tick the "Run in Terminal" option :)

---

