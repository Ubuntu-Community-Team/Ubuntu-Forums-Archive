---
title: "preinstall calendar in Evolution"
date: 2008-03-12
forum: General Help
---

### Post by jmehdi on 2008-03-12
Hi,

I'd like to preinstall calendars in Evolution for the users of my computer. I mean when I create a new user I want that custom calendars be automatically installed for him.
Is there a way to do that? (maybe with the /etc/skel folder?)

---

### Post by Suparious on 2008-03-13
/etc/skel sounds reasonable.

have a look at your ~/.evolution/calendar folder. 

I created a calendar in evolution and I went through all the files in ~/.evolution/calendar to find that nothing was personalized to my user account specifically. There is a good chance that simply copying ~/.evolution/calendar to /etc/skel/.evolution/calendar would work.

---

### Post by jmehdi on 2008-03-15
I did as you said, customized my calendar, copied ~/.evolution/calendar to /etc/skel/.evolution/calendar, created a user then logged in using this new user... but my customizations were not here... :(

---

