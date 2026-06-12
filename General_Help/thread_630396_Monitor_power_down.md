---
title: "Monitor power down"
date: 2007-12-03
forum: General Help
---

### Post by philetus on 2007-12-03
I'm running Gutsy on a desktop. and it was powering down the CRT I had,but I replaced it with a LCD widescreen and now it turns dark but still emits light.

I looked in power mngt. and there is nothing for powering down the monitor when idle.
I opened conf.editor and changed gnome-power-manager/actions/sleep_type_ac to off.
I unchecked activate screensaver.
I'm trying to learn how to manage everything myself but this one has me stumped.

---

### Post by bingoUV on 2007-12-03
What happens when you run 
```

xset dpms force off

```

Does the light emission stop? Move mouse or press key to bring back your monitor to life. If it works, add the following line in your ~/.xsession file; assuming you want it off after 300 seconds(5 minutes) of inactivity
```

xset dpms 300 300 300

```

---

### Post by philetus on 2007-12-03
bingoUV,

Thank you. You must be a genius.

---

