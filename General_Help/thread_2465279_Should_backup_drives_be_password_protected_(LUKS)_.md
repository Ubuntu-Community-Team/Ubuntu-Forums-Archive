---
title: "Should backup drives be password protected (LUKS) &amp; can you protect an existing drive"
date: 2021-07-28
forum: General Help
---

### Post by freeflyjohn on 2021-07-28
I am in the process of setting up a backup system for the HDDs in my server.

I am using external USB HDD's for the backup drives (WD Elements).

I have completed backups on two drives so far -  the first drive was formatted as ext4 and the second drive was formatted as ext4 and with a password (LUKS)

Is it good practice to password protect backup drives ?

I plan to unmount the backup drives once the backup is complete, but my reasoning for considering password protection are:

1. In case someone hacks into my server and gets access to the backup drives (they can simply mount the drive)
2. To prevent ransomware infecting the backup drives
3. To prevent viruses infecting the backup drives

If password protection is good practice, then is it possible to password protect a HDD that already has data on it, or does the drive need to be reformatted to do this ?

---

### Post by sudodus on 2021-07-28
I think you should also consider physical risks: fire, flood, theft. For this reason it is a good idea to have (at least) double backup drives, and one of them always in another house.

There are other people at these forums, who know better the issues you are asking about (how to set up the software for backup) ...

---

### Post by freeflyjohn on 2021-07-28
> **sudodus said:**
> I think you should also consider physical risks: fire, flood, theft. For this reason it is a good idea to have (at least) double backup drives, and one of them always in another house.


Agreed, I used to keep a backup drive at work in the office.

But in my latest job I don't have any drawers, just a desk.  And since COVID Im rarely in the office now and there have been new starters who have been using my desk, so I don't even know if I have a desk anymore !

I moved to a new area, away from friends and family, so I don't know anyone who I could leave a backup drive with, other than my ex who I'd rather not leave personal data with even if its password protected !

I could always bury it in the garden !

---

### Post by TheFu on 2021-07-28
> **freeflyjohn said:**
>  
Is it good practice to password protect backup drives ?

I plan to unmount the backup drives once the backup is complete, but my reasoning for considering password protection are:

1. In case someone hacks into my server and gets access to the backup drives (they can simply mount the drive)
2. To prevent ransomware infecting the backup drives
3. To prevent viruses infecting the backup drives

If password protection is good practice, then is it possible to password protect a HDD that already has data on it, or does the drive need to be reformatted to do this ?

Yes, having data on encrypted storage is a "good practice." Just be 100% certain you have at least 3 copies of the data on different physical storage.

Encryption only helps with protection when the storage is off-line or the system is powered off.  It encrypted storage is mounted, it doesn't provide any extra protection against ransomware or viruses.  No directly connected storage or storage that the client machine can access on network storage provides any protection against either viruses or ransomware.

The protect against viruses or ransomware, the following are necessary:
[LIST]
[*]Backup storage cannot be accessed by the client machine directly.
[*]Versioned backups are mandatory, so if 100,000 files are encrypted, the backup will make a new version of 100.000 files, retaining the prior file versions.
[*]The backup data must be "pulled" by a backup server, never "pushed".
[*]No network file storage method should be used. Don't use CIFS, Samba, NFS, sshfs, sftp, DFS, DAFS, or any other commonly used network storage protocols.
[/LIST]

So, what does that leave?
[LIST=1]
[*]Versioned backup tools. Keep as many versions (also called backup sets) as it would require for you to recognize any file corruption.
[*]Network backup server that can "pull" the data to be backed up.
[*]Encrypted, authenticated client/server network protocols supported like rsync or many of the most common backup tools allow.
[*]Automatic backups. If they aren't automatic, then, being a human, you'll stop doing them as often as you'd like. If they aren't daily, the risk of forgetting or losing track of the prior backup set becomes much greater.
[*]Any backup tool needs to capture the owner, group, permissions, ACLs and xattrs for each file as those values change over time. If backing up just 1 user's HOME, that isn't nearly so important, but Linux is a multi-user OS from the ground up, so for a useful system backup, all of those things AND the actual data in the file must be part of the backups.
[*]Any backup solution that hasn't been test restored to a 100% new HDD, isn't really a backup that you can trust. Until it is actually tested and verified, you don't know what is missing.  Plan on about 5 restore attempts to finally get a good backup process that does include all the steps and data that is needed for a successful restore.  Trust me.  It took me 5 attempts to get it right.
[/LIST]

Encrypted backups are mainly about not worrying if the HDD needs a warranty replacement or if the HDD could walk off or if the HDD needs to be stored off-site in a location you don't physically and legally control 100%.

And always remember that encryption is only useful when the drive is powered off and unused.  Once it is mounted, it is just like any other disk and open to attacks, data corruption, malware, and other bad things.

---

### Post by freeflyjohn on 2021-07-29
Thanks TheFu, you raised some interesting points.

I didn't realise that encryption will not protect against malware and viruses etc so thats useful to know

I was wondering if there is a device that fits inline with the USB cable and allows you to disconnect the HDD with a switch (for example it could turn off the 5V supply?).

The reason for this is to save having to physically connect/disconnect the USB cable each time.

 I have 4 external USB HDDs so it would be a pain to keep connecting/disconnecting and it would eventually lead to wear and damage of the connectors.

Its also interesting what you say about backup must be pulled by the client, not pushed.

I recently backed up the data from my Mac to the server using rsync.  To do this I ran rsync on the Mac over ssh.  So would this be classed as the backup being pushed ?  Should I have done it the other way around and ran rsycn on the server to backup the data from the Mac, is this what you mean by being pulled ?

If so, out of interest what difference does it make whether the data is pushed or pulled ?

You also mentioned that no network file storage method should used such as samba, sshfs etc.  

When I backed up the data from my Mac, I used rsycn with SSH (you may remember my post about this from the other week).  Is this different to sshfs ? Is it ok to use rsycn with SSH ?

---

### Post by sudodus on 2021-07-29
@freeflyjohn,

SSH is standard for rsync, and I think it is OK (as already discussed, 'pull from the server', do *not* 'push from the client'). You should use [authentication with a key](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) (and not with a password).

I *think* the advice by TheFu is applicable to a computer, that can be seen from the internet, a web server, and 'pull from the server' means to run the backup from another computer, a backup server, that is *not* seen from the internet. 

@TheFu, please tell me if I understand correctly :-P

---

### Post by TheFu on 2021-07-29
> **freeflyjohn said:**
> Thanks TheFu, you raised some interesting points.

It is important to learn to think like an attacker would, at least for the obvious attack vectors.

> **freeflyjohn said:**
> 
I didn't realise that encryption will not protect against malware and viruses etc so thats useful to know

Well, it does in that the data can't be stolen. But it does NOT because if the data can be modified, added, or deleted, then the backup isn't really secure.

> **freeflyjohn said:**
> I was wondering if there is a device that fits inline with the USB cable and allows you to disconnect the HDD with a switch (for example it could turn off the 5V supply?).
A properly mounted storage system can't take having the electricity yanked out. Be certain to umount it first.

> **freeflyjohn said:**
> The reason for this is to save having to physically connect/disconnect the USB cable each time.
  Hence, why some sort of backup server is suggested. A raspberry-pi v4 should be able to serve this for about $50. It supports USB3 and has a real GigE NIC, unlike prior models.

> **freeflyjohn said:**
>  I have 4 external USB HDDs so it would be a pain to keep connecting/disconnecting and it would eventually lead to wear and damage of the connectors.
USB is a terrible connection method.  Use eSATA whenever possible.

> **freeflyjohn said:**
> Its also interesting what you say about backup must be pulled by the client, not pushed.
  If the client is hacked and can instigate a connection to the backup server, then the server can be compromised as well. I always thought that was obvious.  Think like an attacker.

> **freeflyjohn said:**
> I recently backed up the data from my Mac to the server using rsync.  To do this I ran rsync on the Mac over ssh.  So would this be classed as the backup being pushed ?  Should I have done it the other way around and ran rsycn on the server to backup the data from the Mac, is this what you mean by being pulled ?
If the Mac "pushed" the data, then yes.  Actually, if the Mac can ssh into the back server at all and that userid can delete any files in the backup area, then it is nearly as vulnerable.
If the backup server has a 1-way connection into the client (Mac) to be backed up, and "pulls" the data, placing it into storage that isn't accessible from any other system on the network, then that should be good enough.  Attackers are likely to do 2 steps, but probably not 3 steps unless we are being directly targeted. 

> **freeflyjohn said:**
> 
If so, out of interest what difference does it make whether the data is pushed or pulled ?
see above.

> **freeflyjohn said:**
> 
You also mentioned that no network file storage method should used such as samba, sshfs etc.  


> **freeflyjohn said:**
> 
When I backed up the data from my Mac, I used rsycn with SSH (you may remember my post about this from the other week).  Is this different to sshfs ? Is it ok to use rsycn with SSH ?

All connections and transfers need to be encrypted. ssh is the standard, assuming ssh-keys/certs are used, not passwords.  Also, only approved client systems should even be allowed to use ssh connections.  For backups, there needs to be a uid=0 connection, which is dangerous, so we have to take extra steps to limit that to be only allowed using ssh-keys/certs AND only initiate from the backup server.  For even more security, we can limit the program allowed to run over that connection.  This is how github works, by limiting the exact commands and the exact userid allowed.  They don't limit which client system any specific userid connects from, but with a root connection, we should.

rsync provides 80% of what a good backup needs.  A real backup tool like rdiff-backup provides 100%.  Where rsync fails is that only the latest user, group, permissions, ACLs, and xattrs are retained.  People under estimate how critical it is to capture this information as it changes over time.  I learned it the hard way.  Please learn from my mistake.  Backups just aren't about have 1 copy and using rsync to mirror a group of corrupted files just makes two copies of the same corruption.  VERSIONED BACKUPS are absolutely critical.

---

