---
title: "Netatalk boot startup problem."
date: 2007-06-28
forum: General Help
---

### Post by Amalekite on 2007-06-28
After installing netatalk on Kubuntu (Fiesty Fawn) as per instructions at

   <http://ubuntuforums.org/showpost.php?p=918060&postcount=16>

to build it with SSL (which allows for encrypted passwords), it works fine except for the minor irritation that it doesn't start automatically at boot itme.

This is really odd because I can start it manually from the command line with the invocation

   sudo /etc/init.d/netatalk start

I checked for the netatalk link in  /etc/rc2.d/  and confirmed its existence.  It points to the appropriate file in /etc/init.d:  S50netatalk -> ../init.d/netatalk.

So that should take care of that, right?  Then why don't the netatalk services start at boot time?

[I've looked through the output of dmesg and haven't found anything (no errors, but also no reference to netatalk at all).  It's as if the install script or some key link is missing.]

Is this one of those subtle differences between Debian & Ubuntu which I haven't quite picked up yet?  [All my (fairly limited) experience is with CLI-only servers running Debian.]

Is it an "upstart" thing?  I've heard that moves are afoot to change from the standard Sys V boot proceudre to this new-fangled upstart ;-)

I'd be grateful if anyone could shed some light on this... even just a pointer on how to proceed would be nice, because I'm not sure what to do next.

Thanks in advance.

---

### Post by kidders on 2007-06-29
Hi there,

I noticed you've had no response to two of the three threads you've started. I'm just posting here to flag you to the Unanswered Posts Team. Hopefully someone can help you!

I'm using a custom netatalk build too ... for the same reason as you are. I haven't had any problems with it, but unfortunately, I can't simply reboot the machine it's running on at will. :-( Next time I do, I'll be sure to check that it actually starts @ boot though.

---

### Post by ajmorris on 2007-07-01
> **Amalekite said:**
> After installing netatalk on Kubuntu (Fiesty Fawn) as per instructions at

   <http://ubuntuforums.org/showpost.php?p=918060&postcount=16>

to build it with SSL (which allows for encrypted passwords), it works fine except for the minor irritation that it doesn't start automatically at boot itme.

This is really odd because I can start it manually from the command line with the invocation

   sudo /etc/init.d/netatalk start

I checked for the netatalk link in  /etc/rc2.d/  and confirmed its existence.  It points to the appropriate file in /etc/init.d:  S50netatalk -> ../init.d/netatalk.

So that should take care of that, right?  Then why don't the netatalk services start at boot time?

[I've looked through the output of dmesg and haven't found anything (no errors, but also no reference to netatalk at all).  It's as if the install script or some key link is missing.]

Is this one of those subtle differences between Debian & Ubuntu which I haven't quite picked up yet?  [All my (fairly limited) experience is with CLI-only servers running Debian.]

Is it an "upstart" thing?  I've heard that moves are afoot to change from the standard Sys V boot proceudre to this new-fangled upstart ;-)

I'd be grateful if anyone could shed some light on this... even just a pointer on how to proceed would be nice, because I'm not sure what to do next.

Thanks in advance.


Now i could be wrong here, but shouldn't it be starting from rc3.d not rc2.d? try changing it to rc3.d to see if that helps.

---

### Post by Amalekite on 2007-07-04
> **ajmorris said:**
> Now i could be wrong here, but shouldn't it be starting from rc3.d not rc2.d? try changing it to rc3.d to see if that helps.

I checked rc2.d, because the runlevel command returns "N 2", which I assume means that my system's normal state is at runlevel 2.  Is that not the default for Linux?

But all the rc?.d folders contain some link to netatalk... rc0.d, rc1.d and rc6.d have

   K50netatalk -> ../init.d/netatalk

whilst rc2.d, rc3.d, rc4.d and rc5.d have

   S50netatalk -> ../init.d/netatalk

and rcS.d contains nothing netatalk-related that I could see.

Also took a look at the upstart website, and apparently it keeps its stuff in /etc/event.d, but all I found there were files such as "rc2", which start with

# rc2 - runlevel 2 compatibility
#
# This task runs the old sysv-rc runlevel 2 ("multi-user") scripts.  It
# is usually started by the telinit compatibility wrapper.

so I guess that upstart is just configured for Sys V compatibility mode...

Is it possible that netatalk is being killed because it takes a long time to start up?

Is there some way I could "trace" the startup process in more detail than what dmesg provides?

Any pointers appreciated.

---

### Post by Amalekite on 2007-09-22
Just a quick update on this: because I haven't had to restart Kubuntu since I last posted, the netatalk startup problem has dropped way down on my list of irritations.

However, I've recently installed all sorts of new hardware in my PC, which obviously required (several) restarts.

The statistics are lean, because I've brought down my PC only 5 or 6 times, but it seems that netatalk has a (roughly) 50% chance of starting up on its own during boot.

Odd, huh?

Oh, yeah, I also found out how to observe the startup process in greater detail: simply edit  /boot/grub/menu.lst  to disable the splash screen... change the boot stanza to comment out the "splash" keyword, as I've done below:

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d43c1c94-9232-47c0-8fd4-50455bb41084 ro quiet# splash
initrd          /boot/initrd.img-2.6.20-16-generic
[...]

Now, at boot itme, I get the more familiar "scrolling text", which details all the services that are starting up, including error messages, etc.

But I discovered this trick fairly recently, and the last couple of times I restarted with the splash screen off, Netatalk came up OK.

Anyway, I'll keep working on it and post anything new I find.

---

### Post by Tommy on 2007-12-10
> **Amalekite said:**
> it seems that netatalk has a (roughly) 50% chance of starting up on its own during boot.

Howdy -- I'm connecting via netatalk for the first time in a few weeks. I upgraded to Ubuntu Gutsy 7.10 (about six weeks ago) and I thought it was working then. Today I was surprised it wasn't starting automatically. It did fine under Feisty 7.04 (as well as under Edgy 6.10 and Dapper 6.06).

I can start it manually with an /etc/init.d/netatalk start

I was first suspicious of the new(?) services tool in Gutsy -- netatalk does NOT appear in it, so I was thinking maybe Ubuntu has a new method of managing services, but I have not seen anything else saying it does. Everything seems to be in the "standard" rc.d files.

I will try disabling the boot splash to see if I see the same improvement you noted, but it's odd that I never noticed this under Feisty, where you first saw it. 

P.S.: I have never had to do anything special to INSTALL netatalk -- I installed the binaries with synaptic and edited the /etc/netatalk/ files, and it worked. The only other problem I've had is I can only use the cleartext password because I can't get any other authentication to work -- maybe that's the encryption issue in the installation link you mentioned ?? (in the top post)

---

### Post by Tommy on 2007-12-14
Since on careful consideration this seems a bit different from the other netatalk bugs, I opened bug #176472 [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/176472](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/176472)

Feel free to add any information you find there, too.

---

### Post by ocdude on 2008-05-28
Just want to see if a solution has been found to this yet. I've searched everywhere and nothing that is suggested seems to work. Is this something we're going to have to wait for a bugfix for?

---

### Post by Tommy on 2008-05-28
> **ocdude said:**
> Just want to see if a solution has been found to this yet. Not that I know of -- I was hoping someone who understands upstart would notice the bug I opened [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/176472](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/176472) and could comment. I am almost certain it's an upstart problem... but I don't understand upstart well enough to know what to look for.

edit: since I'm so certain, maybe I should point the bug at upstart... I'll dig around a little more tonight...

edit 2: I am certain now -- I installed sysvinit (to replace upstart) and netatalk started by itself on system boot. Subscribe to bug 176472 to find out what the upstart folks say about it... I might not remember to update this thread.

---

### Post by tsanga on 2008-07-03
Has anyone made any more headway on this?

Can I just put a line in /etc/rc.local and start it that way?

---

### Post by ocdude on 2008-07-03
The problem seems to have corrected itself on Hardy. Due to the questionable hardware I run Ubuntu on, I ended up having to reinstall everything, and the problem does not occur in Hardy through several restarts.

---

### Post by tsanga on 2008-07-03
Hmm...good for you - still sucks for me. :lolflag:

I have a 2 day old installation of Hardy and I'm running into this same issue of netatalk not starting until I do it manually.

How did you install netatalk on your new Hardy installation?

---

### Post by ocdude on 2008-07-03
I followed the guide here: [http://sethbc.org/2008/02/24/leopard-afp-and-the-hardy-heron/](http://sethbc.org/2008/02/24/leopard-afp-and-the-hardy-heron/)

Then used wajig to hold the package so Ubuntu wouldn't try to update it.

---

### Post by tsanga on 2008-07-03
Thanks...will have to give it another shot.  Last time when I followed damontimm.com's instructions (essentially the same as sethbc's), I ended up with a UAM failure (error -5002) to connect on the Leopard side.

---

### Post by tsanga on 2008-07-04
Tried it again...nope, netatalk still won't start on boot for me.

---

### Post by tsanga on 2008-07-05
Figured it out!

I had to disable "roaming mode" in NetworkAdmin.  Seems like something with roaming mode wasn't making eth0 available to netatalk at startup.  With it turned off, netatalk starts properly in the few times I've rebooted.

Reference:
[https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)

---

