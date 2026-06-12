---
title: "Customizing neofetch / urxvt"
date: 2017-06-05
forum: General Help
---

### Post by Furycd001 on 2017-06-05
[COLOR=#292F34][FONT=verdana]HI Guys.

[/FONT][/COLOR]
[COLOR=#292F34][FONT=verdana]Today I made the switch from screenfetch to neofetch & from xfce4-terminal to urxvt. I have been working away at customizing both but have got one problem which I can't seem to find an answer to. If you would kindly have a look at the screenshot below you will see some red text within neofetch. How can I remove this red color and set it to the same color as the rest of the text showing :? I have attached a screenshot below & added linked to Xresources & neofetch config. Many thanks in advanced for your help.

[Xresources]("http://paste.ubuntu.com/24771809/")  //  [Neofetch]("http://paste.ubuntu.com/24781043/")[/FONT][/COLOR]
[COLOR=#292F34][FONT=verdana][URL="http://paste.ubuntu.com/24771809/"]
[ATTACH=CONFIG]275473[/ATTACH][/URL][/FONT][/COLOR]

---

### Post by Furycd001 on 2017-06-05
Found the code that I needed.

```
URxvt.color0: #5B8CC5
```

Paste that code into your ./Xresources and keep changing the number until you reach 15.

---

