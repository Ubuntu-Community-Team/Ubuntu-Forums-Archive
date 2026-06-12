---
title: "Works fine. Loving it."
date: 2007-05-14
forum: General Help
---

### Post by Sushubh on 2007-05-14
Wubi seems to be made for guys like me. It has worked flawlessly for me and I am loving the Ubuntu Experience.

The question...

Now that I have installed Ubuntu through Wubi... Would I be required to update to updated versions of Wubi? How would that work? I mean the system works fine for me. I need to keep my Ubuntu updated.

---

### Post by ago on 2007-05-14
You can enjoy your ubuntu for a while, you can upgrade it as usual. Check the [https://launchpad.net/lvpm](https://launchpad.net/lvpm)   project for a way to migrate to a real partition later on.

---

### Post by ecology2007 on 2007-05-14
Great :popcorn:


Ago, tux, come here, we have one who got it working.:)

I suggest you  not to try to update your install  with new wubi versions.

Ubuntu has a build in updater which will do the updates magically.

If this is your very first time, you can put this in your bookmarks.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Under firefox press F3 and find the topic you are looking for.

---

### Post by ago on 2007-05-14
> **ecology2007 said:**
> Great :popcorn:


Ago, tux, come here, we have one who got it working.:)
Yeah that's good for a change :)

---

### Post by Sushubh on 2007-05-14
> **ecology2007 said:**
> Great :popcorn:


Ago, tux, come here, we have one who got it working.:)

I suggest you  not to try to update your install  with new wubi versions.

Ubuntu has a build in updater which will do the updates magically.

If this is your very first time, you can put this in your bookmarks.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Under firefox press F3 and find the topic you are looking for.


Yeah. I noticed how it updates all the installed software. pretty cool.

So, I do not try out new Wubi installations considering my current installation works fine. noted.

1 question. Since everything seems to be running from a single file on the ntfs partition, what happens if that file gets corrupted. would i lose everything in one go? :P

looks like i have an option to use the wubi installed ubuntu as a regular installation... would read on that. thanks.

i have enabled writing to ntfs on ubuntu. am scared to use it but need to :) lets hope everything goes fine. 

thanks for the support. i always wanted to have a system like this where i can try out ubuntu in its full glory without compromising my regular system.

as i said on digg. this thing seems to be made for people like me!

---

### Post by ago on 2007-05-14
> **Sushubh said:**
> 
1 question. Since everything seems to be running from a single file on the ntfs partition, what happens if that file gets corrupted. would i lose everything in one go? :P
If you cannot fix it yes. The linux filesystem inside it should be easy to fix if something happens but for the ntfs part I do not know (I am not a windows user). Good thing is that it is easy to backup. All you really have to do is copy the /etc folder to the home folder (sudo rsync -av /etc /home/etc.bu). This way you have all the settings (system and user) in 1 file (home.virtual.disk). That is generally much smaller than the system folder and easier to backup (just copy it somewhere else). If something happens you only have to reinstall ubuntu and all the applications (you can do that with 1 command if you extract the list of installed apps), then copy back /etc. You should be back in 10 minutes flat.

> i have enabled writing to ntfs on ubuntu. am scared to use it but need to :) lets hope everything goes fine.
You are already using that.... 

> as i said on digg. this thing seems to be made for people like me!
good digg us up

---

### Post by Sushubh on 2007-05-14
> You are already using that.... 

i thought it would not hurt till the time i actually tried writing/editing/deleting a file on the ntfs partition from ubuntu. :)

---

### Post by Sushubh on 2007-05-14
cool... can anyone explain what this command will do?

sudo rsync -av /etc /home/etc.bu

/etc is source. etc.bu is a file? or a folder?


aah. etc.backup folder. :D gotcha. cool.

---

### Post by bokcmho on 2007-05-17
Very well done for Wubi.  My Sony Z505 notebook cannot install any distro because of the ext CD-ROM problem.  Finally I've stumbled on Wubi and get Ubuntu 7.04 installed and then transformed into Christian version.  All in one goal without any problem!

BTW, does someone know whether there would be something line Wubi or Lubi for Ubuntu server version?

Cheers.

---

