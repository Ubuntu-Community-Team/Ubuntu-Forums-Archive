---
title: "Deleting Trash"
date: 2007-12-01
forum: General Help
---

### Post by measekite on 2007-12-01
I deleted many items that were in trash.

I have about 6 items left in trash.  The thing they all have in common is that they are all broken links.  I cannot delete them.

I did click "Empty Trash" and most items were gone.

When I hover the mouse over the trash icon it still says 18 items in trash.  But when open the trash can they are not there.

Also when I delete a few files in trash and then close and reopen the trash can they reappear.

How do you solve these issues.  I am using Feisty

---

### Post by skymera on 2007-12-01
ptress ctrl+H whilst in trash

i prefer the terminal way

```

cd ~/.Trash
sudo rm *
sudo rmdir -rf *

```

---

### Post by raul_ on 2007-12-01
> **skymera said:**
> ptress ctrl+H whilst in trash

i prefer the terminal way

```

cd ~/.Trash
sudo rm *
sudo rmdir -rf *

```

I though those -rf commands were banned in the forums :confused:

anyway, you don't need to delete the whole Trash folder. The 18 files listed must be hidden files (they start with a dot), so you just have to enable "show hidden files/folders" in nautilus, and then remove them. Probably the ones that are regenerated are configuration files, and they're safe there.

---

### Post by XVII on 2007-12-01
They are banned.  Please don't post commands like that someone could mess up and destroy their system.

---

### Post by Juffo-Wup on 2007-12-01
> **XVII said:**
> They are banned.  Please don't post commands like that someone could mess up and destroy their system.

But he was doing nothing wrong, those commmands will just empty the (user's own, /home) trash folder when typed in succession, and I think that was what the asker wanted. 

I thought the ban was on those commands disguised as a solution to a problem which isn't, precisely, solved by deleting a bunch of stuff.

---

### Post by skymera on 2007-12-01
> **XVII said:**
> They are banned.  Please don't post commands like that someone could mess up and destroy their system.

how are they banned?
i gave him a command that helps delete his trash, i gave him the correct directory..

also done it wrong:

```
 
cd ~/.Trash
sudo rm -rf *

```

---

### Post by raul_ on 2007-12-01
Nothing against you skymera,  I know your code works, it's just forum policy.

Take a look:

[http://ubuntuforums.org/announcement.php?f=73]("http://ubuntuforums.org/announcement.php?f=73")

---

### Post by XVII on 2007-12-01
Oh okay, I understand now.

---

### Post by ptn107 on 2007-12-01
Also note that each [ext2/3] partition you have mounted on startup will have it's own **/.Trash** folder for a given user, and when you delete stuff it goes to the **/.Trash** folder on that partition for that user.  Either **/home/USER/.Trash** (on partition with the home folder) or **/.Trash-USER** (on all other partitions).  The trash icon on the desktop shows the cumulative trash from all partitions.

*example:*
User **jon** has two hard drives each with a single partition (**/dev/hda1** and **/dev/hdb1**)
His home folder is in **/dev/hda1/home/jon/**.

**jon** deletes **file.one** from the first drive (**/dev/hda1**) it goes to **/dev/hda1/home/jon/.Trash/** (because his home folder is on this partiton)

**jon** now deletes **file.two** from his second drive (**/dev/hdb1**) it goes to **/dev/hdb1/.Trash-jon/** (because his home is NOT on this partition)

When user **jon** clicks the trash icon on his desktop and opens it he sees both **file.one** and **file.two** and can click *empty trash* to remove both files permanently.  If he's cleaning out the trash from the command line he mush delete the files in both **/dev/hda1/jon/.Trash/** and **/dev/hdb1/.Trash-jon/** to get it all.

---

### Post by XVII on 2007-12-01
> **ptn107 said:**
> Also note that each [ext2/3] partition you have mounted on startup will have it's own **/.Trash** folder for a given user, and when you delete stuff it goes to the **/.Trash** folder on that partition for that user.  Either **/home/USER/.Trash** (on partition with the home folder) or **/.Trash-USER** (on all other partitions).  The trash icon on the desktop shows the cumulative trash from all partitions.

*example:*
User **jon** has two hard drives each with a single partition (**/dev/hda1** and **/dev/hdb1**)
His home folder is in **/dev/hda1/home/jon/**.

**jon** deletes **file.one** from the first drive (**/dev/hda1**) it goes to **/dev/hda1/home/jon/.Trash/** (because his home folder is on this partiton)

**jon** now deletes **file.two** from his second drive (**/dev/hdb1**) it goes to **/dev/hdb1/.Trash-jon/** (because his home is NOT on this partition)

When user **jon** clicks the trash icon on his desktop and opens it he sees both **file.one** and **file.two** and can click *empty trash* to remove both files permanently.  If he's cleaning out the trash from the command line he mush delete the files in both **/dev/hda1/jon/.Trash/** and **/dev/hdb1/.Trash-jon/** to get it all.

That sounds like a pain in the butt.

---

### Post by skymera on 2007-12-01
> **raul_ said:**
> Nothing against you skymera,  I know your code works, it's just forum policy.

Take a look:

[http://ubuntuforums.org/announcement.php?f=73]("http://ubuntuforums.org/announcement.php?f=73")

how else is he suppose to delete it from the terminal? 
if it was /dirA/dirB/file

it wouldnt delete, saying its not empty.

i cant see why a few people using the command inappropriately means we cant use it for the right reasons.

ludicrous.

---

### Post by Tyke91 on 2007-12-01
sky has a point, that is the correct command for deleting from the trash folder, that's what it was designed to do and just because it is the "BIG RED DELETE BUTTON" doesn't mean that we can't use it when we need to.

now if he had told you to switch to your home folder, or your / folder and type that, it would be against forum policy as it would delete either all your data or your entire OS...

---

### Post by skymera on 2007-12-01
thank you

---

### Post by measekite on 2008-04-22
> **raul_ said:**
> I though those -rf commands were banned in the forums :confused:

anyway, you don't need to delete the whole Trash folder. The 18 files listed must be hidden files (they start with a dot), so you just have to enable "show hidden files/folders" in nautilus, and then remove them. Probably the ones that are regenerated are configuration files, and they're safe there.

The files are not only hidden but are windows .exe files.  When an attempt to delete them I get a message I am not the owner and do not have permission.

Also what is this -rf commands that are forbidden in forums?

---

### Post by danwood76 on 2008-04-22
-rf does a recursive forced delete if you were to run a sudo rm -rf on your root you would royally screw your system.

They shouldnt be banned when using the correct context like this though.

---

