---
title: "updating problem"
date: 2005-05-05
forum: General Help
---

### Post by ingvildr on 2005-05-05
whenever i try and update something i now get this error

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-bin_1.1.3-8ubuntu2.3_i386.deb
  Bad header line [IP: 82.211.81.151 80]
```

---

### Post by Takis on 2005-05-05
[QUOTE=ingvildr]whenever i try and update something i _now_ get this error[/QUOTE]

Since what change?

---

### Post by ingvildr on 2005-05-05
i had it running on my second workspace, went to take a look how far it had come and it had stopped, so i tried it again now i get the error, and i dont remember changing anything major, i was just doing some gnome theme changes.

---

### Post by Takis on 2005-05-05
Is it just for a single package, or every one?

---

### Post by ingvildr on 2005-05-05
its for openoffice.org 1.1.3-8 ubuntu2.3

---

### Post by Takis on 2005-05-05
[QUOTE=ingvildr]its for openoffice.org 1.1.3-8 ubuntu2.3[/QUOTE]

If it's just for that package, it's probably going to be something to do with the configuration of the download header given to apt, and it's over my head. Sorry.

Edit: Although doing a lookup on 82.211.81.151 doesn't come up with anything that appears to be a public server. If you're *really* keen, you can work out what that IP is meant to be pointing to.

---

### Post by ingvildr on 2005-05-05
when u do updates the info gets cached right?, how do i clear the info

---

### Post by Takis on 2005-05-05
I *think* this should do it:
```
$sudo apt-get update --list-cleanup
```

---

