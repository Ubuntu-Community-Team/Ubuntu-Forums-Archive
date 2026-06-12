---
title: "subversion and thunderbird"
date: 2007-02-12
forum: General Help
---

### Post by tommoyer324 on 2007-02-12
I was wondering if anyone was using subversion to synchronize their home directory/files across multiple computers?  I am trying to determine if I can somehow manage the folder .mozilla-thunderbird (or any other folder for program settings like .mozilla, etc) correctly without a lot of hassle.  The problem I ran into was that if I create a folder in Thunderbird, it won't get added to the subversion repository automatically, and if I forget to add it then I lose anything in that folder when I update another computer.  I have looked at unison, but for my purposes subversion seems to be a better bet, as I need the ability to sync my ubuntu desktop, my powerbook running Mac OS X, and a windows laptop.  Each stores things in different directories relative my "root" or home on that machine
i.e. the thunderbird folder isn't stored in .mozilla-thunderbird in either of the laptops, just on Linux.  Subversion gives me the ability to handle this issue.  So I was just looking for some advice on being able to "automatically" add folders and files that may be created that I wouldn't see, or in case I forget to check.

---

### Post by seppo on 2007-02-12
Did you have a look at iFolder?

It is cross platform(Windows, MacOS ,Linux) and very intelligent with synchronization and conflict resolution.You can als have different paths to the same folder over different machines. It works for me :)

[http://www.ifolder.com/index.php/Download](http://www.ifolder.com/index.php/Download)

---

### Post by tommoyer324 on 2007-02-12
This does look good, but my only question is do I need to install the server somewhere?  I tried running it from my Powerbook, but it doesn't let me do anything until I login to an account, but I thought their site said you don't need the server.

---

### Post by seppo on 2007-02-12
You have to install the ifolder server somewhere, so that it is accessible for each workstation you need to synchronize with. You can run it on the same machine if you want to.

They are working on a workgroup mode:

The sharing capabilities of workgroup mode have not been completed and enabled in the current stable versions. We plan on releasing this capability soon.

---

### Post by tommoyer324 on 2007-02-13
So it would seem that installing iFolder server on Ubuntu is not going to happen yet, as the server dependencies cannot be installed successfully on Edgy Eft, and the build instructions are not for Edgy Eft either.  So I guess my original question still stands.  How can I manage folders created by programs in subversion without a lot of intervention on my part?

---

