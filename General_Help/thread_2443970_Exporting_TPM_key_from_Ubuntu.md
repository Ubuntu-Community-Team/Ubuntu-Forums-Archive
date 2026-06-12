---
title: "Exporting TPM key from Ubuntu?"
date: 2020-05-22
forum: General Help
---

### Post by RabbitWho on 2020-05-22
OK I doused my computer with coffee, didn't realize it, left it on for ages for the coffee to seep through it, came back, realized it, thought it was a splatter, wiped it, turned it back on, it didn't turn on but the fan did groan. "huh?" turned it on again.. nothing at all this time.. realized what had happened.. assumed computer was fried. Realized I couldn't get anything off the SSD due to bios password / encryption. Was devastated. Cleaned every internal part with IPA. Worked. Computer now works. Want to make sure this never happens again. CAn't get rid of drive lock without master password. 

SO

TL;DR In case I break my computer again, how do I export the TPM encryption key so that I will be able to unlock my SSD from another device provided i have its password.... or something? I don't think I am asking the right question because I can't find the answer anywhere. I didn't know what a TPM was until a few days ago.  


It's an intel ssd, hp elitebook laptop, Bionic. managing TPM from the OS is enabled

---

### Post by TheFu on 2020-05-22
There's this thing, perhaps you've heard about it, called a backup.  This is about the data, not the TPM.  

Daily, automatic, versioned, backups aren't optional.  They are mandatory, especially when you use encryption.
Encrypt the backups to, but using a non-hw specific method, like using LUKS encryption. If you want some HW involved, use a u2f key that supports challenge/response. These work with LUKS. Specific models of yubikey devices support this.  Buy 2.  Clone them with your setup, keep one with you and put the other one in your safety deposit box at your local bank or with your lawyer.

If you are interested in this, do a little research in these forums and ask questions.  You can start by doing data backups with versioning, daily, automatically.  Later you can add the encryption, unless you want to use cloudy storage. IF that is the way you want to go, encryption isn't optional.  Some backup tools will encrypt everything - duplicity can as an example.

---

### Post by DuckHook on 2020-05-22
I cannot up-vote TheFu's response enough.

@RabbitWho

Perhaps you are taking the wrong lesson from all this. So long as you are using encryption, focusing on "the keys" or "recovering from disaster" is the wrong approach. The point of encryption is to stop bad guys from accessing your data if your SSD physically falls into their hands. The unspoken assumption is that if that happens, your SDD is likewise gone for good. Therefore, with encryption, your standard operating assumption must be that your data can be rendered irretrievable at any time. Operating under such an assumption means that encryption and backups are so closely intertwined that they are two sides of one coin.

Where I diverge from TheFu's approach is as follows:

After careful consideration, I have reached the conclusion that the majority of my stuff is not that important. The security benefits from encryption is outweighed by the inconvenience of locking myself out. My solution is to set up only an encrypted directory in which all of my sensitive stuff, like private keys, e-mail, browser cache, sensitive documents, etc. are then symlinked back to where the system expects to find them. There's no point encrypting my music or my videos or my ebooks. They aren't private.

But everything is backed up. Twice. Using different technologies for independent redundancy. If I suffered a mishap such as yours, I wouldn't even bother trying to decrypt anything. I would simply replace the SSD and restore all of my data. I am never more than one day's work behind.

The benefit of backups is far greater than HW recovery. This same safeguard means that I am also well defended against ransomware, fire and flood, break & enters and other assorted disasters.

---

### Post by RabbitWho on 2020-05-23
yeah I guess you guys are right. But then I have to also make sure the back up is secure and I am back where I started? if I back up to the cloud, well, I'm a firm believer that nothing online is private. You are telling me the hardware lock is necessary to make this secure but also telling me it would somehow be secure online with regular encryption and no hardware lock? And if i backup to a hard drive it can die or be stolen and decrypted the same as if I just don't have the hard ware lock on the laptop. I never take the laptop anywhere by the way, it has never left my house, it will be right next to the LUKS encrypted back up you are suggesting, so why is that lower level of security not good enough? 

So is there no way to do what I'm asking?


(I do appreciate you guys taking the time to explain to me in detail what you genuinely feel is the best option for me)

edit: I tried set it up so that my important files will get backed up to google drive, i'm using gringotts to encrypt the private ones. I'd really rather not do it this way. I  hate having my data online, I don't do social media or anything.

---

### Post by TheFu on 2020-05-23
Nobody (or very few) do everything perfectly.  Life is about trade offs between risks and mitigation and complexity and cost.  I don't currently encrypt my backups.
I don't currently encrypt all the storage at home or work. 
I do encrypt all portable computing devices. Started doing that after a friend had two smartphones stolen when on travel in 2 days.  My phone, tablet, and all laptops are fully encrypted.  I do versioned backups for each.  Daily when at home, not at all when traveling.
I will probably never encrypt media files.

On my laptops, here's the storage layout:
```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk  
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot 
&#9500;&#9472;sda3                      8:3    0 464.6G  0 part  
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9500;&#9472;ubuntu--vg-swap_1   253:2    0   4.1G  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home 
&#9492;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi
```
This was started using the installer choosing "Whole Drive Encryption with LVM".  Then I resized the default LVs to make them smaller, so /home and /stuff and swap could be sized the way I prefer.  The efi and boot were created automatically for me during the install.  
There is no reason for "stuff" to be encrypted. Resizing the encrypted container to make a non-encrypted area can be done. I've done it on prior storage, but it was a highly manual process full of simple math that is easy to get wrong and no validation checks.  Perhaps the end of the encrypted area and beginning of the non-encrypted area overlapped? I never knew. Fortunately, I never found out before that laptop became unusable.
See the "sda3_crypt"?  That is an encrypted LUKS container for everything in the sda3 partition.  LUKS supports 8 decryption "slots", which means that 8 different methods to unlock the storage are possible.  I have 3 setup today.
[LIST=1]
[*]Really long passphrase - over 80 random characters. This is a fall back should the other methods fail.
[*]Yubikey Neo password+static output (2-halves; I put in a password that I know; The key enters a 30+ character static output when touched in a specific way)
[*]Yubikey 5c challenge/response (I type in the challenge, the key feeds a response into LUKS)
[/LIST]
Someone could get my Neo, get the static output from it, but they wouldn't know the first half that I enter.  LUKS doesn't see any difference between the 1st two methods.  The 3rd method has a specific setup required that took about 20 minutes to read, understand, and complete.  LUKS has to be unlocked before the OS can boot, so this is a pre-boot decryption thing, nearly like using the BIOS+TPM setup, but implemented in hardware agnostic ways.  I've pulled the SSD from one laptop and moved it to another. The LUKS protection is still there, using the same 3 options to open it.  Let's just say, I don't worry about someone being able to hack in. Nor do I worry that I will be locked out.

I only wish that online logins and password managers supported multiple 2FA methods (cell calls/SMS and cell apps don't count).  Really would like to use 2FA with my password manager, but as long as only 1 method is supported, I can't risk it.

---

### Post by DuckHook on 2020-05-23
Most general users I've dealt with make their backup strategies too all-encompassing. I'd like to lay out a more measured approach. It uses less resources, results in faster backups and, in the end, is actually easier to maintain. It isn't as secure as TheFu's methods, but not all of us need his level of security. The old-timers around here suspect that he's a spymaster who launches satellites out of a secret island in the South Pacific. Probably has a mini-me sidekick too.

[list]
[*]Create a list separating your data into three types:
[list=1]
[*]Completely unimportant data that is freely available. Examples: the OS itself, FOSS apps, local copies of music/movies already on the cloud, wallpaper collection, users manuals etc
[*]Non-sensitive personal data. Examples: personal photos, personal videos, most documents, ripped user owned music/movies, etc.
[*]Sensitive personal data. Examples: accounting databases, financial statements, résumés, bank statements, private photos/videos, medical records, e-mail, password databases, private keys, browser history/caches, work documents, 
[/list]
[*]The first type does not need to be backed up. The OS and FOSS apps can just be reinstalled with a bit of time and inconvenience. The rest can just be downloaded again. I never bother to back these up.
[*]The second type requires backup but no encryption. I don't care if someone sees a photo of my ugly mug ruining the background scenery. Nor do I care that they now have my music or movie collection.
[*]The third type requires both backup and encryption. But it's a relatively small dataset and easily manageable. Mine is small enough to fit on a cheap USB stick.
[/list]
I don't use 2FA yet, precisely because I'm concerned about the sort of lockout that you went through. My encryption is just LUKS using [Encrypted Private Directory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory"). Both my login passphrase and mount passphrase are 30+ character phrases that follow [secure high entropy principles]("https://lifehacker.com/using-common-phrases-makes-your-passphrase-password-use-5893510").
If someone is able to crack these, then I'm just out of luck. But I judge this level of encryption to be a good compromise between security and convenience.

The above three data types are just guidelines. Obviously, users are free to slot specific data into whichever type they choose.

[LIST=1]
[*]As already stated, type 1 data is not backed up.
[*]Type 2 data is backed up once a week in two sets. One set is kept in a fire safe. The other is taken off site when I visit my daughter and grand-critters. It's in the form of a 2.5 inch 5 TB external HDD. I rotate among 4 of these. That gives me a one-month rotation schedule.
[*]Type 3 data is backed up daily. Since they are small enough to fit on cheap USB sticks, I use a 7-day supply and physically rotate them. The weekly backup is part of the Type 2 dataset.
[/LIST]
That's it. No need for anything more complex. If people followed some variation of this, they would rarely need to visit the forums.

---

### Post by RabbitWho on 2020-05-23
TheFu thanks but this laptop is not portable. I don't port it. I am unable to port it. It doesn't get ported. No one will ever port it from now until the end of time when every quark in the universe is at least as far away from another quark as you are from me now. It's not portable. I just didn't have space in my flat for a desktop / monitor. I wish I understood what you were saying, it sounds magical. 



Ok I have put all my data online now to work around this problem. This makes it far far less secure and means anyone can read it, hopefully not the encrypted stuff, but probably!  [https://en.wikipedia.org/wiki/List_of_data_breaches ]("https://en.wikipedia.org/wiki/List_of_data_breaches")

DuckHook I love the USB key idea but I have ADHD, if the job doesn't get done automatically it won't get done. Plus, as I said, the USBs would spend their entire lives a few feet from this laptop, which never goes anywhere. So why can't this drive's encryption have the same lack of hardware specificity as they do? I think I'll save up and buy another internal SSD to replace this one and never put a boot password on it

---

### Post by TheFu on 2020-05-23
If it isn't locked in a safe, then that laptop is most definitely portable regardless of your specific use, perhaps.  Portable means someone else can snag it and walk out.  The same applies to USB storage. 30 seconds in your apartment and those are gone.  Probably not now, assuming you are locked at home like much of the world, but most people would leave their homes a few times a week or daily if it wasn't pandemic time.

If, as you say, it will never leave, then why bother with encryption at all? There's no point.  

Last time I was in Prague, our apartment had a "wandering maid" who would show up and check out stuff.  The Do Not Disturb sign didn't matter. I suspect a chain on the door from the inside wouldn't matter either.
Also, the phone system there was always toggled to auto-answer for some reason. I'd toggle it off after getting back daily which seemed to last overnight and to the next morning when we left, but when we returned, it would always - ALWAYS - be toggled to the "auto answer" mode.  That meant the phone wouldn't ring when called, it would auto answer on speaker phone so the other side could just listen.  Other visits had different security-related issues, but most have been quite nice.
That trip, I was travelling with just a tablet and took it with me daily. Must have been frustrating to only find clothing and snack and drinks for him/her.

There are some images here of what the different LUKS screen looks like pre-boot: [https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks](https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks)  It is clearly NOT the BIOS, but the OS handling the decryption.

I bet that disk could be disabled from using TPM, assuming that's actually being used. There's probably some software that toggles it, but there's no way to back encryption out without starting fresh - a completely wiped disk.   Regardless, before you attempt that, make certain you have everything you don't want to lose ... in a backup.

If you know the model, that could be researched.  The model isn't really hidden.  Linux knows what it is. Just ask using lshw or hdparm or smartctl.  All of those should have a switch to provide the vendor and model.

---

### Post by RabbitWho on 2020-05-24
When our house was burgled the laptops were in plain sight and they didn't take it, my partners is quite fancy looking imho, we asked the police about it and they said no one really tries to steal laptops or tablets anymore, they look for cash and jewellery. I just do not see the burglars sitting down with my SSD saying
"Oh no, it's encrypted" 
"No problem! We can crack it"
"No man, it's encrypted using TPM"
":O :O :O" 

My information might be specific to where I live, I can easily imagine if you live in a big city there is a criminal infrastructure where the burglar can sell drives to a higher level criminal in the know for a flat rate, who will then go through the data to try to find sensitive data.. but apparently that's not a thing in my town 


LUKS looks great, I know the data recovery place I contacted brag that they can recover anything encrypted with LUKS, but again the chance of a criminal here being bothered with that kind of knowledge... if he had that kind of knowledge he could make a fortune because they charge 500 euro per recovery, much easier money!

---

