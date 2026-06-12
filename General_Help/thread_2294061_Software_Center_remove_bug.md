---
title: "Software Center remove bug?"
date: 2015-09-09
forum: General Help
---

### Post by roland-logikalsolutions on 2015-09-09
This looks like a bug to me. I see it on Ubuntu 12, 14, and 15 both 32 & 64-bit versions. It is either a bug or an "undocumented feature." I have seen this bug with my own multi-arch .deb as well as other .deb files from various places.

Pull down .deb to home folder.
Open file browser and doubleclick .deb
Eventually Software Center will manage to show your application with an install button.
Click install, enter sudo password, let install complete.

There, on the right hand side, will be a button which says "reinstall" instead of "remove"

What causes this bug?

What work arounds are there?

Is the Software Center really so weak and feeble that once used to install something the only method of un-install is the command line?

Thanks,

---

### Post by v3.xx on 2015-09-09
Could be time to move on

[http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html](http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html)

---

### Post by brian-mccumber on 2015-09-09
I have not seen this problem in Ubuntu 14.04 with anything I have installed from the software center. Even when I have used the advanced packing tool or downloaded debs to install stuff they still show up with a remove button in the Software Center and I went through and checked everything that I have installed. Perhaps it is the way the deb was packaged that is at fault not the software center.

---

### Post by roland-logikalsolutions on 2015-09-09
> **v3.xx said:**
> Could be time to move on

[http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html](http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html)

Thanks for the link. Nice to know Software Center is being taken into the woods and getting 2 behind the ear, but, doesn't solve the current issue. On existing Ubuntu 12, 14, and 15 installations, users will retrieve the .deb, double click on it, and a busted Software Center will be what installs it without providing a method of un-install.

Sad really. I suspect it has always been a wrapper for dpkg and dpkg keeps a list of software it has installed, so even a brute force method of scanning the list and putting up 2 buttons "remove" "re-install" would fix the issue 100%.

Another thing I noticed during testing is after existing Software Center, having installed a .deb not provided by Ubuntu, it cannot find the package.

---

### Post by v3.xx on 2015-09-09
Read this in the last newsletter.

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue433?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue433?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent)

Main way I stay up to date.

---

### Post by roland-logikalsolutions on 2015-09-09
> **brian-mccumber said:**
> I have not seen this problem in Ubuntu 14.04 with anything I have installed from the software center. Even when I have used the advanced packing tool or downloaded debs to install stuff they still show up with a remove button in the Software Center and I went through and checked everything that I have installed. Perhaps it is the way the deb was packaged that is at fault not the software center.

I have seen this issue with multiple .deb files from multiple sources.

You are correct that Software Center may have some undocumented requirement which these not obscure .deb packages know nothing about, but everyone one of those .deb packages work flawlessly with dpgk on the command line. No errors, no warnings, always found for un-install. I have yet to find a place/log where Software Center complained about anything, it simply doesn't work.

If you go to Git and pull down the Atom text editor 64-bit .deb directly from git, it has the same installation issue in Software Center.

---

### Post by ajgreeny on 2015-09-09
Just to add my two-pennyworth; I am one of the many (I think?) people who never uses the software centre.

For normal package management it is usually synaptic for me, partly because I have been using Ubuntu since 5.04 so I was brought up using it when I started my Linux life, and partly because it is so much better than SC, though I do use command line **apt-get** as well.

If I have a **.deb** package from other sources to install I use **gdebi**, which does an admirable job, much quicker than SC.

---

### Post by roland-logikalsolutions on 2015-09-09
> **ajgreeny said:**
> Just to add my two-pennyworth; I am one of the many (I think?) people who never uses the software centre.

For normal package management it is usually synaptic for me, partly because I have been using Ubuntu since 5.04 so I was brought up using it when I started my Linux life, and partly because it is so much better than SC, though I do use command line **apt-get** as well.

If I have a **.deb** package from other sources to install I use **gdebi**, which does an admirable job, much quicker than SC.

I always use synaptic. Herein lies the rub.

This Kiosk type thing will be a .deb. The end users will have some "base install" of Ubuntu which can be 12, 14, or 15 and will most likely be the icky-nasty-Unity desktop. When you double click a .deb on icky-nasty it launches Software Center. I cannot change this, I can only try to endure the humiliation.

---

### Post by v3.xx on 2015-09-09
> If I have a .deb package from other sources to install I use gdebi, which does an admirable job, much quicker than SC.
Gdebi (plus synaptic) is an excellent way to go.  I don't know about games though, I don't do games.

---

### Post by roland-logikalsolutions on 2015-09-09
Synaptic package manager needed no improvement, so naturally the Ubuntu crew tried to replace it. Now I have to deal with the fallout. I'm guessing SC only works correctly if the .deb has been signed by Cononical itself. Just looking for confirmation of that here.

---

