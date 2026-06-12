---
title: "I need  english - spain and english - french dictionaries"
date: 2023-01-15
forum: General Help
---

### Post by nilovsergey on 2023-01-15
Hello,
I need under kubuntu 20.04 to install english - spain and english - french dictionaries
Are there something ?
Thanks!

---

### Post by Holger_Gehrke on 2023-01-16
'dictd' and the dictionary packages 'dict-freedict-eng-fra' and 'dict-freedict-eng-spa' would give you a local dictionary server which you could then use with one of the many dict-clients (dict for the command-line, gnome-dictionary, xfce4-dict, dictem for emacs, dictionaryreader for GNU-step, kdict or ktranslator for KDE ...).

Holger

---

### Post by nilovsergey on 2023-01-16
In my repositoes I did not [COLOR=#000000]kdict or ktranslator for KDE... Please detalize to can I install them?[/COLOR]

---

### Post by Holger_Gehrke on 2023-01-16
Seems I fell for some old information, kdict used to be part of a KDE base install back in the days before KDE 3.5 but was dropped and ktranslator hasn't had an update since KDE 3.3. This leaves you with 'goldendict' (yes, that's a package name, you can just 'sudo apt install goldendict') which is quite a bit more than just a dict client ... you actually don't need the server for it, it will read the dictionary files all by itself and it can use multiple other file formats including several commercial formats.

Holger

---

### Post by nilovsergey on 2023-01-17
Thanks! Does it need other libs installed for different languages ?

---

### Post by Holger_Gehrke on 2023-01-17
Perhaps I should have phrased that more precisely: goldendict doesn't need the server program because it can read the exact same files the server would use directly. So you wouldn't need to install 'dictd' but just the datafiles for the dictionaries, in this case the packages  'dict-freedict-eng-fra' and 'dict-freedict-eng-spa. After you installed those you can then use 'dpkg -L dict-freedict-eng-fra' to find out where the files for the dictionary are and add them in goldendict.

Holger

---

### Post by vmpx on 2023-01-19
qtrans 0.3.2.7 is a word translator. You need following dictionaries: english.dic, EngtoSpa.dic and EngtoFre.dic.

---

