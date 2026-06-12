---
title: "ssh -X forwarding times two"
date: 2004-11-10
forum: General Help
---

### Post by viniosity on 2004-11-10
My office is set up so that there are a few machines (email server, web server) that can be accessed from the outside world.  The rest of the machines (like the one at my desk) has an internal IP like 192.168.1.x.  SSH forwarding was enabled on one of the external machines so conceivably I can run firefox from anywhere assuming it is installed on that machine.  

The problem is that most of the apps I want to run are on my local desktop machine.  If I ssh -X into the external box and then ssh -X to my local machine again and then try to run an app it doesn't work.  Is there some way around this?  Do I have to set my display somewhere?  

(note that using ssh -X works on my desktop machine from within the office so I know it's set up ok)

---

### Post by Steve413z on 2008-05-23
firefox X forwarding is weird, if you want to use x-forwarding on firefox:

```
**User@RemoteMachine:~$** firefox -no-remote
```

---

