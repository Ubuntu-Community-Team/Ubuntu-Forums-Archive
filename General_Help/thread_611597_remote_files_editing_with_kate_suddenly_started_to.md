---
title: "remote files editing with kate suddenly started to fail"
date: 2007-11-13
forum: General Help
---

### Post by jvilares on 2007-11-13
Dear all:

I have always used kate (by browsing with konqueror) for editing files in my remote linux server, usually via sftp. Nevertheless, a week ago it started to fail. If Kate downloads the file, it displays it, but:

* instead of naming it "file.txt", for example, it names it number.number."file.txt"
  (i.e., the local copy)

* if I try to save it, it says "The file 'file:///var/tmp/kde-cache-jvilares/krun/number.number.file.txt' was deleted by another program. Do you really want to save this unmodified file? You could overwrite changed data in the file on disk"

* changes are saved in the local copy, but not in the remote file

* nevertheless, if I don't use konqueror, but only kate (by typing 'kate sftp://..../file.txt'), it works perfectly

I'm quite desperated, since I use quite a lot Kate for remote editing in my work, and I have not been able to find any solution.

does anybody knows how to solve this?

Thanks a lot for your time,
    JESUS

---

