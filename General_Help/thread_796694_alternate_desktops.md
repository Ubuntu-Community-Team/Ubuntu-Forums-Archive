---
title: "alternate desktops"
date: 2008-05-16
forum: General Help
---

### Post by 64dragon on 2008-05-16
i'd like to enable more than the 2 default alternate desktops. i right click on them and go to configure desktop and up it to 4 but nothing happens when i hit apply. i have compiz and want to be able to use the cube effect but i seem to be stuck at 2 desktops so its just a flat plane

---

### Post by keforex on 2008-05-16
I don't have compiz installed (yet) and I can configure as many desktops as I want. This must be some kind of compiz incompatibility or there's an option also in Compiz in regards to the number of desktops.

---

### Post by 64dragon on 2008-05-16
thanks, i missed those options. it worked and got me the cube but still can't put all four on the task bar

---

### Post by overdrank on 2008-05-16
> **64dragon said:**
> thanks, i missed those options. it worked and got me the cube but still can't put all four on the task bar

Hi you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```or search synaptic manager.
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

---

### Post by Joeb454 on 2008-05-16
You can also right click the 2 desktops in the bottom panel, and choose preferences. Then from there you can choose how many workspaces you have, how many rows to show them in, and what they are called :)

Hope this helps :) Also, the compizconfig-settings-manager is pretty good, I use it on my other machine to edit all my compiz options :)

---

### Post by 64dragon on 2008-05-17
> **overdrank said:**
> Hi you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```or search synaptic manager.
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

I already have the manager installed. I found the general options when keforex mentioned them and have the horizontal virtual size set to 4 and that worked, allowing me to use the cube and rotate it. 

[QUOTE=Joeb454]You can also right click the 2 desktops in the bottom panel, and choose preferences. Then from there you can choose how many workspaces you have, how many rows to show them in, and what they are called [/QUOTE]

this is where i'm stuck, i do all of that but when i hit aply nothing changes and if i close out of the config window and go back into it it says 1 desktop even tho i see 2

---

### Post by keforex on 2008-05-17
This might be a stretch, but try to make your panel height bigger. Maybe you see only two desktop icons on the panel because the panel is too "thin" and the other two are underneath... ? Just a guess.

---

### Post by 64dragon on 2008-05-18
i just restarted and everything is fine.

---

