---
title: "secure backup plan needs help"
date: 2007-04-25
forum: General Help
---

### Post by npdweb2700 on 2007-04-25
hey folks,
I've been working on an (overly complex) secure backup plan thats in dire need of some help.

Background:
I have 2 sites, SiteA and SiteB, connected via site-to-site VPN. 
I have 7.04 servers at each site 
each server has hotswappable sata enclosures

Goal: 
backup ~ from macs and linux boxes on each site to their local server. Then back up those backups to the remote servers every night (or so)..and all securely. So MacA will backup to ServerA at SiteA every few hours or nightly or something... then the backup on ServerA at SiteA will be backed up to ServerB at SiteB every so often . Then on the ether end BoxB will backup to ServerB which will in turn backup to ServerA every so often. And it has to be secure once off site. That is that if either server is ever compromised then the data will remain totally locked down.

What I tried:
I had a grand plan...thought it would work... I created a truecrypt volume for each user on ServerA. I used rsync and ssh to pull users' ~ to their respective truecrypt drive. Then I thought I could rsync that truecrypt drive to the remote server...the thought was it would do some kind of binary magic and just sync the subtle differences b/t the truecrypt volumes. 

What is happening:
After writing all the scripts to pull the individual user directories...and the crontabs...and the scripts to mount and unmount the truecrypt volumes... it fails. Apparently truecrypt must totally change the volume when even a subtle change (like adding one file) is made. When I try to rsync the entire volume (as a file) it sends the entire volume... each one is b/t 50gb and 75gb. The link b/t the sites is only a T1 so its not feasible to push that much data. 

So, does anyone have any ideas? 
am I just using rsync wrong?

1) I've come up with 2 solutions.. create very small truecrypt volumes and tell users we can only backup (off site) the most critical files... then at most I'm pushing 2gb / night or less

2) use keyfiles for the truecrypt volumes...scp them to the remote server, mount the truecrypt volume with it, then rsync the *contents* b/t the two truecrypt volumes. Dismount the remote volume and delete the keyfile on the remote server... that way the data is only ever open when the backup is in progress... its not ideal, but I guess it would work. Am I totally insecure since I'd be ussing ssh with key based auth? I need this all to run with out user intervention so its gotta be key based (right?).

I'd appreciate any thoughts  or suggestions!

Thanks everyone

---

### Post by trippinnik on 2007-04-25
Why not go a little simpler with encrypted bzip2 files and keep using rsync?  Asking users to only backup the most critical files is probably not the best idea, and having it all automated without users having to think about it is best.

---

### Post by npdweb2700 on 2007-04-25
I'm open to the idea of a secure bzip2 but dont know anything about it. Can you point me in the direction of some info? I did a man on it and it sounds a lot like just a password protected zip. How strong is the security? 
Will doing it that way allow me to use rsync and only get the differences b/t the files as opposed to sending alllll the data every time a change is made? 

Its not like any of this data is top secret or anything. But to me its a matter of principal. The reason I'm doing this b/t 2 sites and not using a 3rd party service is that I like keeping my data within my control. The reason I want it to be un-openable once its at the remote site is that I dont want to worry about either site being 'compromised'. 

In the interest of full disclosure, this is b/t my house and my parents house. My wife and I are on tech overload so we are backup up about 4 boxes and 3 servers on our end. My folks are not tech savy, but have just suffered a data loss and and to mitigate against that in the future. I also want an off site backup...so its mutually benifical. They backup to my server, I put a server on their end that I backup to. We are about 3 hours away so its relitivly safe. Its the age old privacy thing...its not that I have anything to hide, but the beauty of good strong encryption is that if the server on their end was ever stolen or if the house was raided or something (or if it happened on my end) then neither of us could be forced to give over the other ones data. It also means everyone can trust me as the server admin. I dont snoop through my wife's files and she should feel free to use her computer how ever she wants and part of that is knowing that she owns her backup data wherever it is.

guess that was pretty long winded...but its why I'm going to such extremes... oh, and the other major reason is b/c I'm a geek and should probably find a better hobby but right now I have to solve this problem before I can get it off my mind :D

---

### Post by SpaceBas on 2007-04-25
This is npdweb2700... was finally able to register with my prefered user name. Just subscribing to this thread.

---

