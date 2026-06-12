---
title: "see what's happening"
date: 2008-07-05
forum: General Help
---

### Post by nikosm on 2008-07-05
Dear community,

Often when using ubuntu, I do sth that doesn't have any obvious effect (two examples below). In cases like that I wish I had the command line that was giving back some error to have at least some point to start understanding what goes wrong.

 - the program hugin (to create panoramas) cannot find autopano-complete (even though the path looks fine to me and calling it on the command line works - no idea what's wrong). Unable to fix it, I made a nautilus action script that calls autopano-complete on the selected jpegs. But nothing seems to happen.

 - selecting gimp from the menu gives a really really long "busy" mouse pointer but nothing happens. Calling gimp from the bash starts it in a couple of seconds! (maybe relevant: I have installed gimpshop)

So, is there a way to see what goes wrong in these cases?

Thank you very much in advance!
Nikos

P.S. By the way, hugin seems to crash very often on my computer (segmentation fault) when stitching. Does anybody else observe this?

---

### Post by ad_267 on 2008-07-05
For the first case: No idea what those are sorry.

For the second case: You can right click on your menu and select Edit Menus then right click on the launcher for the application and select properties to see the command it is using. If this is different from the command you entered in the terminal then you may be able to figure out what is going wrong.

---

### Post by nikosm on 2008-07-05
> **ad_267 said:**
> You can right click on your menu and select Edit Menus then right click on the launcher for the application and select properties to see the command it is using.

Ah, thanks! It was "gimp-2.4 %U" instead of "gimp %U". Running gimp-2.4 in a terminal gives

```
~$ gimp-2.4 
gimp-2.4: symbol lookup error: gimp-2.4: undefined symbol: gimp_micro_version
```

The annoying thing is that if I right click on a jpeg and choose "open with > Gimp Image Editor" it tries to open it with gimp-2.4 . Any idea how I can change that?

Thanks again,
Nikos

Sorry, I should have tried by myself before posting: removing the gimp entry from the open with menu, changing the command in the applications>graphics>gimp image editor menu item and then readding gimp to the open with of jpegs did the job
(now that I think of it, maybe only changing the entry in the applications menu would have been enough).

---

