---
title: "Upgrade from 19.04 to 20"
date: 2020-05-27
forum: General Help
---

### Post by juraj-papic on 2020-05-27
Hi all,

I would like to upgrade from 19.04 to 20 with. how can I do this without reinstalling everything or die trying.

thanks.

---

### Post by Holger_Gehrke on 2020-05-27
You'd need to update to 19.10 first. To do this you'll need to follow the procedure for an [EOL-upgrade in the community wiki]("https://help.ubuntu.com/community/EOLUpgrades") since 19.04 is past it's time of support. From 19.10 you can then upgrade to 20.04.

Holger

---

### Post by juraj-papic on 2020-05-27
Hello Holger,

Is there any chance I can break my notebook?

thanks.

---

### Post by CelticWarrior on 2020-05-27
> **juraj-papic said:**
> Hello Holger,

Is there any chance I can break my notebook?

thanks.

Not physically but OS wise yes, of course. That's why what you want to do is NOT recommended. And it takes 10x the time compared to a fresh installation.

---

### Post by juraj-papic on 2020-05-27
Hello CelticWarrios.

Thanks I will reinstall all. 

thanks again

---

### Post by mastablasta on 2020-05-28
EOL upgrade should work well, but you should always have a data backup just in case something gores wrong. if you do the upgrade, make sure you do it via stable internet connection (wired).

you just backup /home, install new OS and then move /home back.

when you install new OS make separate home partition. if you are ever in this situation you will then be able to just overwrite the root partition & keep the data.

alternatively you can do that now as well. when doing fresh install you do not format the drive. new OS will overwrite any files from the old OS, home will stay as it is.

---

### Post by DAVID_LECKIE on 2020-06-24
Hi 
I am running 19.04 and it seems that it is impossible to upgrade to a later version as 19.04 was **NOT a LTS version** and upgrade support has been withdrawn.  
It seems that upgrade support 19.10 only lasted a few months and I missed the "upgrade window".

I get the following
[COLOR=#ff0000]$ do-release-upgrade -c 
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

New release '19.10' available.
Run 'do-release-upgrade' to upgrade to it.
$ do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)[/COLOR]

In the release map there is no mention of 19.04 its as if it never existed.

Software Updater gives

"Failed to download Repository information"

This appears to be due to the fact that the repository for 19.04 has been withdrawn.

If you go to 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
There is no mention of 19.04

I hope I am wrong but it seems as of June 2020 it is impossible to upgrade from 19.04.

The only solution seems to be a clean install of a later LTS version.

Regards

Dave

---

### Post by CelticWarrior on 2020-06-24
So you didn't read either the link in post #2...

There you'd find an explanation about the repositories and the changes required. But, again, a fresh install is a much better solution and 10x faster and 3 weeks ago.

---

### Post by DAVID_LECKIE on 2020-06-24
Sorry missed that link.  I had searched the Forum for "Upgrade from 19.04" but not "EOLUpgrades"

I gather to go from 19.04 to 20.04 LTS I first need to upgrade to 19.10 then to 20.04 LTS[B]?

[/B]My problem with a fresh install is that quite a few of the applications I am running had to be compiled from source so a re-install while easier to start with will be slow to re-install applications.

From now on I am going to avoid non-LTS versions - 

Thanks for the advice

Dave

---

### Post by ajgreeny on 2020-06-24
Any applications that you installed by manual means, ie compiling them from source, would need to be removed and reinstalled if you had updated the OS even if you were just moving from 19.10 to 20.04.

Only applications that are available in the normal ubuntu repositories will behave properly when you update the system; even any ppa repos you may have enabled will have to be disabled and preferably removed or will potentially cause you problems.  I think the release upgrade command will itself disable ppa repos before carrying out the upgrade activity, but I have never upgraded release that way, always using a clean install of the root partition but keeping my /home partition untouched.

---

### Post by CelticWarrior on 2020-06-24
> I think the release upgrade command will itself disable ppa repos before carrying out the upgrade activity

Correct. 
It disables any third-party repositories and adds a "disabled during the upgrade" (or something) comment that is quite annoying. It can bet edited out later when re-enabling the repos with the new release name. At this point it's important to check a) whether or not we still need them and b) if they have contents for the new release.

---

