---
title: "apache2 + mod_ldap + ldaps://"
date: 2007-02-06
forum: General Help
---

### Post by thusi02 on 2007-02-06
Hello, 

I am trying to configure authentication based on ldap using mod_ldap. However, I am having trouble as when I use my URL as ldaps:// apache logs complain saying that ldaps is not support etc etc. Which is true as when I do ldd on mod_ldap.so the libraries: liblber*.so and liblda_r*.so are not associated to it. 

I am on ubuntu using aptitude/apt, so when I install using apt (package manager): libapache-mod-ldap

It installs apache 1.3 version of mod_ldap which does have those associations to the openldap libraries. However, I cannot seem to find a package to install that is the same for apache2. I am in need to get this built for apache2. I came across this:

[http://www.wlug.org.nz/ApacheNotes](http://www.wlug.org.nz/ApacheNotes)

I was hoping that if someone has instructions as to how to build the mod_ldap.so to included the openLdap sdk which will enable me to do ldaps queries that would be AWESOME. Your help would be much appreciated. 

Cheers, 
Thusjanthan Kubendranathan

---

