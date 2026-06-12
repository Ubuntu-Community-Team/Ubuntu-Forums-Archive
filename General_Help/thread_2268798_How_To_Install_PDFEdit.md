---
title: "How To Install PDFEdit"
date: 2015-03-11
forum: General Help
---

### Post by KitchM on 2015-03-11
Being new to Xubuntu, I am unsure as to why my install attempt did not work.  From [http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html) the command given is ```
sudo apt-get install pdfedit
```.  So I opened Terminal Emulator on my Xubuntu (Ubuntu 14.04.2 LTS) and pasted in the command.  it came back with the following message:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pdfedit
What do I need to do to make it work?

Thanks.

---

### Post by Holger_Gehrke on 2015-03-11
That review is from 2007. The program has since been removed from the repositories because it still needs the (old) qt3 libraries (current is qt5). Both it's stability and it's usability seem to be questionable. To make it work on current versions of Ubuntu, you would have to find and install the old libs (from source, they aren't in the repositories either), get the program in source and compile it too. Not a good project for a beginner ...

---

### Post by slickymaster on 2015-03-11
See this: [How can I install PDFedit on Ubuntu 14.04]("http://askubuntu.com/questions/538966/how-can-i-install-pdfedit-on-ubuntu-14-04")

---

### Post by ajgreeny on 2015-03-11
I agree with Holger's comment about the lack of usability of pdfedit.
I tried several times to get it to work but eventually gave up and now if I need to edit a pdf I normally use xournal to open it, make changes, and then export it again to pdf.

---

