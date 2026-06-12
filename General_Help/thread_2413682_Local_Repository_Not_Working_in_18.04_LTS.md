---
title: "Local Repository Not Working in 18.04 LTS"
date: 2019-02-28
forum: General Help
---

### Post by rickschneider17 on 2019-02-28
I have been building and testing some custom .deb packages. 
They are build on a different 18.04 LTS system, using dpkg-deb and then Packages.gz is also done on that server.

I then SCP the files over to a different 18.04 LTS server to test, using a local folder path as a local repository.

deb [trusted=yes] file:/opt/repo ./

I have done this on a 16.04 LTS system previously, and it seemed to work fine.

On the new 18.04 LTS, I am getting issues about missing dependencies, which are part of the local repo and in the directory.

When I do an apt-get update, I get lots of Ign for Translation and others, but Packages seems to work.  

Any ideas?

I have searched this forum, and wasnt finding any answers, but it seems a few had the same or similar issue.

---

