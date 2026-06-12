---
title: "Bluetooth Dialup Stopped Working"
date: 2007-02-15
forum: General Help
---

### Post by igb on 2007-02-15
I have been using my Nokia E61 as a bluetooth modem for some time after following the various guides on these forums. However, it's suddenly stopped working. The logs show:

```
Feb 15 12:21:42 scamper chat[5136]: abort on (\nERROR\r)
Feb 15 12:21:42 scamper chat[5136]: abort on (\nNO ANSWER\r)
Feb 15 12:21:42 scamper chat[5136]: abort on (\nNO CARRIER\r)
Feb 15 12:21:42 scamper chat[5136]: abort on (\nNO DIALTONE\r)
Feb 15 12:21:42 scamper chat[5136]: abort on (\nRINGING\r\n\r\nRINGING\r)
Feb 15 12:21:42 scamper chat[5136]: send (^MAT^M)
Feb 15 12:21:42 scamper chat[5136]: expect (OK)
Feb 15 12:21:42 scamper chat[5136]: warning: read() on stdin returned 0
Feb 15 12:21:42 scamper chat[5136]: Failed
Feb 15 12:21:44 scamper pppd[5133]: Exit.
```

I haven't changed my hardware or dialup configuration. Google doesn't find any similar errors. It looks as though the chatscript suddenly can't read from the modem. Anyone got any ideas?

Ian.

---

