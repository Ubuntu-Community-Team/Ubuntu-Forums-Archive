---
title: "Oh no! &quot;structure needs cleaning&quot; drive error - please help"
date: 2017-04-28
forum: General Help
---

### Post by in2deep2 on 2017-04-28
Hi everyone.

New-ish ubuntu user here. Fairly tech savvy, just inexperienced. I think I've made a major, major error and I need some help or I worry I may lose ALL my data.

I'm running a dual boot with win10, and Ubuntu 16.04 entirely inside a luks encrypted LVM, which I usually back up by dd'in the whole luks partition to an external drive. Yesterday, I installed Ubuntu GNOME, just to give it a try. Use cryptsetup to open the luks container from liveUSB,  format the old unity logical volume and install gnome.  Worked fine, booted no worries with same old encryption key.


I then made the very stupid mistake (in hindsight) of sticking the backup drive in while running the new install, to try and mount it and copy my data over. The unlock dialogue popped up, in went the encryption key, then errror! 'Cannot mount this, encryption key already in use'. It was then I realized by doing this I'd stuck in two partitions with the same UUID and luks key - which they system clearly did not like.

Worse still, through some bad communication on my part, about an hour later my wife unplugged said external drive while it was still 'mounted'.

Now whenever I mount the backup drive (on a different computer), I can unlock it no problem, but when I try to mount the partition inside  it says 

```

Error mounting /dev/dm-4 at /media/user/57960113-31ce-4ced-8654-1fadf6012947:
Command-line 'mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-4" "/media/user/57960113-31ce-4ced-8654-1fadf6012947" ' exited with non-zero exit status 32:
mount: mount /dev/mapper/ubuntu1604-ubuntu1604root on /media/user/57960113-31ce-4ced-8654-1fadf6012947 failed:
**Structure needs cleaning**
```

I have NO IDEA what this means, and google isn't helping

Seeing at this all went wrong before I had a chance to copy my data back, this drive is now the ONLY copy of all my work data, as well as a lot of family photos and my email archive. I've since made a dd copy of the drive to another new hard disk, so I can experiment without making it worse.

But if someone has any idea what this is, I could really use a hand

Thanks

Tim

---

### Post by dragonfly41 on 2017-04-29
> [COLOR=#000000]google isn't helping[/COLOR][COLOR=#000000]
[/COLOR]I found many hits on google .. I guess it depends on the search pattern you are using.

[COLOR=#000000]Here is just one hit I found in a quick search (personally, I don't have the need for encrypted drives since it is one more obstacle in any data recovery) .. 
[/COLOR]
[https://unix.stackexchange.com/questions/330742/cannot-remove-file-structure-needs-cleaning](https://unix.stackexchange.com/questions/330742/cannot-remove-file-structure-needs-cleaning)

Using fsck is recommended .. provided that you have first backed up.

> [COLOR=#242729][FONT=Arial]But remember, you must run fsck only to unmounted partitions to avoid risk of file corruption.[/FONT][/COLOR]

---

### Post by in2deep2 on 2017-05-12
Its not the same problem....if you read my post, it;s different to the problem in that link. Their problem is just one file, mine is mounting the entire drive.


Does anyone have anything relevant to the OP? I've been trying on my own for over a week and I'm getting nowhere....this is ALL my data i might lose here .

---

### Post by dragonfly41 on 2017-05-12
I'm sorry that first idea didn't work out .. I see that you posted on [askubuntu]("https://askubuntu.com/questions/910078/help-structure-needs-cleaning-error-cannot-mount-partition") and the suggestion there was to use fsck.
```
[COLOR=#111111][FONT=Consolas]sudo fsck.ext4 /dev/sdaX[/FONT][/COLOR]
```
I can only offer clues from my own limited reading on the topic ...

[https://www.reddit.com/r/linuxquestions/comments/4b47r2/has_anyone_ever_gotten_structure_needs_cleaning/](https://www.reddit.com/r/linuxquestions/comments/4b47r2/has_anyone_ever_gotten_structure_needs_cleaning/)

i.e. hunting for corrupted files (inodes) which prevent mounting.

I've just tried my own file system with this command to hunt for files with ???????? string in file listing.

```
ls -l -R | grep ????????
```
I just don't use encrypted filesystem so this might be another red herring.

Hope you can get more relevant advice to help you.

---

### Post by in2deep2 on 2017-07-17
Well, an update to this problem.

After the complete lack of any useful replies,  I have since had to pay major money to have the data (or what was left of it) recovered by a professional forensic recovery company. Much that was irreplacable was still lost.

I was given advice by the technician to 'steer entirely clear of amateur-level hobby-systems like ubuntu in future -  the software is backwards, unreliable, unstable, and the people involved are largely in denial about it'. My experience in this case had sadly echoed his statement.

Windows 10 is now back on the main machine and proving a stable and FAR easier platform to use. 

So I guess the only thanks I can offer is for showing me the truth about open-source projects?

---

### Post by gsahli on 2017-07-17
> **in2deep2 said:**
> advice by the technician to 'steer entirely clear of amateur-level hobby-systems like ubuntu in future -  the software is backwards, unreliable, unstable, and the people involved are largely in denial about it'.

I guess that's why 96% of the top million servers around the world are on linux, and 99% of supercomputing projects use linux -- it's just not useful.
reference:
[https://en.wikipedia.org/wiki/Usage_share_of_operating_systems](https://en.wikipedia.org/wiki/Usage_share_of_operating_systems)

---

### Post by QIII on 2017-07-17
There are, by an order of magnitude, more devices running Linux "hobby" OSes than Microsoft's OS.  Only those whose concept of "computer" does not include any of the larger world beyond the confines of the desktop are unaware of this.

The damage to your data, which is quite unfortunate, has nothing at all to do with the OS and everything to do with operator inexperience and inattention.  From the beginning, professional data recovery would pretty much have been the only "useful reply" you might have gotten.

But use what works for you.  Nobody should be trying to convince you to do otherwise.

---

### Post by in2deep2 on 2017-07-19
It's very telling, that since relaying the critical opinion of an experienced professional,  I've received more replies trying to excuse or defelct from the fundamental failings of this system (the inability to mount two cloned drives) than I did trying to help with the original problem.

Even more telling that one of these replies is a personal attack on me for being 'inexperienced and inattentive'. And from a forum admin, no less....

If nothing else, it confirms what I was told about the level of denial. 

I've learned a lot about this OS from my technical misadventure. I guess now I'm learning about the nature of "open" source communities, and the people that inhabit them.

---

### Post by coffeecat on 2017-07-19
And with that, closed.

If you have not done so already - and you should have done - please read the forum [Code of Conduct](https://ubuntuforums.org/misc.php?do=showrules). A snippet from that to reflect upon:

> We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.

---

