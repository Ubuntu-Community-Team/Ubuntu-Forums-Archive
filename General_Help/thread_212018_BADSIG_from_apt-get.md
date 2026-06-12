---
title: "BADSIG from apt-get"
date: 2006-07-09
forum: General Help
---

### Post by viraptor on 2006-07-09
I keep getting BADSIG error lately for updates on Dapper:
[QUOTE="apt-get update"]W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release: Nast&#281;puj&#261;ce sygnatury by&#322;y b&#322;&#281;dne: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[/QUOTE]

Got this key in gpg. Other updates work. Only cups (7 packs) and pmount fails.
Is't like that for some days already. Any informations on correcting this?

---

### Post by mlind on 2006-07-09
> **viraptor said:**
> I keep getting BADSIG error lately for updates on Dapper:


Got this key in gpg. Other updates work. Only cups (7 packs) and pmount fails.
Is't like that for some days already. Any informations on correcting this?

I guess there's not a dapper-backports repository yet. You could try to comment it out from /etc/apt/sources.list


/edit
My keyring doesn't have that key. I guess it's invalid/invalidated.

---

### Post by viraptor on 2006-07-09
I got it from keyserver manually - don't know if it was there originally.
Anyway - I just turned on all repos available from gui for updates. It reports updates, so it's kind of weird, that it's not working. Is it really a "don't care - remove it" case?

---

### Post by mlind on 2006-07-09
I don't think it's nothing to worry about. You could try to update APT keyring with [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)

---

