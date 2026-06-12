---
title: "Question about installing Linux over a network..."
date: 2008-02-15
forum: General Help
---

### Post by XtremeGamer99 on 2008-02-15
Say I have a Debian 4.0 server. That server is connected to a switch, which serves four or five 'client' computers. I have one Debian CD; I'd rather not burn a CD for each and every client, nor do I wish to do the client installation one at a time. I'd like to install Debian to all the clients at once, so that I can leave it alone for a night and it be (somewhat) finished by the next day.

The client machines are more or less the same hardware and are running Ubuntu at the moment. I'd like them to download and install from the Debian CD, which will be found in the server's CD-ROM drive, or by any other means. Basically, I want to upgrade the Ubuntu's to Debian, and for them all to be more or less the same, software-wise.

How would I be able to do this?

---

### Post by kaginken on 2008-02-15
Try an NFS Share on one computer.  I do this a lot using centos, but not sure if the Ubuntu install has an option to install from a network  share - try booting up on your ubuntu cd and look for a network share option...

---

