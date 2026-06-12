---
title: "Password Protecting Files"
date: 2007-01-25
forum: General Help
---

### Post by Prometheum on 2007-01-25
I have read over most of the threads dealing with password protecting FOLDERS, and mostly all that can be said is something along the lines of "well we need filesystem encryption", which leads to a stream of posts outlining how to put everything on an encrypted archive or chmod 700 something. 

Here is my situation. I have a laptop which I bring to school. However, my school is of the conservative kind and some of the books (and movies and pictures) would be grounds for suspension/expulsion. I don't want to mount anything on a new filesystem, I use the files often at home so I don't want to .tar them, and I even read some of the things at school so it would be impractical to compress/decompress. I don't want to screw around with user accounts. Is the ubuntu community really going to tell me (and everyone else asking this, there seem to be a lot) that the only way to password protect my folders is by doing something ridiculous? I don't really care if someone can boot off of a live CD and get at the files, though it'd be nice if they couldn't. I don't really need encryption, but it'd also be nice. Is there anything (a program, a nautilus script) that would allow me to put a password on a folder so that if MY user tried to open it it would display a password prompt?

---

### Post by bruenig on 2007-01-25
> **Prometheum said:**
> I have read over most of the threads dealing with password protecting FOLDERS, and mostly all that can be said is something along the lines of "well we need filesystem encryption", which leads to a stream of posts outlining how to put everything on an encrypted archive or chmod 700 something. 

Here is my situation. I have a laptop which I bring to school. However, my school is of the conservative kind and some of the books (and movies and pictures) would be grounds for suspension/expulsion. I don't want to mount anything on a new filesystem, I use the files often at home so I don't want to .tar them, and I even read some of the things at school so it would be impractical to compress/decompress. I don't want to screw around with user accounts. Is the ubuntu community really going to tell me (and everyone else asking this, there seem to be a lot) that the only way to password protect my folders is by doing something ridiculous? I don't really care if someone can boot off of a live CD and get at the files, though it'd be nice if they couldn't. I don't really need encryption, but it'd also be nice. Is there anything (a program, a nautilus script) that would allow me to put a password on a folder so that if MY user tried to open it it would display a password prompt?

Make root own it and give no permissions to others and use sudo. Seems that you could also put them a . directory and nobody will ever see them. Unless they are clever enough to ctrl + h.

---

### Post by euler_fan on 2007-01-25
Well, TrueCrypt might be an option if you want to learn a command line system for doing encryption, except that you don't seem to want to do folders or encrypted drives. [edit] After re-reading your post, TrueCrypt is definately something to look at. If properly configured it should (so long as you can make the partition big enough for all your files in one place, or perhaps two or three) keep most anyone out.[http://www.truecrypt.org/]("http://www.truecrypt.org/")[/edit]

Nonetheless, if you are serious about security, that is probably the best option.

It creates a "virtual drive" on your machine that is encrypted and password protected, so I would say (from reading the site) it sounds analogous to an encrypted flash-drive to carry all your sensitive data around on. When you want it just mount the partition/flash-drive, enter password, and start working with the data inside. Not sure if it can make encrypted virtual partitions big enough for CD's or anything like that though.

I can only suggest that if you are using one password for all your sensitive files, then unless you have a compelling reason to keep them separate, it might be worth the effort to centralize them and use a system like TrueCrypt to manage them. Then you have great security that I doubt many people at your school would have any idea how to attack unless you left the virtual partition open or they have some serious computer security types and REALLY want to know what's in there. And if you label it something like "Banking and Tax Information" they will probably assume it is just that and never think to try to open it.

my 2 cents.

---

### Post by euler_fan on 2007-01-25
> **bruenig said:**
> Make root own it and give no permissions to others and use sudo. Seems that you could also put them a . directory and nobody will ever see them. Unless they are clever enough to ctrl + h.

Are you worried about someone having/cracking your password? If they do that and find the file then they have access to everything.

---

### Post by Prometheum on 2007-01-27
To clarify, I do want to password protect folders. I want to have an actual password on it that is not my root password, and I want it to be harder to access than hitting a key combo. Encryption is not a must, but if it is, it must be able to do directories.

Come on Ubuntu, this is easy as hell on windows, and not even using the NTFS encryption either. There has to be SOME way to do this on an open-souce OS.

---

### Post by matthewstory on 2007-01-27
not your root password eh?  Ok, make a user: secret:

adduser secret

Then make a folder in secret's home directory called .pornosidontwanttogetcaughtwith, or some other type of name . . . maybe .secretfiles:

su secret
mkdir ~/.pornosidontwanttogetcaughtwith

then put all your nasty files into that folder and . . . change the whole mode to 700 . . . 

su secret
chmod -R 700 ~./pornosidontwanttogetcaughtwith

Nobody aside from secret and root will even be able to cd to this directory or browse the contents . . . all you need to do to open it is to open with sudo:

sudo -u secret <cmd>

your root password will still give access to all this stuff, but it will always give access to anything, so if that gets hacked you're screwed anyway.  

Now i realize this doesn't meet your specifications . . . so here's another idea . . . set up a samba server or an NFS server and then make the same hidden directory somewhere with the chmod of 700 and the owner root, then only root can have it, and you can mount it into your home directory with sudo whenever your deviant little heart feels like reading/watching/looking at something that the man wouldn't want you to be looking at.

Again this might not meet your specifications, but i find it hard to do much of anything when you tie my hands to doing it "the way windows does it."  It's not windows, it's linux . . . do it the linux way.

---

### Post by matthewstory on 2007-01-27
also if you did it with a different user, you could just log in as that user whenever . . . just an idea.

---

### Post by dimeotane on 2007-02-11
One  option that is easy to use and cross compatible with different systems is password protected archives.  You can archive a folder containing your files, and set a password.  You can then copy (or backup) the archive as needed to any computer, even a windows OS and you can extract your files.   You want to use something that is secure, ideally AES encryption. 

On windows there's a number of file compression archive formats like .zip and .7z which supports AES encryption.     That's a pretty damn secure method of locking up files.
However, watch out what the file names in the archive are.. because even though  someone can't extract the files, they may be viewable. 

This is a method people often use to protect their files on a USB memory stick... just in case they lose it, and someone else looks through it. 


Most archive formats don't hide the names of files in the archive... so a filename like "my-favourite-prostitutes-list.txt"  might give away more info than you'd prefer. 
:lolflag: 

Which formats do AES?

In windows:
Winzip: will compress in AES
7-zip:  will use 256 AES.
WinRAR 3.x archives use AES encryption with 128-bit keys.


In ubuntu I find that .7z password protected folders can't be opened in file roller. :confused: 


Ubuntu will compress .zip with password protection and encryption.  The .zip package is v2.32 and is based on the infozip version.  I believe this is a weak 96 bit encryption... kindof insecure. 
see [http://packages.ubuntulinux.org/edgy/utils/zip](http://packages.ubuntulinux.org/edgy/utils/zip)


From what i can tell the rar 3.6 package (I installed with automatix) supports passwords and 128 bit secure passwords.   This currently is the best option for an easy to use file encryption standard which is cross compatible with different OS.

---

### Post by akshaysrinivasan on 2007-02-11
Well you could try ccrypt or bcrypt to encrypt and decrypt files ,but mind you they are on command line.Come to think of it,that is an extra security measure!

---

### Post by euler_fan on 2007-02-11
> **akshaysrinivasan said:**
> Well you could try ccrypt or bcrypt to encrypt and decrypt files ,but mind you they are on command line.Come to think of it,that is an extra security measure!

This is the way it is with TrueCrypt as well. There is doubtless some source forge or freshmeat project that will do AES or Triple-Blowfish with a nice gui.

Then again, it isn't all that hard to learn a command line system, and I agree that it is added security.

Thinking of that, you could make your machine log in to a linux command prompt. That would scare off most casual interloper without them trying to poke around.

All this is of course moot so long as you retain physical possession of your machine. If no one else has access to it, then there is no need for any additional security.

If someone gets a hold of it and has the time and computing power and expertise, then you are hosed no matter what.

EDIT: You could also just change all the names and burn it all to a CD, and pad the rest of the CD with mp3s or something. Then all you have to do pop the CD out of your machine in a pinch and snap it in half. Your average school admin is not going to question that the contents of the are gone for good (even though they most likely aren't).

---

### Post by likeatim on 2007-02-26
> **matthewstory said:**
> not your root password eh?  Ok, make a user: secret:
....
Again this might not meet your specifications, but i find it hard to do much of anything when you tie my hands to doing it "the way windows does it."  It's not windows, it's linux . . . do it the linux way.
just boot from a cd and you can see and open these files..
really bad if your laptop gets stolen.... (and I don't mean porn, I think of business email, passwords, etc.)

---

### Post by nosmada on 2007-02-27
Here is a post you might check out, I'm trying to do the same thing right now:
[http://ubuntuforums.org/showthread.php?t=336370&highlight=gui+encryption]("http://ubuntuforums.org/showthread.php?t=336370&highlight=gui+encryption")

---

### Post by cleverselfreferentialname on 2007-03-22
Unless you're relying entirely on the ignorance of the people in your school, you are going to need encryption. Password protection only works at the OS level, and won't help you if they boot from grub single user, boot another OS from a CD, or pop out the hard disk and view your files after installing windows ext3 driver.

With that said, it's probably safe to rely on their ignorance. Just install sysv-rc-conf, run 'sudo sysv-rc-conf' and remove gdm and/or kdm from the startup. Then, from now on, log in on a TTY and run 'sudo gdm' to log in again on the GUI. If you're worried about your laptop being confiscated, shut down.

Or - and this is the most feasible method - you could keep all the potentially incriminating stuff on a separate partition (with a filesystem other than ext3 so in the unlikely event that they try to read it from Windows). Use gparted to make the partition. Mount it when you're at home, and make sure there's no entry in fstab so it won't be mounted by default.

My ideal setup for a laptop:
*Passworded BIOS, with linuxbios if possible (probably not). All boot options other than the CF card disabled. Note that the BIOS password is easily retrieved or blanked if you have root in the OS.
*GRUB (and, my /boot partition) on a CF card, passworded. Password hashed with MD5. You might have to update your BIOS if booting from a CF card doesn't work (as with some Dell Dimensions)
*Full disk encryption via dm-crypt. Different key for each partition. One password, for the root partition. Other keys stored on the root partition, readable only by root. Maybe an unencrypted partition mounted noexec for music. No swap in case of a flash drive installation. Encrypted swap otherwise.
*Make apt remount system partitions when they need to be updated as writable. Otherwise they're left read-only.
*Once I have the money, set this up on a solid-state disk (flash memory) so that the entire disk can be quickly zeroed with 'shred.'

There's more, but I'm not remembering.

---

### Post by donad on 2007-06-05
I have found that truecrypt/forcefield is the most efficient way to hide files or whole directories.  You create an encrypted "partition" using forcefield the gui interface for truecrypt.  Then when you want to look at the hidden files you mount it via forcefield.  The encrypted files show up as just a plain file when not mounted.  No extension or anything.  

I have not actually created an encrypted file thus far, just mounted and added files withing the encrypted file.

You can get forcefield and truecrypt in one easy click if you use the automatix installer.

[www.getautomatix.com](www.getautomatix.com)

Hope this helps

Brian

---

### Post by jpkotta on 2007-06-06
EncFS is pretty cool.  It's really easy to use.

```
sudo aptitude install encfs
sudo chgrp fuse /dev/fuse
sudo adduser $USER fuse
```

You must log out and log back in if you needed to add yourself to the fuse group.

To make a new encrypted directory:
```
encfs ~/.crypt ~/crypt
```
and answer the questions as you see fit.  This is also how you mount existing encrypted directories.

To unmount, 
```
fusermount -u ~/crypt
```

In this example, the encrypted files are stored in ~/.crypt, and encfs mounts them on ~/crypt (or any other directory) when you supply the correct password.  Note that there is no need to use sudo, because we are using fuse.  There is also an auto-unmount feature, see the man page for details.  

Since encfs is mounting just like any other filesystem, everything is very transparent to other programs.  In my tests, encfs (using paranoid mode) is twice as fast as gpg (I think my gpg is using dsa-something), and only half as fast as normal (I tested by copying a 256 MB file of random data).

---

