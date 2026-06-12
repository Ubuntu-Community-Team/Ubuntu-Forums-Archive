---
title: "Syncing Media files between main pc and media centre."
date: 2013-01-02
forum: General Help
---

### Post by leona on 2013-01-02
I posted this on the Raspberry Pi forum, but couldn't get a satisfactory answer so I thought I would try it here, as its related.

Ok
I am running a Raspberry Pi as a media server with MiniDLNA
On the Pi I have a SSD which contains the media files (destination).
My Ubuntu main machine has the source media files.

What I would like to do, is to sync my main PC (Linux / Ubuntu 12.04) with the Pi, so each time I add media to the main pc its sync'd to the PI's SSD (don't have to be real time, a cron at start up is fine).

I thought this would be straight forward,
I installed luckybackup on my ubuntu machine (front end for rsync).
Now I have tried this 2 ways.
First Samba, I created a samaba share on the Pi and mounted it on my main machine, all good but I coudn't get rsync to work, it gave me "rsync: failed to set permissions on "/media/SSDShare/.": Operation not permitted (1) "
So thinking it wasn't able to obtain the right permissions I opted for the SSH route.
Which took an age to get right, trying to setup password less login's and get the right permissions but I got there.
Setup another task with Rsync but with SSH and this time I get.
"rsync: failed to set times on "/home/shared/.": Operation not permitted (1) "
I'm running this as myself, and I have permission (group) to that dir.

Googling the above errors, tells me that rsync can't set timestamps ont he dirs, I've tried the -O and -a options but to no avail.

Now luckybackup will not allow me to remove options "-tgo -p" if I unselect them and save, they come right back again.

So I don't know, I've exhaused my knowledge and google, I just want the SSD on the PI to hold the same contents of my main pc's media, sounded simple, seems to prove impossible :(

Can someone please point me in the right direction, I feel like I am stumbling around in the dark here.

---

