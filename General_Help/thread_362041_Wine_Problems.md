---
title: "Wine Problems"
date: 2007-02-15
forum: General Help
---

### Post by Praill on 2007-02-15
I'm trying to run world of warcraft through wine (0.9.30) on Ubuntu (Edgy) and am running into troubles.
Basically the game installs, and runs perfectly until character login. Just before the character image loads the whole system hard freezes and can only be restored by powering off.
Through much trial and error and expirimentation I have narrowed the problem down. It seems that when WoW tries to use a 24 bit color depth it causes wine to crash the system.

So, I tried to change the graphic properties in WoW to use a 16bit colors with a 16bit color depth and things work fine for awhile. However, warcraft has this nasty little habit of assuming my graphics card can handle 24 bit color, so randomly changing itself back to use 24 bit colors.
I have exhausted my options on the WoW side to an administrator basically telling me there was no solution. Now it seems I will have to attempt a fix on the wine side.

My first idea was to change the xorg.conf file to default to a 16 bit color depth instead of 24 by changing the DefaultDepth parameters under the "Screen" headings. Whatever I'm doing prevents X from starting entirely, so I have to boot in recovery and change xorg.conf back to using a 24 bit default.


Sorry for the long explination but I wanted to be thorough. Is anyone aware of this wine issue with 24 bit color depth? Is there any way to adjust wine to use a 24 bit color depth?
Any suggestions would be greatly appreciated as they will help me finally get rid of my windows partition.

Thanks.

---

### Post by renzokuken on 2007-02-15
what grafix card/chipset have you got?

do you have the correct drivers installed for it?

---

### Post by Praill on 2007-02-15
Hello, thank you very much for your reply.
I have the correct drivers installed and I have figured out a solution that I want to post for anyone else having this issue.

Essentially, as I said above, WoW decides that it knows whats best for your Config.wtf file and will periodically change it for you. To prevent this, simply make the Config.wtf read-only and then WoW will not be able to change it anymore!!!

I was then able to keep the following two entries in the configuration without WoW changing them:
SET gxColorBits "16"
SET gxDepthBits "16"
and consequently am able to play for an indefinite amount of time on all characters.

The only drawback is that you will no longer be able to modify game settings and have them saved, so you'll have to learn how to edit the Config.wtf on your own.
Here is a comprehensive list of Config.wtf options for anyone affected by this problem:
[http://www.wowwiki.com/Config.wtf_defaults](http://www.wowwiki.com/Config.wtf_defaults)

Cheers.

---

### Post by Praill on 2007-02-15
Alright, unfortunately my success was short lived.

After about 1 or 2 hours of gameplay (I can't be certain) the whole system froze again while I was doing nothing particularily different, just fighting a mob.
The really strange thing is, once it froze on one single character, it would continue to freeze on that specific character. i could log in just fine after the freeze with other characters, but the character I was on at the time of the freeze became unusable.

So naturally this pointed me to the folder where WoW saves character information (~/WTF/Accounts). I deleted the entire contents of this folder, and also deleted the contents of the /Cache folder, for good measure, since I know WoW writes to this folder periodically. Voila, I could now play any character again.
However, upon playing again I noticed that the freeze also occured everytime I died, or resurrected. So it seems to occur randomly, as well as when I change from ghost mode, to regular mode. Each time, in order to fix the problem, I have to completely delete the contents of both the Accounts and Cache folder.

I tried deleting the contents of these folders and removing my users permissions from them (so wow couldnt do whatever it was doing that was corrupting them) but it seems to cause the freeze if it cant read them (and this would also disable all character options including key bindings even if it worked). 

So I am at a loss. I can't possibly play the game if every time i die I have to reboot, delete files, then res, reboot, delete files... its impossible, and annoying.

This problem seems to be so specific I doubt there will be a solution out there. I am writing this merely to serve as a troubleshooting track record for anyone sharing the problem, or as a desperate and unlikely last hope that someone will have a fix.

Thanks again.

---

