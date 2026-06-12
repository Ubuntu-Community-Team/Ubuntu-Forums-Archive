---
title: "Moving close, maximize buttons to the left side"
date: 2017-10-30
forum: General Help
---

### Post by sports fan Matt on 2017-10-30
I know there is a way to, but for the life of me can't figure out how to move these to the left side. (I previously used Gnome-Tweak tool). Can anyone show me how to in Unity Tweak Tool?

---

### Post by ajgreeny on 2017-10-30
Are you using the unity version of 17.10 or the default with a tweaked gnome desktop?

If the latter you need to install gnome-tweak-tool (I think that's what it's called) and use that instead.

---

### Post by monkeybrain20122 on 2017-10-30
Well in unity the buttons are by default on the left so I assume you are talking about gnome shell. In that case it has nothing to do with unity-tweak-tool. AFAIK that option is not in gnome-tweak-tool. Instead you need to install the dconf-editor (or with some cmd line mumbo jumbo with gsettings which is the same thing) 

Open dconf-editor, go to org > gnome > desktop > wm > preferences > button-layout, turn off default layout and type instead 
"close,minimize,maximize:" (without quotes)
in the text book and apply

At this point it will change for some windows but may not others, for it to apply consistently you need to logout and login again.

---

### Post by sports fan Matt on 2017-10-30
Ajgreeny, honestly i'm not sure.  It's been a while since I'm just getting back into Ubuntu.  I just upgraded from Lucid yesterday and now i'm on Artful Aardvark.
Monkeybrain, thanks for that.  It will take a few weeks to get back into all the terms and remembering how things work.

---

