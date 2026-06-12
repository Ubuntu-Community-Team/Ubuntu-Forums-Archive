---
title: "Can't run add/remove or synaptic"
date: 2008-04-25
forum: General Help
---

### Post by bujutsukai on 2008-04-25
So, I took the plunge and upgraded to 8.04 yesterday.  So far, it's nice, except for some little quirks.

Like how I can't actually add anything via Add/Remove because it gets stuck before asking for password.  Also, I can't run Syanptic Manager for the same reason.  I see it try to start, and then nothing.  Any ideas?  Is there something I'm missing?

---

### Post by bujutsukai on 2008-04-25
Update:
It turns out that I really can't run ANY Admin tasks.  They look like they're going to start (placeholder in the bottom panel) but then it just goes away.  PLEASE help.

---

### Post by Seks on 2008-04-25
I'm using Hardy and it works for me, try logging in as root.

---

### Post by bujutsukai on 2008-04-26
This is what I get when I try to switch to root in Text.  I'm not even asked for a password.  I'm pretty sure this worked before.  Anything else that might help?

thomas@thomas-laptop:~$ root
bash: root: command not found
thomas@thomas-laptop:~$

---

### Post by encompass on 2008-04-26
never heard of the "root" command... try this instead...
```
sudo -s
```
anything?
if so, try this after that...
```

synaptic
```
Anything?

---

### Post by Zack McCool on 2008-04-26
root is not a command.

If you want to switch to user root, you use ```
 sudo -i 
``` which will ask for your login password.

---

### Post by tamoneya on 2008-04-26
```
su
```would be the correct way to gain root privilege in this situation.

---

### Post by buntunub on 2008-04-26
I think the point is that you should not have to do that. Add/Remove should just work when you select it from the menu option. Try checking your sources.list and see if you have the right repo's enabled.

---

### Post by FAO56 on 2008-04-26
I am having the same problem.

---

### Post by bujutsukai on 2008-04-26
Sorry about that (root)--I'm a newbie still.  Thanks to buntunub for pointing out that the point is that it's not working.  I appreciate everyone's willingness to help, and hope that we can take it in the direction of resolution rather than workaround.  That being said, any more ideas?  Thanks for your continued help.

---

### Post by Ayzen on 2008-04-26
I have the same problem. I suppose that there is something wrong with gksudo. I see that it is trying to start, but after several seconds it dies. And there no any output information or errors in terminal.

---

### Post by bujutsukai on 2008-04-26
Yes--that's exactly it!  Thanks for having the same problem ;-)

---

### Post by mali2297 on 2008-04-26
In a terminal, run
```

gksudo synaptic

```
If you get an error about a missing *.Xauthority*, create it with
```

touch ~/.Xauthority

```
Then try *gksudo synaptic* again.

---

### Post by bujutsukai on 2008-04-27
Okay, so I've tried to run it from Terminal as well, and with the same result.  Admin tries to start, then goes away.  I then have to force quit terminal (or Add/Remove).  I'm really starting to worry that it was a mistake to upgrade, since no one seems to know what's wrong.

---

### Post by encompass on 2008-04-27
Wish I could help you more.  Are you sure you have tried this command?
```
sudo -s
```
did this give you root?  were you able to run the program then?  You never directly responded to that.

---

### Post by mali2297 on 2008-04-27
Is it just gksudo that does not work or sudo as well?

---

### Post by ad_267 on 2008-04-27
If you run "groups" in a terminal does it say admin in there?

---

### Post by bujutsukai on 2008-04-27
Okay, so here are some results:

~gksudo synaptic -- yields a stalled program that I have to force quit.
~sudo synaptic -- yields "unable to resolve host"
~su -- prompts for password and changes me to root.  I then successfully ran "synaptic" and added a package.
~sudo -s -- yields "su: option requires an argument -- s
Usage: su [options] [LOGIN]
~groups -- shows several group names, including adm and admin


So, at least that works, but still not from GUI.  Does this give us a next step?

---

### Post by bujutsukai on 2008-04-27
Here's a good one--I can't run updates from Update Manager, either.  Is there a way to do this from Terminal?  I'm being advised to do partial upgrade (it would seem something went wrong with mine), but reacts by freezing up when I select it, and never asking for a password.

---

### Post by mali2297 on 2008-04-27
> **bujutsukai said:**
> Here's a good one--I can't run updates from Update Manager, either.  Is there a way to do this from Terminal?  I'm being advised to do partial upgrade (it would seem something went wrong with mine), but reacts by freezing up when I select it, and never asking for a password.

As root, run
```

apt-get update
apt-get upgrade

```

---

### Post by bujutsukai on 2008-04-27
From running apt-get update:
Reading package lists... Done
W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems

The code for upgrade installed two things, but did not reinitiate upgrade (I'm not sure that's what I want anyway).

Thanks for the continued help--how do I get the information needed above?

---

### Post by ludovicc on 2008-04-27
Hi,

It's not a good thing if you did an upgrade with debian in your package sources, that may be the reason why your system broke. Anyway, to 
wget [http://ftp-master.debian.org/archive-key-4.0.asc](http://ftp-master.debian.org/archive-key-4.0.asc)
gpg --import archive-key-4.0.asc

If you are mixing Ubuntu and Debian, you need to also do the following, to avoid in the future that newest (and maybe incompatible) versions of the package present in Debian replace the package supported by Ubuntu:

- create a file called /etc/apt/preferences
- add in it

Package: *
Pin: release a=hardy
Pin-Priority: 700

Package: *
Pin: release a=etch
Pin-Priority: 600

I have not tested it, but I hope that it work (I adapted this trick from the book Ubuntu Hacks, recommanded!)

Ludovic

---

### Post by mali2297 on 2008-04-27
> **bujutsukai said:**
> From running apt-get update:
Reading package lists... Done
W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277


You seem to have added Debian repos. You probably need to fetch the key again. Try to remember the steps you took when adding the repo in the first place. An alternative is simply to remove the repo from sources.list.

---

### Post by Ayzen on 2008-04-27
I solved that problem by removing **postfix** package. If you have "unable to resolve host" error, go to this **[thread]("http://ubuntuforums.org/showthread.php?t=770801&highlight=unable+resolve+host")**.

---

### Post by A$h X on 2008-04-27
Two things to mention here:

1) Everyone who has advised the OP to take drastic measures like install from debian repo's, hang your head in shame. You will only make the problem worse by adding more potentially unstable ingredients into the mix. One of the worse things to do is to try random UNPROVEN things in order to fix a problem, as they often create whole new problems of their own.

2) And to the OP, you need to do some more through searching. I suffered this EXACT same problem, along with a few others on upgrade day, and spent an hour searching, before making a thread, in which a few kind people try their best to help me. While they didn't directly provide a solution, they put me on the right track, and I worked out how to fix it. My thread is here: [http://ubuntuforums.org/showthread.php?t=765433](http://ubuntuforums.org/showthread.php?t=765433)

The short answer is that you need to click on manual network configuration, and then on the hosts tab, then click on add, and enter your machine's IP and hostname in the form of: 

[email]your.IP.add.ress.here@hostname.netw[/email]orkname

This all assumes you are on a network, and probably have a static IP assigned to your machines.

If this doesn't work for you, then disregard all I have said, and I hope someone who knows how to solve your problem steps in. Have a nice day. :)

---

### Post by Patsoe on 2008-04-27
> **Ayzen said:**
> I solved that problem by removing **postfix** package. If you have "unable to resolve host" error, go to this **[thread]("http://ubuntuforums.org/showthread.php?t=770801&highlight=unable+resolve+host")**.

Indeed, that's most likely the solution to the "unable to resolve host" problem. Please consider filing a bug report - there seem to be a few more people with a messed-up /etc/hosts. I don't think they all did that themselves...

bujutsukai, any idea how the debian repo ended up in your sources.list? Intentionally? Otherwise -> another bug somewhere...

Also, it seems your root password has been enabled, since you can execute su successfully. That was intentional I hope?

---

### Post by bujutsukai on 2008-04-27
Thanks to Ayzen for pointing me to the resolution of the "unable to resolve host" error.  Somehow, my laptop name was appended in the host file.  Once I removed the extra (.workgroup, for the record) and that resolved my inability to run anything via sudo.

Thanks also to all who suggested I ditch the Debian repository (A$h X, mali2297, ludovicc--please forgive if I missed anyone).  I think it ended up there when I was trying to install something else and I wasn't paying attention.  I removed it, and now update will run properly.

I went back to the original trouble spot (Add/Remove) and successfully added a game where I wasn't previously able to add anything.  I believe at this point that all is resolved, though I will be watching for updates and how they work.

Thanks to all for your help.  Without forums like this, and the community in general, most of us would never be able to make the switch to Linux.
:-)

---

