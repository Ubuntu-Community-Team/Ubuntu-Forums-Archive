---
title: "update with no internet"
date: 2006-08-06
forum: General Help
---

### Post by pnocti on 2006-08-06
i've got an dapper box with no internet connection.

got an internet connected xp in the office.

googled for howtos on updating ubuntu with no internet, all they say is do a 'apt-get -qq --print-uris install pkg`

but how can i do that if the pkg lists (in /var/lib/apt/lists/*) isn't updated in the first place?

i asked a friend to email me a tarball of his lists, but this method sucks.

is there a better way to update the lists on a non-connected box?

thanks in advance.

---

### Post by ajgreeny on 2006-08-06
From your XP work box you can just download the packages you want/need and burn to a CD.  Then on your ubuntu box copy the package files to your /var/cache/apt/archives and use synaptic (I think this works OK) or you can just right click on the packages on the CD and click install, then dpkg will take over.

My one uncertainty is the url's you need to download the packages, but I'm sure someone else will be able to help out here.

---

### Post by pnocti on 2006-08-06
> **ajgreeny said:**
> From your XP work box you can just download the packages you want/need and burn to a CD.  Then on your ubuntu box copy the package files to your /var/cache/apt/archives and use synaptic (I think this works OK) or you can just right click on the packages on the CD and click install, then dpkg will take over.

My one uncertainty is the url's you need to download the packages, but I'm sure someone else will be able to help out here.

That's what I've been doing and it's such a chore to trace dependencies on packages.ubuntu.com and download them, not knowing which packages I already have on my box at home.

What I'd like is a list of links, like the output of 'apt-get -qq --print-uris install <pkg>' and feed that to a download manager on XP and sit back and wait for it to finish the download, go home, copy it to the archives directory and apt-get install <pkg> or synaptic will do the rest.

I found files in [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) that resembles the files in my /var/lib/apt/lists/*, except for the filenames. I'm thinking: download the lists there, rename, copy to my lists/ directory and do the 'apt-get -qq --print-uris install <pkg>' to generate the links, etc, etc.

If anyone can confirm that the lists in [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) is the same as the ones that get downloaded when someone on a connected ubuntu box does 'apt-get update' then I think I can cook up a simple Perl script to take care of the renaming/copying process to /lists/*

---

