---
title: "Firefox thinks it is running.  It is not!"
date: 2006-10-21
forum: General Help
---

### Post by donz on 2006-10-21
Hi!

I have a minor problem.  Dapper Drake (32-bit AMD), updated to its latest and greatest version, is giving me problems with Firefox.

It always, even as the first thing after a re-boot, thinks that Firefox is running.  I get a dialog box that says:  "Firefox is already open but is not responding.  To open a new window you must first close the existing Firefox process or restart your system." ](*,) 

There is no sign of Firefox, mozilla or any of its relatives in top or ps.

I can run mozilla from the command line with no problem.

How can I convince it that Firefox is NOT running?

Thanks,

donz

---

### Post by taurus on 2006-10-21
Look in your Sessions to make sure you don't have firefox starting up by chance when you log in...

---

### Post by raul_ on 2006-10-21
And check in the system monitor for "firefox" or "firefox-bin" or something like  that

---

### Post by skymt on 2006-10-21
Ignore ^^them^^. You probably need to delete the Firefox lock file:```
rm ~/.mozilla/firefox/*.default/lock
```

---

### Post by marianom on 2006-10-21
I agree with skymt.
Official kb article:
[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by podunk on 2006-10-21
Did you just try to import your book marks from windows by setting up a new profile?

I had the same problem - the profile manager was open as a teeny tiny icon in the upper left of the screen - I mean very small here. :-). I right clicked and chose "Maximize" then chose the profile to start.


This happenned every start up until I re sized the profile manager down by dragging the edges with my mouse after I had maximized it up.

---

### Post by donz on 2006-10-21
Thanks all!

The suggestion to remove the lock file was close.  Tried that but it didn't work.  I renamed the *.default file to *.default.xxx, but that didn't work either.  I finally renamed .mozilla to .mozilla.xxx.  Firefox recreated .mozilla/firefox/... and worked fine after that.  It forgot all it ever knew, but I can reconstruct the bookmarks, etc.

Thanks again!!!!!   :p

---

