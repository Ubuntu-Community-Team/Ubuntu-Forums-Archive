---
title: "Need to copy 6GB over internet between 2 ubuntu 7.10, Remote Desktop good choice?"
date: 2007-11-12
forum: General Help
---

### Post by feisty_hot_lover on 2007-11-12
Hi, I need to copy about 6GB worth of files over broadband Internet connection and my sister uses a different ISP than me.  The 2 computers are Ubuntu 7.10.  I am thinking of using remote desktop (Terminal Server Client) for this task.  I am wondering if it is reliable and secure.  My remote desktop settings in System/Preferences/Remote Desktop are all 4 check boxes are checked and I copied and pasted in a 24 character password using letters & numbers & symbols.  My computer is also behind a nat router specifically a Linksys BefSR41, do you think I need to forward ports.  And Finally since we are using Linux we use VNC as RDP is only for Windows right?

---

### Post by ddrichardson on 2007-11-12
For 6 GB I would be inclined to use something that supports resume - such as ftp personally.

---

### Post by feisty_hot_lover on 2007-11-12
> **ddrichardson said:**
> For 6 GB I would be inclined to use something that supports resume - such as ftp personally.I assume that I could just use ftp through the remote desktop.  Ftp does sound like a good choice.

---

### Post by mchaley on 2007-11-12
Keep in mind that her upload might be a HUGE bottleneck. can you compress the file any? FTP is prob. the best bet.

---

### Post by netztier on 2007-11-12
> **ddrichardson said:**
> For 6 GB I would be inclined to use something that supports resume - such as ftp personally.

Sounds like a job for **unison**, which is kind of rsync-over-SSH with a GUI (when installed with **unison-gtk**)

Make sure you can SSH to the remote machine (might need to play with DynDNS and port-forwarding on the broadband routers) and then make sure you have a user account on both machines, best with same username and PW.

Unison can then take care of sychronising the directory trees across both machines. You need a lot of patience, though, the first initialising run can take hours and hours! But you can leave it running for days, it will pickup where it last was interrupted etc.

best regards

Marc

---

### Post by ddrichardson on 2007-11-12
Also, bear in mind that your upload speed will be nowhere near your download speed. 6 Gb is a lot of data, a physical copy sent by post may well be a lot easier.

---

### Post by feisty_hot_lover on 2007-11-13
> **ddrichardson said:**
> Also, bear in mind that your upload speed will be nowhere near your download speed. 6 Gb is a lot of data, a physical copy sent by post may well be a lot easier.The computer in question does not have a DVD drive.  The time does not matter as the computers are on 24 hours a day and the data is not too critical so taking some days for the transfer is okay.  I decided to go with ftp and I got my server up and running, works great.

---

### Post by songshu on 2007-11-13
if you have to sync it on a regular basis, unison as above mentioned or rsync are the best for the job.

if you only need to do it once then scp would be your best choice i think

---

