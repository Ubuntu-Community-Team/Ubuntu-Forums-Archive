---
title: "NFS Share - Specify Network?  Also Permissions?"
date: 2007-10-27
forum: General Help
---

### Post by becatlibra on 2007-10-27
Okay - So i'm on Gusty now and I want to share a folder that was PREVIOUSLY NTFS.  I changed it over to EXT3 and want to use NFS instead of SMB to share it.  

Going through the GUI to share I am at a screen which says:

Add allowed hosts.  Now I want to add my whole network 192.168.1.0-192.168.1.255 so to speak.  I have seen different notations for this in other things (like smoothwall) and am not sure what is correct here  I go to Specify Network and then I get the options to key in Network and Netmask. 

Can I specify an IP range here?

Also, all the users on my network have the same username and password on each PC so presumably the permissions carry over?  Like, for instance, my son does not have read permission locally on some subdirectories of the shared folder (using group PARENTS to exclude) - I ASSUME an NFS share will take that into consideration - is that correct?

Thanks

Benjamin

---

### Post by kidders on 2007-10-28
Hi there,

> **becatlibra said:**
> I changed it over to EXT3 and want to use NFS instead of SMB to share it.You didn't need to do that ... at least not for sharing purposes. In any case, Ext3 will work better with your Linux. :-)

> **becatlibra said:**
> Can I specify an IP range here?You can specify anything mentioned in the man page for "exports" ... specifically, the stuff in the "Machine Name Formats" section. Out of sheer habit, I would probaby write "192.168.1.0/24" in your case, but there are other choices.

> **becatlibra said:**
> Also, all the users on my network have the same username and password on each PCFor NFS, that's largely irrelevant ... it's UIDs/GIDs and users' passwords on the machine serving the share that matter most. For your own sanity, I would suggest ensuring all user accounts & private groups used by actual people (ie _not_ including root, avahi, uucp, etc.) have the same UIDs & GIDs on all machines. Once that's the case, all ownership & permissions will behave as you would expect them to ... ie the fact that a particular directory may happen to live on a remote machine will be irrelevant, and your various Linuxes will all enforce the same access control restrictions on all PCs.

I hope that helps.

---

### Post by becatlibra on 2007-10-28
I know I didn't need to change to ext3 - that was more of a decision on my part.

As for the IP range, then the notation is the same as it is in smoothwall (ie: 192.168.1.0/24) -- That's great!

As for UIDs and GIDs -- hmm - what?  All the users have the same usernames and passwords on all the linux machines on my network but not the same user id Number.  So if I want my son (shane) to not be allowed to get to things he can't locally (because they are in the group 'parents' and only owner and group have read permissions) I need to REPLICATE that group on HIS MACHINE - as well as my other computers?

Is that what you are saying?

Thanks

Benjamin

---

### Post by becatlibra on 2007-10-30
Ok - there is no way to specify a range in the gui.  The options are host, network or ip and the ip only allows one address (as is to be expected) and the network (which I assumed would be the IP RANGE) does not allow the aforementioned notation of an IP range.  

Also, permissions?  I haven't heard back on this.

I assume there must be a conf file somewhere (possibly hosts.allow?) which I can modify to make this happen.  I just wanted to be able to do it through the GUI if possible, since it's Ubuntu and all.  I mean, personally I LOVE the command line but my family doesn't and I want to be able to show them 'how easy it is'

Anyway, I put in a single IP and the connection is refused from the client.  Any ideas on this either?

---

### Post by Zill on 2007-10-30
I also much prefer a GUI to the command line but have found that, in this case, the CLI really can simplify things.  It is also much simpler if UIDs for each user on each machine are kept the same.   I use NFS to permanently share data between two PCs and would guess that your requirements may be similar...

Create the following directories as root:
user1:/mnt$ sudo mkdir user2
user1:/mnt$ sudo mkdir user3
etc...

Install:
nfs-common
nfs-kernel-server
portmap

Configure:
/etc/exports
/etc/fstab
/etc/hosts
/etc/hosts.allow
/etc/hosts.deny

The man pages will clarify the syntax required for each config file.
Use the following commands to restart NFS after any changes:

sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/nfs-common restart
sudo mount -a -t nfs

---

### Post by becatlibra on 2007-10-30
When you say UIDs are you speaking of the actually user NUMBER or just the names and group names?

---

### Post by Zill on 2007-10-30
As kidders pointed out earlier, I understand that NFS relies on the User ID number, rather than the username.  If you cannot synchronise these then I believe you will need to install a NIS server - which seems far too complicated for me :-(

---

### Post by becatlibra on 2007-10-30
Is there a command to change UID?

---

### Post by kidders on 2007-10-30
Hi guys,

Sorry for ignoring this thread for a whole day ... I've a half-written post from yesterday sitting on a remote X display that might help with some of your questions. I'll submit it ASAP.

---

### Post by Zill on 2007-10-30
Take a look at this link...
[http://ubuntuforums.org/archive/index.php/t-259582.html]("http://ubuntuforums.org/archive/index.php/t-259582.html")
Maybe someone else can give another method.

---

### Post by kidders on 2007-10-30
> **becatlibra said:**
> I know I didn't need to change to ext3 - that was more of a decision on my part.

As for the IP range, then the notation is the same as it is in smoothwall (ie: 192.168.1.0/24) -- That's great!

As for UIDs and GIDs -- hmm - what? All the users have the same usernames and passwords on all the linux machines on my network but not the same user id Number. So if I want my son (shane) to not be allowed to get to things he can't locally (because they are in the group 'parents' and only owner and group have read permissions) I need to REPLICATE that group on HIS MACHINE - as well as my other computers?

Is that what you are saying?

Thanks

Benjamin



[COLOR=Silver](No, not really.) [/COLOR]The first thing worth mentioning is that NFS is a file*system* sharing protocol, not a file sharing protocol (eg AFP, Samba...). Perhaps the most obvious consequence of that is, since user & group names are irrelevant to a filesystem, they are also irrelevant to NFS.

In a larger setting (eg a university), user & group accounts are typically centrally controlled, and replicated (as you suggested) on all client machines. [COLOR=Red][Already mentioned by Zill][/COLOR] In your case, I would consider that unnecessary though. All I would do in your position is ensure that any UIDs and GIDs involved in file sharing are consistent on all PCs.

The usual result of not doing so is sort of the opposite of what you described above ... users may find themselves locked out of things they *should* be allowed to access. For example:[LIST]
[*]User 1010 on machine A mounts an NFS filesystem on machine B.
[*]The NFS share contains files owned by user 1010. Naturally, he will have full control over these, but not necessarily those owned by user 1011.
[*]Now, consider what would happen if the user*name* associated with UID 1010 on machine A is shane, and becatlibra on machine B. On machine B, UID 1011 might be shane.
[*]As a result, were shane to create files on the server, he would be unable to access them when he returned to his own machine.[/LIST]The effect would be very close (but not quite identical) to what would happen if you physically removed the NFS server's hard disk and plugged it into shane's machine. Since usernames are relatively unimportant, it would at least be theoretically possible for the user your PC knows as "shane" to be called "me" on shane's PC ... however consistency is generally preferred in practice.

Changing a UID/GID is relatively trivial, ordinarily. A "usermod" and a "chmod -R" tend to be enough. [COLOR=Red][Already mentioned by Zill]
[COLOR=Black]
**Edit: ** I agree with Zill ... manipulating user accounts & configuring NFS shares is best done with the CLI. That way, no mistakes get made.
[/COLOR][/COLOR]

---

### Post by Zill on 2007-10-30
becatlibra:  The link ["Modifying User and Group IDs to Support a Home Network"]("http://humanreadable.nfshost.com/howtos/modifying_ids.htm") may help demonstrate how to change your UIDs and, if necessary, GIDs.

---

### Post by becatlibra on 2007-10-30
it APPEARS I can do it through the Gnome User Manager.  UID is an option per user with up and down buttons to increment it.  Same with groups it APPEARS

Maybe it isn't the 'same thing'

---

### Post by Zill on 2007-10-30
becatlibra:  The Gnome User Manager will let you change the UID/GID for new users.  However, for existing user accounts you will also need to change ownership for all **existing** files in each home directory, hence the "find" and "chown" examples in my last link.

---

