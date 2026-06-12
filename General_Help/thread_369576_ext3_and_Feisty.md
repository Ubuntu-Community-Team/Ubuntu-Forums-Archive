---
title: "ext3 and Feisty"
date: 2007-02-24
forum: General Help
---

### Post by yme on 2007-02-24
Hello:

I understand the Feisty Fawn, which will be released in April, is going to include Secure Delete. This obviously means that it will not use ext3 as a filesystem but what filesystem will it use?

I'm a relative newbie and all the Linux distros I have tried in the last year have used ext3. Personally I'm rather distrustful of a filesystem that the user cannot fully control.

Can anyone briefly explain why journaling filesystems like ext3 are seen as advance over what went before? Inituitively I would have thought that the journaling was a rather memory hogging procedure ...

me!

---

### Post by llamakc on 2007-02-24
Secure Delete will be included in the Universe repository and not installed by default.

[http://packages.ubuntu.com/feisty/utils/secure-delete](http://packages.ubuntu.com/feisty/utils/secure-delete)

[http://en.wikipedia.org/wiki/File_wiping#File_wiping_on_journaling_file_systems](http://en.wikipedia.org/wiki/File_wiping#File_wiping_on_journaling_file_systems)

---

### Post by yme on 2007-02-24
Hello again lllamak,

The wikipedia entry is very interesting. It is quite brief but it seems that ext3 is designed with data recovery in case of a cock-up in mind rather than secure deletion. I guess it is a playoff and depends on personal preference.

What I really can't get my head around is the statement: 'To increase performance, these file systems will often arrange I/O commands in an efficient manner and may continuously move data around the disk to prevent the need for operations similar to Windows Disk Defragmenter'. I know how slow a Windoze Defragment goes and all this continuous moving of files sounds like a real drag on the system to me. 

What is really interesting though is the statement: 'On ext3, set the journal mode to ordered data mode (the default for newer versions). In ordered mode, ext3 only journals metadata, not actual data. To find out if you are using ordered data mode, type 'dmesg | grep ordered' (on a Debian GNU/Linux system) and look for a message saying that the partition has been mounted ordered data mode'.

I tried with my newly installed Dapper Drake and got:
EXT3-fs: mounted filesystem with ordered data mode.

Does this mean that I can install SecureDelete and it will work (apart from the logs etc)?

And what about the filesystem on Feisty? ext3 with ordered data or something else?

Also,

---

### Post by llamakc on 2007-02-24
I'm sorry but I do not know the answer to your questions. As I know understand things to be, and I had data I was desirous of ensuring deletion, I would have a scratch ext2 partition where I kept data that I had concerns over.

If it were me, I'd join the mailing list for Secure Delete and see what conversations have already occurred concerning this.

Now that you've piqued my interest, I am going to install secure-delete on my Feisty test VM and see what happens.

---

### Post by yme on 2007-03-07
> **llamakc said:**
> I'm sorry but I do not know the answer to your questions. As I know understand things to be, and I had data I was desirous of ensuring deletion, I would have a scratch ext2 partition where I kept data that I had concerns over.

I think this is an issue that should concern all users. I can see that there is a trade off between recoverability and security in what filesystem Ubuntu uses. 

Some may call me paranoid but I think like most people I get more pishing scam emails a month than I could count. If only one in a thousand of those scammers has hacking skills it still makes the net a very insecure place. 

Most people worry about burglars and muggers but identity fraud is far bigger than both of those put together. So would say to the developers of Ubuntu put security first when choosing the default filesystem (certainly nobody has given me any reason for thinking ext3 has any great advantages over ext2 on any other score). 

me!

---

