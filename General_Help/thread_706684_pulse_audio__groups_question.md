---
title: "pulse audio / groups question"
date: 2008-02-24
forum: General Help
---

### Post by Culito on 2008-02-24
Hi all,
I have pulse audio installed, and it works fine, unless I switch users.  I have one other user account, and even if I log out, it only works on the first account I log into.  On the other one, it gives me the message, "connection refused".
I figured it was a matter of adding the user to the "pulse-rt" group, but when I went to do that, I noticed that there were 7 separate instances of each group I have!
Each group I have is listed 7 times.  Is that normal?  If I add a user to the group, it only "sticks" on the last listed instance of that group.  And it doesn't help my pulse audio situation.
I don't know if any of that makes sense, but any help is appreciated!

-C

---

### Post by Culito on 2008-02-25
No ideas?  Anybody?

---

### Post by Culito on 2008-02-27
Here's another quick tidbit.
When I go into my other user account, and the sound connection is refused:
I go into the system>admin>system monitor and kill pulseaudio.
Guess what - it works perfectly after I do that.  Is it trying to start a second pulseaudio daemon when you log into the second accout or something?

---

