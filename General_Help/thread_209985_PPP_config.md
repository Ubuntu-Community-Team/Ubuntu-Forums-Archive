---
title: "PPP config"
date: 2006-07-06
forum: General Help
---

### Post by cssutto on 2006-07-06
I am setting up a Kyocera card for wireless broadband and I have the card identified, pon talks to the card, it dials out....

The log shows everything going fine until this point.

Jul  6 01:00:49 localhost chat[11700]: abort on (BUSY)
Jul  6 01:00:49 localhost chat[11700]: abort on (NO CARRIER)
Jul  6 01:00:49 localhost chat[11700]: abort on (VOICE)
Jul  6 01:00:49 localhost chat[11700]: abort on (NO DIALTONE)
Jul  6 01:00:49 localhost chat[11700]: abort on (NO DIAL TONE)
Jul  6 01:00:49 localhost chat[11700]: abort on (NO ANSWER)
Jul  6 01:00:49 localhost chat[11700]: abort on (DELAYED)
Jul  6 01:00:49 localhost chat[11700]: send (ATZ^M)
Jul  6 01:00:50 localhost chat[11700]: expect (OK)
Jul  6 01:00:50 localhost chat[11700]: ATZ^M^M
Jul  6 01:00:50 localhost chat[11700]: OK
Jul  6 01:00:50 localhost chat[11700]:  -- got it
Jul  6 01:00:50 localhost chat[11700]: send (ATDT3394202^M)
Jul  6 01:00:50 localhost chat[11700]: expect (CONNECT)
Jul  6 01:00:50 localhost chat[11700]: ^M
Jul  6 01:01:07 localhost chat[11700]: ATDT3394202^M^M
Jul  6 01:01:07 localhost chat[11700]: NO CARRIER
Jul  6 01:01:07 localhost chat[11700]:  -- failed
Jul  6 01:01:07 localhost chat[11700]: Failed (NO CARRIER)
Jul  6 01:01:08 localhost pppd[11682]: Exit.
Jul  6 01:01:31 localhost kernel: [17185238.

What do I need to change?

CSSJR

---

