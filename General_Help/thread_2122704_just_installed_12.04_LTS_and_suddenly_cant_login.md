---
title: "just installed 12.04 LTS and suddenly cant login"
date: 2013-03-05
forum: General Help
---

### Post by kline on 2013-03-05
guys, 
this is a bizarre an event as i have even seem in my off-again/on-again times i've been using ubuntu.  last year i quit freebsd because it was too hard to keep the ports current.  now, all  3 tower cases are using some flavor on linux.   here's my trouble:  i was tuned into some URL on my ubuntu box when i realized it   was time to switch over to Ustream to watch a live stream.  the stream hung immediately,; nothing i could do could get  the stream going =Or=  to get anything else going.  i used the mouse to shutdown and reboot.  

when the KDE interface showed "kline", i tried to login.   i couldn't.  i figured i must be messing up my 8-byte password.  after trying  this very slowly and failing  5 or 6 times, i gave up.  my  12.04 LTS  kept presenting the KDE login.  so used my  kvm switch and brought up   an older   interal dual.  with this i should reach my newer KDE tower case.   everything was these same as previous.  

I have not had much success with this forum in the past couple/three years.   but maybe someone of you can help me this time....

tx in advance!

gary kline

PS:  everything is safely backuped on on my two othrt tower cases and ever my =laptop=.  i just need help getting back into my default KDE desktop.  {none of the secure logins spawned a graphic shell.}

---

### Post by UltimateCat on 2013-03-05
Hi:

You could re-set your password-

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


Or you could edit your /etc/password file:
[http://manpages.ubuntu.com/manpages/intrepid/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/passwd.5.html)

Hope this helps

---

### Post by kline on 2013-03-06
no joy.

i reboot using the KDE screen, and holding down the "shift" key does nothing.  from another desktop, i can ssh into kline; i can use sudo.  nothing seems to be amiss.  it's just that when i login as kline on the KDE screen that i get an immediate return asking me me to re-login as kline.  it seems to not  recognize me.  i'm stumped.

---

### Post by kline on 2013-03-19
Apologies for the delay in this upgrade, but after spending two days, i finally did a re-install frfom scratch.  instead of getting my familiar kde screen, i got gnome.  i dont know.  maybe it's t ime to finish my voice by computer program for the disabled and hang it up... .

If there is any way of auto-switching over to kde, i       would like the magic incantation.

---

