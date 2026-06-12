---
title: "Changing User access permissions for applications"
date: 2014-01-24
forum: General Help
---

### Post by JohnJames86 on 2014-01-24
Hi!

I'm sure this must have been asked before but I can't find a suitable thread.

When I run an application (Digikam) I can read photo files but I can load, edit, change or delete.
When I inspect the properties-permissions of the application shortcut it shows,
Owner - David, Access - Read & Write
Group - david,  Access - Write only
Others - Read only

I am running Ubuntu Studio 13.10 with a Synology NAS on the network.  Setting up the NAS was a problem to me as a newbie and I am not sure I have full access permission as I have had several attempts a mounting the NAS via both cifs and nfs.  At the present time I am using cifs and the fstab entry is as follows

//192.168.1.253/PUBLIC/My\040Documents /media/My_Documents cifs user,uid=david2,gid=users,rw,suid,credentials=/root/.smbcredentials 0 0

The application Digikam was installed via the Ubuntu Software Centre

Something else I should point out is that, using a Windows, Linux mix on the network required me to change my user name from david to david2 because I already existed on the networks as david using a different password on a Windows PC.  I also changed the home folder from /home/david to /home/david2.  I hope this isn't part of the problem.

Any help pointing me in the right direction would be appreciated.

Thanks

---

### Post by Lars Noodén on 2014-01-24
When sharing filesystems between operating systems, it is the numeric user id and numeric group id that count.  Regardless of what that number is called, the system uses that number.  That said, it is easier for people to work with names rather than numbers.  

So it might be a permissions problem.  If you are user david2, then you can take ownership of the files with [chown](http://manpages.ubuntu.com/manpages/trusty/en/man1/chown.1posix.html)

```

sudo chown -R david2:david2 /home/david2/

```

However, if the numeric ids are different for the main accounts on your two systems, then you will have to keep chowning until the ids are synchronized.

---

### Post by JohnJames86 on 2014-01-24
Hi!

You're fast .... thanks.

When I run that chown code it replies


chown: invalid group: 'david2:david2'

Maybe this says it all. I've just looked using  Users and Groups in the available groups and sadly, I don't exist as david2, just plain old david.  How do I rectify this?

Thanks

---

### Post by Lars Noodén on 2014-01-24
What user are you logged in as?  That's the one you should give ownership of the directory to.  

```

whoami
id

```

---

### Post by JohnJames86 on 2014-01-24
Hi!

I created the group david2 and chown'd my home folder as you suggested and that was error free

This is what I get.

david2@david-N68S3:~$ whoami
david2
david2@david-N68S3:~$ id
uid=1000(david2) gid=0(root) groups=100(users),0(root),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),104(fuse),108(netdev),112(lpadmin),123(sambashare),1002(privileged),1003(david2)

I'm suprised how many groups I belong to

---

### Post by Lars Noodén on 2014-01-24
Membership in all those groups is given to the first user.  

The uid and gid in the fstab entry for cifs should to be set to match the ones your account is using, if not already.

People more familiar with cifs might spot something more.

---

### Post by JohnJames86 on 2014-01-24
@lars

Thanks for the attention.  A feeling of total confusion is descending as I have drilled down into the NAS folder system and I see for every folder I look at the permissions are set as follows

Owner: David (david2)  Access: Read & Write
Group: Users               Access: Read & Write
Others:                       Access: Read & Write

But with all the files in all the folders I see,

Owner: David (david2)  Access: None
Group: Users               Access: None
Others:                       Access: Read & Write

I think I need to read the book more regarding the priviledges set up in the NAS and the use of cifs

I'll post back if I sort anything

Thanks once again

---

