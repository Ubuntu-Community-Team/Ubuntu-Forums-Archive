---
title: "cuple important questions..."
date: 2007-07-03
forum: General Help
---

### Post by nate22 on 2007-07-03
have sum question hope sum one can answer...

1- i only have 1 workspace...why? i used to have 4.. can i get them back? if so how?


2- ROOT ROOT ROOT! blah blah blah aparently i dont have acces to ANYTHING! booo
im tring to edit some config files on laamp located in the opt folder..but i dont have permission to edit this file....how do i get permission?

3- compiz?? ok so i downloaded compiz...now what?? how do i start it up?

---

### Post by Juan_VCS on 2007-07-03
1 - Right click on the workspaces panel - Preferences
2 - In a terminal window, type **sudo *yourcommand***
3 - In a terminal window, type **compiz --replace** or just enable **Desktop Effects** under **System > Preferences**

---

### Post by nate22 on 2007-07-03
yea i did that.and guess what? i dont have the window borders anymore...boooo



so i read up and saw that i shud load emerald..did that ..and guess what...no window border still

---

### Post by hikaricore on 2007-07-03
Maybe you should investigate the issue further instead of being short with someone helping you..

What type of video hardware do you have?

Did you install the drivers for your video hardware?

Do the linux drivers for your video hardware support direct rendering?

What is the terminal output of:

```
glxinfo | grep rendering
```


If beryl/compiz isn't functioning properly due to rendering issues, the software is unable to render the window borders at all.

If metacity does not reload after disabling desktop effects, you will need to run:

```
metacity --replace
```

---

### Post by nate22 on 2007-07-03
yea i fiexed thhat whole compiz thing

and the output was "YES"

---

