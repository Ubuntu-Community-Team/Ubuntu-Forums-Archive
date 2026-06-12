---
title: "Secondary disk shared between Ubuntu and Mint"
date: 2018-07-28
forum: General Help
---

### Post by joselitux on 2018-07-28
Hi

I have a secondary internal disk with all my music and videos  accessed from mint with no issue. Installed Ubuntu as secondary OS but can&#8217;t play my music. Every time I try to access secondary disk Ubuntu ask for root password per every file , so you can imagine this makes my secondary disk unusable.

How I can share media between two Linux systems?

---

### Post by TheFu on 2018-07-28
To help, we need to know a few things.
* which file system is used?   Linux file systems require permissions and groups to work.
* how is the storage mounted? If through the fstab, then you can control things for NTFS file systems.  If it is automatically mounted, we need more data.
* which userid (use the 'id' command) can access it on Mint?  Does the same userid based on the 'id' command on Ubuntu work?

It is important this remember that Unix systems are multiuser, always.  File permissions are the cornerstone of all Unix security.  Always.

---

### Post by joselitux on 2018-07-30
Hi TheFu

file system is EXT4 and secondary disk mounts at boot with no intervention on my part. 

id command on Mint:
uid=1000(jomaweb) gid=985(users) grupos=985(users),998(wheel),1000(autologin)

id command on ubuntu:
uid=1001(joe) gid=1000(joe) grupos=1000(joe),27(sudo),108(syslog)

---

### Post by TheFu on 2018-07-30
Ok, so Linux file systems use the uid (a number) and gid (a number) to determine owner and group permissions.

Joe uid  = 1001.
jomaweb uid = 1000.

Those aren't the same, therefore only 1 of them can be the owner.  No way around that except to make the uid numbers match on both systems.  They can have any username joe/jomaweb, that doesn't matter, just the uid (number) matters.  But I suspect there is already a uid 1000 on Ubuntu.

As for groups, they work similarly, but 1000 is used in an odd way for "autologin", which doesn't make sense to me.  Groups like that should be under 500.  The users and wheel gids are higher than normal too.  If you don't want or cannot fix those things, you can always make a new group on both systems (important part is that the gid number match.  Then  add both of these users into the group on both systems, and follow normal make-users-work-together permissions techniques so both userids can create and edit and read the files.  Normally that is ug+rwx,g+s permissions on the top level directory and forcing the group to be whatever you name it.  Then any new files or directories  will always retain the correct permissions automatically.  Any existing files and directories under there will need their permissions modified manually.  Clear as mud?

BTW, Unix permissions is a basic skill that everyone using it should understand.  It works on every platform that isn't Windows or mainframes, so learning this stuff pays off on OSX, iOS, Android, all Linuxen and all Unixen. Also, it hasn't changed since 1970-ish, so you don't need to worry that something new will come along in 3 yrs.  I expect normal Unix permissions to be what we use in 100+ yrs.

Sorry I'm being vague - it is because there are many different ways to solve the problem.  Often on a network with multiple systems, either LDAP or NIS would be setup to ensure userids and groups worked across every computer on that network. But I suspect those aren't something you'd want, but they are handy.

---

