---
title: "Backuping files via SFTP"
date: 2008-07-09
forum: General Help
---

### Post by gizm0 on 2008-07-09
I'm trying to setup a system to backup my documents&images from Ubuntu to remote Ubuntu Server. I have tried to think how i would do it, but it seems to be bit complicated. This is what i'm trying to do:
[LIST=1]
[*]Program checks what files are new and packs them to zip file (also putting password for the zip file)
[*]Program transfers the newest zip files to remote location
[*]Program removes the zip file(s) from the source 
[/LIST]

So the main problem is that i want files to be encrypted in the Ubuntu server so that no one can read them without the password. There are about 50Gb of files to backup and about 10mb of new files every week.

Any suggestions how to do this?

---

### Post by ghostdog74 on 2008-07-09
> **gizm0 said:**
> I'm trying to setup a system to backup my documents&images from Ubuntu to remote Ubuntu Server. I have tried to think how i would do it, but it seems to be bit complicated. This is what i'm trying to do:
[LIST=1]
[*]Program checks what files are new and packs them to zip file (also putting password for the zip file)

check the man page of tar and zip. zip can let you include a password
> 
[*]Program transfers the newest zip files to remote location

sftp, ftp 
> 
[*]Program removes the zip file(s) from the source 
[/LIST]

you just need the rm command

---

### Post by HermanAB on 2008-07-09
Hmm, Rsync over SSH is generally the best way to do it.  Some Googling and man page reading will get you going.  It is not difficult.

Cheers,

Herman

---

### Post by p_quarles on 2008-07-09
> **HermanAB said:**
> Hmm, Rsync over SSH is generally the best way to do it.  Some Googling and man page reading will get you going.  It is not difficult.

Cheers,

Herman
+1 that's the best way handle the file transfer.

For protecting your files from prying eyes, Zip is not the best way to go. The password protection is very weak and won't stop anyone. Plus, it would unnecessarily complicated to automate this along with rsync.

I would suggest, instead, an encrypted partition -- this can be either a real partition/disk drive or a loopback device acting as a container for the encrypted filesystem. It's relatively simple to set this up to mount this encrypted filesystem when you're running the file transfer and then unmounting it (and thereby effectively closing it from everyone who doesn't own a quantum supercomputer) when it's not in use.

---

### Post by gizm0 on 2008-07-09
> **p_quarles said:**
> +1 that's the best way handle the file transfer.

For protecting your files from prying eyes, Zip is not the best way to go. The password protection is very weak and won't stop anyone. Plus, it would unnecessarily complicated to automate this along with rsync.

I would suggest, instead, an encrypted partition -- this can be either a real partition/disk drive or a loopback device acting as a container for the encrypted filesystem. It's relatively simple to set this up to mount this encrypted filesystem when you're running the file transfer and then unmounting it (and thereby effectively closing it from everyone who doesn't own a quantum supercomputer) when it's not in use.

How do i automate the mounting and unmounting of the truecrypt partition? As far as i know i think i need to manually enter the password for the partition.

---

### Post by kevdog on 2008-07-09
I prefer unison for two way synchronization -- rsync for one way transfers.

---

### Post by gizm0 on 2008-07-09
> **kevdog said:**
> I prefer unison for two way synchronization -- rsync for one way transfers.

In this case i will use rsync. So any suggestions for automating truecrypt?

---

### Post by gizm0 on 2008-07-10
I figured out last night one way to do this:
[LIST=1]
[*]Source workstation connects to remote server via SFTP using public key
[*]Workstation uploads Truecrypt key to remote server
[*]Workstation sends command to mount truecrypt partition using the uploaded key
[*]Rsync connect to the remote server and starts uploading new files to the remote server
[*]Workstation sends command to umount truecrypt partition in remote server
[*]And at the last stage workstation sends command to remove the truecrypt key from the remote server and disconnects the connection
[/LIST]

Does this sound secure enough or am i making it too complicated?

---

### Post by gizm0 on 2008-07-10
I'm now trying to create truecrypt keyfile, but i can't find option to create it. I have searched guides and found that i need to use command: truecrypt --keyfile-create /media/disk/mynewkey4

This command does not work and i get error:
Unknown long option 'keyfile-create'
Error: Incorrect command line specified.

So have they removed that option from truecrypt 6.0a?

*SOLVED* I created the keyfile with "openssl genrsa -des3 -out mykey 1024". 

*EDIT* I still have one problem with Truecrypt mounting. It asks system administrator's password from time to time. How do i mount my partition without Truecrypt asking the system administrator's password?

*SOLVED* I have created user group for the users using truecrypt and that's how i got it working. ([http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10-p2](http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10-p2))

---

