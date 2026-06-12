---
title: "When I installed cinelerra it said it wasn't authenticated.."
date: 2007-02-21
forum: General Help
---

### Post by billdotson on 2007-02-21
* Edit your /etc/apt/sources.list, and add the following repository:
          o deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
          o deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
    * On the command line, run the following:
          o sudo apt-get update
          o sudo apt-get install cinelerra
  It said that what I was installing was unauthenticated.  Is this normal?

---

### Post by billdotson on 2007-02-21
I think it was because those are dapper repositores

---

### Post by ~LoKe on 2007-02-21
Unofficial repositories sometimes give that notice.

If you trust the repo, go ahead and install.

---

### Post by billdotson on 2007-02-22
I don't really know the repo but it installed cinerlerra so...

---

