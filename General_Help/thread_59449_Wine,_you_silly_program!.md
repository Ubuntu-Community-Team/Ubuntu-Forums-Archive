---
title: "Wine, you silly program!"
date: 2005-08-24
forum: General Help
---

### Post by Koba on 2005-08-24
ok, i have wine, and i recently installed this google talk to see what the hype is about, and now, i can't figure out how to access the darned file, seeing how there are folders in my way, with spaces in thier names, console doesn't allow that, folders like Application Data, and Local Settings... if anybody has a fast and easy way of getting past these, please do so

---

### Post by drummer on 2005-08-24
[QUOTE=Koba]ok, i have wine, and i recently installed this google talk to see what the hype is about, and now, i can't figure out how to access the darned file, seeing how there are folders in my way, with spaces in thier names, console doesn't allow that, folders like Application Data, and Local Settings... if anybody has a fast and easy way of getting past these, please do so[/QUOTE]
 to type file paths with spaces in a terminal, preceed each space with a backslash ("\"), also, if you press tab after typing part of the folder/filename if will autocomplete if there is one possible name, if there is more than one match press tab again to get a list of possible options and type a bit more. Hope that made sense.

If you navigate to the folder where the exe is located (.wine/something/something.exe, not sure exactly) and right-click the file, there should be an "open with: wine" option.

---

### Post by wellery on 2005-08-24
[QUOTE=Koba]ok, i have wine, and i recently installed this google talk to see what the hype is about, and now, i can't figure out how to access the darned file, seeing how there are folders in my way, with spaces in thier names, console doesn't allow that, folders like Application Data, and Local Settings... if anybody has a fast and easy way of getting past these, please do so[/QUOTE]

You can still use the console if there are spaces in the directory names. 

You just do this:

```
cd this\ has\ spaces
```

---

