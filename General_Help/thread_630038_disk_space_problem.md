---
title: "disk space problem"
date: 2007-12-02
forum: General Help
---

### Post by jvain2005@gmail.com on 2007-12-02
Hi All,
I installed ubuntu on 4gb space left of my laptop. now in /tmp folder i have only 867mb left. How can I check what are the unnecessary software taking space so that I can gain something?

Problem is I want to burn DVD of 2 gb and k3b is giving error as there is no enough space in /tmp.

is 4gb not enough for ubuntu? do you think I should resize the partition? if so, what would be idle size? please note that i have only one / partition. I don't make /tmp /home /boot etc.

Thanks

---

### Post by bwald on 2007-12-02
You can use one of the programs from [this site]("http://geekmadness.wordpress.com/2007/05/10/visualizing-drive-space/") to visualize drive space, but if you're already running low on room that might not be an option.  4 Gigs is a pretty small space for Ubuntu, but it could run in there if you don't need to install a lot of programs/create a lot of files.  If you can resize your partition, I'd recommend adding a few more gigs for the Ubuntu partition.

---

### Post by ptn107 on 2007-12-03
/tmp is emptied on every restart

---

### Post by bwald on 2007-12-03
You are correct, I'm sorry if I misunderstood your problem.  Everything in /tmp is, by definition, temporary and is deleted at logout.  If you find that it fills up very often, you might want to consider enlarging your Ubuntu partition anyway, so you can avoid the hassle of logging out all the time.

---

