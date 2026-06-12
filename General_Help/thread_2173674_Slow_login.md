---
title: "Slow login"
date: 2013-09-10
forum: General Help
---

### Post by watgrad2 on 2013-09-10
Hello - a search of the internet and forums didn't help me here...
I have Ubuntu 13.04 installed on a MacBookPro8,1.  
Previously, I ran 12.04 and found boot/login to be very fast.

After upgrading to 13.04, my computer still boots to the login screen within 30 seconds, however, the lag between entering a password and getting to a usable desktop can be over 1 minute.

I am at a loss as to how to resolve this.  I've check dmesg logs but cannot find a process slowing the login...am I looking in the correct place.?  
Is there some other cause of this type of delay?

Any help or suggestions would be much appreciated.

---

### Post by Panderz on 2013-09-10
May be a long shot, type "ls -lah" into the terminal and search in the column on the far right for .Xauthority and make sure it has you username in the 3rd column from the left.

---

### Post by watgrad2 on 2013-09-11
Hello - thanks for your reply.  
Yes that checks out OK.

---

### Post by Panderz on 2013-09-11
Just for clarity, the actual login is fast and your desktop enviroment takes a while to load in? Or do i have that backward? Also, are you using Unity or a different DE?

---

### Post by watgrad2 on 2013-09-12
At startup, the computer gets to the log in screen in under 30 sec.
After typing in my login password and hitting enter, the screen freezes and the computer takes a minute or longer to get to the desktop.
It does not seem to matter if I log into a different account - all accounts have this delay.  I have disabled all unessential startup applications...no effect...

I am using unity.  (I did tried installing cinnamon hoping this would improve the problem - but still experienced the long delay at startup.  I have since removed cinnamon.)

---

### Post by watgrad2 on 2013-09-17
Any suggestions or ideas for this?

---

### Post by watgrad2 on 2013-09-24
I finally reinstalled ubuntu - after a bit of hassle got the system back to the way I like.  Login and boot are back to the normal 30 sec boot - 2-5 sec for login.

---

