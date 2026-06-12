---
title: "Lock an account"
date: 2006-07-26
forum: General Help
---

### Post by rob3000 on 2006-07-26
Hello,

I want to lock a certain account on my ubuntu system. For that I want to write a tailscript which should display a certain message if the certain user wants to log in the system.

In the course of that I wrote a normal script

```

#!/bin/bash

echo Your Account was deactivated for maintenance reasons!

sleep 5

```

I saved that script under /home/script. In the /etc/passwd I modified the entry of the certain user from /bin/bash to /home/script.

Is that an clever and adequate solution for my plan to lock a certain user by writing a tailscript and display the message when the user wants to login?

---

### Post by taurus on 2006-07-26
If you don't want somebody to log into a specific account, then use /bin/false as the shell in /etc/passwd!!!  Fast and simple...

---

### Post by cilynx on 2006-07-26
As the original post said, he wants to have it display a message, not just log them back out....which is what said script does.  So long as the script exits clean, it looks good to me.

---

### Post by rob3000 on 2006-07-26
What do you mean with that the script should exit clean? 

The script looks only like this:

```

#!/bin/bash

echo Your Account was deactivated for maintenance reasons!

sleep 5

```

---

### Post by cilynx on 2006-07-26
My comment was more to taurus' remark.  Your script will exit cleanly.  If you had written a script that looped or some such, it wouldn't exit and the user trying to log it would get stuck and have to kill the app they used to connect.

You should be fine..

---

