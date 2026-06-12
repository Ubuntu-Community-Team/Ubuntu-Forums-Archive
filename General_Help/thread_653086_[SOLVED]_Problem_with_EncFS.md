---
title: "[SOLVED] Problem with EncFS"
date: 2007-12-29
forum: General Help
---

### Post by Simplicius on 2007-12-29
I have been using EncFS for a while and it always worked fine. Now I get an error and I can't access my files anymore :(

> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
fuse failed.

I searched a little and then tried

$ fusermount -u ~/visible

but I get 

> fusermount: entry for /home/io/visible not found in /etc/mtab

Any suggestions?

---

### Post by Simplicius on 2007-12-30
bump?

---

### Post by Simplicius on 2007-12-31
Last attempt: bump

Does anyone understand what the error I get means?

---

### Post by vermoos on 2008-01-06
This is what I did to get encfs working properly (ubuntu 7.10)

sudo apt-get install encfs
sudo adduser mic fuse
groups			<-- note that fuse will not be in the list of groups until restart, and fusermount will not be in /usr/bin
*NOW restart*
groups			<-- fuse should now be in the list of groups, and 'which fusermount' should --> /usr/bin/fusermount
sudo chmod u+s /usr/bin/fusermount 		 

(now do the following while in your home directory)
mkdir /home/mic/secret
mkdir /home/mic/decrypted
encfs ~/secret ~/decrypted
	<Enter or press p and enter for paranoia mode>
	<enter password> 
[use the decrypted directory as usual by placing a file in it]
fusermount -u /home/mic/decrypted		<-- make sure to unmount the decrypted directory, and make sure it's contents disappear when you press reload in nautilus

Get the files back:
	encfs ~/secret ~/decrypted		
	... etc
       remember to unmount... 

encfs should work if you follow the above. 

The only problem I have had is that I can't delete the .Trash folder from decrypted. I get a permission denied message, even if I use sudo.  Also I can't identify which folder is the .Trash one in secret because its all written in gibberish.

p.s. how do I post a post on ubuntuforums? So far I have only been able to reply to posts. <-- quite important!

thanks in advance.

---

