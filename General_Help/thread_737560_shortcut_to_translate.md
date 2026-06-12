---
title: "shortcut to translate"
date: 2008-03-27
forum: General Help
---

### Post by elektronaut on 2008-03-27
Hi,

is there some way to get an instant translation for a word no matter in which application window without having to use the clipboard? So far I tried gnome-translate, youTranslate and freeSpeak. But you need to paste the word into those programs, I'd like to have some kind of pop-up displayed after pressing some keyboard shortcut. Kind of like WordTranslator (part of Google Toolbar) works in the browser window. Just that the translation shouldn't appear before pressing the shortcut.

If there is no such app (which seems to be the case as googling showed me), would it be somehow possible to implement a similar solution with a combination of some script and one of the translation apps mentioned?

---

### Post by elektronaut on 2008-03-27
Thinking about it... the word probably at least needs to be in the clipboard in order for some other application to access it. So 
```
Ctrl-C
keyboard-shortcut
```
should pop up the translation. That would still be much better than navigating with the mouse to the translation app and then pasting and clicking the translate button.

---

### Post by elektronaut on 2008-03-27
Just to give you a better idea what I'm thinking of:

Google Desktop is an application which is close to this. It pops up a little search box after the shortcut (2x Ctrl). But it's options don't offer the translation service yet. Also it doesn't take the word from the clipboard, you still have to paste it.

---

### Post by pointone on 2008-03-27
```
apt-get install xsel
```

```
#! /bin/bash

xsel --clipboard | translator | xsel --clipboard -i
```

"xsel --clipboard" outputs the current contents of the clipboard.

The first pipe "|" sends the output to the translator.

The second pipe "|" sends the output from the translator to the next xsel command.

"xsel --clipboard -i" reads standard input into the clipboard; standard input will be the output of the translator that is piped to this command.

```
chmod +x /path/to/script
```

[Bind the desired key to this script]("http://justanothertechblog.blogspot.com/2006/12/defining-keyboard-shortcuts-in-gnome.html").

Use as follows:

- Select the word to be translated.
- Ctrl+C (or however you copy to the clipboard)
- Script Shortcut (that you configured as detailed in the link)
- Ctrl+V (or however you paste from the clipboard)

---

### Post by elektronaut on 2008-03-28
Thank you for the input. Unfortunately it doesn't seem to work with one of these: 
translate, gnome-translate, youtranslate, freespeak

Freespeak already offers clipboard-grabbing by the way, but there is too much mouse clicking involved until you get the translation. I want something simple, at max two keystrokes. I guees I would need to write my own program =8-O

---

