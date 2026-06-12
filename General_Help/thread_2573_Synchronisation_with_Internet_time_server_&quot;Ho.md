---
title: "Synchronisation with Internet time server &quot;How&quot;"
date: 2004-10-29
forum: General Help
---

### Post by united on 2004-10-29
How do I get NTP support started to enable Synchronisation with Internet time server?

thanks John

---

### Post by jdong on 2004-10-29
Welcome to the Ubuntu forums!


NTP synchronization should be automatically enabled.

---

### Post by united on 2004-10-29
That's what I thought - but mine is not. When I sudo time-admin the Synchronize clock . . . . button is not checked. When I try to check it - it tells me  "NTP support is not running". And as such it will not allow me to check it.

John

---

### Post by tanari on 2004-10-29
i have the same problem :(

---

### Post by scias on 2004-10-29
and how do i disable time synchronization?

---

### Post by cacofonix on 2004-10-29
[QUOTE=united]How do I get NTP support started to enable Synchronisation with Internet time server?

thanks John[/QUOTE]

to synchronize your time manually 
go to: [http://www.eecis.udel.edu/~mills/ntp/clock1b.html](http://www.eecis.udel.edu/~mills/ntp/clock1b.html) look for a mirror closest to you and type in sudo ntpdate and the server 
```

getafix@ubuntu ~ $ sudo ntpdate ntp0.cs.mu.OZ.AU
30 Oct 01:52:53 ntpdate[5566]: adjust time server 128.250.36.2 offset 0.010232 sec

```

Hope that helps I dont know how to make it update automatically

---

