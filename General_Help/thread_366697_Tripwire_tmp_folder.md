---
title: "Tripwire tmp folder"
date: 2007-02-21
forum: General Help
---

### Post by dannyboy79 on 2007-02-21
I am using tripwire and in the man pages it suggested that I create a folder within /tmp for tripwire's temporary files due to /tmp being insecure.

TEMPDIRECTORY
              This variable can be set to the location to which tripwire should write its temporary files. By
              default it is /tmp, which due to the default permissions can be very insecure. It is recommended that
              you use this configuration variable to provide tripwire with a secure place to write temporary files.
              The directory used should have its permissions set such that only the owning process can read/write
              to it, i.e. "chmod 700".
              Initial value: /tmp


 Well I did that and I chmod'd it to 700 and I made it's owner:group root. well this darn directory keeps disappearing?? can anyone tell me why this is?? this is what the cron.daily for tripwire looks like if it matters:


#!/bin/sh -e

tripwire=/usr/sbin/tripwire

[ -x $tripwire ] || exit 0

umask 027

$tripwire --check --quiet --email-report

any help would be appreciated.

---

### Post by dannyboy79 on 2007-02-27
can some1 please inform me how to make it so that a folder within the /tmp directory doesn't get deleted after a restart? the fricking man pages tell me to create a folder within /tmp, tell me chmod it to 700 and I do that but then when I shut down, the folder goes bye-bye then my program fails since it's folder it is suppose to write it's temp files to is gone. Help please. I know I can change how often the /tmp directory gets cleaned out in a set amount of days within a certain file but I want to be able to keep this folder permanently. thank you.

---

### Post by dannyboy79 on 2007-02-28
ah, another polite bump. I am starting to actually believe what I friend told me about the open source world. You don't get back half of what you give because out of the over 1400 posts that I have made 95% of them are helpling others aqnd there are very few asking for help which I most of the time don't get it. So, please, anyone, help me with this? I have looked in this on gogle as well and I only found 1 place and it only talked about being able to change the amount of days or something like that before it erased all /tmp files but that's not what I want, I need this folder to be there and stay there. thanks of you can provide any insight.

---

### Post by srt4play on 2007-02-28
I think you're making this harder than it needs to be.  I have no experience with tripwire, but reading the excerpt from the man page you posted I see that it's not asking you to create a folder in /tmp. It's telling you the default value is set to /tmp and you should change it.

[QUOTE=dannyboy79] By default it is /tmp, which due to the default permissions can be very insecure. It is recommended that you use this configuration variable to provide tripwire with a secure place [/QUOTE]

It tells you the default is insecure, and then asks you to provide a secure place.

So choose a different directory not in /tmp, and you're problem of disappearing files after reboot is gone.

---

### Post by dannyboy79 on 2007-02-28
ok, greate idea. However, I still want the temp files to be removed from that folder after a shutdown or restart, I just want the folder to stay there so that tripwire doesn't fail to run. is there some kind of script I can create and put in rc0.d and rc6.d which will clean out ANY files within /var/tmp/tripwire? thanks for your help. I am very happy that at least some1 responded. That's all it takes some times, is just some1 elses thought, I was so hung up on thinking the directory had to be in the /tmp folder that I never thought about what you're suggesting. I do still wonder if this is possible though. Like what if Open office stored files in /tmp, and then what if your machine crashed before you could save it, the /tmp folder would be cleared out so what good what it be for storing temp files. Well I guess I can change the setting in that 1 file that controls how often the /tmp folder is cleaned out, do you recall where that setting is? I know I found it once but now I am drawing a blank, it's not in /etc/inittab cause I just checked. thanks again.

---

### Post by lamego on 2007-02-28
> I am starting to actually believe what I friend told me about the open source world. You don't get back half of what you give because out of the over 1400 posts that I have made 95% of them are helpling others aqnd there are very few asking for help which I most of the time don't get it.
Did you gave anything to the open source world besides complains? Or do you believe that tripwire is a commonly used tool for people which spends time on general help support forums ?

All files and directories within /tmp are deleted during the system boot because as the name suggest it is a temporary folder, its contents are not expected to be required after a reboot.

You can edit /etc/rc.local and add the rm /var/tmp/tripwire/*

---

### Post by cookfromfrozen on 2007-02-28
I know that it can be frustrating when nobody answers your post, but I'm sure you can appreciate that Tripwire is a security auditing tool and is not something that is used by most Linux newcomers; therefore the level of response to your question will probably be lower than a forum built upon Tripwire experts.

As you now realise, the documentation wasn't actually asking you to use /tmp as the configuration dir, but actually *not* to use /tmp.  /tmp should not be used for storing data you want to keep as it is volatile after a reboot.

Specifically, I don't know about OpenOffice, but I would be quite sure that it doesn't store data that the user might need in /tmp.

---

### Post by dannyboy79 on 2007-02-28
> **cookfromfrozen said:**
> I know that it can be frustrating when nobody answers your post, but I'm sure you can appreciate that Tripwire is a security auditing tool and is not something that is used by most Linux newcomers; therefore the level of response to your question will probably be lower than a forum built upon Tripwire experts.

As you now realise, the documentation wasn't actually asking you to use /tmp as the configuration dir, but actually *not* to use /tmp.  /tmp should not be used for storing data you want to keep as it is volatile after a reboot.

Specifically, I don't know about OpenOffice, but I would be quite sure that it doesn't store data that the user might need in /tmp.


well actually the default setting in tw.cfg is the /tmp folder! it just was pointing out that /tmp is not secure. So I am curious, I have created a folder within /var/tmp/ and I want the temp files that tripwire creates to be deleted upon shutdown, how would I accomplish this?

---

