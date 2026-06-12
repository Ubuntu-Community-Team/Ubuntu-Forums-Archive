---
title: "How to read an evolution address book backup folder ?"
date: 2016-01-15
forum: General Help
---

### Post by grey1beard on 2016-01-15
Away from home(UK), I've brought an hdd with my Evolution back up folder, ready to install on a new laptop in USA.
Fresh install of 14.04, and installed Evolution(my preference).
The only backup folder I could find on the hdd was a .tar.gz folder, so a series of double clicks got me to the Evolution Account Assistant, which tells me that this is not a valid back up file ??????

An exploration of the various folders in the original .tar.gz folder showed an address book.db file,( along with mail.db etc.) but I can find no way to open it.

If this were possible, I would at least be able to recover my addresses manually, slow but acceptable.

All help gratefully received, as at the moment I'm totally cut off from friends.

John

---

### Post by howefield on 2016-01-16
So long since I used Evolution,  not sure of this will work as it is complaining about the tar.gz being invalid, but you could try stopping all running evolution processes and removing (or renaming if you want to keep a copy) the following folders.. do this with Evolution closed.

```
~/.config/evolution
```
```
~/.local/share/evolution
```
```
~/.cache/evolution
```

Then manually copy (extract) the relevant tar.gz folders to ~/.config/evolution and ~/.local/share/evolution

---

