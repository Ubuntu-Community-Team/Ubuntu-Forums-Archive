---
title: "Where is g77?"
date: 2012-11-21
forum: General Help
---

### Post by sgy on 2012-11-21
I just installed Ubuntu 12.10 and I can't find the package g77.  Where has it gone?  Why has it been removed from the default repositories?

Where do I find g77?

Thanks.

---

### Post by raja.genupula on 2012-11-21
what you got after trying this in your terminal 

```
sudo apt-get update
```. 

If you got no errors then try again one more time . 

easy ways are looking at Software center and Synaptic .

---

### Post by sgy on 2012-11-21
I ran apt-get update and still get the following when I search for g77.

```
$ sudo apt-cache search g77
f2c - FORTRAN 77 to C/C++ translator
ratfor - Rational Fortran preprocessor for Fortran 77
```Thanks.

---

### Post by sgy on 2012-11-21
I just included the Canonical repositories and re-ran apt-get update.

I still cannot find g77.

Thanks.

---

### Post by steeldriver on 2012-11-21
I *think* that g77 was deprecated (replaced by gfortran) in Oneiric and subsequent releases?

---

