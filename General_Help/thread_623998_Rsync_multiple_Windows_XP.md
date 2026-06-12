---
title: "Rsync multiple Windows XP"
date: 2007-11-26
forum: General Help
---

### Post by BadTimmy on 2007-11-26
Repost: *Originally posted in Absolute Beginner*
Hello everyone,

I know that there will be several of you that roll your eyes in disgust at what you are about to read but please; humor me!  (I'm still somewhat new to Linux - I'm sure it shows)
[B]
The situation:[/B]
- I need to synchronize data on several Windows XP clients.
- The clients are used by a single user but are in multiple locations across North America.
- All client locations have cable (or better) connections to the internet.
- The user needs to be able to create, modify, or delete a document on one of his XP clients and have the change reflected on each of the other clients.
- I'm cheap and I don't want to pay for a subscription service this will do this for me (not to mention that I don't trust them).
- This needs to be completely transparent to the user (because if the user can tinker, the user *will* tinker and undoubtedly mess it up).
[B]
My plan (thus far):[/B]
- Using Ubuntu create a "server" in a centralized location and synchronize over VPN.
- Apps I'm using to do this:
   - Rsync (will look after the transfers and the versioning of the files)
   - Hamachi VPN (will give me a secure pipe to each of the clients that will traverse NAT securely so I don't have to go and punch holes in any firewalls)
   - Cygwin (enables me to run Rsync on the clients as a service)
[B]
Progress:[/B]
I've followed [this handy guide]("http://www.gaztronics.net/rsync.php") but I must be missing something somewhere because I'm having problems on the server side.  The author of that page also didn't assume that his readers would be synchronizing the data to/from multiple clients.  

Right now I'm calling rsync from a batch file from the task scheduler (for now) and that part seems to be working well.

Here is what my rsync command looks like on the XP clients:
```
rsync -vrutzh --stats --progress --password-file=c:\cygwin\secret --delete "cygwindrive/c/Documents and Settings/<username>/My Documents" <username>@<server's Hamachi IP>::<module name>
```

Here is what my /etc/rsyncd.conf looks like on the Ubuntu "server":
```
# GLOBAL OPTIONS
log file=/var/log/rsyncd
pid file=/var/run/rsyncd.pid

# MODULE OPTIONS

[mod1]

        path = /home/<username>/backup
        uid = <username>
        gid = <username>
        read only = false
        auth users = <username>
        secrets file = /etc/rsyncd.secrets
        list = yes
        transfer logging = yes
        log format = %t: host %h (%a) %o %f (%l bytes). Total %b bytes.
        timeout = 600
        dont compress = *.gz *.tgz *.zip *.z *.rpm *.deb *.iso *.bz2 *.tbz
```
[B]
Questions:[/B]
- Am I headed down the right path or is there something that is bigger/better/easier/cooler that will do everything that I need?
- Are my client side rsync options correct or am I going to cause myself data loss at some point?  Will this keep all of the computers up to date without risking unwanted deletes?
- Where (how) should I be automatically executing "rsync --daemon" on the Ubuntu machine?
- Where (how) should I be automatically executing "hamachi start" on the Ubuntu machine?

Please be gentle... I'm kinda/sorta new still!  How-tos appreciated.[B]

Thanks for reading this far![/B]:)

---

### Post by lptr on 2007-11-28
Hello,

if I understand you right, then all clients using the same file pool and will independently have the possibility to modify, remove, move or create files?

You are playing a dangerous game. Do you having a special update schema. Are there access rights to certain files etc.? Otherwise what happens when client A modifies file A and at the same time client B and C does? What file will be copied to your server? What modifications will be valid? Does server resync changes itself or how will parallel changes be handled?

Just my 2 ct.

rob*

---

### Post by timcredible on 2007-11-28
can't you just setup the ubuntu server as a samba server and have the windows machines all mount the drive from that one server?  then you don't need rsync, or any other software.

---

### Post by BadTimmy on 2007-11-28
Hey Tim, Rob - thanks for the replies.

A little clarification; there is only one user (so I shouldn't have to worry about syncs overriding each-other because I'm using date-stamp).  The reason I can't just mount the dirve is that sometimes the user isn't connected to the internet (IE  working on docs while on a plane / train / automobile).

/me scratches head

I've seen other products out there like Delta Copy but it seems overly complex (and the user can get in there and mess it up).

---

### Post by lptr on 2007-12-02
Sounds for an real easy sync process. Why complicated when there is an easier way?

You've ever heard about **[SyncToy]("http://www.microsoft.com/windowsxp/using/digitalphotography/prophoto/synctoy.mspx")**? I'm using it here, too.
[SIZE=1]BTW: Best things in life are FREE 
:)[/SIZE]

rob*

---

### Post by BadTimmy on 2007-12-03
Hey Rob, thanks for your reply.

The thing that I dislike about the MS Synctoy is that (to my knowledge) it can only run in the foreground which means that the user sees it, can mess with it, and generally cause me more headaches.

One of the requirements that I can't bend on is the fact it has to be as transparent as possible because my users like to 'tinker'.  (Jerks!)  lol

Thanks again, and yes, you're right, the best things in life are free.

(edit: we're currently using this method but it is a bandwidth hog and isn't intelligent in its methods as compared to rsync or Unison)

---

### Post by lptr on 2007-12-04
> **BadTimmy said:**
> The thing that I dislike about the MS Synctoy is that (to my knowledge) it can only run in the foreground which means that the user sees it, can mess with it, and generally cause me more headaches.
...
(edit: we're currently using this method but it is a bandwidth hog and isn't intelligent in its methods as compared to rsync or Unison)

Ok - for first part: Look into the built in help. There they show, how it can be started from scheduler. 

Second: Well - if you are transfering many data, then this will consume lots of bandwidth. rsync may throtle bandwidth. All Samba based transfers using that MS stuff so you probably should provide a rsync solution. The other way is to split your data intelligently so only few compares will be necessary. I would in every case starting with the last one. This will help other syncs, too.

rob*

---

