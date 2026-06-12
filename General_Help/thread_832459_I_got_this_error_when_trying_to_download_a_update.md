---
title: "I got this error when trying to download a update"
date: 2008-06-17
forum: General Help
---

### Post by nick09 on 2008-06-17
```
W: Failed to fetch http://playonlinux.botux.net/pool/main/p/playonlinux/playonlinux_3.0.3_all.deb
  404 Not Found
```

I get the error when I try to get a update or even install a new program.

---

### Post by avtolle on 2008-06-17
Is it just this site or for everything? If for this site, have you cut and pasted the url into a browser address bar to see if it is up?

---

### Post by tamoneya on 2008-06-17
thats because they updated to 3.0.4 instead of 3.0.3.  Replace the url with ```
http://playonlinux.botux.net/pool/main/p/playonlinux/playonlinux_3.0.4_all.deb
```

---

### Post by nick09 on 2008-06-17
I get a 404 not found. I found out that the file is not available also the new version 3.0.4 on the server. And I can't find the latest updates through the update manager.

---

### Post by manfer on 2008-06-17
That is not an error, it is a warning. It won't affect the upgrade of the system.

You have anytime added [http://playonlinux.botux.net/pool/main/p/playonlinux/playonlinux_3.0.3_all.deb](http://playonlinux.botux.net/pool/main/p/playonlinux/playonlinux_3.0.3_all.deb) to your repositories list (/etc/apt/sources.list). That is a package, not a repository. Besides that, it is no more on that location on the web.

You have to delete that line in your sources.list and the warning must disappear.

---

### Post by nick09 on 2008-06-17
I know I locked up my firewall using firestarter and I could not load the web so I got scared, removed firestarter and thats when this problem came up.

Is there an command that would scan for errors in my system?

EDIT: All I had to do was run a update for the update manager. Now to try out Firefox 3 Final.:)

---

### Post by manfer on 2008-06-17
If you want that package being always updated when developers upgrade it, you have to add the repository the correct way as they explain on:

[http://playonlinux.botux.net/pool/main/p/playonlinux/](http://playonlinux.botux.net/pool/main/p/playonlinux/)

for gutsy, hardy, debian etch and debian lenny.

---

