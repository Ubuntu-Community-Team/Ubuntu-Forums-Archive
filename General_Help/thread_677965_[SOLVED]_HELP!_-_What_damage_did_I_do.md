---
title: "[SOLVED] HELP! - What damage did I do?"
date: 2008-01-25
forum: General Help
---

### Post by Bruce M. on 2008-01-25
This is so embarrassing.  I need to know what damage I did, if any.

Last night I backed up my /home folder to my second drive. That's a relief!!

This morning I shrunk my /dev/sda5 to 22GB and created a 45GB partition for my new /home formatted it as ext3. 

Of all things, I then went looking and found this guide that I copied to gedit from [http://www.psychocats.net/ubuntu/separatehome:](http://www.psychocats.net/ubuntu/separatehome:)

Changed all references of hda to sda for my system and started here:

```

Using the new partition
Now, back in the terminal, I'm going to mount /dev/sda1 and /dev/sda7:

sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda7 /new

Now we're going to back up the /home directory on the old partition and move it to the new partition:

cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

Yes, one of those lines looks really complicated--please type it as is--or, if you're unsure of your typing skills, copy and paste it into the terminal. Believe me--the command is necessary.

Next, we're going to specify to use the new home partition as /home:

sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:

/dev/sda7 /home ext3 nodev,nosuid 0 2

Then save (Control-X), confirm (Y), and exit (Enter)

After you reboot, you should be now using your new /home partition.

If you find that you are running out of room on your old partition and you're pretty confident everything is working as it should be, then go ahead and delete the backup of home:

sudo rm -rf /home_backup

What if it doesn't work?
You know, it really should work, but if you somehow messed up your /etc/fstab and didn't configure it correctly... well, that's why we have a live CD, so we can fix things.

Boot up the live CD, go to a terminal, and type:

sudo mkdir /recovery
sudo mount -t ext3 /dev/sda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

Then, reboot. 

```

Then I made my mistake, I cut an pasted the first command seen below to terminal, and hit enter.  My wife called me!  :(

```

sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda7 /new

Now we're going to back up the /home directory on the old partition and move it to the new partition:

cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
```

Upon coming back I said to myself, OK, line two, but I cut and pasted line two from the lower grouping.  :(
The: ```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
``` one......

And in terminal I now see the last few lines:

```

/new//./.dia/objects
/new//./.dia/defaults.dia
/new//./.dia/sheets
/new//./.dia
/new//./.gworldclock
/new//./.conkyscripts/conkymain
/new//./.conkyscripts/conkytest
/new//./.conkyscripts/conky_top_left
/new//./.conkyscripts
8238019 blocks
bruloo@The-Team:~$ 

```

So before I proceed, what have I done damage wise?
Is it reversible?
Or do I need a new install and restore from my backup?
Please say; No, that's not necessary.

Waiting patiently online.
Thanks
Bruce

[B]EDIT: OH, this is worse, I didn't,

mount /dev/sda1 and /dev/sda7

¿How dumb can I be?[/B]

 **2.** Wife needs something at the store, she is sick and can't go, back in 15 min (15:18:30 now)
 **3.** Back online
 **4.** Just noticed his hda1 is my sda5 - replaced in my txt file.
 **5.** found /old/ and /new/ under "File System" - /new/ is a copy of my /home - hmm, looking better *I think.*

---

### Post by aonegodman on 2008-01-25
WOW!  I just skimmed over your post and that alone scared the p*** out of me.

What made you jump on that bad boy sooooooo fast?

Not knowing your computer config I can't comment much. Is hda1 your windows HD?

If your /home was sda* then your "stuff" should be theoretically safe if I read your post correctly.  Keep me posted. Hope all turns well for you.

Prayers for the wife to Bruce.   :)

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> WOW!  I just skimmed over your post and that alone scared the p*** out of me.

You!  I flushed twice, once for simply filling it, the second time because I was finally done!  :)

> **aonegodman said:**
> What made you jump on that bad boy sooooooo fast?

Lost concentration when I was called... "OK, where were we ... oh yea, command number 2.  Just picked the wrong grouping.   :(

> **aonegodman said:**
> Not knowing your computer config I can't comment much. Is hda1 your windows HD?

All sda's here.  Yes sda1 is a bare bones W2K install with freeware antivirus (AVG Pro Freeware version), freeware firewall (COMODO) and ZonedOut (freeware) ... something I recommend to ALL windows users, my version put just over 12,000 restricted sites into MSIE's "Restricted Zone", a lot of them MS sites to because they "listen" to you.  :)  Still have that stuff on CD's too.

> **aonegodman said:**
> If your /home was sda* then your "stuff" should be theoretically safe if I read your post correctly.  Keep me posted. Hope all turns well for you.

I'm thinking that it's safe, and since I've not had a nibble here help wise, I'm continuing.  Now that's scary!  But in the past hour and 45 minutes I've done more reading & research.  Time will tell.

> **aonegodman said:**
> Prayers for the wife to Bruce.   :)

GRACIAS!  Thank you.
Bruce

---

### Post by Zwack on 2008-01-25
Based on what you appear to be trying to do, probably not too much.

First I'd check what is mounted where (mount)
and if anything is mounted on /new or /old then check the contents.

Otherwise you might just have copied /home to /new on your root directory.

Rather than on your new /home partition.

I hope that this helps,

Z.

---

### Post by Bruce M. on 2008-01-25
> **Zwack said:**
> Based on what you appear to be trying to do, probably not too much.

First I'd check what is mounted where (mount)
and if anything is mounted on /new or /old then check the contents.

Otherwise you might just have copied /home to /new on your root directory.

Rather than on your new /home partition.

I hope that this helps,

Z.

That's it to a **"T"**, I now have a few /home folders (called other things), but most importantly /sda7/home is up and running.
Just have to clean out some garbage now.  :)
That was a close shave!

---

### Post by Bruce M. on 2008-01-25
[CENTER]**Working as it should!**[/CENTER]

Zwack was right, but even more so:

In Thunar I have:

bruloo - at the top it is /sda7/home
Trash
W2K
40G Volume
File System
 /home/bruloo/ - full c/w hidden files
 /home_backup/bruloo/ - full c/w hidden files
 /new/ - full c/w hidden files
 /old/ - empty

When it got to the part where it said OK, now reboot, I did.

Ubuntu was loading fine ...

[SIZE="4"]**POOF!**[/SIZE] **Gone** - black screen with white text flying by with the odd red flash.

When it stopped I saw a [[COLOR="Red"]**Failed**[/COLOR]] on the right hand side of my screen. And the text ending with (something like):

fsck failed at Default 4

So I typed: fsck - figured I couldn't do any harm, and got a warning this was a bad thing to do on a mounted drive (something like that)
Do you want to continue? [Y]es [N]o  <--- NO!

That brought more prompts:
Found error with ..............
Do you want to fix it?  [Y]es [N]o  <--- YES!
4 times ....

Back to a steady prompt!

OK, kid, time to reboot again.

MAN I LOVE UBUNTU! It worked just like the advertising said it would!

[CENTER][[IMG]http://img89.imageshack.us/img89/9224/gpartedth7.th.png[/IMG]](http://img89.imageshack.us/my.php?image=gpartedth7.png)[/CENTER]

Bruce is a Happy Camper.

And I had to change my conky too to reflect the changes, roughly 80G just for me now.  Love it.
[CENTER]
[[IMG]http://img111.imageshack.us/img111/3706/conkyvz6.th.png[/IMG]](http://img111.imageshack.us/my.php?image=conkyvz6.png)
[/CENTER]
Gee that new conky line: **Home (sda7)** sure looks nice.
So that's it folks, **Solved**.  Just have to delete some stuff.
Bruce

---

