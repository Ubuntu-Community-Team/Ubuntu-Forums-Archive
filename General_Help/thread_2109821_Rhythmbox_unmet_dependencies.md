---
title: "Rhythmbox unmet dependencies"
date: 2013-01-28
forum: General Help
---

### Post by ohmy28 on 2013-01-28
Hi all 
I tried to update my rhythmbox when all of a sudden I realised it was removed from my system. I tryed install ing it again but I keep getting a messages for unmet dependencies. 

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 rhythmbox : Depends: libmusicbrainz4-3 but it is not installable
             Recommends: rhythmbox-mozilla but it is not going to be installed
             Recommends: rhythmbox-plugin-cdrecorder but it is not going to be installed
             Recommends: rhythmbox-plugin-zeitgeist but it is not going to be installed
             Recommends: rhythmbox-plugins but it is not going to be installed


Also
> The following packages have unmet dependencies:

rhythmbox: Depends: libgtk-3-0 (>= 3.2.0) but 3.6.0-0ubuntu3.2 is to be installed
           Depends: libmusicbrainz4-3 but it is not going to be installed
           Depends: librhythmbox-core6 (= 2.98.really.2.97-1ubuntu6.1~precise1) but 2.98.really.2.97-1ubuntu6.1~precise1 is to be installed
           Depends: rhythmbox-data (= 2.98.really.2.97-1ubuntu6.1~precise1) but 2.98.really.2.97-1ubuntu6.1~precise1 is to be installed
           Depends: gir1.2-rb-3.0 (= 2.98.really.2.97-1ubuntu6.1~precise1) but 2.98.really.2.97-1ubuntu6.1~precise1 is to be installed


---

### Post by srekcahrai on 2013-01-28
try changing your server from system settings > software sources

---

### Post by ohmy28 on 2013-01-28
No luck

---

### Post by srekcahrai on 2013-01-28
Post the result of
```

sudo apt-get check

```

---

### Post by ohmy28 on 2013-01-28
I tried to install libmusicbrainz4-3but I get: 
> Package libmusicbrainz4-3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libmusicbrainz4-3' has no installation candidate


---

### Post by ohmy28 on 2013-01-28
> **srekcahrai said:**
> Post the result of
```

sudo apt-get check

```

I get
> max@Dayman:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
max@Dayman:~$ 



---

