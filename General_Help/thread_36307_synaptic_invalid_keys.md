---
title: "synaptic invalid keys"
date: 2005-05-22
forum: General Help
---

### Post by bobgreen5s on 2005-05-22
When I try to update the package list in synaptic, (it says your package list is more then 48 hours old) it downloads and gives me this error:

```
W: GPG error: http://archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

Don't really know what it means.

Any help is appreciated.  :wink:

---

### Post by blouzak on 2005-05-22
[QUOTE=bobgreen5s]When I try to update the package list in synaptic, (it says your package list is more then 48 hours old) it downloads and gives me this error:

```
W: GPG error: http://archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

Don't really know what it means.

Any help is appreciated.  :wink:[/QUOTE]


Have you added the extra repositories according to the [http://ubuntuguide.org/](http://ubuntuguide.org/)  ?

Have you tried this?

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update

---

### Post by bobgreen5s on 2005-05-22
did both things and still get the same error 

 :?

---

### Post by blouzak on 2005-05-22
ok. sorry, what I suggested is supposed to work for the marillat repository  8-[ 

tried Synaptics->Settings->Repositories->Authentication->Restore default keys?

---

### Post by blouzak on 2005-05-23
i don't know if there is anything you can do about it!

check this 
[out](http://www.ubuntuforums.org/showthread.php?p=181321#post181321)

---

### Post by bobgreen5s on 2005-05-23
yeah that doesnt work either :(

---

