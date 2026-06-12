---
title: "utorrent error message"
date: 2006-11-05
forum: General Help
---

### Post by of_darkness on 2006-11-05
Hi i get a error message when running utorrent on wine: (translated from swedish)
[I]
Could not save the resume-file. You can Lose parts of the download.
Another program could have the file open, or the disk is full. Correckt and push Try again button. If you push Abort the resume-file whill not be saved.
[/I]

If i push abort the same error window whill pop upp again.
 when running in console i se this error message:
[I]
blutengel@blutengel:~$ utorrent
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.[/I]

kernel 2.6.17-10-generic
kubunbtu edgy .. latest wine..

---

### Post by NESFreak on 2006-11-09
maybe the error message is what it says to be: another app can be opening the files &#956;torrent uses.

For the command line its "wine utorrent" not just utorrent.

NESFreak

---

### Post by of_darkness on 2006-11-10
It has solwed ist self by deleteing .wine folder iin the home folder.. then running winecfg again.. 

then eddeting the uttorent binary in /user/bin that i created as described in [http://ubuntuforums.org/showthread.php?t=209773](http://ubuntuforums.org/showthread.php?t=209773)

so prob. it was taht i made some error in conf. the drives in wine..

---

