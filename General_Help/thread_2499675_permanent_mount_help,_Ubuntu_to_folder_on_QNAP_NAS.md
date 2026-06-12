---
title: "permanent mount help, Ubuntu to folder on QNAP NAS"
date: 2024-08-06
forum: General Help
---

### Post by marklyn on 2024-08-06
Hi, I'm fairly new to Ubuntu and could use some help in making a permanent mount from my Ubuntu 22.04 vm to my "download" folder on my QNAP.  The download folder already has me with full rights.
I've come across a number of websites that had me edit the fstab file but there are so many variations returned from google searches, I feel like I keep going down the wrong rabbit hole.
My QNAP uses QTS, based on linux, and I assumed it'd be easy to setup a direct and permanent mount with read/write privileges, but I'm still green and learning.
I've come across many guides that talk about Ubuntu -> Window shares, but that's not going to help.

---

### Post by TheFu on 2024-08-06
So, do you want to use NFS or CIFS?  NFS should be preferred for all Unix-like clients.
So, use google to search the QNAP support site and find their how-to NFS mount their stuff.  There are things that need to happen on the QNAP and there are things that need to happen on the Linux server/desktop side.

On the Ubuntu client side of NFS, there's nothing special. Any NFS how-to will show examples.  You might not want to use the fstab to mount NFS storage, however. There are other, more flexible tools, but those are slightly more complex to setup.

BTW, just a few days ago (less than a week), I posted an NFS mount line for a client in these forums. You can search that out, if you like, but the QNAP guide should be sufficient.

NFS storage behaves like local storage for the most part, except that snap packages cannot access both CIFS nor NFS without some special constraint options that the packager has to specifically allow in their snap packaging. If you are a heavy user of snaps, that needs to be a consideration, unfortunately. The good news is that 4 yrs ago, snaps didn't support **any** NFS storage at all, so they are getting a little better.  Until snaps allow any storage of any sort to be mounted anywhere and accessed, it will be broken for many people, including me.

I would avoid using CIFS unless the client runs MS-Windows.  There are many reasons.

NFS mounts just look like directories.  Don't look for a "Drive".  That isn't how it works. NFS mounts to directories, so you'll just want to access the storage by looking in the directory where it is mounted.  This seems to confuse people coming from that other, shall not be named, OS.

---

### Post by marklyn on 2024-08-06
I initially tried cifs but didn't have success even after weeks of researching and trying different methods on various websites.
Today, I was looking into NFS, so I turned on NFS access on that QNAP shared folder and started investigating that angle.
I installed nfs-common on Ubuntu, then I did a showmount -e (my qnap ip address) but received an error "clnt_create:RPC: unable to receive", so I'm stuck at this point.
My ultimate goal is to have Qbitorrent on my Ubuntu drop files into a 'download' folder on my QNAP NAS.  If I can set something up and edit fstab to make it permanent, that would be best.
  As of now Qbittorrent will create a folder and file name in my QNAP folder which is empty and qbittorrent gives an error for that downloaded file.  I feel like I"m close, and it has to do with permissions on my QNAP folder.
I'm going to hunt for your post regarding the nfs mount line and see if that gets me further.

---

### Post by TheFu on 2024-08-06
If qbittorrent is a snap package, you'll want to use a non-snap packaged version.

As for qnap issues, I cannot help. That's a qnap-specific question. They do some odd things, but most people don't have the issue with NFS you you've had.  I suspect it is something that is just a blind spot for your knowledge and nobody here can help.  

But if you post your fstab line, I will be able to say what's wrong, if anything.  That doesn't mean a firewall issue isn't there or that the qnap settings aren't correct.

The underlying way that NFS access is handled is that the uid/gid of the users on the client and the server need to match.  Those are the 'numbers' that the 'id' command shows.  Having never used a home-commercial NAS device, I don't know how they manage the mapping of users/groups - or if they do at all.  On my NFS servers, I use centralized user management so all users (and uid/gids) are the same across all my different systems.  I've been doing this for about 25 yrs with NFS.

At work, we use enterprise SAN storage, so management is completely different than what any storage costing less than $100K uses.

BTW, you'll likely need to setup a new Unix group for the qbittorrent user and your user to share so you can easily manage the files.  Look for my posts on "working together", "chgrp" and "chmod" for steps. Those posts are not recent, but should be easily found.

---

### Post by marklyn on 2024-08-06
I did a snap list and it wasn't listed as a snap package.
will look into the posts you mentioned.

---

### Post by TheFu on 2024-08-06
You know, I didn't intend for you to disappear for a day reading.
If you post your fstab entry, at least that side is maybe 3 minutes to get correct AND you'll know it is, so you can move onto other likely issues.

Or you can post a CLI mount command that isn't working with the errors it returns.  Use the exact command AND wrap it all in forum code tags.

However, if **showmount -e ** isn't showing any NFS shares from the NAS, that's a NAS issue.

---

### Post by marklyn on 2024-08-06
sorry, I don't have a fstab entry right now because I've tried some other things since I made that entry.
I am looking into using a NFS mounting scenario so I've started down that path but I get what you mean.
When I'm at the point where I'm editing the fstab file or mount command and getting errors, I will post.
btw, the showmount -e didn't show any nfs shares earlier when I was trying that angle. I do remember that.

---

