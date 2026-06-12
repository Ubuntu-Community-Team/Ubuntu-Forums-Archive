---
title: "Expanding linux partition"
date: 2006-08-11
forum: General Help
---

### Post by mikewashere05 on 2006-08-11
Hey all,

I'm looking to deleting my Windows partition and expanding my Linux one to use the newly freed space. I searched around and came to the conclusion that I need to completely re-install Linux to do this. My first question, is this true?

If it is true, then I'm willing to do that. However, I've spent a good amount of time setting up Ubuntu how I like it, installing all my programs, all that kind of stuff. Can I just back *everything* up to say, an external hd, and then reload it later? How?

Thanks,
Mike

---

### Post by vigleik on 2006-08-11
Sure, you can back everything up and reinstall. If you just want to back up your home directory and reinstall the programs you have installed, that should be relatively painless. All (well, almost all) the customization is in those hidden files in your home directory. Just make a list of what you have installed first. It's also possible to back up everything, though it's a bit harder.

Another, easier solution, is to just format the windows partition and put some of your data there. For example, if you have a lot of music, move your music to the new partition and make a link from your home directory. This frees up space in your home directory (which I assume is much needed, since you've decided to sacrifice windows), and should have no adverse affects.

Vigleik

---

### Post by ifokkema on 2006-08-12
Isn't gparted capable of resizing an ext3 partition?
sudo apt-get install gparted
It's a graphical interface to partition your drives.

---

