---
title: "Log Failed SSH attempt passwords"
date: 2008-02-11
forum: General Help
---

### Post by hooksie on 2008-02-11
Quick question, and I cant seem to find it anywhere on google...

I'm aware of the huge privacy issue with this, but this is on a testing server, so don't warn me about that, I'm not worried about it.

Is there some way to log the actual failed attempts, bother username AND password, in SSH?

For example, someone tries to log into root with "root" and 12345, how can I see that they used username "root" and password "12345".

Thanks.

---

### Post by apetresc on 2008-02-11
I'm fairly certain that's not possible because it would present a pretty serious security problem. Here's how you could find out anyone's password if incorrect password attempts were logged:

1) Go to the passwords file and modify the hash to something else, anything else. It doesn't matter that you don't know what the new password has become, as long as its different from before.
2) Wait for that user to try to login through SSH
3) They will put in their (old) correct password. Since the password hash has changed, it will be reported as an "incorrect" password, and their "incorrect" attempt will be logged, available for the admin to see.
4) ???
5) PROFIT!!

---

