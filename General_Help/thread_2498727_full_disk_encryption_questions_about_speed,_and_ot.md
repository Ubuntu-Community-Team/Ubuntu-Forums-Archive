---
title: "full disk encryption: questions about speed, and other issues"
date: 2024-06-25
forum: General Help
---

### Post by Old Jimma on 2024-06-25
Hello Ubuntuers:

First: Thanks for all of your help over alll of these years!

My questions pertain to full disc encryption. Here they are:

**How fast is decryption?**
My computers all of 1TB NVMEs that are used for the opperating system and home directory. I typically use arround 600Gb of stuff stored in my home directory. My understanding is that on system start-up the home directory will by descripted. I wondered if that would take a long time or is quite fast even if there is alot of data on it. How fast is decription?

**Multiple SSDs within 1 computer question**
I believe that it may not be possible to configure anything other than a main hard drive for the opperating system and home directory when Ubuntu is installed. What about other SSDs and NVMEs that are mounted at system start up from the /etc/fstab file? Can these be encrypted, also? Are there drawbacks?


Thank you!
Old

---

### Post by currentshaft on 2024-06-25
Full volume encryption doesn't require decrypting individual files like file-based encryption does. In terms of performance, you are unlikely to see any impacts in daily, non-specialized use, even on an older system with LUKS.

It is indeed a good idea to encrypt additional drives with LUKS, especially if they have sensitive data on them. You can use the cryptsetup command to do so. The only drawback I can think of is losing your passphrase and being unable to recover files.

---

### Post by TheFu on 2024-06-25
For CPUs with AES-Ni instructions, I think the normal expected performance hit is about 3%.  Doubtful you'd notice.

Using encrypted HOME directories on a per-userid basis has been deprecated for a long time - over 6 yrs - pre-18.04.  There are issues that you can look up.  Stick with LUKS and the defaults for LUKS.  That's a per-partition encryption method.  It isn't hard to setup manually, but it is easiest to use when selected at installation time.

I consider having LUKS encryption on my laptops the minimal amount of extra security needed.  Additionally, I use a hardware key for decryption along with a 10+ character passphrase which gets merged with the hardware key output for a sufficiently long decryption passphrase that I don't actually know.  The HW key uses a challenge/response method.

For safety, I use multiple LUKS key slots, so that other HW keys can be used to unlock the storage. Additionally, having excellent backups isn't optional when we use whole disk encryption.  It is mandatory, since a small hardware issue in a critical block where the encryption header is stored can block all access to anything on the entire HDD.  Have your backups down first.

---

### Post by Old Jimma on 2024-06-26
Hello currentshaft and TheFamousFu:

Thank you for your replies. Sorry for my delay in reading them: I have just awoken from a longer-than-normal senior "moment." I'm back on it now!

I have one more question:

I was advised by "Forum People" to back up my files on each of my computers to a "backup server" that doesn't do much else than rsync over ssh to grab and store the files on my laptop and other computers. 

My question here is: will that "backup server" be able to backup files on my laptop and other computers if I go to full encrypiton on my laptop and other computers?

Thank you!
Too Old for my Own Good, 
Old

---

### Post by TheFu on 2024-06-26
If you use whole drive encryption, like LUKS, then yes.  When the encrypted volumes are "OPEN/mounted", they are no different than any other storage.  Encryption only works when the data is at rest - the machine is powered off, not standby, not hibernated.

Also, rsync isn't a good backup tool.  For almost no added complexity, you can use rdiff-backup to "pull" the backups and have faster, efficient, backup versions built-in.  I've posted hundreds of times in these forums about rdiff-backup, including some simple commands/scripts.

---

### Post by Old Jimma on 2024-06-26
Thanks for your august reply. I respect it!

I plan to upgrade to 24.04 as soon for all of my machines. I had hoped to do an upgrade, but I can see that a fresh install  using LUKS is the way to go now.

Yes. rdiff-backup is superior in every way to rsync. Would you please reply, provinding a URL of one of your tutorials on rdiff-backup for a server?

Thanks again,
Old

---

### Post by Old Jimma on 2024-06-26
Thanks for your august reply. I respect it!

I plan to upgrade to 24.04 as soon for all of my machines. I had hoped to do an upgrade, but I can see that a fresh install  using LUKS is the way to go now.

I found your web page on rdiff-backup: 

Thanks again,
Old[HTML]https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html[/HTML]

---

### Post by Old Jimma on 2024-07-04
Hello TheFu:

I disliked 24.04.... many crash reports.... got tired of sending info to canonical. So, I' reverted to an encrypted 22.04 set up for my laption with no additional internal drives other than the one with th 22.04 and my home directory. Seems like a prefect soluiton for a computer that will do some traveling.

While I found a way to encrypt addiitonal internal drives, and back up to them, there are obvious problems with that and there were problems: Once one gets this done, each internal encrypted drive has 2 representations... hard to describe it... but learned that when I restore data to the wrong representation, I wrote over the opperating system. Further, since I have a really nice backup system from on another 22.04 computer (set up as you recommended), why bother with extra internal drives for backup when I've got a great one on another computer on my network?

I'm ready to take the next step that you've suggested: backing my computer up to my "backup computer" using rdiff-backup instead of rsync.

I wonrdered if it is anymore complicated than 

[QUOTE][**/rdiff-backup     from_origin_computer     to_destination_computer::path_to_backup_locaton**QUOTE]

Pretty sure it is, as I saw... but lost... your web page that pointed to further complexity.

TheFu, how do I start learning your way of getting this done?

Do you attend ALE?

Thanks,
Old

---

### Post by dragonfly41 on 2024-07-04
> [COLOR=#000000] .... for a computer that will do some traveling.[/COLOR][COLOR=#000000]
Are you encrypting because of your travelling?
How much of your encrypted drive(s) do you use/need when travelling?
There is another scenario. Save encrypted data in a zerocloud framework such as tresorit.com (Swiss based) to be accessed in your travels. Or look at ProtonVault (I have only just started using Proton .. again Swiss based).
[/COLOR]

---

### Post by TheFu on 2024-07-04
> how do I start learning your way of getting this done?

My methods are much more complex than most people want.  I have LVM and use LVM snapshots. I "pull" backups to the server. The client systems don't have any access at all to the backup server or the storage used for backups.

But the link you already found should be sufficient to do either local or "push" backups.  There are parts of scripts to show each stage in that link.  I figure if someone can't read and understand what those pages say, then they probably won't be able to actually restore the backups later, so some other, much more wasteful (disk and time) method will be necessary for them. 

> I wonrdered if it is anymore complicated than 
yes.   Please don't ask any questions until you've gone through the link and tried your hardest to make it work.   Asking questions before you've created your own script is a waste of your time AND mine.  There aren't any "simple" answers outside the total answer.  Each of the parts are important.  Picking a single line with a command on it will not work. 

As for encryption ... there are lots of good reasons to encrypt storage that doesn't move at all.  I would caution anyone against using any encryption methods that don't work at the partition level with file systems inside (basically LUKS).  The others have a number of security issues ... and it appears that Old Jimma may have choose one of those less good encryption options.  There are times when "easy" is also BAD.

---

### Post by Old Jimma on 2024-07-04
Hi TheFu:

I got 2 replies from you, an asked questions, so I'll answer both.

Everybody in my family uses protonmail, and we use proton drive to store and share secure stuff. The Swiss are one of the 2 countries that refused to sign the treaty that enables other coutries to share confidential information collected through the many ways they collect and sell info now. That, along with the revision of the US telecommunication act after 9/11 is the reason why we don't have privacy or an ammendment to the Constituion about privacy that works like it used to.

Switzerland is good with privacy, but ya gotta keep an eye on them when it comes to hagglings.  I worked there for my agency for several years towad the end of my career. I liked it alot. However, there is a reason why the Swiss love privacy and it started with that guy who buried alot of "borrowed" stuff in huge vaults under what is now the Bahnhofstrasse. Ying/yang.

I'm concerned with privacy.... was involved in the 2015 data breech. Im am sufficiently geezer lost memory that I know that swapping stuff back and forth between proton drive and my computer would result in lost data. So, i'm happy with an encrypted laptop. Its actually a pretty simple soluiton. Hope it works.

I guess, I'll get buy with my current backup to using rsync and not go to rdiff-backup, except for a few simple things. rsync works well enough, and besides I've got alot of old and new hard drives, SSDs, and NVMEs laying arround, and can put them to use in my current backup set up. Thanks for pointing me in the direction of having a pi that does backups. It works fine, an dI really don't want to bug you. Simply wanted to follow up on another of your suggestions.

Have a great day, and expect the Braves to have a surge toward the end of he season and challenge the Phillies.... or maby not. They are 8 games behind.

Thanks for all of your suggestions, already!

Best,
Old

---

