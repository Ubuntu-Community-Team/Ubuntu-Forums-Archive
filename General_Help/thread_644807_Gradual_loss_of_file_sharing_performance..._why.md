---
title: "Gradual loss of file sharing performance... why?"
date: 2007-12-19
forum: General Help
---

### Post by dwasifar on 2007-12-19
I have a machine set up as a file and media server.  It's a straight Ubuntu installation (i.e. not a LAMP installation) on which I installed nfs, samba, and twonkymedia to perform the various file-serving tasks.  It lives in the basement where I'm not tempted to tweak around with it.

It had been running for six months without a reboot until yesterday, when I did a version upgrade on it (from Edgy to Feisty). When it came back up, its performance was significantly improved.  I had noticed the throughput degrading over the past couple of months, but it had not become bad enough for me to put aside my other tasks and go looking for the problem (because, of course, it could have been any number of things).  Now everything is snappy and speedy; shares come right up on the client machines without delay, like they did when I first set it up.

My question is, why did this happen?  Is there some maintenance process or utility that should be run on the server to keep things from getting bogged down?  I know that in theory I should not have to do periodic reboots to keep the server services up to speed; that's Microsoft's department.

---

### Post by david3d on 2007-12-19
Well this can be a number of things outside your computer such as network or client configurations/issues.  If you're using wireless in particular I would rescan your area for other networks and make sure you're operating on a free channel and that you're getting network speeds that you expect.

Your email didn't go into this particular aspect but here is one server side possibility.  Samba can get a bit slow on larger directories due to the fact that Windows is not case sensitive where *nix is.  So Samba has to do what's called file mangling in order to try to resolve a file request to a filename on the file system.  I believe that they do some tricks here to help reduce the number of case combination calls it takes but it still has a significant overhead when dealing with directories that contain a large number of files.  There are a few steps that you can take to prevent this however by adding the following lines to your global or to a shares parameters in the smb.conf file.

    case sensitive = yes
    default case = lower
    preserve case = no

Then you'll need to go through and force all file names on your shares to be all lower case.
--
David

---

### Post by dwasifar on 2007-12-19
Hi David,

I appreciate your detailed reply, but I don't think the issue is with the network; the fact that a server restart improved performance points pretty clearly to the server being the guilty party.

But a few more details would probably have helped, huh?  :)

There is a wireless network in place; however, the speed issues (and their eventual resolution) were apparent over all connections, including wired connections.  All the wired connections are gigabit.

Samba is still in place on the server but is no longer actually being used, because I banished Windows from my house.  :)  All the clients connect with nfs or through the twonkymedia server, which is a uPnP server running as a daemon.

Does the "file mangling" take system resources and hold on to them?  Is it caching its results indefinitely?  Because I can see how that would cause a slowdown over time.

---

### Post by david3d on 2007-12-19
I doubt your problem is Samba but, if you no longer need it I would start by disabling it.  At least you can rule it out as a cause.

How long does the system have to be up before you run into this problem?  Have you tried just restarting nfs or twonky?  If that doesn't do anything try restarting the networking with "sudo /etc/init.d/networking restart".  If one of these solutions work maybe you can set it up as a cron job to restart the services every so often as a work around until you can sort out a better solution.
--
David

---

### Post by dwasifar on 2007-12-19
> **david3d said:**
> I doubt your problem is Samba but, if you no longer need it I would start by disabling it.  At least you can rule it out as a cause.

How long does the system have to be up before you run into this problem?  Have you tried just restarting nfs or twonky?  If that doesn't do anything try restarting the networking with "sudo /etc/init.d/networking restart".  If one of these solutions work maybe you can set it up as a cron job to restart the services every so often as a work around until you can sort out a better solution.
--
David

How long?  I don't know exactly.  A long time.  :)  The system was up for six months (175 days, to be exact), but I'm not sure exactly when it started slowing down.  It was gradual enough not to emerge on my radar for a while.

I'll remember the networking restart idea.  It will doubtless be a while before I can test.  What would the corresponding command be for nfs - "sudo /etc/init.d/nfs-common restart"?

---

### Post by david3d on 2007-12-20
Yeah at 6 months out it will take some time to do some testing.  I've never run nfs server so I'm not sure what init.d script controls that.
--
David Miller

---

