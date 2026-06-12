---
title: "Applications launching automatically at start after crash"
date: 2013-08-18
forum: General Help
---

### Post by jjsh2 on 2013-08-18
Hi

I had to hard reset my PC after NZB V0.2 crashed and brought the whole system to its knees. Now, whenever I start my PC and log in, NZB, Firefox and a folder I had open during the crash launch automatically. Everything works fine, its just a bit annoying. Can anyone suggest how I can stop this happening?



Many TIA

---

### Post by meilin on 2013-08-18
Did you try the **Startup Application **and see if they are in list? You can run command in terminal (Ctrl+Alt+T) to see all startup apps.

[COLOR=#000000][FONT=monospace]sudo sed -i &#8216;s/NoDisplay=true/NoDisplay=false/g&#8217; /etc/xdg/autostart/*.desktop


[/FONT][/COLOR]

---

### Post by Toz on 2013-08-18
Hello jjsh2 and welcome to the forums.

They are probably starting because they are in your saved sessions cache.

If you are usung Xubuntu 13.04 or later, go to Settings Manager -> Session and Startup - > Session tab and click on the "Clear saved sessions" button. Log out and back in again to test.

If you are using a version earlier than 13.04, you need to:
1. Log out of the gui.
2. Go to the first tty (Ctrl+Alt+F1)
3. Log in to the text console
4. Manually clear the sessions cache by:
```
cd .cache
rm -rf sessions
```
...be extra careful entering the "rm -rf" command
5. Go back to the gui (Ctrl+Alt+F7)
6. Log back into the gui and see if they start up again.

---

### Post by jjsh2 on 2013-08-19
Thanks for the help, guys. Sorry, I forgot to mention the Xubuntu verision, doh!  Yes I am on 13.04, and clearing the saved sessions in Settings Manager worked a treat.

:D 

Thanks again.

---

