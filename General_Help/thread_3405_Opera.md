---
title: "Opera"
date: 2004-11-05
forum: General Help
---

### Post by Allen S on 2004-11-05
Has anyone had any luck in getting Opera installed under Ubuntu?

---

### Post by ming0 on 2004-11-05
Yes, just grab the opera 7.54 .deb package from opera.com and then do:

dpkg -i /path/to/opera-7.54.deb

works well for me...

---

### Post by claymore on 2004-11-06
I got it working by downloading the tar.gz file, extracting it then running the install script with sudo.

---

### Post by cseg on 2004-11-06
If you get the .deb, you probably want to get the /static/ one.

---

### Post by Allen S on 2004-11-06
Thanks, the statc one did the trick for me. I was getting a conflict because I have a amd64 and the package was for i386 so I use --force-architure to get around it.

I like Thunderbird but have been suing Opera for several years and am more comfortable with it.

---

