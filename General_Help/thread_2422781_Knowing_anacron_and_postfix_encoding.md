---
title: "Knowing anacron and postfix encoding"
date: 2019-07-12
forum: General Help
---

### Post by BmrfxKG on 2019-07-12
Hi,

I'm using blackblaze to store my data for a backup. I have a  script and I'm using anacron to run it. I regularly get an email with  the text "WARNING:b2sdk.sync.report:could not output the following line  with  encoding None on stdout due to 'ascii' codec can't encode character  u'\u2013' in position 31: ordinal not in range(128): upload Podcast/Song  of the Day – KUTX/Lee-Ann-Womack-Hollywood.mp3" i got in contact with  the B2 team and they told me that tre cause was an encoding issue. I  already check b2 encoding and is UTF8. What can I find the encoding for  anacron and postfix?

I'm using a system68 laptop with ubuntu 19.4 anacron 2.3 and postfix 3.3.2

---

### Post by TheFu on 2019-07-12
Email needs to be 8-bit ASCII clean.  If you want to upload binary files, then either mime-encode it or uuencode it BEFORE trying to sent it through any email system.

anacron, like all cron tools outputs stdout and stderr to the MTA on the system.  If you don't want this, then redirect one or both somewhere else.  Many people want stderr to be emailed and send just stdout to /dev/null.

BTW, this is the wrong sub-forum for this type of question. > Forum Feedback and Help is not for general support enquiries

---

### Post by wildmanne39 on 2019-07-12
*Thread moved to **General Help a more appropriate sub-forum**.*

---

