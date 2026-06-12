---
title: "cannot see desktop"
date: 2007-03-18
forum: General Help
---

### Post by varun23 on 2007-03-18
After I enter my user name and password, Ubuntu does not show the desktop. It brings me back to the screen where I have to enter the user name.

The user name and password that I enter is correct.

I have been using Ubuntu for a year and this is the first time this has happened. Any help will be appreciated.

Thanks,
Varun

---

### Post by CocoAUS on 2007-03-18
I think I had this happen to me once after mucking with AIGLX and Beryl and all that.  Have you done anything with your X, graphics card, or composite desktop effects recently?

---

### Post by varun23 on 2007-03-18
I do have Beryl installed, but this was done a few months ago. 

I could login to earlier today and everything worked fine. I did not apply any updates the last time i logged in either. 

I haven't changed anything with X or my graphics card.

---

### Post by CocoAUS on 2007-03-18
What version of Ubuntu are you running?  And can you boot into safe mode?

---

### Post by varun23 on 2007-03-18
I am using Edgy 6.10

Kernel 2.6.17-11-386

I can boot in the recovery mode (is safe mode the same as recovery mode?). It takes me to the prompt. There is however one fail message before it goes to the prompt which is :

Unable to find swap space signature [fail]

---

### Post by varun23 on 2007-03-19
I fixed the problem. I had been copying files on to Edgy from a DVD, and it ran out of disk space. I then deleted some files by accessing the ext file system through the windows boot and using fs-driver from [www.fs-driver.org](www.fs-driver.org)

---

