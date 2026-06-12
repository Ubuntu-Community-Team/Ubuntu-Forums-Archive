---
title: "Problem with update"
date: 2013-12-02
forum: General Help
---

### Post by L3monPi3 on 2013-12-02
When updating the system the update-manager fails, this is the error:

installArchives() failed: 
Extracting templates from packages: 49%%
Extracting templates from packages: 98%%
Extracting templates from packages: 100%%
Preconfiguring packages ...


Extracting templates from packages: 49%%
Extracting templates from packages: 98%%
Extracting templates from packages: 100%%
Preconfiguring packages ...


Extracting templates from packages: 49%%
Extracting templates from packages: 98%%
Extracting templates from packages: 100%%
Preconfiguring packages ...


Extracting templates from packages: 49%%
Extracting templates from packages: 98%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 field name `../../../help-langpack/ja/empathy/geolocation-not-showing.page' must be followed by colon
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


this is my ubuntu version
&#10140;  ~  lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

---

### Post by Bashing-om on 2013-12-02
L3monPi3; Hi ! Welcome back to the forum.

Let's take a peek at the file the package manager is fussing about:
Post back the output of terminal code;
```

head -10 /var/lib/dpkg/available

```
Maybe a simple fix.

[INDENT][INDENT]don't know 'till you look
[/INDENT][/INDENT]

---

