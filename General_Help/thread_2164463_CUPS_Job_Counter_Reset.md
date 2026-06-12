---
title: "CUPS Job Counter Reset"
date: 2013-07-31
forum: General Help
---

### Post by eyeprotocol on 2013-07-31
Hello. I wish i knew a way to completely reset the job counter of my CUPS printing server. No matter what i have tried, it somehow keeps the counter intact, while it is essential to be able to reset it to zero/one, at will. Please point me to the right direction. Thanks.

---

### Post by papibe on 2013-07-31
Hi  eyeprotocol.

Try this:
Connect to your admin cups page and delete all jobs (http:/machine_name/:631)

Then stop the service:
```
sudo service cups stop
```
Finally remove all files in the cups' spool:
```
sudo bash -c 'rm -rf /var/spool/cups/*'
```
Restart the service:
```
sudo service cups start
```
Hope it helps. Let us know how it went.
Regards.

---

### Post by eyeprotocol on 2013-07-31
Hello pabipe. I had already tried that. It does not reset the job counter. The information about the next available number must be somewhere else... :(

---

### Post by papibe on 2013-07-31
Sorry to hear that.

I edited my post and changed the rm command, could you try again?

Regards.

---

### Post by eyeprotocol on 2013-07-31
I understand that you want to me to delete everything under /var/spool/cups. This is exactly what i have tried, and failed.

I have to say that this very advice, i found on several locations and i was amazed that it was not working. But it does not.

---

