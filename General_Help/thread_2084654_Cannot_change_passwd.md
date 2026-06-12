---
title: "Cannot change passwd"
date: 2012-11-16
forum: General Help
---

### Post by jon80 on 2012-11-16
I loaded my machine in recovery mode([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)), however, when typing in the new password the following is returned.  I am logged with the root user.
Authentication token manipulation error
password unchanged

I cannot paste the contents of my /etc/shadow file, however, it includes my username, encrypted password, and, numbers which I cannot interpret.  Suggested at [http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error).

Any ideas?

---

### Post by steeldriver on 2012-11-16
sounds like you maybe missed this step?

>  In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 
```
mount -o rw,remount /

```

---

