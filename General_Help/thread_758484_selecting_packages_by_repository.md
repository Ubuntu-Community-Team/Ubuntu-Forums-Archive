---
title: "selecting packages by repository"
date: 2008-04-18
forum: General Help
---

### Post by egalua on 2008-04-18
Hi,

in synaptic you have the choice of displaying only the packages contained  in a repository, via the "Origin" button. 
I am wondering if there is a similar possibility in adept manager: I looked through all the tags, but there seems to be no such filter, nor I could find anything else for this purpose.

And what about the same problem for aptitude?

Thanks

Fabio

---

### Post by AlphaWu on 2008-04-18
If you sure which repository your packages in.You can comment other sources,then upgrade or install.

---

### Post by jrib on 2008-04-18
Aptitude solution: ```
aptitude search ~Oorigin
``` Matches package versions whose origin matches the regular expression *origin*.

See: [http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)

---

### Post by egalua on 2008-04-18
> **_jason said:**
> Aptitude solution: ```
aptitude search ~Oorigin
``` Matches package versions whose origin matches the regular expression *origin*.

See: [http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)

Thanks: it is exactly what I wanted (for aptitude)

Fabio

---

### Post by egalua on 2008-04-18
> **AlphaWu said:**
> If you sure which repository your packages in.You can comment other sources,then upgrade or install.

Well, I already tried this, but it is not very practical: every time you look in a different repository you have to reload the source... Moreover, if you select a package for installation, you may have broken dependencies.

I was looking for a solution like the one which was indicated for aptitude: is it possible that the feature is present both in aptitude and synaptic and not in adept?!? That's really strange.

Fabio

---

