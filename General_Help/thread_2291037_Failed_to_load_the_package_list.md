---
title: "Failed to load the package list"
date: 2015-08-17
forum: General Help
---

### Post by mike347 on 2015-08-17
I don't even know if these issues are related but I'm assuming they are. I cannot open the Software Center, it starts loading up then just crashes and then I get a small warning (like a stop sign) in the top right corner: 

an error has occured, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E: Encountered a section with no Package: Header, E: Problem with MergeList /var/lib/apt/lists
archive.ubuntu.com_Ubuntu_dists_trusty_main_i18n_Translation-en%5fUS, E:The Package lists or status file could not be parsed or opened.)' This usually means that your installed packages have unmet dependencies

I have no clue what that means, but anyway there's an option to click "preferences" which takes me to the update manager, so thats' what I did. However when I try to update, I get what appears to be the same error message: 

Failed to load the package list
This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.

Details
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%%5fUS, E:The package lists or status file could not be parsed or opened.

Any ideas how to fix this please?

---

### Post by dino99 on 2015-08-17
Dont worry about that; i know its disturbing & confusing, and should not happen, but ... this is due to the borked index while the server is itself updated & you also request a download: at that time the index is refreshed and then you get that error. Simply retry a few seconds later.

---

