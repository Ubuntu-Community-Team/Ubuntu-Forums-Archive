---
title: "Thunderbird has no access to usr/bin and can't open attachments as a result"
date: 2019-07-09
forum: General Help
---

### Post by user_of_gnomes on 2019-07-09
Ubuntu 19.04 / Thunderbird 60.3.0

I can't open attachments that require an external program. If I select a different program to open attachments with (from edit -> preferences -> attachments) it tells me /usr/bin access has been denied and I am assuming this is the problem.
Right now I have to save all the attachments to the drive before opening them.

How do I fix this? Can't run Thunderbird as sudo to test my theory, it won't let me.

I think it started when I choose a minimum install by accident. Should have just gone for a full install but figured I'd just install the programs by hand.

---

### Post by Impavidus on 2019-07-09
You've got a weird version of Thunderbird for Ubuntu 19.04. You should have 60.7.2 from the repositories. How did you install Thunderbird? If it's not the regular .deb (but, for example, a snap), it may be sandboxed for security.

And never run Thunderbird, or any other application facing the web, with sudo. Most other applications you should never run with sudo either, but the web-facing ones are the worst.

---

### Post by SeijiSensei on 2019-07-09
What does "ls -l /usr/" show?  /usr/bin should have drwxr-xr-x permissions. 

Like impavidus says, you should remove the version of TBird you're running now and install the current version from the repositories.  If that doesn't help, you may need to remove or rename $HOME/.thunderbird and recreate your profile.

---

### Post by TheFu on 2019-07-09
I'd bet this is a snap issue.  Either
a) remove the thunderbird snap package and install the normal one
or
b) look up how to add access to more directory areas using the snap tools. 

This will likely be a little rabbit hole for "b", since each addon/external program will have dependencies too which are blocked.

The more secure answer is to save attachments to your ~/Download/ directory any manually open them from there.  Web browsers and email programs are generally on the front lines of Linux security, so having those run in a container or sandbox is something that I do.  I am not a fan of snaps and definitely not a fan of how Canonical decided that breaking lots of functionality by making snap installs the default for many programs.  Flatpaks and app-images are the same as snaps, BTW.  They have a place, but end-users need to understand the ideas around running these types of programs inside a constrained environment.

I use thunderbird, daily, all day. It runs in a constrained environment, but I don't open attachments and only allow 7-bit ASCII email for security reasons.  English is my native language, so I don't have to choose to allow other character sets/languages for daily communications.  Most of the world doesn't have that luxury.

[https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces) might be helpful.

---

### Post by PaulW2U on 2019-07-10
Quoting from [this]("https://forum.snapcraft.io/t/future-maintaining-thunderbird/10845/4?u=paulw2u") post on the Snapcraft forum probably explains what happened if Thunderbird was installed from GNOME Software:
> If a user removes Thunderbird (or installs Ubuntu with the minimal option), the only Thunderbird they see is an out-of-date, buggy version.
There isn't currently a stable snap of Thunderbird.

All releases have, as far as I can remember, been in the edge or beta channels so should not appear in Software at all. That's bug [#1835625]("https://launchpad.net/bugs/1835625").

---

### Post by user_of_gnomes on 2019-07-11
Thanks for the replies! It seems PaulW2U has found the  bug I ran into. 

Here's some of the information asked for: 

> What does "ls -l /usr/" show? /usr/bin should have drwxr-xr-x permissions. 

It shows the permissions stated above. 

> How did you install Thunderbird?

I don't honestly remember. sudo apt-get install thunderbird or through Ubuntu Software. I'm waging it was the latter given what I found below:

> Like impavidus says, you should remove the version of TBird you're running now and install the current version from the repositories

I seemed to have two versions of Thunderbird on my computer. One I could remove through apt-get remove/purge and one I had to remove from the Software Centre. Much to my surprise Thunderbird kept working despite having purged it but 
Whereis showed me there was still a version of the snap which I had to uninstall through the software centre so I must have installed it that way as well.

 Once removed I could reinstall Thunderdbird from the command line (luckily I had already discovered that my profile wasn't in the usual directory a day before) and put my profile back in place.
($ whereis thunderbirdthunderbird: /etc/thunderbird /snap/bin/thunderbird)

I know that was against recommendations to put the profile back but I find the Thunderbird profile system to be very robust and forgiving AND I now have version 60.7.2 and I can open attachments again! 

> The more secure answer is to save attachments to your ~/Download/ directory any manually open them from there

Unfortunately that will result in a lot of bills being left unpaid as I simply forget to open them afterwards as I have the attention span of a goldfish.

Thanks a lot

Still don't really understand how I could end up with this bugged version in the first place. I figured it'd be a safer bet to get it from the Software Centre but I guess I should just continue using the command line so I don't end up with these annoying snaps ...

---

### Post by PaulW2U on 2019-07-11
Nice to hear that you've got Thunderbird working now. Today I read elsewhere that the snap version of Thunderbird is going to be updated and made stable so some of the problems that you encountered may be resolved soon.

If you install anything using GNOME Software make sure you read the details section below the screenshot. That is where you can establish whether you are installing a snap or the regular deb version. Alternatively, install the Synaptic Package Manager like many of the users here do. No snaps anywhere to be seen but a complete listing of every package available for your release. Much more complete than GNOME Software.

You should see Thunderbird update to version 60.8 sometime over the next week as part of the regular updates.

---

### Post by user_of_gnomes on 2019-07-12
Thanks! I will look into the the SPM.

---

