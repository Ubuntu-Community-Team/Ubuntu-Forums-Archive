---
title: "multiple instances of a user on my box"
date: 2004-11-08
forum: General Help
---

### Post by penipol on 2004-11-08
When I type users at the command line I find that there are 2 or 3 instances of a user (me) logged in. I would like to know why there are so many users logged in when I am the only one on my box.

Thanks in advance.

---

### Post by jwenting on 2004-11-08
That's unix for you.
Each terminal window you open automatically creates a user process.
In addition the X session creates one as well.

So if you have 1 terminal window open you have at least 2 users reported by who.

Now try using su on the terminal to log in as another user on that terminal. You'll see that both the other user and you yourself are logged in on that one terminal.

---

### Post by penipol on 2004-11-08
Thank you for clearing that up for me.

---

