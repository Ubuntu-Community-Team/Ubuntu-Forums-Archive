---
title: "Gnome Search Tool"
date: 2018-03-09
forum: General Help
---

### Post by makitso on 2018-03-09
I noticed that the gnome-search-tool is no longer in the universe repository.  Any thoughts?

---

### Post by mc4man on 2018-03-09
Deleted in bionic-release (Reason: (From Debian) RoM; unmaintained limited usefulness; ....) 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=885975](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=885975)

---

### Post by makitso on 2018-03-09
That's a shame :-(  Its the only full text tool that does not create an index.  In my case, I use it quite a bit since my file system is dynamic.

---

### Post by Olivier Berten on 2018-04-24
+1 :-(

---

### Post by logix2 on 2018-04-26
You can give Catfish, an Xfce tool, a try: [https://bluesabre.org/projects/catfish/](https://bluesabre.org/projects/catfish/) It should be available in the Ubuntu repositories.

---

### Post by Mehmet_nal on 2018-04-27
Can gnome-search-tool be brought back to Ubuntu 18.04? I used it to search text in c++ files. Catfish is not nearly as practical and functional as gnome-search-tool. Or is there some other alternative which is as good as gnome-search-tool?

---

### Post by cariboo on 2018-04-27
Thread moved, as Bionic has been released.

---

### Post by dragonfly41 on 2018-04-27
I use searchmonkey.

---

### Post by logix2 on 2018-04-27
You can also use an IDE / code editor to search for text in files. Try Sublime Text 3 or Atom.

---

### Post by Mehmet_nal on 2018-04-27
I used gnome-search-tool for searching all text files under a directory that contained a certain text. I'm not sure a code editor can have such a built-in utility.

I tried searchmonkey, it's quite good, almost the same as gnome-search-tool.

---

### Post by Mehmet_nal on 2018-04-27
mate-search-tool is the same as gnome-search-tool and can be installed in 18.04.

---

### Post by mc4man on 2018-04-28
> **Mehmet_nal said:**
> Can gnome-search-tool be brought back to Ubuntu 18.04? I used it to search text in c++ files. Catfish is not nearly as practical and functional as gnome-search-tool. Or is there some other alternative which is as good as gnome-search-tool?
While it doesn't seem to do anything a file manager search can't do if you want it then just download the 16.04 .deb & install with apt.
[https://packages.ubuntu.com/xenial/gnome-search-tool](https://packages.ubuntu.com/xenial/gnome-search-tool)

---

### Post by Mehmet_nal on 2018-04-28
I think you can't search text inside text files using nautilus or nemo or any other file manager. You can only search text in file names.

---

### Post by vanadium on 2018-04-29
Searching text inside text files using the file manager (nautilus) requires tracker. In an Ubuntu install, tracker is not installed by default. It can hog quite some resources. Some of the gnome shell utilities including "Documents" and "Photos" also require tracker. These also do not come with a default Ubuntu installation.

---

### Post by kazakore on 2018-04-29
Personally I just use the grep command, as per the top answer to the Q
[https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux](https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux)

---

### Post by edwardsah3-3 on 2018-08-31
Wow, I'm going to miss that. I used it all the time. Is there any independent repository keeping it alive?

---

### Post by Ophidion on 2018-09-01
Follow this link: [https://www.ubuntuupdates.org/package/core/artful/universe/base/gnome-search-tool](https://www.ubuntuupdates.org/package/core/artful/universe/base/gnome-search-tool) then download the package that matches your system 32 or 64 bits. 
open terminal then type ```
sudo apt install gdebi
``` hit enter
After install finish go to where you downloaded gnome-search-tool package right click it then choose > ...gdebi then you are DONE!:P

---

### Post by edwardsah3-3 on 2018-09-01
Again, Wow!. Thanks. it worked perfectly. Nice to have this back.

---

### Post by raleigh3 on 2018-09-01
> **dragonfly41 said:**
> I use searchmonkey.

Thanks for searchmonkey.

I love it.

---

### Post by OldGrampa on 2018-09-28
I use KFind, and search for text inside most files.

---

