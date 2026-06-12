---
title: "Database management software"
date: 2016-12-29
forum: General Help
---

### Post by tahaan on 2016-12-29
I'm a bit disappointed with DataGrip which I finally decided to evaluate.  The performance on the Visualization side is dismal, adding or removing a relation to the visualization causes it to discard and "re-optimize" where you have manually placed tables on the diagram, instantly undoing all your with no way to undo the damage.  You need to drop to the scripting console to do seemingly simple things like creating an Enumerated type and, it doesn't seem to allow you to create inherited tables, nor does it show you that tables are inherited from other tables.

So...

What are my options?  My primary environment is Postgres and will probably be the only environment that I will work in for the foreseeable future.

Pretty diagrams is almost essential.  Online would be nice with support for multiple users a nice bonus, but not required. Support for Postgres' more esoteric features is essential at least be aware of the existing of native types like UUID.

---

