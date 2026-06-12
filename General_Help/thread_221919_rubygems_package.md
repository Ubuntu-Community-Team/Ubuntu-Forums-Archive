---
title: "rubygems package??"
date: 2006-07-24
forum: General Help
---

### Post by johann_p on 2006-07-24
Is it true that there is no package to install rubygems? 

It is recommended to install many Ruby packages (e.g. rails) with gems and keep them updated this way ... so Ubuntu should provide a package for gems ... is there one?

---

### Post by sulobanks on 2006-07-24
I have not seen a package for rubygems, and the gems website even mentions that if you're using Debian you'll have to compile it from source.  Here's the link to the install page [http://docs.rubygems.org/read/chapter/3#page13](http://docs.rubygems.org/read/chapter/3#page13)

I agree. There should be a package available.  If I knew how to do that, I'd submit one.

---

### Post by johann_p on 2006-07-24
From bug 53900 (Rejected):
"This is a deliberated choice: Ubuntu came with it owns system of packages apt and gem is useless with apt. The only thing that gem tool will bring in Ubuntu is packages breakage by installing incompatible versions of library or installing both Ubuntu and coming from gem libraries. That would be a big mess. Definitely, if you want to keep your system clean, keep gem away."

---

### Post by johann_p on 2006-07-24
Just realized that neither for FreeRIDE nor for FxRuby do exist Ubuntu packages. How am I supposed to install those? Manually? Or by manually installing RubyGems from source myself before using it? 

What the heck is the advantage of letting users do this themselves? 

I am getting more and more frustrated with the Ubuntu/Debian package system and the decisions behind it. :mad:

---

