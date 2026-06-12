---
title: "Ever since ubuntu 15.10 update, sftp does not work with editors (sublime, etc)"
date: 2015-11-30
forum: General Help
---

### Post by me-patrickavella on 2015-11-30
I've been googling and not finding much other than a few whispers of other people having the same issue. 

My normal day consists of me typing an sftp address into nautilus, and editing the files there with sublime. Ever since the 15.10 update editors will just open a blank file. The ONLY editor that still works is gedit for some reason. But sublime 2, sublime 3, and atom, have all stopped working.

I really need this to work again, but I don't even have the slightest idea about what changed or what to do. I either need to get this working with sublime or atom again, or I need an editor similar to those that still works. Gedit just doesn't cut it for me unfortunately. 

Any help is sooo greatly appreciated. 

If it helps any, this is a system76 laptop that was previously running the LTS. The update went awry and I ended up doing a full install. Everything else works mostly normal. Just the sftp support no longer works in external programs.

---

### Post by me-patrickavella on 2015-12-01
Hello everyone, I just want to follow up on my own thread.

I deleted the contents of the ~/.ssh folder (known hosts, my pre-existing keys). And after a few restarts knock on wood it seems to be working again... if haphazardly. Seems like a restart fixes it but I've had it go back to not working as well requiring another restart. 

I have no clue what causes it or how to debug it. I just know purging ~/.ssh got it to work some of the time.

Thanks

---

### Post by Habitual on 2015-12-01
The fix is as strange as the symptom.
I''ve had Filezilla +sublime_text2 + the same ssh_keys for years and I've never run into this.

---

