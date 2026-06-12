---
title: "How to choose depend package"
date: 2006-08-15
forum: General Help
---

### Post by quizas on 2006-08-15
I try to install tomcat5.

apt-cache show tomcat5:

Depends: kaffe (>= 2:1.1.6-3) | java-gcj-compat-dev (>= 1.0.41-1) | java2-runtime, libtomcat5-java (>= 5.0.30-9), adduser (>= 3.34), apache-utils (>= 1.3.33-1) | apache2-common

it show that tomcat5 depends on kaffe or java-gcj-compat-dev or java2-runtime.

On default it uses java-gcj-compat-dev and install its packages.

But i have installed java2-runtime and want to use its packages as dependency (instead of java-gcj-compat-dev).

How to do it?

---

### Post by Ramses de Norre on 2006-08-15
I'm pretty sure that this info is hardcoded into the .deb package.. 
Maybe after installing you could edit the tomcat5 entry in /var/lib/dpkg/status, change the dependency and uninstall the java-gcj-compat-dev package. I'm not sure that this works though, I never tried it before.

---

