---
title: "Upgrade to edgy"
date: 2006-11-29
forum: General Help
---

### Post by marianom on 2006-11-29
Tired of several problems with sound I'll try to upgrade to edgy, searching for happiness.
My doubts:
1- will my /home as it is today survive the experience (I do have a backup of my files, it's just to know) without losing files?
2- I have a few programs compiled from source, will they be there when it's done?
3- I have a few programs in my /opt, will they be there when it's done?

I appreciate your suggestions.

---

### Post by jimbren on 2006-11-29
If /home is on it's own partition, then all you have to do is not format that partition when you're doing the installation.  Flag the partition as /home, and you're good to go.

If /home is not on it's own partition, then you're right--it will be written over.  But that is where your backups come in.  

The programs you have compiled form source will be overwritten, as will the /opt directory.  If you still have the binaries of the programs you've done from source, you can always just install them again.  

You can also opt to upgrade from the repositories, but I personally don't look to this method as an option when I'm looking to resolve a problem.  Your mileage may vary.

jimbo

---

### Post by marianom on 2006-11-29
Ok thanks for your input.
Looks like a few hours of work are ahead of me. 
Looking in the bright side, maybe I can create some howtos this time while compiling again a few programs from source.

---

