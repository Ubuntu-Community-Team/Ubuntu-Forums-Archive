---
title: "How can I remove old sandbox folders?"
date: 2023-07-02
forum: General Help
---

### Post by Dennis N on 2023-07-02
I would like to remove some obsolete folders from /run/user/1000/doc. I think these were sandboxes for flatpak applications. They are long done with but persist. I have been unable to remove them. Some information follows:

```
dmn@Kayleigh:/run/user/1000/doc$ tree
.
&#9500;&#9472;&#9472; 596c6cde
&#9500;&#9472;&#9472; b4dc3859
&#9500;&#9472;&#9472; by-app
&#9474;** &#9500;&#9472;&#9472; com.github.dail8859.NotepadNext
&#9474;** &#9474;** &#9492;&#9472;&#9472; ed999bb
&#9474;** &#9500;&#9472;&#9472; io.gitlab.adhami3310.Converter
&#9474;** &#9474;** &#9500;&#9472;&#9472; 596c6cde
&#9474;** &#9474;** &#9500;&#9472;&#9472; b4dc3859
&#9474;** &#9474;** &#9500;&#9472;&#9472; cdcce87
&#9474;** &#9474;** &#9492;&#9472;&#9472; d19de800
&#9474;** &#9500;&#9472;&#9472; org.mozilla.firefox
&#9474;** &#9474;** &#9492;&#9472;&#9472; dcd45c64
&#9474;** &#9492;&#9472;&#9472; snap.snapd-desktop-integration
&#9500;&#9472;&#9472; cdcce87
&#9500;&#9472;&#9472; d19de800
&#9500;&#9472;&#9472; dcd45c64
&#9492;&#9472;&#9472; ed999bb


```
The folders in question are those with the random hex digit names.

Ownership and permissions:

```
dmn@Kayleigh:/run/user/1000/doc$ ls -l
total 0
drwx------ 2 dmn dmn 0 Dec 31  1969 596c6cde
drwx------ 2 dmn dmn 0 Dec 31  1969 b4dc3859
dr-x------ 2 dmn dmn 0 Dec 31  1969 by-app
drwx------ 2 dmn dmn 0 Dec 31  1969 cdcce87
drwx------ 2 dmn dmn 0 Dec 31  1969 d19de800
drwx------ 2 dmn dmn 0 Dec 31  1969 dcd45c64
drwx------ 2 dmn dmn 0 Dec 31  1969 ed999bb


```My attempt to remove cdcce87

```
dmn@Kayleigh:/run/user/1000/doc$ rm -r cdcce87/
rm: cannot remove 'cdcce87/videos2.jpg': No such file or directory
rm: cannot remove 'cdcce87/': Operation not permitted
```

Here is contents of cdcce87: What does it mean?

```
dmn@Kayleigh:/run/user/1000/doc$ ls -l cdcce87/
ls: cannot access 'cdcce87/videos2.jpg': No such file or directory
total 0
-????????? ? ? ? ?            ? videos2.jpg
```

For some, there is no output for ls -l:

```
dmn@Kayleigh:/run/user/1000/doc$ ls -l ed999bb/
total 0
```
In the above case&#8593;, the app which apparently used ed999bb was the Flatpak "NotepadNext". But, I uninstalled that app long ago. Still, it's abandoned sandbox remains and cannot be removed either - even with sudo, I get "Permission denied".

Again, my question is, how could I remove these sandboxes? My other computer has 80+ similar folders, and the number grows.

I had thought folders such as these were temporary and automatically removed when the file accessed is closed? That's not happening.

---

### Post by idmbe on 2023-07-02
access as root 
```
sudo su
```

then you will have access to do it

---

### Post by #&amp;thj^% on 2023-07-02
> **Dennis N said:**
> 
Again, my question is, how could I remove these sandboxes? My other computer has 80+ similar folders, and the number grows.

I had thought folders such as these were temporary and automatically removed when the file accessed is closed? That's not happening.

 Just remove** ~/.local/share/flatpak/db** and restart. The system will recreate** ~/.local/share/flatpak/db **and start to populate /run/user/1000/doc/ on the go, again, as document portal demands go on. Might be good to make a back-up first.
```
*sudo stat -f /run/user/1000/doc
[sudo] password for me: 
  File: "/run/user/1000/doc"
    ID: 0        Namelen: 0       Type: fuseblk
Block size: 0          Fundamental block size: 0
Blocks: Total: 0          Free: 0          Available: 0
Inodes: Total: 0          Free: 0
*me*&#57520;*~*&#57520;*

```

---

### Post by Dennis N on 2023-07-02
> **idmbe said:**
> access as root 
```
sudo su
```

then you will have access to do it

I did try sudo, but it made no difference.

---

### Post by Dennis N on 2023-07-02
> **1fallen said:**
> Just remove** ~/.local/share/flatpak/db** and restart. The system will recreate** ~/.local/share/flatpak/db **and start to populate /run/user/1000/doc/ on the go, again, as document portal demands go on. Might be good to make a back-up first.


Good. This solved the problem. Thanks.

---

