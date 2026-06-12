---
title: "General Questions about &quot;sudo passwd&quot; and the &quot;who&quot; command"
date: 2007-06-14
forum: General Help
---

### Post by 200mg on 2007-06-14
Please keep in mind im a linux noob.

[IMG]http://i10.photobucket.com/albums/a109/ntalbot77/who.jpg[/IMG]

When I do a who command, why am I logged in twice?  And can someone explain what the rest of that means the ie: pts/0 , and :0

Also on the sudo passwd command.  Once you log in and type sudo passwd root, it just says type a new unix passwd, it doesn't ask you to verify your existing password, this doesn't make sense to me.

---

### Post by Catsworth on 2007-06-14
> **200mg said:**
> Also on the sudo passwd command.  Once you log in and type sudo passwd root, it just says type a new unix passwd, it doesn't ask you to verify your existing password, this doesn't make sense to me.

This is because the root password is currently 'null', not set, doesn't exist.  When you type 'sudo passwd root' you are essentially saying 'hello, I would like to set a root password please'.

You really shouldn't set a root password, everything you are likely to need to do that would require root privileges can be accomplished with the sudo (or su) commands.

---

### Post by jasonlfunk on 2007-06-14
When you sudo you run the command as root. Root can do whatever it wants without verifing anything. Thus root can change anyone's password without having to know the password.

I don't know about the who. :)

---

### Post by Wicca on 2007-06-14
> When I do a who command, why am I logged in twice?  And can someone explain what the rest of that means the ie: pts/0 , and :0

:0 is the display the X-server is using. So you are logged on a X-session (graphical environment). This is your main logon.
pts/0 represents your logon to a terminal session, in which you typed 'who'. You will logout this session as soon as you close the terminal. Open another tab in terminal (Ctrl+Shift+t) and do a 'who' again: You'll notice a third logon.

> Also on the sudo passwd command.  Once you log in and type sudo passwd root, it just says type a new unix passwd, it doesn't ask you to verify your existing password, this doesn't make sense to me.

I'm not sure about this, but you might have used sudo before in the same terminal window. If you use sudo your password will be remembered as long as the window stays open. The second time you use sudo you wont be asked for a password. Even if you close the window the sudo session will remain active for a certain amount of time, time which I don't know exactly.

---

### Post by 200mg on 2007-06-14
thanks for the replies..

Any idea on the logged inn twice under "who"??

---

### Post by 200mg on 2007-06-14
thanks wicca

---

### Post by meman63 on 2007-06-14
I believe the default time out for sudo is 15 minutes.Could be wrong,though.

Cheers,
   Meman63

---

