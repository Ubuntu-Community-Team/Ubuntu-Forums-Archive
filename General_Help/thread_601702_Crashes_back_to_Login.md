---
title: "Crashes back to Login"
date: 2007-11-03
forum: General Help
---

### Post by iankellogg on 2007-11-03
I have no idea what happened but now everytime I try to log into my normal session, it goes black, shows some text, shows the nvidia logo and then finally ends up right back at the log in screen. I have no problem loading the failsafe gnome but other than that, no luck. Any ideas?

---

### Post by iankellogg on 2007-11-03
After playing around a bit. I think it has to do with compiz, Not sure what happened because it was working perfectly before, and now it doesnt work during startup. I can manually enable it but some things are not working right. Also when I log out it does the same thing as when i Log in with the black screen and nvidia logo.

---

### Post by iankellogg on 2007-11-03
I know this isn't that important, because I found a workaround, But I would really like to just use the computer without doing the workaround every time. I tried putting compiz --replace in the .profile but it crashes, I can only get that command to work when it finishes loading the desktop completely.

---

### Post by Thyme on 2007-11-03
Hi iankellogg,

I've also had this problem before .. it took me a while to figure how to start compiz automatically when logging in. All I remember is that there were conflicts when all the lines with "/usr/bin/compiz.real" got added to the session. I also remember removing them (in which case I could login successfully) and then adding them one by one until I got it right.

In ~/.gnome2/session, try and remove all the lines with "/usr/bin/compiz.real" in them. Logout and then when you login in again, add "compiz --replace" in the system->preferences->sessions. Then logout and see if you can login again.

Hope this works :)

---

### Post by iankellogg on 2007-11-05
Worked like a charm, thanks!

---

