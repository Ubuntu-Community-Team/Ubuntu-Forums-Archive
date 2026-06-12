---
title: "Amazon prime video problems"
date: 2015-07-05
forum: General Help
---

### Post by skippylou on 2015-07-05
Ububtu 14.04LTS fresh install and updated
Firefox 38.0
Adobe Flash 11.2.202.468

Amazon Prime video tells me to update my browser or flash plugin.  I believe these are most recent versions.

Suggestions or solutions?  Thanks

---

### Post by papibe on 2015-07-05
Hi skippylou.

You need to install hal:
```
sudo add-apt-repository ppa:mjblenner/ppa-hal

sudo apt-get update

sudo apt-get install hal
```
Then restart Firefox.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by skippylou on 2015-07-05
That was easy.  Many thanks.

---

### Post by rem8114 on 2015-10-23
Amazon prime has been working for some time (14.04 w/firefox v38? w/pipelight), but yesterday I got the message "This web browser isn't compatible with Amazon Video".  I upgraded to FireFox 41.0.2 and re-did pipelight (Silverlight 5.1 add-on is activated).  Still gives me the same message.  Any ideas?  I have tried HAL install as well, but no success.  Did Amazon change something???

---

### Post by SeijiSensei on 2015-10-23
Do you use an add-on to spoof your User-Agent string?  I had to change the version number in the string I report to 41 when Netflix complained my browser was out-of-date.

You might also want to take a look at the most recent postings in this Amazon discussion thread.  People there have found Google Chrome works with Amazon Instant without any fiddling: [http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_t_rvt_np?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=9&cdThread=Tx167YET6CH0PQI#CustomerDiscussionsNew](http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_t_rvt_np?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=9&cdThread=Tx167YET6CH0PQI#CustomerDiscussionsNew)

---

