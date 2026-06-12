---
title: "Restricting a user's harddisk usage"
date: 2018-07-22
forum: General Help
---

### Post by bjngchn on 2018-07-22
Let's say..: I plan to install new k/ubuntu  on a computer. There will be more than one users.  I want to limit maximum harddisk space  amount a user can use, for some users.  Is there a way to do this?  Why: There can be multiple reasons. One may want to erase all data  associated to a user (such as gambling activity) and  emptying trash won't help. Old data need to be overwritten, and filling the disc with something (such as junk data) to overwrite that data  would be  time consuming and make the  computer age fast.    Any solution?  If any, does this need to be done during installation?

---

### Post by TheFu on 2018-07-22
quotas.
[https://www.howtoforge.com/tutorial/linux-quota-ubuntu-debian/](https://www.howtoforge.com/tutorial/linux-quota-ubuntu-debian/)

Or just setup a different LV for each userid and dynamically create and remove them as needed.  You can overwrite the LV with random data as you like - /dev/urandom

That won't prevent a smart user from creating a symlink into /tmp/ to get access to more temporary storage.

---

### Post by bjngchn on 2018-08-04
Thanks. The first option is too long. The second option I don't tunderstand yet. But both may be worth working on.  New question: Can both of these be done  after installation?   I remember when installing I was being shown options related to LVM.  Do I need to make a specific choice during installation,   to mak e either of this  work?    Also, what happens  to such rules if I remove a user?   Would that user's space beome available to the rest automatically (if they don't have  such  space restrictions)?

---

### Post by TheFu on 2018-08-04
I've never used disk quotas.  We expect our people to behave like adults and not fill up storage.  I would expect quotas to be added at any point and work.  Try it out. See if it does what you need.  I'd do that testing inside a VM.  Same for LVM and LVs.

LVM is easier when done at install time since installing the OS onto storage with LVM brings great flexibility and many added capabilities. If you create new userids, then you can force their HOME directories to be anywhere you like, say on a new LV that is created on-the-fly on compatible storage.  All Linux systems allow adding custom userid creation scripts.  Based on your questions, using LVM with a separate, limited LV for each user would be too hard for your current skill level.

When you remove a user, you need to clean up after them, doing whatever is required.  You are the admin. Don't assume anything is automatic.  Userid cleanup scripts can also be customized.

And the answer to the last question is "it depends."   User storage is limited by where their permissions allow write access and the amount of storage on that partition/LV.  Any userid can fill any partition where they have write permissions, unless quotas prevent it.  Which is why I suggested have a separate, dedicated, LV for each userid.  That way, you'd limit how much storage they could possibly fill and creating LVs, using them, and later removal, is nearly instant.

Setup a view virtual machines and try each method out.  If you want to add even more security, you could use some sort of file system level encryption for each LV created.  I'm not certain how to tie this back to a login, but if each LV had a different crypto key for access, removal of that key would make the storage inaccessible and the data on it would appear as random data to anyone looking when it wasn't unlocked.

I think you should use quotas.

---

### Post by bjngchn on 2018-08-04
Thanks again. My skill level is: no skill.  Then I shouldn't choose LVM option when installing, correct?  Beause it would be difficult to manage.  Also isn't the encryption provided during installation good enough to protect files, when  computer is turned off (assuming pw is strong?  )    .... My purpose is not only to protect files, but also limit any kind of damage  made on  computer.  In other words, to have as much control as possible.

---

### Post by TheFu on 2018-08-04
Using LVM at install time isn't the same as setting up a separate LVM for a transient userid on-demand.  Vastly different. A checkbox during install is easy and allows you have flexibility 6 months later, should you need it.  You may never need it and for most things, it doesn't matter.
[B]
You should stick with quotas until your skills advance significantly.  [/B]

If you want to protect files, make versioned backups.  Nothing replaces backups. Nothing.  If you use encryption and anything bad happens, your data is gone without backups.  You cannot hope to do a deep surface scan and recover any data on a properly encrypted disk. But encryption alone doesn't make a system secure.   On properly designed encryption solutions, the strength of the password really only unlocks the access key for the real keys used to encrypt data. The data on the disk should be highly secure regardless, but a weak passphrase **is** a huge problem.  For encrypted storage, I use over 30 random characters as my key.  Most of those come from a hardware token. Some come from my brain - effectively 2FA.

There are 3 different types of encryption solutions commonly deployed on Linux systems.   Each has attack vectors. None are 100% secure on their own, though FDE using dm-crypt+LUKS is significantly better than the other two options.. There are mitigation strategies for each, with different level of effectiveness.  But this is a different rabbit hole.

Your current skills don't let you have as much control as possible. Sorry. That is your current limitation, IMHO.

---

### Post by bjngchn on 2018-08-04
Great answers.  Can there be  backdoors against  encryption used  on ubuntu installations?  I  mean if there is no keystroke reader to steal pw, and pw is not weak.   Let's say I know the encryption key, and take out the harddisk, and connect it to another computer via a harddisk reader. Then can I access the data using that pw?  Whether I can do it, and whether an expert can do it, are different questions.

---

### Post by TheFu on 2018-08-04
> **bjngchn said:**
> Great answers.  Can there be  backdoors against  encryption used  on ubuntu installations?  I  mean if there is no keystroke reader to steal pw, and pw is not weak.   Let's say I know the encryption key, and take out the harddisk, and connect it to another computer via a harddisk reader. Then can I access the data using that pw?  Whether I can do it, and whether an expert can do it, are different questions.

I know of no known backdoors for dm-crypt/LUKS in a FDE environment.  But the boot process CAN be hijacked by the "evil maid" attack, which would provide access later to an attacker. The mitigation for this is to always boot from storage that you never allow out of your sight.

Encryption doesn't stop network attacks or rubber hose attacks.

I cannot answer the last question. It isn't hard, but it is non-trivial, especially if LVM is used. LVM adds an extra layer and 3-4 more commands to access any data.

Seems you have your answers.  Good luck.

---

