---
title: "filezilla ftp client in the repository?"
date: 2007-02-25
forum: General Help
---

### Post by bone2006 on 2007-02-25
When you install something from the repository, will it notify when there's an update just like anything that came with ubuntu?  

I really like filezilla, especially since I can use it on windows or ubuntu.  I was actaully using it before I even started to use linux.  It would be nice if I could add it to the repository so that it does updated automatically or is that not possible?

This is where I downloaded the deb file to install [http://linuxappfinder.com/package/filezilla](http://linuxappfinder.com/package/filezilla) and I see that there's a link that says Available deb Repositories, but those commands don't work, I'm guessing becasue it's only for debian distro?

The link is beta 2, but beta 5 is already out.

---

### Post by Maestro23 on 2007-02-25
Yeah, I saw that Ver 3.0 beta 2-2 is in the repositories. Did you add the debian repositories for the latest beta in the /etc/apt/sources.list ?
[http://linuxappfinder.com/addrepo](http://linuxappfinder.com/addrepo)

Then run 

> sudo apt-get update

---

### Post by bone2006 on 2007-02-25
maybe it's my ignorance, but I never added the repository to the sources.list file.  One reason is that doesn't ubuntu require a key as well, because I added some repository a long time ago and when I do updates, it keeps asking me about some key. 

Second is that it seems if the repository only has the older version.  Is it possible that ubuntu would put the software on their repository someday?  When I go to filezilla's website it seems that they say debian has it in their repository, thought that they shared some repositories?  

Maybe when it's final it can be added to ubuntu's repository?  It's free and open source and the best ftp client I've used and now that it's on linux it just seems like a major improvement.

---

### Post by Maestro23 on 2007-02-25
> **bone2006 said:**
> maybe it's my ignorance, but I never added the repository to the sources.list file.  One reason is that doesn't ubuntu require a key as well, because I added some repository a long time ago and when I do updates, it keeps asking me about some key. 

Second is that it seems if the repository only has the older version.  Is it possible that ubuntu would put the software on their repository someday?  When I go to filezilla's website it seems that they say debian has it in their repository, thought that they shared some repositories?  

Maybe when it's final it can be added to ubuntu's repository?  It's free and open source and the best ftp client I've used and now that it's on linux it just seems like a major improvement.

The new version will eventually make it into the Respositories. Just takes time.  I used it on the XP side of the house, and like you am glad linux has it now.

---

