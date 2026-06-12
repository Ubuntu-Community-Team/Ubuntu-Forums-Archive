---
title: "Getting Strongs to work right with Bibletime 2.8.1"
date: 2015-03-18
forum: General Help
---

### Post by William_F._Maddock on 2015-03-18
I recently had to re-install the OS on my laptop.

One of the difficulties I have run into is that I cannot get Bibletime 2.8.1 to recognize that i have StrongsGreek and StrongsHebrew modules installed. I also have the OSMHB and TextusReceptus modules installed. Previous to the re-install these modules all worked together. Now, Bibletime does not recognize the Strongs modules in a way that tells me the definitions of the Greek or Hebrew words of those modules.

I have not been able to find help from the developers, so i am trying here.

---

### Post by amanchesterman on 2015-03-19
I don't use Bibletime myself, but problems like this often arise when an application 'forgets' where its modules are stored on your computer.

When you re-installed the OS did you format your home folder? If so, all those settings will have been deleted.

The instructions for Bibletime say that the modules should be in the ~/.sword folder. Does that exist on your machine? Are the modules in it? Have you specified that location in the 'select bookshelf path dropdown list'?
(see [https://bible.org/assets/sword/bible%20time_net_install.html](https://bible.org/assets/sword/bible%20time_net_install.html)  paragraph 3)

---

### Post by William_F._Maddock on 2015-03-22
I did not format the home partition, so all of that stuff is still there, but I did discover that it's not so much the Strongs that isn't working right, but the mag window. It doesn't seem to work at all, beyond displaying its introductory text.

**UPDATE**: I discovered that there was a problem with certain versions of QT with Bibletime 2.8.1, and that the problem has been fixed in later versions of Bibletime, so I searched out a backports PPA and am trying that to get my installation of Bibletime up to the fixed version.

**UPDATE2**: Updating Bibletime to 2.9.1 fixed the problem. The backports PPA that I used can be found here: [https://launchpad.net/~micahg/+archive/ubuntu/ppa](https://launchpad.net/~micahg/+archive/ubuntu/ppa)

---

