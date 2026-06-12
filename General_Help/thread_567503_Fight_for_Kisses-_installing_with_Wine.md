---
title: "Fight for Kisses- installing with Wine"
date: 2007-10-04
forum: General Help
---

### Post by Protagonistics on 2007-10-04
Ok, so I found this game.  it's made for windows. I downloaded it, and right clicked the .exe file and told the computer to open it with Wine. to my astonishment, it worked (i've never used wine before). It installed the thing succesffully but then closed as you might imagine it would do. How do I open the program and play it?

I have no idea.

thanks!

---

### Post by por100pre1 on 2007-10-04
Was the exe file an installer? If yes, look for it in your ~/.wine/drive_c folder inside your user folder (press CTRL+H too se hidden files). If not, just right click the exe file again

---

### Post by Protagonistics on 2007-10-05
hmmm, no I can't find it in my wine folder.

When I run the .exe it runs an installation where I can choose a number of drives in which to install it. I am doing it in the C drive- but is that the one that Wine would expect or does it matter? there are the choices of the Z, H, C, and one other drive.

---

### Post by por100pre1 on 2007-10-05
Try this command in Terminal to find it:

```
locate .exe
```

---

