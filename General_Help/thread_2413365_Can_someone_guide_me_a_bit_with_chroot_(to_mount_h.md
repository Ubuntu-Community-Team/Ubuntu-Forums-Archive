---
title: "Can someone guide me a bit with chroot (to mount home from liveusb)?"
date: 2019-02-24
forum: General Help
---

### Post by usernamoi on 2019-02-24
I need to mount my home partition, which is encrypted, and i also need help figuring out why and how one kernel became duplicated, and how that stops me from reaching login screen.

Also, any information about how to backup configuration files (from things like docky, icon themes and so on, and also how to recover the list of ppa).

Any information to solve this will be very appreciated, thanks.

---

### Post by TheFu on 2019-02-25
Best to ask 1 question per thread, especially when they are unrelated.

User settings are stored per user inside their HOME, but you should probably backup everything except cache files under ~/.

PPAs are stored under /etc/apt/ ... but you should probably backup everything in /etc/. It is tiny.

I'm not up on chroot recently, and the question is vague, so I won't try to help.

No clue about encrypted home - the question isn't perfectly clear. It is really the entire partition that is encrypted?  Which encryption is used?  Or is it just the individual HOME directory that was possible to encrypt and decrypt at login?  These are completely different, each with different complications.

---

### Post by usernamoi on 2019-02-28
> **TheFu said:**
> 
I'm not up on chroot recently, and the question is vague, so I won't try to help.


How can i improve the question, so you could try? 
Is there another way to mount my encryted home partition to then backup files, and try to repair the problem?

> **TheFu said:**
> 
No clue about encrypted home - the question isn't perfectly clear. It is really the entire partition that is encrypted? 


Home partition is encrypted; when ubuntu is going to be installed, it asks if you want to encrypt home folder. i encrypted it, but im unsure i saved a backup of the passphrase; anyway, ive read that shouldnt matter as long as files in home and root arent corrupted, and it should be perfectly save to mount it using user and login password (which is something i dont know how to do, but from what ive read one way is using chroot)

If you need more details, i made another post, but no one has answered and i really need to learn and hopefully have someone guide me to fix the problem.

[https://ubuntuforums.org/showthread.php?t=2413287](https://ubuntuforums.org/showthread.php?t=2413287)

---

### Post by TheFu on 2019-02-28
I've never heard of checking the "encrypt home" during installation doing anything more than using encrytfs. It doesn't encrypt the entire partition.

BTW, this install option was removed for a number of reasons in 18.04 and later.

chroot doesn't have anything to do with accessing encrypted anything as far as I know and certainly wouldn't be needed for HOME access.

HOME <--- that is per-userid. It is an environment variable set at login using the data in the password entry (local or LDAP provided).
/home <--- that is a partition that is normally shared by all end-users on the systems, but in a corporate env, that may not be true.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) has links to other helpful articles on this topic.
There is a section, _Recovering Your Data Automatically_, which seems the most likely for your needs.

I used the encrypted HOME for a few weeks about 5 yrs ago, but found it didn't meet my security or backup requirements.  I switched to LUKS/dm-crypt encryption and never looked back. I still use this with LVM and LVs.

---

### Post by usernamoi on 2019-02-28
In relation to what you know,  what i have to do to remove all trace from a kernel, find how or where  it became cloned (or why it appears to be cloned), and then install it  properly from a liveusb? thats kind of what im trying to do, after im  able to backup as many files as possible. Or what i can try to help producing a diagnostic with the necessary information to figure out how the problem happened.

> **TheFu said:**
> 
I've never heard of checking the "encrypt home" during installation doing anything more than using encrytfs. It doesn't encrypt the entire partition.


yes, I mean this:
[IMG]https://www.howtogeek.com/wp-content/uploads/2012/06/image138.png[/IMG]

> **TheFu said:**
> 
BTW, this install option was removed for a number of reasons in 18.04 and later.


I dindt knew about that, since i have been using 16.04, and plan to keep using it until i learn how to properly make appimages from some outdated programs to try to run them in more recent systems. i use many appimages, but i placed them in home folder, so i must decrypt it to recover them since i can remember all of them, because some are tools i use very little, but like to have at hand. I think i will organize files a bit differently to avoid this issue, and make things easier to reset from similar problems. 

> **TheFu said:**
> 
chroot doesn't have anything to do with accessing encrypted anything as far as I know and certainly wouldn't be needed for HOME access.


Im using this article as reference, among others.
[https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

> **TheFu said:**
> 
HOME <--- that is per-userid. It is an environment variable set at login using the data in the password entry (local or LDAP provided).
/home <--- that is a partition that is normally shared by all end-users on the systems, but in a corporate env, that may not be true.


i do mean home partition. if i open the partition where /home and /root are, i obviously have "permission denied" since im using a liveusb, with a different user; i dont want to change permissions because i know that can create a mess, unless you are planning on deleting everything and re-install the os, which is something im not currently interested before trying to fix the actual problem.

Ive been using on and off ubuntu for at least 7 or so years, but i havent invest time in properly learning linux, so i know bits from reading articles and tutorials, even if i still need to find and read a few books to understand things better, and maybe be more clear i how i express myself at least when im seeking help. so, im thankful you are answering me even if i may not be as precise as i should.

Could you tell me what things i should consider in relation to this article if i want to remove a kernel (header, and related files)? i know its outdated, and probably im mixing things up, but if this is related to "**ecryptfs-recover-private**" then, can i still use it or should i avoid this article?

[https://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](https://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

Thanks again for your answers. I think every bit helps.

---

