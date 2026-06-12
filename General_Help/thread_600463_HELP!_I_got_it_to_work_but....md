---
title: "HELP! I got it to work but..."
date: 2007-11-02
forum: General Help
---

### Post by Dotsona on 2007-11-02
I need some help expanding my drive (using wubi), I got the alpha to finally work, but I sadly only gave myself 4gb of space to work with, I was wondering if it was possible to expand it, and if so, are there any easy to understand guides out there.

Thanks,
Andrew

---

### Post by Dotsona on 2007-11-02
Anyone? Sorry for my poor english

---

### Post by ericesque on 2007-11-02
I was kinda' wondering the same thing.  Don't sweat no reply in 3 hours.  Ago is very faithful to this community and he answers questions quite quickly for the amount of questions coming at him. 

I don't know how long you've had it running and how much effort you've put into your config, but the quickest way to get more space may simply be reinstalling...   I know that I went from fresh install to fully configed in about 3 hours yesterday.  Not all that bad.

---

### Post by ericesque on 2007-11-02
--and your english is far better than most people I've encountered whose first language is english. :)

---

### Post by Dotsona on 2007-11-02
hehe thanks, and yes I put plenty of time into it, I have been configuring compiz like crazy and been tweaking things to my liking so I really want to keep what I have.

---

### Post by ago on 2007-11-02
It is possible to extend but not completely trivial (dd seek + online resing), probably the better way is to create a second file of the desired size (dd), create ext3 on it, copy the content over, then on next reboot replace the original file with the new one. I believe that LVPM automates that process, so you may want to try that.

---

