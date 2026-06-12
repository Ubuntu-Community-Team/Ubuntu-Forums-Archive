---
title: "disabling screen lock after suspend"
date: 2024-08-20
forum: General Help
---

### Post by Norm24 on 2024-08-20
Recently did a clean install of Mate 24.04 on a Dell Latitude E7450 laptop and pretty much have everything the way I want it except for one truly annoying thing which is having to enter my password after waking from suspend,my machines are in a completely secure environment so I'm not worried about security.I was able to resolve this in years past on my other laptops running 18.04 and 22.04 respectively.I've tried just about every solution I could find by searching the web and here on the forums but so far no love with 24.04.

I'm stumped or losing my mind or both at not being able to resolve this.Any help would be much appreciated.

---

### Post by Norm24 on 2024-08-20
Found a solution that worked for me.

```
dconf write /org/gnome/desktop/suspend/lock-enabled false
```

---

