---
title: "how do i Delete folder with files from another computer"
date: 2015-03-01
forum: General Help
---

### Post by offir on 2015-03-01
I have several computers Connected to pfsense router

Two computers that are running ubuntu 12.04 with cairo dock
Two computers that are running ubuntu 14.04 with cairo dock

i remove unity gui from all

and several computers that are running windows xp and win7


i have a folder on my computer (ubuntu14.04) with files from an old computer with ubuntu 10.04 (The computer has been formatted)

i want to delete this folder but i cant 
I do not have permission (wtf? how the hell I do not have permission in my computer ????   it is my computer!!!)
in the premission tab it says the owner is ```
Avahi mDNS daemon
```

the only Avahi mDNS daemon i know of is install on pfsense Machine (another old computer)

how do i Get ownership on this folder

---

### Post by offir on 2015-03-01
So:-s
Is there a way to get this folder permissions
I'm stuck if it ??:confused:



Question for the future
How do I avoid this situation again


All file-sharing I do are like that

---

### Post by CaptainMark on 2015-03-02
It's a simple scenario with a simple fix, the files were created on a different computer by a different user so as far as the system is concerned they belong to someone else and wont let you edit them, fortunately you can over ride this easily enough using this command ```
sudo chown offir:offir /home/old\ computer
```If you want to do this to all directories and sub-directories use  ```
sudo chown -R offir:offir /home/old\ computer
```Note: I dont know your specific user name or where you have this folder on your computer so you may have to amend this slightly but I don't think you'll have trouble with that.

---

### Post by offir on 2015-03-02
Thank you
It worked

How do we do it will not be that way in the future
I have all kinds of folders every time they demand a username and password ?

---

### Post by CaptainMark on 2015-03-03
That will work for any folder that you have this trouble with, once you make your user the owner of the files then they are yours for good, if you have another specific example of issues like this then feel free to explain the issue you're having.

---

### Post by offir on 2015-03-03
There are all kinds
If for example I use a computer running Windows 7
And want to save files on a computer running Ubuntu

in Ubuntu I get a message that I have no permissions
Only the user of Windows 7 has


As in this case only 
Or the opposite


How do I do not have this problem again

I will be able to save files to any computer on the network
And access them from any computer on the network

And it was like that
I do not know why it has gone crazy

---

### Post by bab1 on 2015-03-03
> **offir said:**
> There are all kinds
If for example I use a computer running Windows 7
And want to save files on a computer running Ubuntu

in Ubuntu I get a message that I have no permissions
Only the user of Windows 7 has


As in this case only 
Or the opposite


How do I do not have this problem again

I will be able to save files to any computer on the network
And access them from any computer on the network



And it was like that
I do not know why it has gone crazy
File and directory ownership and permissions on locally mounted file systems (external or internal) act differently from remote mounted file systems (SMB or NFS).  In addition remotely mounted NTFS file systems assign file and directory ownership and permissions ONLY at mount time.

If you configure your file system with user and user-groups in mind you can have accessible by all users or some users or specific users only.  You should specify what you want to do exactly.  Then you can design the file system from that point on.

I have both SMB (Samba file shares) and NFS (file exports) available to all from 1 file server.  Some of these remote file shares are private to specific users.  Some are available to specific sets of users defined by user groups and some of these shares are open to all users of the system (including guests).

In short; if you serve files and directories to remote clients the ownership and permissions do not need to follow the original permissions and ownership.

---

### Post by offir on 2015-03-04
There are several computers in a network
(Mother father sister brother sister)
Everyone has at least one folder
Running the sharing
Usually 3 (music, video, pic, doc, etc etc)

I want all the files of all
Be accessible to all
Without any permissions messages


My plan was to build a NAS 
But it turns out that it costs a lot of money
So now we're using file sharing like this

---

### Post by bab1 on 2015-03-04
At this point we are seriously OT (off topic).  I suggest you start a separate thread with the subject of: Sharing FIles using SMB or NFS.

With that we can address: file systems, user management and data sharing.  It is worth exploring whether you should use distributed file sharing or centralize the data on one of the machines and share that data to the others.

---

### Post by offir on 2015-03-04
> At this point we are seriously OT (off topic). I suggest you start a separate thread with the subject of: Sharing FIles using SMB or NFS.


I wanted to do it after I got a solution to the first problem
But
I did not know where it belongs
Networking & Wireless forum
Or here

I will mark this issue is resolved
And will open a new message here
If it does not fit the manager will delete
And I will open a new message in Networking & Wireless forum

---

