---
title: "Moving Directorys?"
date: 2008-01-05
forum: General Help
---

### Post by Kadrus on 2008-01-05
Hello,I'm a facing a little problem...I know how to move files from a directory using 
```
sudo cp '/directory/' '/var/www/' 
```...etc
But if I want to move an entire folder..I get** cp: omitting directory**
Because there are so many files in the directory..and I really don't want to waste an hour writing 
**sudo cp 'etc' 'etc'**..etc..
Anyone knows how can I move them?
Thanks anyway..:)

---

### Post by geirha on 2008-01-05
You say you want to move files, but you use the copy-command, a bit confused about what you actually want to do, but here's a few examples both copying and moving:

```
cp -R /src/dir /dest/dir  # Will recursively copy /src/dir and all subdirs to /dest/dir
cp -a /src/dir /dest/dir # Same as -R but also preserves ownership and permissions
mv /src/dir /dest/dir # Will recursively move /src/dir to /dest/dir, deleting /src/dir when everything is copied.
```

---

### Post by Kadrus on 2008-01-05
> **geirha said:**
> You say you want to move files, but you use the copy-command, a bit confused about what you actually want to do, but here's a few examples both copying and moving:

```
cp -R /src/dir /dest/dir  # Will recursively copy /src/dir and all subdirs to /dest/dir
cp -a /src/dir /dest/dir # Same as -R but also preserves ownership and permissions
mv /src/dir /dest/dir # Will recursively move /src/dir to /dest/dir, deleting /src/dir when everything is copied.
```
What I was trying to do..is move an entire folder to /var/www/..for example...if on my desktop there is a folder called EXAMPLE..and I wanted to move it to /var/www/..I used to create a directory in /var/www/ called EXAMPLE..and move the files inside EXAMPLE that's on my destkop..to the EXAMPLE folder that's on /var/www/...but thanks that solved it.
:)

---

