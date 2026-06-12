---
title: "apt-get broken (Dynamic MMap ran out of room)"
date: 2007-06-29
forum: General Help
---

### Post by dfdumaresq on 2007-06-29
I've started having problems with apt-get after adding a debian sources site (yes, I Am Newbie)

When I run apt-get commands I get the following errors:

Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing python2.4-pycurl (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I have tried some suggestions from the forums, for example:
sudo dpkg --configure -a

without any luck.

Someone posted a similar problem, which they fixed, but unfortunately didn't post what they did.
Can I rebuild my repositories to fix this?

Thanks in advance!
Dave

---

### Post by dfdumaresq on 2007-06-29
Whew! I fixed it - thanks to this helpful link:
[http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/](http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/)

Adding this entry to /etc/apt/apt.conf worked:

APT::Cache-Limit "20000000";

Whereas a smaller value of 1000000 did not.

Thanks,
Dave

---

