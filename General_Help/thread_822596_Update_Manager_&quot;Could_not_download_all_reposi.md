---
title: "Update Manager: &quot;Could not download all repository indexes&quot;"
date: 2008-06-08
forum: General Help
---

### Post by asintu on 2008-06-08
I get this error when i try to update my system using Update Manager.
In the details of the error message it says bunch of this type of line:
"Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found" + many other .gz files

---

### Post by ibutho on 2008-06-08
I get the same error. It could be that the server is down for some reason.

---

### Post by Nepherte on 2008-06-08
Yup, it means there is a problem with the mirror. Using another mirror should resolve the issue.

---

### Post by asintu on 2008-06-08
> **Nepherte said:**
> Yup, it means there is a problem with the mirror. Using another mirror should resolve the issue.

and how would you do that?

---

### Post by plucky on 2008-06-08
> and how would you do that? 


**System > Administration > Software Sources** and click in **Download From** and select another server.


Good Luck

---

### Post by asintu on 2008-06-08
> **plucky said:**
> **System > Administration > Software Sources** and click in **Download From** and select another server.


Good Luck

worked..thanx.

---

