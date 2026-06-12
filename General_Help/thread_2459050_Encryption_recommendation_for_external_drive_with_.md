---
title: "Encryption recommendation for external drive with data"
date: 2021-03-09
forum: General Help
---

### Post by jgwphd on 2021-03-09
I want to encrypt an old external hard drive with a lot of data on it. Is there a way, using my current OS, to do the external drive encryption without formatting over or erasing the existing data? ...or having to copy and move it back?  If so what is the best way recommendation. I am using Ubuntu 20.10. Thank-you

BTW, I looked at the prior posts on this topic but they are quite a few years back in a fast moving field. I am hoping better, much more user friendly, solutions are available today. Ideally, I'd like to plug any external USB drive or USB stick and then "click on something" that leads me down a path that simply results asking me for an encryption phrase/key (I can choose the strength of the key I need) and then results in an encrypted drive that at a minimum is portable/recognizable between Ubuntu systems. My needs are meager  :-)    ...I just want a protected drive/stick in case it gets lost.

---

### Post by TheFu on 2021-03-09
> I want to encrypt an old external hard drive with a lot of data on it. 
Backup the data.  Lay down the encrypted container, then move the data back.  There are other methods, but they all have flaws in the encryption so they have been deprecated.  OTOH, if you just want to keep cat videos save from a 10 yr old, then use ZIP files with encrypted passwords and call it "done."

encfs, encryptfs, and other similar solutions all have failures.  Achivers with encryption all have failures too.  But that may not matter to you.

The recommended storage encryption is performed at the partition or logical volume level using dm-crypt with LUKS.  You'll want the OS and swap to be encrypted as well, to prevent any accidental leaks of the encryption used.  And you'll probably want to use 2FA for unlocking the encrypted container(s). A challenge-response method would be best, not a static passphrase.

Which attack vectors are you trying to protect the data against?

---

### Post by jgwphd on 2021-03-09
Which attack vectors are you trying to protect the data against?    ---  just protection against a lost or stolen drive and a determined hacker trying to get access to read the data. Specifically what Ubuntu command or tool should I use? I have VeraCrypt installed but never used it. Is there something better? 

I am also interested in convenience. If it is too complicated then I'll be worrying if I did it correctly and the data is not safe when lost. You seem to indicate that I should encrypt the OS too. I am thinking that I need to reinstall Unbuntu with encryption and start from there. Wow, I thought the state of the art would be further along....

---

### Post by TheFu on 2021-03-09
> **jgwphd said:**
> Which attack vectors are you trying to protect the data against?    ---  just protection against a lost or stolen drive and a determined hacker trying to get access to read the data.

A determined **cracker** (cracker is a criminal) - let's use correct terms please - will spend months trying to gain access to encrypted storage. If you don't setup 2FA or massively long passphrases, they will get in, eventually.  In theory, a 13 character, random, passphrase should be sufficient to secure any storage, but humans are notoriously bad at random anything, so it is best not to try.  The old idea that choosing 3 random words and putting those together was good, until the crackers built tools to brute force those as well.  If you mix in Unicode characters and alternate languages, that could be good enough.  
[https://security.stackexchange.com/questions/169485/hash-list-for-practicing-password-cracking](https://security.stackexchange.com/questions/169485/hash-list-for-practicing-password-cracking) has links for more background.

We know that professional password cracking competitions generally crack about 80% of all the passwords within a few days thanks to humans being bad at "random".  The solution just needs to make it hard enough that they give up, right?  We want to be in the last 10% that they never crack AND we need to use the best, proven, encrypted storage solution possible on our hardware.

My systems don't have a TPM chip, so that limits some of the stuff that is possible to tie the data to a single system.
I know I'm bad at random, so I use 2FA with LUKS encryption.
I also know not to trust the hardware encryption that some HDDs have included in their firmware. I want software to perform the encryption and use some hardware for performance, but I don't want an all-in-one solution. Too each for that single organization to be ... er ... encouraged to break our trust, should we say.

---

### Post by jgwphd on 2021-03-10
One last question. Is there an Ubuntu app similar to (I think) bitlocker. A few weeks ago had to decrypt a windows hard drive on a new machine to make a partition for a dual boot with Ubuntu. It did everything in place, there was no moving or copying. I just did a few clicks and was able to make space on the hard drive for my Ubuntu install. Been living happily ever after. Is there anything that simple in Ubuntu?

---

### Post by TheFu on 2021-03-10
Nothing secure, unless you are protecting cat videos from 10 yr olds.

It comes down to the difference of having 1 corporate overlord vs 10,000 distinct projects.  
With an overlord, the file system and encryption are under the same dictator. 
With F/LOSS projects, the different parts work off APIs, so encryption isn't tied to any file system.  They are completely separate. It is a layered approach and part of the Unix Philosophy which is a key reason why every popular OS in the world today, except 1, is built on Unix.  Interchangeable parts are very nice. That's what Unix provides.
Plus, everyone knows they should have backups.  Right?

Linux doesn't have a "restore point" either.  Why not?
Ans: Everyone knows they should have backups.  Right?

By having replaceable parts, there are all sorts of kewl things we can accomplish that don't need to be blessed by the overlord.
You can ignore these links, but they are related to this idea:
* [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
* [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

---

### Post by mastablasta on 2021-03-11
> **jgwphd said:**
> One last question. Is there an Ubuntu app similar to (I think) bitlocker. A few weeks ago had to decrypt a windows hard drive on a new machine to make a partition for a dual boot with Ubuntu. It did everything in place, there was no moving or copying. I just did a few clicks and was able to make space on the hard drive for my Ubuntu install. Been living happily ever after. Is there anything that simple in Ubuntu?

LUKS (dm-crypt)

but you also have veracrypt or similar containers. 
veracrypt vs bitlocker: [https://lifehacker.com/windows-encryption-showdown-veracrypt-vs-bitlocker-1777855025](https://lifehacker.com/windows-encryption-showdown-veracrypt-vs-bitlocker-1777855025)

here is an overall list and comparison:
[https://en.wikipedia.org/wiki/Comparison_of_disk_encryption_software](https://en.wikipedia.org/wiki/Comparison_of_disk_encryption_software)

---

### Post by HermanAB on 2021-03-11
BTW, the regular Gnome disk utility does LUKS encryption.

---

### Post by jgwphd on 2021-03-11
Thanks for everyone's assistance in answering my questions. I took an old USB 2 TB hard drive and formatted it fresh with Ubuntu "Disks" (no data on it). I am using VeraCrypt and installing a 1800 GB NTFS container on it. The encryption of the container is still running. "Volume format" window started with 4 hours left ...and after 2 hours the drive is getting quite warm ...Yikes!!!!   Am I doing something wrong? I hope when I mount it to use it it won't take hours to recognize and become usable?

---

### Post by mastablasta on 2021-03-12
if you are using NTFS, then do it from windows.

if you are using the drive for linux then use opensource linux formats instead (e.g. ext4)

---

### Post by dinkidonk on 2021-03-12
I would strongly encourage you to NOT use a passWORD but instead use a passPHRASE! An example of a strong passphrase could be: "in the field there are 2 cows and a sheep". It is easier to remember and it is much harder to crack than something like: "s67bWkp?ns#g2" which you will need to write down somewhere in order to remember it.

---

### Post by TheFu on 2021-03-12
> **dinkidonk said:**
> I would strongly encourage you to NOT use a passWORD but instead use a passPHRASE! An example of a strong passphrase could be: "in the field there are 2 cows and a sheep". It is easier to remember and it is much harder to crack than something like: "s67bWkp?ns#g2" which you will need to write down somewhere in order to remember it.

I would say that using "s67bWkp?ns#g2" + {something you never write down} would be better.  Random characters are better, always, provided they are long enough.  For most people, there is nothing wrong with having a yellow sticky on their monitor at home with 10 random passphrases in the list, provided that is just the 1st half of the total passphrase (or the second half).

{from your mind} + {random 13+ characters}
or 
{random 13+ characters} + {from your mind}

Then you can take the random parts on a small paper in your wallet, keep it like you'd protect a credit card or $500 bill.

At work, things are different.  IT Security would freak out over a yellow sticky with random stuff on it. These days, someone with a cell phone could walk passed and snap a photo for attempted cracking later.

Phrases are great, provided they aren't in any books.  I know people who use ISBN numbers for passwords or music album numbers - and so do the crackers.  Those have all been added to their crack-list.  Remember, they will let their password cracker run for months trying to learn the passwords.  Humans are really bad at random.  Have the computer create the random half and make certain it is long enough.

---

### Post by jgwphd on 2021-03-12
As I mentioned before. I am new to encryption and learning a lot these past few days. I am initially trying to get the most usable, convenient and portable encryption I can find (security is second at this time because if it is too difficult to use then I won't use it). I am still evaluating things. I am finding that If I create a container I can't seem to find a quick way to see how much free space is left in the container unless I open it and then click on properties. Other attempts through nautilus (for example) will yield no/erroneous information. Are there short cuts anywhere that tells me encrypted storage sizes and free space?

---

### Post by The Cog on 2021-03-12
Not for an encrypted container. You have to look inside it to see how full it is.
Encfs does individual file encryption, so you can see how much disk space that uses, although it has other weaknesses so you may not want to use that.
Being able to see the file sizes does give something away about what kind of material may be encrypted.

---

### Post by TheFu on 2021-03-12
Forget the GUIs. They lie.

Be careful using "container" alone.  It has many different meanings, mostly nothing to do with storage or encryption.  The LUKS container doesn't have free space. The objects held inside do.

Remember, Linux is about layers.

HDD --> Partition --> Encryption Container --> LVM-PV --> LVM-VG --> LVM-LV ---> File system

The file system (say ext4), has free space for files and directories.  The file system doesn't need to use the entire LV, but usually it does.  The LV shouldn't use all the VG space - really, ever. That would be a terrible LVM design and deployment.  Multiple PVs can be merged/connected to 1 VG. This is an extremely powerful idea.  LVM may or may not be used with LUKS or any other encryption method.  LVM is just a layer, which is optional.

So ... if you want summaries of these things, this link has some command examples : 
   [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
I use a few aliases to make life easier:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -o name,size,type,fstype,mountpoint'
```

And for LVM summaries, use:
```
sudo lvs
sudo vgs
sudo pvs
```
This only works if the VG has been "activated", which should happen automatically on an LVM setup created by the installer. Manually created LVM stuff most likely doesn't get activated until you run **sudo vgchange -ay** AFTER the LUKS container has been successfully opened.

I get that this can seem overwhelming and complex. There are reasons for how this is. Brilliant reasons, but until you have more experience those reasons won't be clear.

---

### Post by DuckHook on 2021-03-12
Though I'm known in these parts to be very keen on security/encryption/privacy etc, I feel it may be useful to play devil's advocate here.

There's always a tradeoff between security and convenience. Always. Don't believe anyone who tells you otherwise. So, at what point does the security become overbearing? If you are trying to keep vacation photos safe from prying eyes, then LUKS+full disk encryption may be overkill. Just maybe. OTOH, if you must protect secret next gen missile plans from other state actors, then it's not remotely sufficient. Point is, there's a continuum. Matching the level of encryption to the significance of the data is an important principle. Otherwise, we run the danger of either overdoing or underdoing. The former makes computing an ordeal; the latter leads to danger, possibly disaster.

On these forums, we routinely run into new users who go whole hog on full disk encryption, suffer some otherwise minor mishap, forgot their encryption key, and turn a small matter into an insoluble one.

You don't tell us what sort of data you are concerned about and we don't need to know. But you need to do this assessment. As much as protecting ones data is important, the solution must be proportional to the sensitivity of the data.

---

### Post by dinkidonk on 2021-03-12
> **TheFu said:**
> I would say that using "s67bWkp?ns#g2" + {something you never write down} would be better.  Random characters are better, always, provided they are long enough.  I disagree. If one would try to access an encrypted volume, the usual approach would be to run through a list of well known passwords. If that does not give access, brute force may be one of the next steps. Brute force basically means to run first through all numeric/binary values from 8-bit and up until access is achieved and that leads to the fact that longer (and maybe easy to remember) phrases are more secure than shorter (hard to remember) ones are. "s67bWkp?ns#g2" = 256^13, "in the field there are 2 cows and a sheep" = 256^42 which is an enormous difference. If SHA256 is used for key generation, 32 bytes is the limit though.

@jgwphd: If portability is a requirement, use VeraCrypt since this is accessible from all systems (Linux, MAC & Windows). If you want full disk encryption for Linux systems only, you can use LUKS. For backwards compatibility use LUKS1, for better security use LUKS2. Use at least 256 bit hash for the master key.

EDIT: Don't use EncFS unless you absolutely have to.

---

### Post by jgwphd on 2021-03-12
Due to my portability needs I am focusing on VeraCrypt. 

But I find the following statement troubling from developers "There's always a tradeoff between security and convenience." Why?  ...Does it have to be this way?  ...have we "given up"?

Frankly, I want it all! Ideally I'd like to have security, sort of built in or added on Ubuntu in such a way that it is "very easy to use". And then install a dial that matches my desire for the level of security that meets my needs and let the system do the rest. **For example**, point at a drive, a partition, volume etc. and then click on "secure it" and then turn the dial presented for the level of security that meets my needs. Go have a beer and let the system do the rest  ...after all that's what computers are for????

---

### Post by TheFu on 2021-03-12
> **jgwphd said:**
> Due to my portability needs I am focusing on VeraCrypt. 

But I find the following statement troubling from developers "There's always a tradeoff between security and convenience." Why?  ...Does it have to be this way?  ...have we "given up"?

Frankly, I want it all! Ideally I'd like to have security, sort of built in or added on Ubuntu in such a way that it is "very easy to use". And then install a dial that matches my desire for the level of security that meets my needs and let the system do the rest. **For example**, point at a drive, a partition, volume etc. and then click on "secure it" and then turn the dial presented for the level of security that meets my needs. Go have a beer and let the system do the rest  ...after all that's what computers are for????

Why?  Because higher security is an extra thing added. Not having that means 1 less thing to worry about.
With encryption of storage, you must
[LIST]
[*]Have excellent backups. Disk recovery tools won't help.
[*]Performance will be impacted. Good encryption does require some extra processing, and that does slow things down, if only a little.  LUKS is about 3% slower than non-LUKS.  Other encrypted storage tools have higher processing requirements than LUKS.
[*]Key management is a hassle if you've never dealt with it before.
[*]It is another password to be remembered, entered, stored.  For a few releases, Ubuntu used the login password as the unlock-encryption-code for per-user HOME directory encryption. This was acceptable to many, but it broke my backups and at major release upgrade times, sometimes the upgrade would fail.  Remember, Linux is always multi-user, even if you are the only human using a computer.
[/LIST]

I know of only 1 situation where it is both more secure and more convenient. This is with ssh remote connections using ssh-keys. Hopping from system to system to system to system securely is relatively easy, once the keys have been exchanged.  That's just 2 commands  for the first system, then 1 command for every system after that.  Then you'll only be prompted to unlock your ssh-keys periodically. How often is tunable.  Never wouldn't be very secure.  Every 5 minutes would be too inconvenient.  I find somewhere between 4 and 12 hours the right mix for me, but many people would be happy with once an hour, I suppose.

ssh rocks completely. Most of my work uses ssh. Right now, I have at least 10 ssh remote sessions connected to other systems of all types in multiple locations.  People who use ssh with passwords are doing it the hard way and certainly less secure than a 2K RSA ssh-key or 400 byte ed25519 ssh-key.

Important take-a-ways: 
[LIST]
[*]When you use encryption for file storage, be 100% certain you have excellent backups.
[*]Security isn't just 1 thing.  Encryption isn't just 1 thing.  The user can encrypt everything, yet a bonehead choice will completely undo all that effort.  No software can fix an ignorant end-user. Every time developers try, dog makes a someone even more less informed.
[/LIST]

And let's not forget that MSFT has an implementation of encrypted storage, which will post your decryption key to their online servers if you use the online microsoft.com account they push.  That means THEY have access to the data even if you lose the decryption key.  That doesn't sound very secure to me.  If we aren't the only person in charge of and retaining the decryption key, that's a huge security failure in my book.

---

### Post by DuckHook on 2021-03-12
> **jgwphd said:**
> …I find the following statement troubling from developers "There's always a tradeoff between security and convenience." Why?  ...Does it have to be this way?  ...have we "given up"?

Frankly, I want it all! Ideally I'd like to have security, sort of built in or added on Ubuntu in such a way that it is "very easy to use". And then install a dial that matches my desire for the level of security that meets my needs and let the system do the rest. **For example**, point at a drive, a partition, volume etc. and then click on "secure it" and then turn the dial presented for the level of security that meets my needs. Go have a beer and let the system do the rest  ...after all that's what computers are for????
At the risk of offending you, this sounds like the sort of approach that gets Windows users into so much trouble. It's a tired truism by now, but *security is not an app (or a dial).* Rather, it is many things: a process, a frame of mind, a set of habits, a study of basic knowledge, a commitment to continuing learning, an ascetic and disciplined lifestyle if you will. Most are unwilling to learn or adopt the necessary self&#8209;discipline. Trying to substitute an app for these qualities is just wishful thinking.

Security will never be a fire&#8209;and&#8209;forget affair because, by its very nature, it cannot be. Using your dial metaphor: what would things look like at the low end of the dial? Does it enable the root account? Does it default to autologin? Does it install telnet? I would answer "No" to all of these. Someone else might answer "Yes". At the high end, does it enforce whole disk encryption? Does it disable all browsers? Does it default to a totally sealed firewall? Again, I would say "No" to any of them. Others might say "Yes".

We cannot address complex issues with simplistic approaches any more than we can solve complex problems with simplistic answers. Users who disagree tend to avoid Linux altogether precisely because it refuses to beguile with easy "solutions". They stick with Windows or Apple where dozens of companies have made billions by selling them the fantasy that an app will protect them from themselves. I'm not trying to be argumentative, but that's the reality.

---

### Post by jgwphd on 2021-03-12
I am thinking VeraCrypt is the way to go. I will just "totally" encrypt an external USB drive and use it as a place to put files that I want secured. That way I can unplug it and move to any other PC. I will attempt, with VeraCrypt, to do the encryption at the drive level (maybe partition), if possible (still learning). In other words if anything is on the drive then it is encrypted. I remember that ...according to a previous post that: HDD --> Partition --> Encryption Container --> LVM-PV --> LVM-VG --> LVM-LV ---> File system      .....so I'd like to have encryption done as close to the HDD as possible which I think will be the simplest and therefore the easiest to mange. For backup I'll have two encrypted drives!

---

### Post by jgwphd on 2021-03-12
@duckhook I am **not** offended and still learning and very much appreciate your insight. If I am doing something dumb tell me. And I haven't used windows in a decade at least! I understand that security, along with encryption, is massively complicated but I don't want to have extreme knowledge about it to use it effectively. My brain is getting full ...and other stuff will drop out  LoL!

---

### Post by TheFu on 2021-03-12
a) HDD --> Partition --> Encryption Container --> LVM-PV --> LVM-VG --> LVM-LV ---> File system
is the default when you have Ubuntu install the OS fully encrypted. 99% of the time, you don't see any of the LVM stuff. It is only at setup and when resizing an LV that it matters.

You can manually setup, 
b) HDD --> Partition --> Encryption Container ---> File system
or 
c) HDD --> Encryption Container ---> File system
But those are usually very poor choices from a management standpoint.
"c" breaks all sorts of best practices, but you can do it.  Don't blame anyone else if some Windows tool decides to wipe that disk or if in Linux you click the wrong button and wipe it yourself.

Not using partitions is a really bad idea almost always and it is always a bad idea for self-described "noobs". Sounds like you want "b", just with Veracrypt instead of LUKS.

If it isn't clear, we've been trying to lead you to the "correct answer" for the most secure situation, but with a few trade-offs that won't trap you in the future. Only you can decide what fits your needs and expertise level.

---

### Post by jgwphd on 2021-03-12
@TheFu ok, thanks. I'll rely on your experience and follow choice (b) as the way to go. **Unless** you strongly feel that I need to reinstall Ubuntu (21.04 will be out soon) as a totally encrypted system to stay out of future trouble (but for portability I'll still need VeraCrypt won't i?). Otherwise I'll proceed with the solution behind door (b) and do the normal upgrades to the next Ubuntu 21.04. Is seems (b) might simplest for me to manage using VeraCrypt? Your suggestions are very much appreciated!

---

### Post by DuckHook on 2021-03-12
> **jgwphd said:**
> @duckhook I am **not** offended and still learning and very much appreciate your insight. If I am doing something dumb tell me.
Thank goodness. I can come across as overly forceful sometimes, hence my opening caveat.

You are not doing anything remotely dumb. The concern you've shown already puts you in the top 1 or 2% of users when it comes to encrypting their data. Most do nothing at all. It also appears from this: > **jgwphd said:**
> …I'd like to have encryption done as close to the HDD as possible which I think will be the simplest and therefore the easiest to mange. For backup I'll have two encrypted drives!…that you have arrived at a solution with which you can work and are comfortable.

My response was purely with respect to the desire for a simple dial&#8209;like setting. We get a lot of that from new Windows visitors, so I felt that it would be useful for posterity to set the record straight. No worries. There are times I too find myself wishing for such a dial!

---

### Post by jgwphd on 2021-03-13
@DuckHook  I appreciate your passion AND EXPERTISE  ...from everyone! I gave up on windows a long time ago. But some of my friends still have windows and like me to help them occasionally, which always serves as a great reminder, to me, why I left windows long ago. Obviously windows security has sucked for decades and probably remains the premier example of what NOT to do. 

My solution is to use VeraCrypt and encrypt a few external hard drives and use them as secure portable storage "containers". I don't want to lock myself into a dead end path. I created a 2TB test volume (took 4 hours) and moved some interactive stuff on it and it operated just fine. If there was any encryption overhead, I couldn't tell (I have an Intel® Core&#8482; i7-9700 CPU @ 3.00GHz × 8 machine). I plugged (USB connection) the encrypted volume to several other machines (with VeraCrypt) and everything worked well. So my testing, so to speak,  confirmed what I am doing will work.

I just created a volume of 3.1TB on an external hard drive (USB 3.0) and it took 8 hours! I am now copying 2.1TB of files onto the secure volume that I created and Nautilus tells me it will take 16 hours to do the copy. Are these time durations to be expected or am I doing something wrong?  BTW, I am copying from one one spot on the 6TB drive to an excerpted 3.1TB volume on the "same" drive so I expect some contention on the USB - that may explain why 8 hours to create and 16 hours to copy. But still 8 hours seems excessive. any guidance here or is this to be expected?

---

### Post by TheFu on 2021-03-13
LUKS + LVM + ext4  would be much faster. 
With LUKS, the actual encryption can be delayed until those blocks are written, further speeding things up.
The mkfs on LVM is nearly instant too.

If you don't have Windows, why have any ntfs?  That makes no sense to me. Linux storage can be accesed over the network from anywhere in the world in a secure way.

I'm confused, as usual.

---

### Post by jgwphd on 2021-03-13
@TheFU Maybe I am confused so please explain. My first disk used NTFS with VeraCrypt and took 4 hours to "create" a 2TB volume. Which I tested with several machines to make sure I could move/copy/play a video from encrypted files among them. It worked fine. My second external drive was 6 TB and VeraCrypt took 8 hours to create the 3.1TB volume with ext4. So now I copying 2.1TB of files onto this newly created volume with an ext4 file system with VeraCrypt which nautlius says will take 16 hours. Also, I need some compatibility with windows to occasionally swap files.

---

### Post by TheFu on 2021-03-13
Copying using a gui will be slow.
The way storage is mounted can drastically impact performance.
Kernel drivers are always faster than others.
USB storage performance can vary wildly depending on the port used, cable, drive interface, available power. 2.5 inch will always be slower than 3.5in with external power.

---

### Post by jgwphd on 2021-03-13
"The way storage is mounted can drastically impact performance"  What does this mean? I have been just clicking "mount" for years and never noticed any issues.

---

### Post by TheFu on 2021-03-13
> **jgwphd said:**
> "The way storage is mounted can drastically impact performance"  What does this mean? I have been just clicking "mount" for years and never noticed any issues.

Well, if you are happy with that, great! Mounts can often use some performance parameters that aren't set by default. Almost always, using a GUI to access storage means having convenience over performance.  This is true for non-native Linux.

There are many threads in these forums about this issue.

But if you've never noticed poor performance, maybe it is best not to look. You are happy now, usually.

---

### Post by dinkidonk on 2021-03-14
> **jgwphd said:**
> "The way storage is mounted can drastically impact performance"  What does this mean? I have been just clicking "mount" for years and never noticed any issues.  For some file systems, file access time is enabled by default which means that each time a file is read from, the driver writes back to disk in order to update the files access time. By (manually) declaring the "noatime" mount option you disable this "feature" which causes less write back and increased read performance - especially for hard disk (by some referred to as "spinning rust"). This is just an example, there are other mount options which will optimize I/O performance as well. My guess is that you may loose up to half the I/O speed of a HDD if it is not mounted optimally.

---

### Post by jgwphd on 2021-03-14
@dinkidonk This is news to me??? I thought Ubuntu "optimally mounts" the  file systems automatically. Are you saying that when using encryption,  you need to mount the file system with different "manual" options. I am  using VeraCrypt and I just click "mount" and VeraCrypt does not offer  any mount options that I can see. I am interested in speeding things up,  at least the initial volume creation. Once up an running it seems ok.  In preferences there are mount option selections. What I have is below.  Do you have any suggestions? Thanks!
[ATTACH=CONFIG]288113[/ATTACH][ATTACH=CONFIG]288114[/ATTACH][ATTACH=CONFIG]288115[/ATTACH]

---

### Post by dinkidonk on 2021-03-14
Ubuntu uses the default mount options unless you tell Ubuntu to do something different. In the first picture, you have mount options for the file system at the bottom, entering "noatime" into that field should disable access time and increase read performance if the file system supports noatime.

EDIT: You can look at the [manpage for the mount command](https://man7.org/linux/man-pages/man8/mount.8.html) and check the "-o" switch and the options you can use with it.

---

### Post by jgwphd on 2021-03-14
@dinkidonk Is the "noatime" an appropriate mount option for SSD's?   ...or is this just for HDD's? Hopefully both so I can leave the option set in VeraCrypt preferences rather than remembering it every time I mount a USB device!  I truly appreciate the information that helps with encryption performance. Many Thanks

---

### Post by TheFu on 2021-03-14
atime is a minor thing. 50% less performance is an overstatement, imho.
NTFS without non-default options can be impacted 30%.

Google "gio performance" and
"gvfs performance"
if you actually want to learn more.

---

### Post by jgwphd on 2021-03-14
I am using "ext4" file system. What about SSDs? is there any possible encryption performance gain here using non-default options?

---

### Post by dinkidonk on 2021-03-14
> **TheFu said:**
> atime is a minor thing. 50% less performance is an overstatement, imho. NTFS without non-default options can be impacted 30%.  I had [this post once](https://ubuntuforums.org/showthread.php?t=2442923) and in that particular case default mount options had a performance impact of more than 50%. I did also try with noatime but that had much less impact than mounting as read-only.  > **jgwphd said:**
> I am using "ext4" file system. What about SSDs? is there any possible encryption performance gain here using non-default options?  There will most likely not be any notable performance gain but you will decrease wear due to unnecessary writes on the drive.

---

### Post by jgwphd on 2021-03-14
Many Thanks to everyone letting me tap into your knowledge and experience. Again THANKS!

---

### Post by TheFu on 2021-03-14
> **jgwphd said:**
> I am using "ext4" file system. What about SSDs? is there any possible encryption performance gain here using non-default options?

You seem to want easy answers where there are none.  The entire data chain from source to last write matters - both hardware and software - when it comes to performance.  Examine the entire software chain and the entire hardware chain. Test the performance removing 1 item at a time, see which impacts the performance for your workload.  How things are mounted matters.  Which file system is used matters. Physical interfaces used on the computer AND on the storage matter. We don't have your exact setup so our prior tests and guesses are just that - guesses.

You said there was NTFS on VeriCrypt.  That isn't what you care claiming now. I'm confused.  Each setup that is different will have ... er ... different results.  There could be impacts or not.  Generally, SSDs are so fast that only really bad setups will make a noticeable difference.  But people connect SSDs through all sorts of funky interfaces all the time expecting the "SSD-ness" to make up for crappy limitations elsewhere. Sometimes it can and sometimes it cannot.

Sorry, but there aren't any easy answers.

---

### Post by jgwphd on 2021-03-15
@TheFu I have been working with three external drives (testing things out). One HDD has NTFS the others ext4 with an HDD and an SSD. Sorry for any confusion. Yes I am looking for the easy answers and I'll take them whenever possible. I am new to using encryption but unless I ask, how do I know "easy answers" don't exist? I am trying to keep things simple for me and I do understand "bottleneck" analysis and performance is very complicated. I am "assuming" that NTFS is needed for any windows compatibility...(unless windows supports ext4, I haven't checked yet because I try not to use windows except to help friends and family). But my main focus is using ext4 on Ubuntu. I seem to be at a place where "using" VeraCrypt with ext4 meets my needs. I really do very much appreciate the opportunity to pick everyone's brain and get a deeper understanding about how to use encription :-)

---

### Post by TheFu on 2021-03-15
We are 41 posts in a single thread.  That says "this is complex" to me.

I wish you luck and success.

---

### Post by jgwphd on 2021-03-15
One more question. Can an encrypted container (volume or file) be placed inside another encrypted container (volume)? Recursively? Does this improve security for the "double/triple/etc encrypted" stuff, if it is possible?   ...the reason I am asking is that if I am moving stuff around not having to decrypt and re-encrypt would save some steps and time, "I think"  :-)

---

### Post by dinkidonk on 2021-03-16
Yes, you can "matryoshka doll" your encrypted containers, but that would make very little sense. Understanding the encryption parameters and how they impact the security of the encrypted data will be more secure than the sloth and hassle related to encrypting encrypted containers.

---

### Post by jgwphd on 2021-03-17
THANK-YOU to everyone for your assistance and patience in answering my questions.

---

### Post by Skaperen on 2021-03-17
> **jgwphd said:**
> I have been just clicking "mount" for years and never noticed any issues.

if you've only been doing things one way, you have no way to see how that is different than some other way.

---

### Post by Skaperen on 2021-03-17
> **TheFu said:**
> Well, if you are happy with that, great! Mounts can often use some performance parameters that aren't set by default. Almost always, using a GUI to access storage means having convenience over performance.  This is true for non-native Linux.

There are many threads in these forums about this issue.

But if you've never noticed poor performance, maybe it is best not to look. You are happy now, usually.

i think the conclusion of what he said is that whether it is the worst or best performance, it is tolerable.

---

