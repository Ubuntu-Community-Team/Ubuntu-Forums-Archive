---
title: "Query about 'search' in ubuntu 13.04"
date: 2013-06-30
forum: General Help
---

### Post by Harshwardhan on 2013-06-30
Installed Ubuntu 13.04 about a week ago. 

Its on a 120G SSD along with 5 other HDDs (9TB of NTFS) for storage. 

I has installed and used 12.04 briefly last year and iirc, one just had to hit the super key and start typing to search for stuff.

In 13.04 though it does not search in the storage drives, only the home folder. 
Coming from W8 this is quite annoying. Cause I was under the impression that ubuntu search is much more efficient than windows.  

Do I need to start indexing or something? I can't figure it out. Please help.

---

### Post by mc4man on 2013-06-30
The new search in nautilus searches recursively starting at the directory where the search is initiated
So if you open at your home folder it will search there & in any dir/sub dir.'s inside your home folder.

If you wanted to search an external partition then open that partition in nautilus & search from there.
If you wanted to search the complete filesystem then you'd go to / in nautilus & search from there (Computer

Obviously the farther away the longer a search may take so makes sense to shorten the search paths 

If you want,  the old "Search for Files' app can be installed & used -  screen
```
sudo apt-get install gnome-search-tool
```

Myself find the nautilus search to work quite well & rarely use gnome-search-tool anymore

---

### Post by Harshwardhan on 2013-06-30
mmkay.  
Thanks for the quick reply Mc4man!

---

