---
title: "Difference between &quot;shutdown -r now&quot; and &quot;reboot&quot;"
date: 2008-03-27
forum: General Help
---

### Post by sri1025 on 2008-03-27
What is the difference? Can someone explain me? I have tried both and they seem to be doing the same thing.

Thanks!

---

### Post by Existentialist on 2008-03-27
Under normal circumstances reboot just makes the same "shutdown -r now" call, but under some run levels (1 or 6 I believe)  it preforms a hard reboot.

---

### Post by nick_h on 2008-03-27
From the man page for reboot:
> "When called without the -f option, they simply invoke shutdown with the appropriate arguments."

For details type:
```
man reboot
```

---

### Post by dcstar on 2008-03-27
And all shutdown really does is put out nice messages to the system (and users) before using the requested init run level call - so there's nothing much in all of them when it comes to actual end result.

I still use **init 0** to shutdown, just an old Unix habit (and less to type) I suppose......

---

