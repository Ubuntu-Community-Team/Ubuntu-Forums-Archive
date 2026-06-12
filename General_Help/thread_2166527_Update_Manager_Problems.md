---
title: "Update Manager Problems"
date: 2013-08-09
forum: General Help
---

### Post by PEM59 on 2013-08-09
I am having two problems using the Ubuntu update manager for Ubuntu 12.04. I have been using Ubuntu for years  and have never had this kind of problem before.  I do not know if they are related.
 
 It gives an error  
   
 Requires installation of untrusted packages 
  
 The action would require the installation of packages from not authenticated sources.  
 
 master-pdf-editor master-pdf-editor-bin:i386
 
 Note that I downloaded this software from the Ubuntu software center.   If there is a problem, It should give me the option of not updating this particular software and continuing with the software that can be verified.
 
I can wade through the 141 items to be updated to try to find it but this is not easy to do and frustrating.   
 
 After I find the package and uncheck it I also have the following error:
 
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.91.13 80] 
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.91.13 80] 
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.91.13 80] 
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_17.0.7+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.91.13 80] 
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en-us_17.0.7+build1-0ubuntu0.12.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en-us_17.0.7+build1-0ubuntu0.12.04.1_all.deb) 404  Not Found [IP: 91.189.91.13 80]

---

### Post by QIII on 2013-08-09
Hello!

Is the pdf app something you purchased?

The 404 errors mean the resource is not available.  It may be down for maintenance or some other reason.  You can try changing to anothere mirror or just waitingan hour.  That might also take care of the verification issue.

---

### Post by PEM59 on 2013-08-09
I dowloaded master pdf editor for free from the Ubuntu software center, so I assumed that it would not have any problems.   Even if there are problems, it would be much eaasier if I could tell the update manager to not update that particular software when it has a problem, as opposed to searching for the problem among the 141 updates.](*,)

---

### Post by ibjsb4 on 2013-08-09
Free ?

Have you read the reviews?

[https://apps.ubuntu.com/cat/applications/master-pdf-editor/](https://apps.ubuntu.com/cat/applications/master-pdf-editor/)

---

