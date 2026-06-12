---
title: "crashed while using guest account, that guest id still exists; can I delete it?? how?"
date: 2015-09-12
forum: General Help
---

### Post by a-you on 2015-09-12
There were two users logged in, one was my normal username account and the other was a "guest session" login. Oddly, the computer crashed while that guest session was active. By that I mean that the screen all of a sudden became just blank white. Everything became unresponsive and the only way out seemed to be to restart by holding the power button for some seconds, which I did. After that I did

```
sudo touch /forcefsck
```

and restarted. All seems to be well. But now if I cat /etc/passwd I see that that guest session ID is still there as a user. The temporary home in /tmp has been deleted though. Can I delete that user?? And what would be the proper way to go about that? And is there anything else that I should do or be aware of in this situation? The guest group seems still to exist too, so I'd like to delete that as well.

Thanks in advance!!

This is ubuntu studio 14.4, so perhaps more like xubuntu than vanilla ubuntu.

---

### Post by dino99 on 2015-09-12
[http://ubuntuforums.org/showthread.php?t=1024371](http://ubuntuforums.org/showthread.php?t=1024371)
[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

---

### Post by a-you on 2015-09-13
Thanks dino99 for your thoughts but I guess I didn't make clear enough what I was asking. I don't want to disable the guest session feature, nor do I want to customize it (actually I have already customized it).

The issue for me at the moment is that while a guest session was logged in the system crashed. The problem now is that that guest user---its uid and group---still exists. In other words, they were apparently not deleted because the session was cut short and not allowed to end normally.

I'm simply asking if anybody might be able to tell me please what I need to do to perform all the steps that the system would have performed to eliminate all traces of that guest user, as would have happened if the session had ended normally.

I guess that I must use the deluser command to remove the user and its group, but I have no idea what else a guest session creates or does or sets up, all of which would normally be temporary, but in this special case have become permanent.

---

### Post by a-you on 2015-09-15
I removed that user and its group and reset the guest session stuff. I still don't know what all the guest session does but assuming that all it does is to basically copy everything from /etc/guest-session/skel to a temporary HOME in /tmp then I guess it's now back to normal.

---

