---
title: "kile help menu problem"
date: 2008-07-05
forum: General Help
---

### Post by sefaklc on 2008-07-05
Hello all ,
I've install kile to my Ubuntu 8.04.
But i have problems with the help menu in kile. 

When i try to open 'Latex Reference' from the help it gives me :

[ViewHTML] latexhelp.html (konqueror)
[ViewHTML] finished with exit status 127


When i try open 'Kile Handbook' a error message box appers and it says:

Could not launch the KDE help center:
Could not find service 'khelpcenter'


How can i fix this problem ?

Thanks a lot!

--sefaklc

---

### Post by cariboo on 2008-07-05
Have you installed khelpcenter? it is in the repositories and you can use synaptic to install it.

Jim

---

### Post by hannah-ju on 2009-04-18
Hello, 
I also install khelpcenter
but I get the same messagges

---

### Post by simcha on 2010-02-09
The file that isn't found is for some reason compressed.
If you uncompress it everything works fine.
This is where the file is on my system:
/usr/share/doc/kde/HTML/en/kile/

To fix this, open a terminal and change to this directory, and
uncpomress the file

```

cd /usr/share/doc/kde/HTML/en/kile/
sudo gzip -d index.docbook.gz

```

---

### Post by gmargo on 2010-02-09
I just installed Kile on 8.04 and both the Kile help (in khelpcenter) and the Latex reference (in konquerer) work fine.  No file decompression needed for either file (they're not compressed).  If you just installed khelpcenter, perhaps you need to quit kde and start it again?  But I've no explanation for the latexhelp.html file failure.  Is your system up to date?  Perhaps remove and reinstall kile?

---

