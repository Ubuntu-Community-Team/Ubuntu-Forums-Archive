---
title: "Odd Menu lag!"
date: 2008-05-25
forum: General Help
---

### Post by leodido on 2008-05-25
I'm quite new with Ubuntu 8.04 but i managed to make everything i wanted to work. I have even managed to make my dual monitor work but since that when i'm on my main screen and i try to navigate in the Applications, places or system menu after clicking there is like 2-3 sec lag before the menu actually opens thing is if i go to the second monitor menu it's instant. I don't really see what could be causing this, do you guys have any clue?

---

### Post by leodido on 2008-05-25
So i narrowed down the problem and it is really the dual display that make it lag, but i have no clue why or how to remove the problem.

---

### Post by forestpixie on 2008-05-25
Hi - it is having two monitors that does it, I thought it was related to nvidia cards if that's the case for you then look in this thread - there is a script there which you can run at logon - the information is in the post.

> There is a fix here for the menu lag, and you still get to keep the effects (solution starting from page 3):
[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

I had to amend the script slightly - this is what mine looks like 
>  #!/bin/bash
sleep 5
DISPLAY=:0.0 compiz --only-current-screen &
sleep 5
DISPLAY=:0.1 compiz --only-current-screen &

Follow the thread and the astalavista post 27 and 42 are the ones you mostly want, but check it all out to be sure.

Hope that helps

---

### Post by leodido on 2008-05-26
Thank you mate, but it still doesn't work but maybe i'm doing it wrong. What i do is make a new file in gedit and save it with the script you gave me then i add it in session startup but i still have the lag with the menues :(

---

### Post by leodido on 2008-05-26
Actually it worked !! hehe thank you :p

But now i have a small window on the top left corner of my screener, it's called Controller.py but i can't get rid of it.

---

