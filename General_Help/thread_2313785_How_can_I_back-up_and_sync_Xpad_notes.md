---
title: "How can I back-up and sync Xpad notes?"
date: 2016-02-15
forum: General Help
---

### Post by tahitiwibble on 2016-02-15
Good day to all,

I must be getting too old and/or tired to figure this out but I have found the following solutions to my problem and can't make any of them work, I am far from mastering the CL and I don't know why. Please, how can I get my xpad notes into my DropBox folder and then sync to my laptop?

> Okay -solution was simple.
On 'mother' computer:
cd ~/Dropbox/
mkdir xpad_synch
ln -s /home/andreas/.config/xpad
On synch computers
cd ~/.config/
cp -r xpad xpad_backup
rm -rf xpad
ln -s ~/Dropbox/xpad_synch/xpad

> Can be synced through the cloud (for example DropBox) Put folder in cloud: ln -s ~/.config/xpad/ ~/Dropbox/.config/ Link subsequent computers to it: ln -s ~/Dropbox/.config/xpad ~/.config/

> Device A: Put folder in cloud
ln -s ~/.config/xpad/ ~/Dropbox/.config/
Subsequent Devices to Sync:
ln -s ~/Dropbox/.config/xpad ~/.config/

Many, many thanks.

---

### Post by newbie-user on 2016-02-15
Use rsync for local copies: [https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

For rsync to the laptop, do it over ssh: [https://www.digitalocean.com/community/tutorials/how-to-copy-files-with-rsync-over-ssh]("https://www.digitalocean.com/community/tutorials/how-to-copy-files-with-rsync-over-ssh")

This will copy the files into your Dropbox folder, and then copy the files over to your laptop. Then you can script it to run however often you want.

---

### Post by tahitiwibble on 2016-02-16
> **newbie-user said:**
> Use rsync for local copies: [https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

For rsync to the laptop, do it over ssh: [https://www.digitalocean.com/community/tutorials/how-to-copy-files-with-rsync-over-ssh]("https://www.digitalocean.com/community/tutorials/how-to-copy-files-with-rsync-over-ssh")

This will copy the files into your Dropbox folder, and then copy the files over to your laptop. Then you can script it to run however often you want.

OK **newbie-user** I'll give it a go. You know the one about "I don't like it 'coz I've never tried it"? That's me and scripts. A long time ago I was pretty accomplished in Excel macro language (and then they flummoxed me with Visual Basic and I lost the fruit of 1000s of hours of effort overnight) and I guess it takes the same kind of logic.

Thanks for the references. :cool:

---

### Post by newbie-user on 2016-02-16
If you need help writing the script, it's basically this:
```

#!/bin/sh
rsync -a --delete ~/.config/xpad ~/Dropbox/xpad_synch

```
The script uses rsync to archive (-a) the contents of ~/.config/xpad into the folder ~/Dropbox/xpad_synch, while deleting (--delete) old versions of any files that are synced.

Then you could make the script executable:
```
chmod +x nameofscript
```

And then run the script:
```
./nameofscript
```

---

### Post by tahitiwibble on 2016-02-17
Thanks a lot **newbie-user**, it's a lot easier to have a point to start muddling from. All the best.

Jeepers, I just read and digested what you suggested; is it really that short and simple?

---

### Post by newbie-user on 2016-02-18
Yes, it's that simple, assuming I'm understanding your need correctly. You just want to copy your xpad notes into the Dropbox folder, right? Oh, and you can create a cron job for the script so it runs automatically.

---

