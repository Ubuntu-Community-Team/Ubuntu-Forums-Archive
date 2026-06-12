---
title: "update Issue"
date: 2013-05-02
forum: General Help
---

### Post by CCgirl6690 on 2013-05-02
hello . hope yall are fine 
when i try to do an apt-get update  i get this error  and i dunno how to fix it 

[HTML]E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_i18n_Translation-en%%5fUS, E:The package lists or status file could not be parsed or opened.[/HTML]

Help Please if you can 
Thank you

---

### Post by grahammechanical on 2013-05-02
I have had that error in the past and it has been with that file i18n_Translation. I fixed by running

```
sudo rm /var/lib/apt/lists/* -rf
```

followed by 

```
sudo apt-get update
```

The first command removes/deletes (rm) all the scripts/files in the lists directory, The second command replaces then with new ones.

When we run an update the system compares the information in the scripts directory with the information on the servers and then works out what libraries can be updated. I think the Update Manager expects to find some information at the very top of each file. Sometimes the script has a blank line at the top and this is causing Update Manager to trip up. This is how I see what is happening here.

Regards.

---

