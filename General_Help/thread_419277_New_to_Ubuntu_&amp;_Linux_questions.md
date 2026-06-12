---
title: "New to Ubuntu &amp; Linux questions"
date: 2007-04-22
forum: General Help
---

### Post by James SoCal USA on 2007-04-22
I am considering getting into Linux with Ubuntu bot would like to know - if possible

1)  Presently dual booting W98se & 2k on 3 machines.  Does Ubuntu respect prior installs when being installed to its own partition so all 3 can be optional boots?

2) I have a file server on W98se with a raid 5 drive using the Highpoint Teck Rocket Raid 454 daughter board with 5 WD160G drives.  They indicate there are linux drivers available  on their site at [www.highpoint-tech.com](www.highpoint-tech.com) but I don't know if they will work with Ubuntu.  Does anyone have any experience, good or bad, in this area?

3)  Is there a firewall, similar to Zone Alarm, available for Ubuntu?

4)  I have some apps that must run ona Wx platform 2k+ using MSSql database.  I know MySQL is a good system as well but this is a "canned" product over which I have no control but need it to continue my income.  Has anyone run it on Ubuntu or possibly on Win4Lin?  [www.win4lin.com](www.win4lin.com)

Any direction would be very much appreciated regarding these questions & possible setup procedures.

James

---

### Post by Mike'sHardLinux on 2007-04-22
Hi!

1) My experience has been that Ubuntu is VERY good about respecting other installed OSes. For me, the other OSes are installed in Grub automatically, and just work. I don't remember having any issues with this, especially if you install all the MS OSes first and then install Linux.

2) sorry, no experience here.

3) One reason Windows needs a firewall is because of services are running by default that really shouldn't be and they often have vulnerabilities that are exploitable. Linux, at least generally speaking by default does not have services such as remote assistance or messenger running and therefore isn't susceptible to the same type of exploitations.

With that said, Linux distros come with iptables, the most widely used firewall for Linux, AFAIK, but it command-line only. You can install a frontend like Firestarter to make it easy to use....somewhat similar to Zonealarm....better IMO. I remember Zonealarm would often need to be reinstalled because something would become corrupted for no apparent reason....but that was a while ago.

4) One possible workaround is to use virtualization. For example, with VMware, you can run windows inside a VM, and in the VM you can run any typical application, like MSSQL. Another VM which seems to be getting more popular is VirtualBox.

edit: I wanted to add that one big reason I like virtualization is because you don't need to reboot into the other OS. It runs concurrently inside your current session.

---

### Post by James SoCal USA on 2007-04-23
Thanks Mike

Hope someone will come up with a possible for _2_. 

I forgot to ask about the virtualization since I have not done that as yet but your answer was most timely.  When M$ announced that people could run Linux, etc. on top of M$ I must say that struck me as very funny.  A stable system on top of one of the most unstable ones available.  M$'s attempt to remain relevant.

Thanks again.

James

---

