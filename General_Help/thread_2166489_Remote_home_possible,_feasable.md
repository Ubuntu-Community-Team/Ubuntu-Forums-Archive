---
title: "Remote /home possible, feasable?"
date: 2013-08-09
forum: General Help
---

### Post by zero2xiii on 2013-08-09
Hay all,

Not sure where this should be posted so I am trying here.

Right so my question is:
Is it possible to have a remote /home partition, or user home folder? If so, what would the preferred method be? sftp jumps to mind.

The idea is, I want to install another ubuntu on a machine in a studio at my house, which joins to the main LAN (wired) of the house, but have a duplicate account as on my current main PC. Thus, I figured I could just mount my local /home (or /home/user) on the remote system and work as if infront of the main computer and only needing a minimal partition (say 4 - 8 GB) just to house the main install and main applications.

It this at all possible?

Thanks

---

### Post by cool110 on 2013-08-09
Generally remote home directory only work well when all client machines  have identical hardware and software as all user settings will carry  over which can cause issues with differencing screen resolutions, etc.  Also it's important that local home directories exist that the remote  share is mounted over otherwise it will be impossible to log in if  there's a network issue. Finally on a private network NFS is a lot  simpler to use than SFTP.

---

### Post by 1clue on 2013-08-09
Sure.

You can use an NFS share and boot the whole machine off of it if you want.

Technically all you need as an X server on your workstation (this would be like Remote Desktop in Windows), you can have a remote login session that exists on one machine from many terminals, or you can have a shared home for many computers, you have to decide exactly what you want though and how much sharing you want.

This is a can of worms.  It sounds super simple at first, but the decision points are critical.  It starts with your expectations, and then you have to follow the line of logic that makes those expectations most feasible.

Not sure a good place to start on this, but you might try here:  [https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)

You might also want to look at NAS (maybe FreeNAS, which is a FreeBSD implementation that seems pretty good) and keep that in mind when you read up.

---

### Post by 1clue on 2013-08-09
Another thing I've heard of in conjunction with this is that people will carry a USB stick in their pocket, and stick it into whatever workstation they're sitting on.  That allows individual settings on each workstation (say one is dual huge monitors and lots of goodies, another is just a minimal workstation, and a third is a Windows box) and still have common file space.

---

### Post by sanderj on 2013-08-09
> **zero2xiii said:**
> 

Right so my question is:
Is it possible to have a remote /home partition, or user home folder? If so, what would the preferred method be? sftp jumps to mind.


Yes, apparently that's possible: that's how it worked on the SUN stations I logged on to in ... 1990. Different workstations each with SUN OS, and your home directory was just there. I believe that worked over NFS

---

### Post by 1clue on 2013-08-09
The native network file system for UN*X is NFS.  You could also do it easily enough with CIFS.

---

### Post by bab1 on 2013-08-09
> **1clue said:**
> The native network file system for UN*X is NFS.  You could also do it easily enough with CIFS.

Just being picky here :)

Neither NFS or SMB (CIFS) are native to UNIX.  SUN developed NFS and DEC/Microsoft developed SMB.  Both are userland vfs.

---

### Post by 1clue on 2013-08-09
> **bab1 said:**
> Just being picky here :)

Neither NFS or SMB (CIFS) are native to UNIX.  SUN developed NFS and DEC/Microsoft developed SMB.  Both are userland vfs.

Yes, I believe NFS first debuted for the public on Solaris (which is a licensed UNIX) and was fairly quickly adopted elsewhere.  That's off the top of my head and so may be wrong, but my memory usually doesn't fail me very much.

Nonetheless, NFS is the default networked file sharing protocol on most UN*X systems today, which doesn't mean it always has been but only what is today.  Even systems which have some other as the default will have solid support for NFS in any case I know of except maybe Android.  It's probably there too, at least as a client.

CIFS was mentioned because there's good Linux support for it, and because it's supported on virtually every computing platform currently in use, and because I like it.

Yes, Microsoft can come out with something good every now and then. Another goodie is ODBC 2.0.  1.0 came from elsewhere, but Microsoft came out with the 2.0 spec and it was what the 1.0 would have been had the other guys been thinking about it.  And this paragraph is entirely off topic.

Anyway back to the point, CIFS and NFS both have solid support on every serious computing OS, unless maybe Android but I don't know there.

---

### Post by zero2xiii on 2013-08-10
Hay all,

Thanks for all the replies! Appreciate them all.

So the only "issue" I see is the sharing of the configuration files that might cause issues across different hardware (which in this case is a definite) so I guess I will only be mounting the data directories, or mount the entire /home partition of the remote computer as a sub directory eg /home/remote_home so I still have access to all the data but not using it as the actual home directory.

Thanks again for all the input

---

### Post by 1clue on 2013-08-10
You might consider a central authentication scheme too, at least read about it.  Maybe read here a bit: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

I actually had to look for that, if you google anything reasonable it seems like most people are using Windows-based authentication.

---

### Post by bab1 on 2013-08-10
> **1clue said:**
> You might consider a central authentication scheme too, at least read about it.  Maybe read here a bit: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

I actually had to look for that, if you google anything reasonable it seems like most people are using Windows-based authentication.

I used NIS back in my Solaris days too.  The important thing that NIS provides (really any centralized authentication) for a Linux based network is common user/group id numbers (UID/GID) for the various users.  NFS depends upon this.  NIS is just something more to learn. For my home network I don't use it however.  I only have to keep track of a few users UID/GID so I do it manually.  Of course I am user 1000 and my wife is 1001.  The tricky part is the GID (group ID's).  Ubuntu just uses the next available GID if you don't explicitly state the GID for any group.

Let me state that in a different way.  Use a common users and group when you share data between machines and possibly users with NFS.  

As you can see it is more to it than just sharing one machines /home directory.

---

### Post by zero2xiii on 2013-08-11
Hay,

Since it will only be two machines (one client, one host if you wish) it will be simple I guess. Just setting up the "client" to use the same username (Even the host only has a single user account) as the host will already remove some issues, getting the GID UID the same should not be that difficult. The rest of the stuff seems to only apply on a larger scale deployment (virtual workstations?) where more than one "client" will connect to a "host".

I'll set up a test scenario in a virtual environment first and see how it goes, if I encounter to many issues, I will just buy some more TB drives and rsync data between them (This might actually help since I then have a "backup" of my entire system as well.... hmmmmm)

Anyway thanks again for all the help, now I only need to start trying it out and see if it works or not.

Thanks

---

### Post by bab1 on 2013-08-11
> **zero2xiii said:**
> Hay,

Since it will only be two machines (one client, one host if you wish) it will be simple I guess. Just setting up the "client" to use the same username (Even the host only has a single user account) as the host will already remove some issues, getting the GID UID the same should not be that difficult. The rest of the stuff seems to only apply on a larger scale deployment (virtual workstations?) where more than one "client" will connect to a "host".

I'll set up a test scenario in a virtual environment first and see how it goes, if I encounter to many issues, I will just buy some more TB drives and rsync data between them (This might actually help since I then have a "backup" of my entire system as well.... hmmmmm)

Anyway thanks again for all the help, now I only need to start trying it out and see if it works or not.

Thanks

A couple of points of clarification.

Hosts can be either clients or servers of both.  The host is the real or virtual machine.  This means the OS running on physical  or virtual hardware.  A server in this context is the *process running in the background* waiting for a request from a client.  The client on the other hand is the application that is the requester of those services.  An example the server HTTPD can run on a host and that host can (through a browser) request web pages from itself.  Think localhost.

In Linux, The UID and GID is how file ownership is set.  The user and group names are *not* how these entities are defined.  Most of the time it will be the GID that will trip you up if you are the only user on both hosts.  By definition on an Ubuntu host the first user is always 1000.  The private user group is usually 1000, *but it does not absolutely  *have to be so,  The other group ID's should be monitored to see that they match up between the 2 hosts too.

I have had to correct GID's when I got lazy, so I know it can happen.

---

### Post by zero2xiii on 2013-08-12
> **bab1 said:**
> A couple of points of clarification.

Hosts can be either clients or servers of both.  The host is the real or virtual machine.  This means the OS running on physical  or virtual hardware.  A server in this context is the *process running in the background* waiting for a request from a client.  The client on the other hand is the application that is the requester of those services.  An example the server HTTPD can run on a host and that host can (through a browser) request web pages from itself.  Think localhost.

In Linux, The UID and GID is how file ownership is set.  The user and group names are *not* how these entities are defined.  Most of the time it will be the GID that will trip you up if you are the only user on both hosts.  By definition on an Ubuntu host the first user is always 1000.  The private user group is usually 1000, *but it does not absolutely  *have to be so,  The other group ID's should be monitored to see that they match up between the 2 hosts too.

I have had to correct GID's when I got lazy, so I know it can happen.

Sorry about the host vs server slip up. Must have been over tired when I typed it like that.

Also agreed with the GID and UID issue, I will address those, although it seems my current user is 1000. My user is part of different groups so I guess I should match up all of those on the remote "client" then.

Cheers

---

