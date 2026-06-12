---
title: "Prevent X server from loading on startup"
date: 2007-05-11
forum: General Help
---

### Post by Ashex on 2007-05-11
So, I've got a Computer with Ubuntu Dapper on it that was slated for my dad. However, I've discovered my current server doesn't really cut it so I'm going to use that computer as my server. 

However, I don't want to install server edition on it (Should my dad ever decide to request it, I'd need to give it to him), So I was wondering what steps I'd need to take to disable Xserver from loading up on startup. It's already been suggested to me that I uninstall gdm, however I want to run FreeNX on it, and I think I need to have gdm installed for it to function properly.

---

### Post by heimo on 2007-05-11
This is how I do it. This should work on Feisty and probably works in Dapper too, but there's possibility that the numer 13 is different. You can easily check this by listing files in /etc/rc3.d/
```
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/K13gdm 
```

---

