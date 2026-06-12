---
title: "no longer able to log in"
date: 2008-04-24
forum: General Help
---

### Post by cheeseman557 on 2008-04-24
hi,

i booted up my comp today only to find that i was no longer able to log in. i normally have it on auto-login, but today it stopped at the login screen. i punched in my username and password and hit enter, but it just cleared the field and changed it back to the username input box. i tried punching in a false id/pass and it did say something along the lines of "invalid id, try again",  but when i put in my correct id/pass, i did not get that message. it just changed back to the username input box.

last night, i did add this to my system through:
[http://ubuntuforums.org/showthread.php?t=764303](http://ubuntuforums.org/showthread.php?t=764303)

any ideas? thanks!

---

### Post by ibuclaw on 2008-04-24
It's not refusing to log in.
It is sleeping. (ie: till 4:30pm) before logging in.

Erm, not too sure why. I tested it before I posted that to you.

ahh well. I am very sorry for that.

Switch to a virtual terminal:
Hit "**Alt+Ctrl+F1**"

Then log in through there.

And type in:
```
sudo chmod -x /etc/gdm/PostLogin/Default
```
That should prevent it from running.

then type the word "exit" to log out, and then switch back to gdm:
"**Alt+Ctrl+F7**"

Again, sorry.

Regards
Iain

---

### Post by cheeseman557 on 2008-04-24
oh no problem at all! your fix worked and that alarm applet is really terrific. thanks a lot for everything! i really appreciate all your efforts. :)

---

### Post by ibuclaw on 2008-04-24
Did you make any changes to the script, by the way?

I'm just curious as I've just had the exact same script in my startup scripts, and I've already rebooted three times...
And have had no problems with it.

As sorry and embarrassed as I am, I'm really stumped as to why this happened.

Also, since you'll be needing it no longer, you can remove it.
Hit "**Alt+F2**" and type in:
```
 gksu nautilus /etc/gdm/PostLogin/
```
Then delete the "**Default**" file in the New Nautilus window that opens.

Anyways. I'm glad you like the alarm app!

Regards
Iain

---

### Post by cheeseman557 on 2008-05-01
i finally got a chance to take it a look at it again. your script/directions are flawless, the only problem is that i already had some stuff in my postlogin and when i pasted your commands in there, i pasted it to the wrong spot :S. but now its working prefectly! thanks! :)

---

