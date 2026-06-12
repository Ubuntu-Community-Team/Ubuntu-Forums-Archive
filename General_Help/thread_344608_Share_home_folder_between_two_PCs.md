---
title: "Share home folder between two PCs"
date: 2007-01-23
forum: General Help
---

### Post by isync on 2007-01-23
Hit there!

I am running edgy on two identical machines and would like to share their home folders between them. So far I tried the built in functions of ubuntu but had no real luck on getting it to work easily.

Either I could only transfer from A to B but not from B to A or I got permanent password/ security issues.

Can anyone post a quick step by step instruction? Samba or NFS doesn't care, it should just work. Basically I am trying to save a fileserver here, as one machine would more or less end up as such.
Would be nice if you could post a few notes if this opens up security holes...

THANKS in advance! ):P

---

### Post by isync on 2007-01-23
Anyone with a quick copy&paste HOW TO for me?

---

### Post by lol on 2007-01-23
Just to make sure, are you trying to:

1 - have two independant PC with a synchronized home folder, which means that you will be able to boot and use either of the PC even if the other is down, or

2 - have one PC (A) acting as a file server and another (B) that will mount a remote partition on which to users' home will be located. In this case you will always need A to be up and running to be able to use B...

---

### Post by isync on 2007-01-23
> **lol said:**
> Just to make sure, are you trying to:

1 - have two independant PC with a synchronized home folder, which means that you will be able to boot and use either of the PC even if the other is down, or

2 - have one PC (A) acting as a file server and another (B) that will mount a remote partition on which to users' home will be located. In this case you will always need A to be up and running to be able to use B...

1. would require a fileserver, right? Not what I had in mind.

2 is the desired configuration. Essentially one machine (which is not a dedicated fileserver but a normal desktop using the shared home folder) should act as a kind of fileserver, while another has write access and may put files onto it. But it should be transparently, just as if you would have two boxes in front of you and you can stuff things in let's say box A or box B and you could see both boxes from both machines.

Just this:
Box A has a /home dir and Box B can put things into it.
Box B has a /home dir and Box A can put things into it.

Is this impossible as only one machine can act as fileserver??

---

### Post by bodhi.zazen on 2007-01-23
I would use nfs:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

You must set you mount point other then /home for the nfs /home

---

### Post by matthewstory on 2007-01-23
yeah, i'd go NFS as well . . . 

on the file server:

aptitude install nfs-user-server

then configure it (you'll need to use sudo to edit these):

edit the /etc/exports file add this line:

/home/<name of dir> <ip of other machine>(rw)

edit the /etc/hosts.allow file add this line

ALL:<ip of other machine>

edit the /etc/hosts.deny file add this line:

portmap:ALL

on that machine restart nfs:

sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/nfs-user-server restart

Then edit the /etc/fstab file on the other machine add this line:
<ip address of the server>:/home/<name of dir>/ /home/<name of dir> nfs defaults 0 0

Then mount it:
sudo mount <ip address of the server>:/home/<name of dir>/

and you're good, it should mount on boot after the initial config.  Also you'll need to make sure that the UIDs of the two users on the different machine are the same, so that the read write access are the same, thiscan get nasty.  But you'll need to change the UID values on one of the boxes if they aren't the same do this by editing the /etc/passwd and /etc/group files and changing the UID values to match the other server and you should be good.  Then you'll just have to sudo chown <username>:<username> all the files that person owned before so that it matches properly again.

If you have any questions just ask.

---

### Post by isync on 2007-01-24
It works! Thanks for the short walkthrough!

Some comments:

When I wanted to
```
sudo /etc/init.d/nfs-common restart
```
the machine complained about no exisiting nfs-common, so I did
```
sudo aptitude install nfs-common
```
Was this right? (It worked then)

Next on
```
sudo mount <ip address of the server>:/home/<name of dir>/
```
it complained that <name of dir> doesn't exists.
In the HOWTO supplied by bodhi.zazen ([http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)) it says the dir has to exist on the CLIENT machien as well, so I created it and it worked.

Then the 
sudo mount <ip address of the server>:/home/<name of dir>/
ran OK but took some time (~20 secs) - does this hint on malconfiguration?

Last thing is a probable mis-design on my side: I chose /home/shared on the fileserver-machine as shared dir, which I had to create using sudo (as it seems, ubuntu does only allow the root to create files under /home...
Now I am only able to write to this dir (from client and from fileserver itself) as root!!
So: Should I create the folder under /home/<user>/shared or is it possible to change permissions on dirs under the /home folder?

Thanks a LOT! ):P

---

### Post by Jason_25 on 2007-01-24
My NFS shares also mount slow.  I use the nfs-kernel-server though for supposedly better performance.  Strangely, when I mount the same shares from my GNU/Solaris server it is instant.  Also , I have no problem sharing my home directory.  I usually share that and a usbdisk.

---

### Post by isync on 2007-01-24
Mmh, in the HOWTO which is mentioned on this thread, they also use the nfs-kernel-server. What do I have to edit to switch between these two?

Regarding the permission issues - Could someone please shed some light?

Actually machine A (server) and B (client) have now files in their /home/exampleuser directory. That's why I created the fresh /home/shared folder.
1. How can I share this /home/shared directory over to the client machine and have write access on both machines A and B?

2. Is it possible to just share the /home/exampleuser dir on the server A, without getting into conflict with the files already residing in the /home/exampleuser dir on B (not the same files). Wouldn't this mean that on B is actually no physical /home/exampleuser dir, until it is mounted and thus virtually present on B? (I admit, a cleaner Client-Server design..) And wouldn't this impose conflicts when both machines are up and used under the same user "exampleuser" (i.e. with files like in .mozilla etc.)?

---

### Post by SyvanX on 2007-01-24
Consider unison, I don't share my entire home directory, but a major portion of it between 3 computers on 3 different networks + an apache server running DAV.  Unison syncs up two directories through ssh, you can setup passwordless logins using ssh-agent and run it via crontab on a custom schedule.

If anyone is interested I'll post a how-to.
[URL="http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html"]
Unison Manual[/URL]

---

### Post by isync on 2007-01-24
Although I though about the network activity produced by a NFS mounted directoy (is there any?), I would prefer to stick with the NFS solution and not a synchronizing solution.

Could anyone comment on my previous post?

> Mmh, in the HOWTO which is mentioned on this thread, they also use the nfs-kernel-server. What do I have to edit to switch between these two?

Regarding the permission issues - Could someone please shed some light?

Actually machine A (server) and B (client) have now files in their /home/exampleuser directory. That's why I created the fresh /home/shared folder.
1. How can I share this /home/shared directory over to the client machine and have write access on both machines A and B?

2. Is it possible to just share the /home/exampleuser dir on the server A, without getting into conflict with the files already residing in the /home/exampleuser dir on B (not the same files). Wouldn't this mean that on B is actually no physical /home/exampleuser dir, until it is mounted and thus virtually present on B? (I admit, a cleaner Client-Server design..) And wouldn't this impose conflicts when both machines are up and used under the same user "exampleuser" (i.e. with files like in .mozilla etc.)?

---

### Post by bodhi.zazen on 2007-01-24
> **isync said:**
> Although I though about the network activity produced by a NFS mounted directoy (is there any?), I would prefer to stick with the NFS solution and not a synchronizing solution.

Could anyone comment on my previous post?

I think you can do what you want but it is hard to follow what you are asking and your structure.

Of course nfs allows you to mount a directory read-write. This is done via configuration of nfs on the server and configuration on the mount point on the client.

Second, as with all file systems you must have a mount point. The mount point will be an empty directory when the nfs is not mounted.

I do not under stand what exactly you are doing. Are you mounting /home or /home/user_name or /home/data_partition ???

I think you are using the same directory for nfs share and mounting on both machines at the same time and that will not work.

On each server you need to define you shared directory.

On each client you need a mount point.

For example, on the server you can have a directory, /home/share that is available to clients.

On the client you can have a mount point /home/share.

You mount with mount IP:/home/share /home/share

But the client remains a client and does not offer /home/share back to the first machine as a share ....

---

### Post by isync on 2007-01-24
> You mount with mount IP:/home/share /home/share

But the client remains a client and does not offer /home/share back to the first machine as a share ....

I know. (That's what I did.)
But I have a permission problem. As it seems only root is allowed to write to /home/shared in ubuntu... Any solution?

Thanks!
(I won' t drift off into OT themes like network overhead in this thread again... ;-) )

---

### Post by bodhi.zazen on 2007-01-24
I understand your question now. Yes, there is an easy solution.

On the client, in a terminal (with the share mounted):```
sudo chown root:users /home/shared
sudo chmod 777 /home/shared
```

---

### Post by matthewstory on 2007-01-24
if you wanted to switch to the kernel server (which i wouldn't recommend for a novice, which is why i went with the user server . . . easier to configure and maintain, and all that . . . and the performance hit isnt' that bad compared to the ease of use).  Simply install the kernel server, it will  automatically uninstall the user server:

sudo aptitude install nfs-kernel-server

As far as your question about conflicts, you could just mount the original home share, there won't be conflicts.  When you mount an NFS share on a folder, the content of that folder will "disappear."  Meaning that the only stuff you will see in the mounted folder is the stuff on the NFS share.  When you unmount it, all of the local files will "reappear."  So there is no danger of conflict.

---

### Post by isync on 2007-01-25
It works! Thanks, bodhi.zazen for the chown hint!
And matthewstory, thanks for the walkthrough and such (I will not touch nfs-kernel-server..).

Thanks all!
:D

---

### Post by gkffjcs on 2008-05-23
I know this is a little bit late, but here goes!
The reason the folder your are going to mount on the client needs to pre exist on the client is because of how linux the underlying system in debian/ubuntu deals with filesystems. Linux/Unix alike mount file systems onto folders. Nfs is basically the same as any other file system in this regard. You mount it onto a preexisting directory. Also if you already have files in the directory you want to mount you can leave them there. For instance if /home/<username> has files in it, you can leave them there and mount another file system on top of them without effecting the files already there. Of course while another file system is mounted there you will not have access to the file that are on the local filesystem, essentially under the new file system. 

  Also about file permissions. Each file in a linux/unix compatable file system, nfs being one of them along with ext3, ext2, riserfs, and also hfs+ on mac OSX, as well as many others; contain special bits on every file and folder denoting who owns, has rights to or can read form it. The folder /home is owned by root. The only user on the system who can right to it is the root. The folder /home/<username> is owned by <username> this allows the user to write to his/her own home folder. These permissions can be changed by using the chmod and or chown commands. There are many good resources that explain how these work, as well as many further details that I have not gone into when it comes to folder permissions.

---

