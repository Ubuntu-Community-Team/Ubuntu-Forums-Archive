---
title: "the state of hot imaging these days..."
date: 2008-05-14
forum: General Help
---

### Post by starkes on 2008-05-14
Hey there,


I'm trying to make an image of a machine in production that can't be taken down. It's not a big deal if it does go down, but I would rather not have to boot into something like g4l if I can avoid it.

Also, it's rack-mount so I'd like to leave it in the rack, and i'd have to make a trip to do it anyway.

I notice theres more and more options for windows users in this regard, but even still I see a lot of talk about the quality of the backups being bad.

I've thought of using something like rsync to preserve all the file's attributes and whatnot, but I thought someone here must have run into this situation before...


Any ideas?

---

### Post by scorp123 on 2008-05-14
Can you explain more about what this server is doing and why you can't take it down? If it's a really important machine you should consider adding the right hardware and do e.g. mirroring so in case of a disk crash you'd have a second harddisk that still has the data.

Also, as you mentioned that this machine is mounted in a rack, I suppose this is a server that your company owns? Don't you already have things like tape streamers or other backup mechanisms in place so you could take snapshots of the machine anytime you want or you need to?

---

### Post by starkes on 2008-05-14
basically im working for a production company that does 2d and 3d animation.
we have 1 2d render node on the network and 12 3d ones. 

because the load is exponentially higher for 3d rendering basically. we're at a point where we need more 2d rendering power and aren't using all the 3d nodes, so we want to image the 2d one and make a few of the 3d machines into 2d machines. 

we can take down our only 2d machine, but we'd rather not.. as it is the only one right now...

again though, its not like a business style massive critical operation kind of thing here. we're just interested in figuring out the process for times when it will be that crucial.

---

### Post by scorp123 on 2008-05-14
But I am correct to assume that there are no databases (e.g. Oracle) or something similar running in the background? The reason I ask: Most if not all databases have their own file caching and file locking mechanisms, or sometiems even their own filesystems ... So it's rather hard to take reliable snapshots from them, especially if they are running and you can't take the DB down.

But you said you're rendering stuff ... so I assume the only thing really running on the machine in the background is your rendering software and whatever it is crunching numbers on? e.g. no process whatsoever that would have its own filesystem mechanism anywhere (such as databases) ... ?

Well in that case I'd suggest "tar". Tar will grab snapshots of whatever is on your filesystems at the moment it is being executed, and the nice thing is that you could also execute it remotely (e.g. via a "ssh" connection) and hence store the resulting *.tar.gz somewhere else.

I once wrote a backup "how to" for the Linux Mint forums. It can be found here:

"How to backup your stuff UNIX-style"
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

The advantage of the "tar" method is that it pretty much "just works". All the tools are already there in the OS, no need to download anything.


Other threads around here that might interest you:

"Re: tar directly across ssh link"
[http://ubuntuforums.org/showpost.php?p=4760998&postcount=5](http://ubuntuforums.org/showpost.php?p=4760998&postcount=5)

---

