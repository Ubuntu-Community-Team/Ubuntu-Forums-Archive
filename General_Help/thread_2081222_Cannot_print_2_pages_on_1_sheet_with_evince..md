---
title: "Cannot print 2 pages on 1 sheet with evince."
date: 2012-11-06
forum: General Help
---

### Post by fujisan on 2012-11-06
Hello,

I'm trying to print a pdf file (2 pages / sheet) with evince.
In tab "Page Setup", I select "Long Edge (standard)" for option "Two-sided" but I always get 1 page printed per sheet.

My colleague has no problem printing the same pdf file with the two-sided option. He gets 2 pages per sheet.

So there must be some config file that prevents me to print correctly 2 pages per sheet.

Removing the file [FONT=Courier New].config/evince/print-settings[/FONT] or copying the one from my colleague does not solve the problem.

Any idea how to solve this?

Thanks.
F.

---

### Post by Matt 6:27 on 2013-05-10
I have experienced similar problems with evince.  Check your media settings.  I have found if I use the borderless setting, it won't give you the option to print double-sided.  But if I change the media to US Letter, duplexing works for me.  I've also found Acrobat Reader (though bigger than I like) does allow duplexing on borderless settings.

---

