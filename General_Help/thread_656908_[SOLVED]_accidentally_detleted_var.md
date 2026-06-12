---
title: "[SOLVED] accidentally detleted /var"
date: 2008-01-03
forum: General Help
---

### Post by sandclock on 2008-01-03
Hi 
I accidentally deleted /var directory then i had error "server authorization directrou (daemon/serveauthdir)" but then i got around this by changing gdm.conf that solved problem some what and let me login in to gdm but now it gives me error "failed to initialize HAL"
any one has ideas?
Regards
Nik

---

### Post by ~LoKe on 2008-01-03
I think you're screwed...there is a lot of stuff in /var...a lot of essential stuff.

---

### Post by sandclock on 2008-01-03
ooops
then what do i do?
Regards
Nik

---

### Post by ~LoKe on 2008-01-03
> **sandclock said:**
> ooops
then what do i do?
Regards
Nik

My suggestion would be to reinstall, but sit tight and maybe someone more qualified will come by and give you a much simpler solution.

---

### Post by sandclock on 2008-01-03
hummm okay i guess i will wait for better solution than reinstall hopefully some one has that solutions :):lolflag:

---

### Post by rubicon on 2008-01-03
You may also boot via Live-CD and copy /var directory to your /media/sda1/var (replace it with actual path). I think it worth trying in this situation :) 
Hope this helps without much pain!

---

### Post by harold4 on 2008-01-03
The live CD idea is worth a shot.  Worst case, you can backup needed info while using the live CD.

Personally,  I would "sudo mkdir /var," restart and see what happens.

---

### Post by sandclock on 2008-01-03
thanks copying from live cd solved the issue
Thanks
NIk

---

