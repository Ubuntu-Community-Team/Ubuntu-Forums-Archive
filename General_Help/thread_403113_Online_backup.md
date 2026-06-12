---
title: "Online backup"
date: 2007-04-06
forum: General Help
---

### Post by tc101 on 2007-04-06
Is anyone here doing online backup?  If so, what service are you using, or how are you doing it?

A friend highly recommends this company, but I think it is only for windows:
[http://www.eweek.com/article2/0,1895,2073628,00.asp](http://www.eweek.com/article2/0,1895,2073628,00.asp)

---

### Post by munkiepus on 2007-04-17
I've been looking at this too and it seems a lot more difficult to use any of these free services with linux. Mediamax.com gives you 25GB of free storage. This sounds great as long as you either have windows to install their client software or can be bothered doing manual backups of all your stuff :frown: 

Before i transitioned to ubuntu i was using my webhost (which has unlimited space) as a backup via ftp. Using a windows sync by ftp program, it worked great. 

Now having moved to ubuntu the choice seems to be, use rsync, which none of the hosting companies seem to support at their ends. (not the free ones anyway). I cannot seem to find anything for linux which does the sync by ftp, save having to write a custom script which would probably end in years of lost photos and then tears. :( 

So for now it's onsite storage and just hope my flat doesnt burn down.

If anyone has any better ideas on how to get a free online storage service working with ubuntu i'd love to hear it.

Cheers

---

### Post by tc101 on 2007-04-17
I just zip up the most important stuff and email it to myself at my yahoo email account so I have some offsight backup.

---

### Post by munkiepus on 2007-04-17
Yeah that's ok if you only have a small amount of stuff to backup and you remember to do it. I'm talking 5-6Gb of photos and i want something to do it automatically from linux. It was easy on my windoze box but i'm not going back now just for one thing. Ubuntu wins hands down on a ton of other stuff.

Any more ideas? Ive been reading about lftp does anyone have any experience of this working?

Cheers :)

---

### Post by tc101 on 2007-04-18
I did a google on linux backup service.  Look at this:

[http://www.novastor.com/windows/linux-backup.html](http://www.novastor.com/windows/linux-backup.html)

This one is probably too expensive:

[http://www.fortuitous.com/en/services/it/backups/](http://www.fortuitous.com/en/services/it/backups/)

Anyway, that was just a quick search.  Keep me informed if you find anything good.

---

### Post by munkiepus on 2007-04-18
I guess the simple solutions are the best,

so here's how it's going so far, i'm using lftp to do a backup/mirror from my local drive to my webhost. I've set it on a cron job so it should do it automatically once a day.

lftp -c 'open ftp.streamline.net; user *username userpass*; mirror -p -R  /media/media/photos /private/media/photos'

/media/media/photos  is the local folder
/private/media/photos is the remote folder

once it's run the first cron run i'll get back to you and tell you how it went. Next i have to get it backed up to one of those free online storage things like mediamax as the t&c's of my unlimited webhosting plan means that i'm not allowed to use it as backup storage, DOH! Luckily i think mediamax uses ftp so it shouldnt be too much of a problem.

Laters :)

---

### Post by tc101 on 2007-04-19
Do you feel comfortable backing up everything to a free online storage place?

I am a victim of identity theft.  Some criminal or criminal organization got my social security number and other info and was able to open up lots of phoney credit card accounts in my name and steal lots of money.  It didn't cost me anything but it has been a time consuming mess cleaning up my credit history.

I have always wondered how they got the info.  One possibility is that I did offsight backups of everything, which would include my turbo tax files, which would give them everything they need. 

There are lots of other ways they might have gotten the info, but I would double check with someone more knowledgeable before you do a backup of everything to a free storage site.

---

### Post by munkiepus on 2007-04-24
I'm not too worried about that, the stuff i'm backing up is not really personally identifiable. Its just photos and web development work. Nothing really that's stealable or worth any value to anyone else but definately irreplaceable.

As far as the ftp to mediamax goes it's not that great, the ftp server is separate from your account so you can ftp stuff up to the ftp server but it is transferred from there onto your account and deleted from the ftp server, this means that i cant scan the contents online so i cantt backup the missing files, it keeps trying to backup everything every day. Maybe i need to limit it to just uploading the last 24hours changes or something. Using LFTP works really well for the backup onto my web host though although my webhosts ftp connection is a bit tempramental. 

Still trying to find a decent amount of free online storage that lets you use rsync, that would be perfect.

Later :)

---

### Post by munkiepus on 2007-10-02
> **tc101 said:**
> I did a google on linux backup service.  Look at this:

[http://www.novastor.com/windows/linux-backup.html](http://www.novastor.com/windows/linux-backup.html)

This one is probably too expensive:

[http://www.fortuitous.com/en/services/it/backups/](http://www.fortuitous.com/en/services/it/backups/)

Anyway, that was just a quick search.  Keep me informed if you find anything good.



I finally got rumbled by my web hosts, what's the point of having unlimited storage and nothing to put in it. Oh well.... Back to the search for a cheap off site storage thing.

I have found this one [http://www.simplyoffsite.com](http://www.simplyoffsite.com) which works for linux and is a LOT cheaper than the ones mentioned above. However it's still not free which would be better.

I really wish mediamax would sort out their ftp situation then i could just use that.


Anyone got any other ideas for backup or sync online?

---

### Post by misfitpierce on 2007-10-02
I do Wixi and Gmail. Mailbox acts as a fine backup for some things. Wixi holds alot of my music backed up.

---

### Post by munkiepus on 2007-10-02
I'v esigned up  to wixi see how that works out , just need to wait for an invite.  Cheers.

---

### Post by lavendermi on 2007-11-03
Take a look at [http://www.vembu.com]("http://www.vembu.com"). It isn't free but if you have a friend then you can setup a remote peer-to-peer based backup using the StoreGrid software.

Mike Lavender
Simply Offsite

---

### Post by munkiepus on 2007-11-04
> **misfitpierce said:**
> I do Wixi and Gmail. Mailbox acts as a fine backup for some things. Wixi holds alot of my music backed up.

I just got my wixi beta access yesterday.....

Wixi is good as long as you have signed up to the beta version which gives you unlimited storage space, great for storing mp3s. the regular account gives you 3 GB for free and the option of up to 10gb for about $50 per year.  Not so good :(

The only problem is that there is no way to automatically backup all your stuff it must all be loaded manually onto the wixi website using the web interface which will take ages as i have 70 + GB of toonz.


The search continues...

---

### Post by munkiepus on 2007-11-04
> **lavendermi said:**
> Take a look at [http://www.vembu.com]("http://www.vembu.com"). It isn't free but if you have a friend then you can setup a remote peer-to-peer based backup using the StoreGrid software.

Mike Lavender
Simply Offsite



I do have a friend.... :)

But instead of buying software for $30 per yer per computer to do that. I'd be better off setting up a nas box with ftp or a server at my friends house and then i could use rsync. A cheap nas box costs about $50 + hard drive cost then there's no ongoing costs. I think this might be the way forward :)

Cheers

---

### Post by davidpodhola on 2008-02-07
Great idea, helped me a lot, thanks :-)

---

