---
title: "How I got suspend to work"
date: 2007-01-31
forum: General Help
---

### Post by oracle5 on 2007-01-31
I have an ATI Radeon Xpress 200M with the fglrx driver.

I typed 

> sudo gedit /etc/default/acpi-support

Then found this section

> # Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

and changed it to

> POST_VIDEO=false

But now I have a problem when reconnecting to my wired network. I end up having to reboot to reconnect because even deactivating and reactivating the device doesn't work. If anyone has any suggestions on how to fix this it would be appreciated. 

oracle5

---

### Post by motoperpetuo on 2008-01-30
this seems to have maybe worked for me. at least, i was able to come back after having my laptop's lid closed for a few minutes (which should have caused it to go into suspend) and get it started again without my GUI getting hopelessly scrambled to the point of having to reboot, which usually happens. i'll test again tomorrow after having it closed all day. that's when it usually goes completely haywire.

---

