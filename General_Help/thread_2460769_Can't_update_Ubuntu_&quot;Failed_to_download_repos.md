---
title: "Can't update Ubuntu: &quot;Failed to download repository information&quot; + error 404"
date: 2021-04-18
forum: General Help
---

### Post by empleat on 2021-04-18
I can't update Ubuntu, Using software-updater, it ran automatically after system bootup and failed with this message: 
"Failed to download repository information". I tried: "sudo apt update", it didn't work as well. At each IP there was error 404! But my connection should be fine, I can connect to the internet. No idea why it doesn't work. I tried to change mirrors, but there are many of them and post wasn't specific on which one to change! No idea why this error is happening!

I wasn't using this system awhile, it is clean system and there is barely anything on it! It worked fine last time. 

I am on Ubuntu 19.10.

Thanks for help.

---

### Post by CelticWarrior on 2021-04-18
> [COLOR=#000000]I am on Ubuntu 19.10.[/COLOR]


Being on a obsolete release **IS** the problem. Repositories have been moved to archive a long time ago (almost an year ago, actually).
Please do your backups if not done already and install a supported release. Ubuntu 20.04 is a LTS and supported until April 2025.

---

### Post by empleat on 2021-04-18
Install? So it can't be updated you say?

---

### Post by CelticWarrior on 2021-04-18
It can, there's a [whole page of Help Ubuntu about it]("https://help.ubuntu.com/community/EOLUpgrades"), but because you can do something doesn't mean you should. 
In this case it will take 3x or 4x the amount of time required for a new installation with possible worse results.

And sorry for being blunt but having [interacted with you in the past]("https://ubuntuforums.org/showthread.php?t=2455650") I know the whole process is too much for your level of understanding.

---

### Post by ajgreeny on 2021-04-18
Yes, as CW has said, trying to upgrade from an EOL  version is something that, though possible, is not very simple for a new user, and in all honesty, is something even I would probably not bother with after 16 years of using Ubuntu.

To backup your personal files sounds as if it will be a simple operation if you have not used the system for a long time, and as you say, you have practically nothing on it. Had you continued to use it over the last year it might very easily be severly compromised and dangerous to continue using even after an upgrade.

So backup those personal files in your home including all those hidden files and folders with names starting with a point, ie dotted name such as ***.config***.
Once you have that backup do a clean install of 20.04 and restore the backed up files and folders to your new home.

Much quicker; much safer!

---

