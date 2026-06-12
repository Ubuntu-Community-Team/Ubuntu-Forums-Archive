---
title: "Minimise/maximize buttons dissapear"
date: 2008-06-29
forum: General Help
---

### Post by M3TAL1QU1D on 2008-06-29
I have emerald theme manager downloaded and i have a theme enabled. but the only way to enable the theme was to run a command in the terminal

emerald -- replace

and the theme came on. i went to close out the terminal, the theme dissapears and my close.min.max buttons with it!!!

whats going on???


btw.. im a linux noob:)

---

### Post by isaacj87 on 2008-06-29
Hey there,

There are numerous things you can do. The first option is temp. The second and third are the best solutions.

1) *This is a temporary solution, after a reboot you'll have to do this again* You can press alt+f2 and type:

```

emerald --replace
```

2) Install CCSM and in the "Window Decoration" plugin, tell it to use Emerald. Simply do this:

Install CCSM (if you don't have it aleady):

```
sudo apt-get install compizconfig-settings-manager
```

Open it, go into the "Window Decoration" plugin and where it says "Command" type this:

```
emerald --replace
```

3) The last and easiest solution is the fusion-icon. Install it like this:

```
sudo apt-get install fusion-icon
```

Run it (Applications->System Tools), then right click it and select the decoration.

Hope that's helpful. Let me know how it goes. :)

Oh, and BTW...the reason why it "disappears" after you close terminal is because you're running emerald from Terminal. So, when you close terminal, you're terminating emerald as well.

---

### Post by M3TAL1QU1D on 2008-06-29
It worked! Well, the second option that is lol. when i right clicked on compiz fuison icon, it didnt have the option on there. o well, it worked either way! And thanks about the terminal info, i kinda figured :)

---

