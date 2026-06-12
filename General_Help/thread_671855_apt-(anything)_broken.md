---
title: "apt-(anything) broken"
date: 2008-01-19
forum: General Help
---

### Post by whytheam on 2008-01-19
So, when I open synaptic it tells me: 

```
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

Soo, when I try to install the .deb it tells me:

```
Could not open 'secondlife-install_1.18.5.3-1~getdeb1_i386.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```

Sooo, when I try to update it tells me: 

```
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 
```

I can't install or remove anything, please help! :confused:

---

### Post by zvacet on 2008-01-19
```
sudo apt-get install --reinstall  secondlife-install
```

---

### Post by whytheam on 2008-01-19
It didn't work.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by zvacet on 2008-01-19
Thaen try to delete it with 

```
sudo apt-get --purge remove  secondlife-install
```

or 

```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```

---

### Post by whytheam on 2008-01-19
Thanks! Everything is fine now.

---

