---
title: "Automatiize quota using bash script"
date: 2013-04-22
forum: General Help
---

### Post by Messzir on 2013-04-22
Hello folks.

I have read plenty of tutorials about setting up quota on Ubuntu ([like this]("http://unixprofessionals.blogspot.hu/2012/05/how-to-apply-quota-on-ubuntu-server.html")) but as you can see, one must edit manually the quota settings using edquota. My aim is to set quota limit for [username] like this:
```
sudo setquotafor -u [username] -h 500
```
(-h stands for hard quota limit in MB or whatever else)
Is there any way to do it using one bash script (and if it is possible in a single line)? I hope you can help me.
Thank you for your answer in advance.

---

### Post by schragge on 2013-04-22
Just use [setquota(8)](http://manpages.ubuntu.com/manpages/quantal/en/man8/setquota.8.html)

---

### Post by Messzir on 2013-04-22
Well, you saved the day, sir! Thank you.

---

