---
title: "&quot;The package lists or status file could not be parsed or opened&quot;"
date: 2012-11-01
forum: General Help
---

### Post by jeffbilling on 2012-11-01
I got this error when trying to update - can anyone help please ::confused:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by MG&amp;TL on 2012-11-01
EDIT: I'm an idiot in the mornings. Check the answer given below.

---

### Post by 2F4U on 2012-11-01
Try this

```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by jeffbilling on 2012-11-06
Many thanks 2F4U.
Sorry for delay in reply but I had used up my months data quota with the downloads! 
Worked a treat and everything seems fine.
Jeff

---

### Post by jeduffey on 2013-01-09
This solution worked for me also.

+1 Thanks.

---

### Post by rckker on 2013-02-27
I'm new to Ubuntu and had same problem.
This solved my problem.
                       Thank.

---

### Post by glenesis on 2013-03-07
Thank you very much!! Fixed me!

---

### Post by T_u on 2014-01-25
Worked for me on 12.04.3! Thanks!

---

