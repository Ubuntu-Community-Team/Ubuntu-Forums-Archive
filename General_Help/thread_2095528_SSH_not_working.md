---
title: "SSH not working"
date: 2012-12-17
forum: General Help
---

### Post by digitography on 2012-12-17
I have recently built a new PC with 12.04.
I installed openssh-server

However I simply cannot get it to accept a connection, it responds with "Connection Refused". This is a bog standard setup, I haven't done anything clever with ssh yet, as it's on a local network.

if I run 
ssh localhost, all works fine and dandy, but connection over the network just won't work.

I have scoured several sites looking for the answer.
I have created new keys.
I have purged openss-server and reinstalled
----------------------------------------
Oh dear fixed it, operator error, only 3 hrs wasted.



If I run in test mode, I get

sshd -t
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key

Anyone got an answer?
Thanks in anticipation.

---

### Post by papibe on 2012-12-17
Thread title was marked as SOLVED. Edited back to unsolved.

---

### Post by digitography on 2012-12-18
I marked it as Solved because it was.
If you read the post, you will see it was operator error.

I won't go into details, as everyone will wet their collective pants. It was a monumentally stupid error.

And that's all I'll say :p

---

### Post by papibe on 2012-12-18
:oops: Oopsy, sorry then. Glad it's solved.

---

### Post by digitography on 2012-12-18
In fact you could just delete the thread, I couldn't work out how.

---

