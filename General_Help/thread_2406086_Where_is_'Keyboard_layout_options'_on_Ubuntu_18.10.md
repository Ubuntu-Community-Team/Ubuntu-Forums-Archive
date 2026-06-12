---
title: "Where is 'Keyboard layout options' on Ubuntu 18.10?"
date: 2018-11-15
forum: General Help
---

### Post by Masoris on 2018-11-15
[ATTACH=CONFIG]281642[/ATTACH]
I can fould this window in Linux Mint and old version of Ubuntu.
But can't find it on Ubuntu 18.10

---

### Post by #&amp;thj^% on 2018-11-15
To change the keyboard layouts, go to the system menu at the top right corner of your screen and select System Settings 
Then select Region & Language on the left of the items list to open the panel.

Click the + button in the Input Sources section, select the language which is associated with the layout, then select a layout and press Add.

Please Note: Some rarely used keyboard layout variants are not available by default when you click the + button. To make also those input sources available you can open a terminal window by pressing Ctrl + Alt + T and run this command:
```

gsettings set org.gnome.desktop.input-sources show-all-sources true
```

---

### Post by Masoris on 2018-11-15
I want to change keyboard setting such as 
'Alt/Win key behavior'
'Adding Esperanto supersigned letters'

---

### Post by #&amp;thj^% on 2018-11-15
Have a look: [https://askubuntu.com/questions/1029588/18-04-ctrlshift-to-change-language](https://askubuntu.com/questions/1029588/18-04-ctrlshift-to-change-language)

Also From the console I use:
```

setxkbmap -option esperanto:qwerty
```
For Esperanto Letters. 
Gnome has regressed in IMHO :(

---

