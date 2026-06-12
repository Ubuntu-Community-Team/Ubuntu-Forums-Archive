---
title: "Unity Tweak Tool &quot;Restore Defaults&quot; Not Working!"
date: 2013-05-01
forum: General Help
---

### Post by MaZaMo on 2013-05-01
Hello,
I have Ubuntu 13.04, and just earlier today installed the new program Unity Tweak Tool. In the "launcher" section I changed the transparency level, but the "restore defaults" button isn't working correctly and I'm not sure what the defaut is! I want to restore everything to default and then remove this program that ruined my desktop.
Anything I can do to restore everything to default? Perhaps by command-line? If there's a way to fix this program I would like to keep it as it has some cool settings. :)
Thank you!

---

### Post by hil4vitkutin on 2013-05-01
Hello, you could try resetting your unity with *dconf-tools.* Give it a try:

```

sudo apt-get install dconf-tools

dconf reset -f /org/compiz/

setsid unity

```

---

### Post by monkeybrain2012 on 2013-05-01
Can't you just change that with ccsm?

---

### Post by hil4vitkutin on 2013-05-01
Well yes you could, by going to 'Preferences' -> 'Profile & Backend' and selecting 'Reset to defaults' under 'Profile'.

---

### Post by MaZaMo on 2013-05-03
Thank you so much!

---

### Post by hil4vitkutin on 2013-05-03
You're welcome!

I'm glad if this helped you :)

---

