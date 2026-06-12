---
title: "Is there a repository with swiftfox?"
date: 2008-05-14
forum: General Help
---

### Post by agim on 2008-05-14
I would much rather use a repository, so I can get updates. I am hoping someone knows. No luck with google yet .
thanks

---

### Post by agim on 2008-05-15
bump

---

### Post by ChameleonDave on 2008-05-26
> **agim said:**
> I would much rather use a repository, so I can get updates. I am hoping someone knows. No luck with google yet .
thanks

If you just go to the [Swiftfox]("http://getswiftfox.com/deb.htm") site, you'll see that they say to add

```
deb http://getswiftfox.com/builds/debian unstable non-free
```

to your /etc/apt/sources.list file.

---

### Post by kesman on 2008-05-26
The repository is for debian, which usually has newer packages and different dependecies than ubuntu, but it should still be safe to add this to your /etc/apt/sources.list though.

---

### Post by agim on 2008-05-26
I had heard that debian had older packages and different dependencies than ubuntu, not newer packages. Am I mistaken?

---

### Post by kesman on 2008-05-27
Maybe, or then I am. Anyway, if it complains something about dependencies, DO NOT CONTINUE as it might result in a dependecy hell.

---

### Post by ChameleonDave on 2008-05-27
Look, you're not adding an actual Debian repo here.  All it has in it is Swiftfox, which has exactly the same dependencies as Firefox.

It's really the same as downloading a .deb file and installing it, except that this way you'll get updates.

It's safe for any .deb-based system to use this repo.

---

