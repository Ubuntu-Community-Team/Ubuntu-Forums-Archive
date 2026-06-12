---
title: "auto remove things not needed?"
date: 2007-12-14
forum: General Help
---

### Post by android6011 on 2007-12-14
I just did a reinstall and I had somethings to add/make so I had to install things like libgtk2.0-dev and build-essential etc. I noticed this takes up a lot of room and I was wondering if there is a way to search for things I dont need or use like these and have them removed. can I just go ahead and remove the couple things i installed like libgtk2.0-dev because that is only needed for building right? is it needed after i compile and install? thanks

---

### Post by overdrank on 2007-12-15
> **android6011 said:**
> I just did a reinstall and I had somethings to add/make so I had to install things like libgtk2.0-dev and build-essential etc. I noticed this takes up a lot of room and I was wondering if there is a way to search for things I dont need or use like these and have them removed. can I just go ahead and remove the couple things i installed like libgtk2.0-dev because that is only needed for building right? is it needed after i compile and install? thanks

Hi have you tried the commands 
```
sudo apt-get autoremove
sudo apt-get autoclean
```

---

