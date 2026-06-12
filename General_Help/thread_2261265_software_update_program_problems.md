---
title: "software update program problems"
date: 2015-01-17
forum: General Help
---

### Post by jgw on 2015-01-17
I have been trying to run the software update program.  After invocation it duly searches for updates and then gives one the opportunity to perform the update.  When one pushes the start button the program simply goes away (stops) and then I get an error message to send a problem.    In the last instance of this I had 2 things to update, something and ubuntu core.  I then went to synaptic and had it mark all updates, clicked to fix packages and let it run.  There were 14 things to update.  I then rebooted my system and tried the software update again.  It did its thing and then told me that there was nothing to update (synaptic did its job!).

In theory I am, now, all updated and everything is dandy.  My problem is that this seems to be an ongoing problem.  I also had one other strange thing occur.  My firefox icon, in unity, switched to a grey question mark.  After reading about fixing unity icon, etc. I decided to unlock the grey question mark (get rid of it) and then simply drag firefox from an unity application search back over to the launchpad.  One other thing is that files no longer works as it should.  To bring that up I needed to tell it to open in a new window although its not running ('new' seemed to infer it was).  I unlocked that and substituted Nemo (which I actually like better).

Anyway, as far as I know I am running just fine but thought I would send this off and, perhaps, somebody might offer up some thoughts.  I have a photo of entries in other software (problems seem to lurk here) and also ran a program called system testing and have that report available too.  Everything seemed to be fine.

My concern is that I might have had a mean spirited visitor but have no idea how to deal with that and do have the firewall installed (defaults set)

Thank you........

---

### Post by Bashing-om on 2015-01-17
jgw; Hello, again;

The GUI front ends do not provide the details that one gets from the terminal.
To get a status of the system/package manager run terminal commands:
```

sudo apt-get update ##syncs the data bases between your system and your mirror site##
sudo apt-get update ## updates installed software to what is current on your mirror##
sudo apt-get dist-upgrade ## installs new software (kernel) that 'update' does not handle##
sudo apt-get -f install ## looks and tries to 'fix' broken packages##
sudo dpkg -C ## runs an 'audit' of the package management system

```

As to FireFox and it's Icons, I can offer no help there, I do not run Firefox or unity .

> 
I have a photo of entries in other software (problems seem to lurk here)


In that case we need to look at those sources and see what the system is attempting to "fetch".
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

"a mean spirited visitor" possible, but, highly unlikely and low on the probability list. Testing for such an event I will leave to others better qualified to offer advise.
Please use codes tags for all outputs:

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We fix all things
[INDENT][INDENT][INDENT]broken hearts takes a while
[/INDENT][/INDENT][/INDENT]

---

### Post by jgw on 2015-01-17
Thank you for the reply.  I did all the things you suggested.  Everything seems to be dandy but, given that I have little understanding of what I am dealing with you can find the results of the last 2 commands at [http://pastebin.com/PJ0U0spP](http://pastebin.com/PJ0U0spP).  I do have the other stuff if you wish.  

Thanks again!

---

### Post by Bucky Ball on 2015-01-17
> **Bashing-om said:**
> jgw; Hello, again;

The GUI front ends do not provide the details that one gets from the terminal.
To get a status of the system/package manager run terminal commands:
```

sudo apt-get update ##syncs the data bases between your system and your mirror site##
**sudo apt-get update **## updates installed software to what is current on your mirror##
sudo apt-get dist-upgrade ## installs new software (kernel) that 'update' does not handle##
sudo apt-get -f install ## looks and tries to 'fix' broken packages##
sudo dpkg -C ## runs an 'audit' of the package management system

```



Hi all. Bashing Om, just wondering if you noticed that the part of your instructions in bold, shouldn't that be:

```
sudo apt-get upgrade
```

?

So:

```

sudo apt-get update ##syncs the data bases between your system and your mirror site##
sudo apt-get up**grade **## updates installed software to what is current on your mirror##
sudo apt-get dist-upgrade ## installs new software (kernel) that 'update' does not handle##
```

Just thought I'd mention. :)

@jgw: Always run those commands in that sequence. The 'upgrade' command should come before the 'dist-upgrade' one.

---

### Post by Bashing-om on 2015-01-17
@Bucky Ball; Yepper !
You are so correct ... moving too fast I guess and things get lost in the dust . ( I do try and proof read, I do )

jgw; so ...

Now we are down to the sources:
I find
1) [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) -> comes up not valid. but I do not know how to verify this ## 
2) [http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu](http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu) -> not supported in utopic
3) [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) -> has no candidate for utopic

I do suggest that these sources be disabled ( Software Sources -> other software ).
Then run :
```

sudo apt-get update
sudo apt-get upgrade

```

see now what the state of the system is in.

[INDENT][INDENT]the cleanup is never pretty
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-01-17
After disabling those repos, maybe you could add:

```
sudo apt-get autoremove
```

prior to running Bashing Om's commands. That might get rid of anything that has been installed inadvertantly and is getting in the way. Just a thought ...

---

### Post by jgw on 2015-01-19
thank you all for all the replies!

I was wondering.  As I move through the other software, on another machine, I find that there are several entries for 'trusty'.  I have also noticed that some are duplicated, say 1 for trusty and 1 for utopic.  I am assuming that I really want to disable those that are duplicated (saving for utopic).  Should I also be disable any that are not for utopic?

---

### Post by Bashing-om on 2015-01-19
jgw; Hey !

Yes, Yes and Yes .

an entry 'src' however would not be a duplicate .. IF you are not into compiling and "reading the source' best to also disable ALL the 'src' sources .. updates then will go much faster .

Never ever mix release distro's .. IF you are on 'trusty' only use trusty sources
IF you are on 'utopic' only use 'utopic' sources.
Mixing releases leads to dependency issues that are difficult to resolve.
If a PPA does not support, say 'utopic', then disable that PPA until such time as the author can catch up and upgrade his code.

If you are stepping out into deep water ->
[INDENT][INDENT]dual boot and break the 'testing' install 
[INDENT][INDENT][INDENT](many advocate virtual machine installation) 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

