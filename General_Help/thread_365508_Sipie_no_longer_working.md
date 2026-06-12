---
title: "Sipie no longer working"
date: 2007-02-19
forum: General Help
---

### Post by skoalman88 on 2007-02-19
I installed sipie a while back and it was working fine. Lately, however, when I click the icon to bring up the captcha thing, nothing happens. I checked in /usr/bin and sipie is now a text file. I also cannot make it executable (unless I am doing something incorrectly). ANyone experience this and if so, do you have a solution?

Thanks

---

### Post by myname on 2007-02-19
sipie is no longer working for me either, I have a post here:

[http://www.ubuntuforums.org/showthread.php?t=365207&highlight=sipie](http://www.ubuntuforums.org/showthread.php?t=365207&highlight=sipie)


Also, the authors website cannot be found.  It would be a shame that sipie depended on his website.

Anyone have any ideas?

--kevin

---

### Post by Pseudo Idol on 2007-02-19
I have been using sipie for a few weeks now and it was working fine until Sunday around 2 am.  I hope they get the site back up and running... I usually listen most of the day when I am working.:sad:

<edit>It looks like they reinstalled apache. [http://eli.criffield.net/](http://eli.criffield.net/) leads to the default apache page.</edit>

---

### Post by tomwsmf on 2007-02-20
I am using the cli version and all I had to do was to comment out line 890 (or so)..the checkupdates function call...and it worked again.

Hope nothing is wrong with the site, or related to the recent merger.

-tomhiggins

---

### Post by Pseudo Idol on 2007-02-20
The site is back up and sipie is now working, but thanks for the info on commenting that line out.  It may come in handy. :)

---

### Post by myname on 2007-02-20
The author also updated the software to not rely on his site to work.

--Kevin

---

