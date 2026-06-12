---
title: "Errors compiling Apache (1.3.33)"
date: 2005-04-16
forum: General Help
---

### Post by russx2 on 2005-04-16
Hello,

I'm trying to compile Apache 1.3.33 on Hoary. I keep getting this error when performing the ./configure:

+ adding selected modules
    o rewrite_module uses ConfigStart/End
      disabling DBM support for mod_rewrite
      (perhaps you need to add -ldbm, -lndbm or -lgdbm to EXTRA_LIBS)
    o dbm_auth_module uses ConfigStart/End

I've installed libgdbm3 and libgdbm-dev through apt but this didn't help. What package is it looking for?

Advice appreciated!

Thanks,
Ruiss

---

### Post by Rock on 2005-04-16
Install it in Synaptic.

---

### Post by russx2 on 2005-04-16
But that won't help me compile it, will it?  :? 

I'd just like to know what package the error message is refering to - the few references I've found to this error message (regarding other distros) all recommend installing the libgdm-dev package - which I have.

Does anyone have any experience compiling Apache under Ubuntu/Hoary? Seen the above error message before?

Thanks,
Russ

---

### Post by russx2 on 2005-04-17
Anyone? Been stuck on this for 3 days now. Really need to be able to compile it myself (or I would use the pre-compiled version in the apt respository).

Sure I'm missing something simple - any ideas? :neutral: 

Thanks,
Russ

---

