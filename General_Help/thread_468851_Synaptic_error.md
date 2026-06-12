---
title: "Synaptic error"
date: 2007-06-09
forum: General Help
---

### Post by omarino on 2007-06-09
On 
sudo apt-get update
i get this eror. Any idea what it menas and how to solve it?
[PHP]Branje seznama paketov ... Napaka!
E: Problem parsing dependency Depends
E: Prišlo je do napake pri obdelavi gnome-applets-data (Nova razli&#269;ica 1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: Ni mogo&#269;e odprti ali raz&#269;leniti seznama paketov ali datoteke stanja.
[/PHP]

---

### Post by WakkiTabakki on 2007-06-09
Well, my Chech is almost non-existent (except for a small selection of curse words, of course) but I sort-of recognize the shape of the error message. (Edit: It was Slovienian, right? In that case, can't even swear in that language :D)

Try running these in a shell:
```

sudo apt-get clean
sudo apt-get update

```

/N

---

### Post by omarino on 2007-06-09
Thanks, but it didn't do much! I still get the same erroor, which - translated to english woul be:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing gnome-applets-data (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Thanks for suggestions.

---

### Post by WakkiTabakki on 2007-06-10
Did the command apt-get update give you the same error?

Check this out [http://www.linuxforums.org/forum/debian-linux-help/51937-aptitude-problem-problem-mergelist.html](http://www.linuxforums.org/forum/debian-linux-help/51937-aptitude-problem-problem-mergelist.html) someone seemsto have solved a similar problem simply by deleting everything i /var/lib/apt/lists

/N

---

