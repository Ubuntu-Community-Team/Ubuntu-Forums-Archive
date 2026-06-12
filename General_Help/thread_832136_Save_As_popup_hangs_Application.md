---
title: "Save As popup hangs Application"
date: 2008-06-17
forum: General Help
---

### Post by stubones99 on 2008-06-17
Whenever I select the SaveAs option on just about any application in Ubuntu, it hangs up the application. It pops up the window with the filename / path field and then hangs. The field is empty. Is there somewhere this value is stored that could be set wrong, and when the SaveAs option is launched, it tries to restore the previous location and that hangs the app?

Does anyone know where this data is stored? Or can someone tell me how to reload / reset it so that any app that wants to save a file won't lock up?

Thanks!

---

### Post by mempman on 2008-06-17
> **stubones99 said:**
> Whenever I select the SaveAs option on just about any application in Ubuntu, it hangs up the application. It pops up the window with the filename / path field and then hangs. The field is empty. Is there somewhere this value is stored that could be set wrong, and when the SaveAs option is launched, it tries to restore the previous location and that hangs the app?

Does anyone know where this data is stored? Or can someone tell me how to reload / reset it so that any app that wants to save a file won't lock up?

Thanks!


This seems like an incredible unlikely scenario; thus, I would suggest for you to ensure that no "Pop up boxes" or anything are in the background - these would hang the SaveAs Box and the application until the pop ups have been resolved.

---

### Post by stubones99 on 2008-06-17
As unlikely as it sounds, it's true. It appears in GTK environment, there is a SaveAS function that pops up a window and collects the destination filename. Lots of applications use it. And in my ubuntu system, the default filename must be mapped to some strange destination. 

So, regardless of what application I have tried, when I choose SaveAs, it's the end, because the SaveAs window pops up and never lets me enter the file path name. It won't let me X out or anything. the application that started it also locks up. The only way out is to stop the app.

I've tried several apps and all act the same when I select SaveAs, or Save if the filename has not been selected.

I don't know if ubuntu has a registry or something where it saves the default settings and such. Does anyone know where this default info must be kept?
 
I would hate to have to reinstall the ubuntu just to fix this problem but will if necessary..

Thanks in advance!

---

