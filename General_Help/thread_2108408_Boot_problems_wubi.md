---
title: "Boot problems wubi"
date: 2013-01-24
forum: General Help
---

### Post by yelfel on 2013-01-24
Not sure if this is the right place to post, but I'm new to the forums and in need of help!

I have ubuntu currently installed via WUBI on my laptop, everything seems to work fine however recently, when restarting the machine from ubuntu in order to switch to windows it fails to boot. On some occasions I manage to get to the OS choosing screen in which case if I choose ubuntu, things proceed fine, however if I choose windows I get to the 'starting windows' screen before the system hangs again permanently until I force shutdown.

In all cases the HDD light on the machine is not flashing when it is failing to proceed.  I don't think it is an issue with hardware however as it is a problem which has only arisen on using ubuntu. I've gone for days using only windows since installing WUBI and not encountered anything, it only seems to occur when trying to restart from ubuntu to windows.

The only solution to get back to a consistent boot seems to be to take out the battery and power, after which it is fine until I try to make the switch again.

I'm not particularly tech savvy, but hopefully someone can help?

Cheers

---

### Post by oldfred on 2013-01-24
Welcome to the forums.

I do not know a lot about wubi. But it uses the Windows boot loader and is a file inside the Windows NTFS partition. It saves having to create partitions and makes it easy to uninstall. But it relies on Windows so it not a true dual boot.

The Windows entry in wubi grub is not for booting Windows as you have already booted Windows.

You should be getting a Windows boot menu from XP's boot.ini or Vista/7's BCD that offers just windows & ubuntu. Then in Ubuntu you get the standard grub menu, but the Windows entries are not there to boot Windows as they would be in a full partitioned install.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by yelfel on 2013-01-24
Thank you very much,

I think I understand the above, the problem seems to arise when I press restart from within Ubuntu. Are you saying that to avoid the problem I should fully shut down? I'm kind of imagining this as, when restarting from within Ubuntu (wubi), it not fully 'exiting' out of the virtualisation which is why I end up having to essentially hard reset the machine (which I hear is bad)

Is that at all analogous to the problem or partially informed nonsense?

Cheers

---

### Post by oldfred on 2013-01-24
A restart from Ubuntu show take you to a reboot. Did you by any chance change the startup time in Windows to 0 and default to Ubuntu? Then you would not see the first Windows boot.

Do you have XP or Vista/7?

---

### Post by yelfel on 2013-01-24
I have not knowingly altered any settings to do with the boot, I've only used Ubuntu a couple of times since WUBIing it.

It's not so much that the window's boot isn't there, it's more after using Ubuntu when I turn on the laptop the HDD light doesn't turn on and I get a blank screen for a prolonged period of time. Eventually if I'm lucky I get to the boot select screen, if I select windows then the hdd light turns back off and the 'starting up' screen hangs, the one time I've selected Ubuntu it loaded fine, I can't confirm that this is consistent though.
As I said, once this has happened the only way to get back to reliable startup is taking the battery out and replacing it. I never get this problem when only using windows for any period of time.

When the machine is failing to turn on all the lights are on and the fan is going, just not the hdd light if that helps.

I'm running windows 7 64 bit with the 64 bit ubuntu and have not knowingly altered any settings regarding the dual boot.

Cheers

---

### Post by oldfred on 2013-01-24
Wubi is just a file inside the Windows NTFS partition. So I am not sure what may be occurring.

Have you run chkdsk on Windows recently?
 I would do backups of important data first. Most times chkdsk resolves file issues but on occasion if you have a lot of file issues it can move a lot of files around.

added wubi to your title, only a few here know wubi.

---

### Post by yelfel on 2013-01-24
I'm trying to run chkdsk now, not a lot appears to be happening, I see a flash of cmd, is this normal? Again I apologise for lack of knowledge.

I'm temped to uninstall WUBI and just partition my disk, the only thing stopping me from doing that is fear of this happening in that case and resulting in worse repercussions.

EDIT: Just ran CHKDSK and got no errors found.

---

### Post by oldfred on 2013-01-24
Since you are booting from Windows it seems very strange. 

Do you hibernate in Windows?
Are you running any DRM licensed software in Windows? But that usually used to be an issue with full partitioned installs not wubi. 
Not sure what else might be an issue as I do not use wubi.

This is an old thread so I do not know if any issue apply still or not.
       how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by yelfel on 2013-01-24
I do hibernate in windows almost daily, the problem only seems to arise post-wubi session though.
I can also now confirm that it's not just hitting restart from ubuntu which causes this. Basically every time I try to turn on my laptop when my last session was on Ubuntu, I get this issue.

Yeah I checked that thread before coming here, I couldn't immediately find anything similar.

I can honestly say I wouldn't know if I was running any DRM software, I can guess that I haven't though.

In case any background helps, I installed wubi around 2 months ago and used ubuntu once at which time it was painfully slow, I did not get this boot problem though, cut to a week ago and I used ubuntu again for the second time and a few times since then and while it now runs at a decent speed, I get the discussed issue.

Cheers

---

### Post by Mark Phelps on 2013-01-25
Hibernation is NOT supported with Wubi -- look in the section names Limitation in the link below:

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

---

### Post by yelfel on 2013-01-25
Ah, I assumed that only meant in the case of hibernation from Ubuntu, not windows also. Thank you.
Does this mean as I have hibernated in the past I will encounter this now permanently or only after hibernating prior to the switch to Ubuntu/recently?

Can I avoid this in future by no longer hibernating in any case or has the damage been done by doing it once?

Cheers

---

