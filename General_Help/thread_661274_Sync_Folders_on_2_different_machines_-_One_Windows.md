---
title: "Sync Folders on 2 different machines - One Windows One Ubuntu"
date: 2008-01-07
forum: General Help
---

### Post by geoffcj on 2008-01-07
Ok, I've just spent about three hours looking at options online to do what I want, and I'm more confused than ever.  

I have a laptop that runs windows, and I'll keep running windows, as there are 3-4 pieces of software I just can't commit to abandoning, and I use the windows laptop when I travel. 

I also have a Ubuntu box at home.  I use this 95% of the time, and do most of my work on it. 

I have a couple folders that I'd like to share between the two, but I'd like it to occur over the internet.  I have an FTP account I can use, but I'm open to other ideas. 

What I'd really like to be able to do is when I'm done working at home, click a "sync" button and have all my files sync to something online from the linux box.   Then when I get to a hotel, I open my laptop and hit Sync again, and things show up there.   I'd prefer not to leave the linux box running at home for energy conservation reasons.  Then when I'm done with the laptop, I hit sync again, and then at home, fire up the linux box. 

I looked at Mozy and Unison and rsync.   I even considered using google documents, but it doesn't work for some of the filetypes....

Any ideas?  Suggestions on step-by-step tutorials are appreciated. 
Geoff

---

### Post by der_joachim on 2008-01-08
How about an external harddisk, combined with (g)rsync? Rsync has a windows version as well. If you are concerned about security, you can encrypt it with truecrypt (which is cross-platform as well).

---

