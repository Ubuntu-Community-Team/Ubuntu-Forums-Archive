---
title: "Screen flicker with Live USB--13.04 and Toshiba Satellite with Radeon"
date: 2013-07-19
forum: General Help
---

### Post by kokoshmusun on 2013-07-19
I was hoping linux could once again save me from Win (this time 8... just horrible).  I got a new Toshiba Satellite laptop L830-135 with AMD Radeon card.  I tried Ubuntu 13.04 on live USB that I made with unetbootin.  It booted and I could see the desktop but it flickered like crazy.  I then tried Linux Mint 15 with Cinnamon just to see if the same happens and it was worse.  I couldn't even see the desktop. 
  Anybody know a way out of this?

---

### Post by kokoshmusun on 2013-07-19
SOLVED:

This is really interesting.  I had just given up and thought "ok, at  least I can downgrade to Win 7" and then it wouldn't boot into the Win 7  USB.  So I figured out I have to change boot mode from UEFI to CSM but  it was grayed out.  I followed this video:

[http://www.youtube.com/watch?v=tHJ7qiKC0go](http://www.youtube.com/watch?v=tHJ7qiKC0go)

And  when I changed the boot mode to CSM, I tried the ubuntu USB to  see if the flickering is gone and voila!  The same happened with mint USB.

---

