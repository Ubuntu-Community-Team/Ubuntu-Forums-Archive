---
title: "[SOLVED] unable to change compiz window borders"
date: 2008-05-30
forum: General Help
---

### Post by hotani on 2008-05-30
When compiz is activated on default installs of 8.04, it uses metacity borders from the appearance control panel.

However, I have upgraded to 8.04 after having compiz running previously and am stuck with the default compiz borders. 

How can I change back to the default of using metacity? Choices in Appearance control panel have no effect.

Emerald is installed, but does not change them either. Plus I don't really want the borders from emerald.

---

### Post by Forlong on 2008-05-30
Please post the output of ```
ps -e | grep "gtk-window\|emerald"
```

---

### Post by hotani on 2008-05-30
here's the output:
```

... /usr/bin/gtk-window-decorator

```

---

### Post by Forlong on 2008-05-31
Really? But you didn't use the command I posted, did you?

Anyway... post the output of
```
gconftool-2 -g /apps/gwd/use_metacity_theme
```

---

### Post by hotani on 2008-06-01
I used 'ps -ef...' which returns the full path of the binary. But adding the 'f' was the only diff from what you posted. With just 'e' it came back with 'gtk-window-deco'

I'm not on the machine right now but running that command remotely came back with 'false.'

Thanks for the help--getting tired of these compiz borders. Maybe next time I'll do a clean install.

EDIT: 
looks like i'm having the same problem on my home machine; compiz enabled but no metacity borders or way to change them. Output from the first command is: '...gtk-window-deco', and from the second: 'false'.

EDIT 2: 
This is why the compiz borders bug me:
[img]http://hotani.net/images/screenshots/compiz-borders.png[/img]

---

### Post by Forlong on 2008-06-01
```
gconftool-2 -s -t bool /apps/gwd/use_metacity_theme true
```
should solve the problem.

---

### Post by sayakb on 2008-06-01
```
gtk-window-decorator --replace &
```Add this to your startup if you wish to.

---

### Post by hotani on 2008-06-02
> **Forlong said:**
> ```
gconftool-2 -s -t bool /apps/gwd/use_metacity_theme true
```
should solve the problem.

Yep that fixed it up--thanks!

---

