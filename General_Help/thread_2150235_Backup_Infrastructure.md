---
title: "Backup Infrastructure"
date: 2013-05-31
forum: General Help
---

### Post by twinturbotom on 2013-05-31
I'm writing in hopes to gain a better understanding of how to properly implement a backup structure for my home network data.  Specifically, how to organize and implement a structure which enables the distribution and back up of data across multiple machines without too much redundancy.

My network consists of several machines (linux, mac osx, & windows) as well as an apple time capsule (router plus hard drive).  Some data is stored on the media server (apple time capsule shared directory) and accessed by all devices (such as a music library).  Other data can be generated locally on individual machines but access by all machines, there may even be direct copies of the same files on each machine (so the data can be accessed when off the network).  An example of this may be a presentation file I'm working on from one machine, then go to another machine the next day to complete the work.

Right now.... each machine has a directory where data for back up is located.  That directory is routinely backed up to the media server under the individual computers name.  The entire media server can then be backed up; effectively backing up each machine and media server while each machine is backed up on the media server as well.
  This creates some good and bad redundancy as I may have bkups/CPU1/shared_file & bkups/CPU2/shared_file on the media server.  I was thinking about a slick way to potentially combine all /bkup/ data from the server but that would require all machines to have similar directory structure to reverse the process.

Any other implementations to achieve my goals of organizing & backing up shared and unique network data?

Any direction would be greatly appreciated.  Thank you!

---

### Post by dino99 on 2013-05-31
not direct answer(s) but an overview about ):P

[http://askubuntu.com/questions/166142/how-would-you-go-about-backing-up-a-remote-ubuntu-vps-via-ssh](http://askubuntu.com/questions/166142/how-would-you-go-about-backing-up-a-remote-ubuntu-vps-via-ssh)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
[http://karuppuswamy.com/wordpress/2010/08/28/automated-data-backup-of-ubuntu-linux-using-remote-backup-software-rsnapshot-in-debian/](http://karuppuswamy.com/wordpress/2010/08/28/automated-data-backup-of-ubuntu-linux-using-remote-backup-software-rsnapshot-in-debian/)

---

### Post by twinturbotom on 2013-07-01
Thanks for the info.  These are more about how to physically transfer the data.  I'm interested in the structure the data should have.  Things like having each machine backed up to it's own respective directory on the network then consolidating and redistributing data from there?   Thanks, I'll keep digging.

---

