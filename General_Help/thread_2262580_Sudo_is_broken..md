---
title: "Sudo is broken."
date: 2015-01-25
forum: General Help
---

### Post by akel3 on 2015-01-25
So I updated to 14.04.1, and I can't execute sudo/su (It gives me a Fragment Violation error) so I supose the binary is damaged, and everything that depends on it fails as well.
So how do I replace the binary with a new one without access to root permisions?
Please don't tell me to reinstall.

---

### Post by akel3 on 2015-01-25
[IMG]http://i.imgur.com/cLfAl8C.png[/IMG]
This isn't good isn't it.

---

### Post by nerdtron on 2015-01-25
From which version did you upgrade? Does replacing the binary even works? You can try booting a liveCD and replace (copy and paste) the file in question (if you know which file to replace).

---

### Post by QIII on 2015-01-26
I suspect that not being able to use sudo may be the very least of your problems.

Please, when you answer nerdtron's questions, also include the method by which you attempted to upgrade.

---

### Post by akel3 on 2015-01-26
> From which version did you upgrade?
From precise
 > Does replacing the binary even  works?
I don't think I can replace the sudo binary without superuser rights. I downloaded a deb for the version of sudo that works with my version of libc6, but I can't use it because it doesn't have superuser rights itself. I got the link to the updated libc6, but it tells me that like half the things I have installed will be incompatible with it. Maybe I could download it, use dkpg with a root recuperation console telling it to not uninstall packages broken by it, and then boot up normally and use sudo to update everything else?
 > You can try booting a liveCD and replace (copy and paste) the  file in question (if you know which file to replace).
My computer doesn't have a cdtray, and I don't have a pendrive or another computer to net-boot it at hand at the moment.
> Please, when you answer nerdtron's questions, also include the method by which you attempted to upgrade.
do-release-upgrade.
The only weird thing I did with this was using CTRL+ALT+F1 to start a tty and do it without the fear of clossing my console by mistake, as I am irrationaly scared of doing that every time I do anything important. Then when it was downloading the last deb (qBittorrent I think) I interrupted it and started it again in a normal console and let it finish that download so I could check the setup messages (If I wanted to finish X daemon or wanted to keep the old configuration of another one, you know what I mean) comfortably.
When it was installing the packages, it gave me some errors related to QT I think that I now realise that I should have saved, it was the same error again and again about qpixbuffer or something like that. When it finished upgrading, it just stayed there and I had to manually reset the computer (The shutdown menu had all the characters as the small squares of unrecognised character, by the way).
I guess that the packages where dkpg failed are the ones that would be uninstalled if I update libc6 manually?

---

### Post by nerdtron on 2015-01-26
I really have no idea. 12.04 and 14.04  are different versions. I wouldn't even try to do an in place upgrade my work desktop much more on a server.  (always do tests before upgrades)

---

### Post by akel3 on 2015-01-26
> 12.04 and 14.04  are different version. I wouldn't even try to do an in  place upgrade my work desktops.
I updated from 10 to 12 without any problem
 > much more on a server.
I am on a desktop computer.
  > (always do tests  before upgrades)
What kind of tests do you recomend? I don't really think I there is a test for "Everything goes kaput because".
And I just found out I can't mount one of my harddrives because I aparently need root access to that. Great.

---

### Post by ian-weisser on 2015-01-26
I suspect you will find *lots* of stuff broken and inaccessible.
Is your data backed up?
How much time do you want to invest trying to fix it before you are willing to reinstall? Couple hours? Couple days?

---

### Post by akel3 on 2015-01-26
Taking into account that I have no way to reinstall right now, I will take as long as it takes me to buy a good quality pendrive.

---

### Post by MeanRoy on 2015-01-26
> I updated from 10 to 12 without any problem

I was advised to do a clean install and did, but wanted to try it anyway.

I didn't get any error messages but it was actually messed up.
I only found out when I continued and upgraded to 14.04, at which point like you, I found that some fundamental utilities didn't work.

The problem is that 10 and 12 are both obsolete and unsupported.

I recommend installing an LTS version alongside your broken system after you get a pendrive or whatever.

This will *probably* allow you to migrate your data, mail, etc. to the new installation.

Worked for me, though it's kind of a pain locating everything.

-----------------------
as noted by deadflowr 12 is still supported, nonetheless it didn't work well for me.

---

### Post by deadflowr on 2015-01-26
> **MeanRoy said:**
> 

The problem is that 10 and 12 are both obsolete and unsupported.

I recommend installing an LTS version alongside your broken system after you get a pendrive or whatever.



Both  10.04 and 12.04 are LTS and still supported, though 10.04 is only supported on servers.
12.04 is supported until  April 2017.

It is unclear whether or not the OP can boot into a recovery mode session from the grub boot menu selection.
If possible, you can try to enable networking and when/if you do so, you access the root shell and perform any maintenance you need without sudo.

Just a thought.
(And I am not clear if this is something you have tried...)

---

### Post by akel3 on 2015-01-26
I can start un recovery mode, it gives me errors from freedesktop that I think are related to the monitor (freedesktop@org[mumbojumbo][Number that increases by one until it reaches around a thousand]) but it works. When I try to enable the network in the options, it shows me a comand in fstab and just stays there forever until I restart. I can get into the console just fine, but it doesn't seem to have root rights and sudo also gives me the fragmentation error there.
If I put sudo alone, it does give me the help prompt, but that's as far as it works.

EDIT:OH! and last night I was restarting from the recovery console and in the shutdown log I saw "Systemd login system [[COLOR=#ff0000]FAIL[/COLOR]]" (Or something like that, I don't have exactly a photographic memory) nearly at the start, it was the second item on the list. I haven't seen it appear again, tho.

---

### Post by deadflowr on 2015-01-26
the root shell in recovery mode is just that a root shell.
The problem is it mounts read-only.
When/if you try enabling the networking option, it automatically remounts it read/write.
if networking isn't possible, you can still remount it from the root shell option with
```
mount -o rw,remount /
```
No sudo needed in a root shell.

Though I do not know how helpful that would be...

---

### Post by akel3 on 2015-01-26
> mount -o rw,remount /

Oooh I feel dumb now, this sounds like something that must have appeared in at least half the pages I've visited by now.
Thanks for having patience with my lack of experience, really. I'll save that on a txt to have it at hand and restart in recovery mode again.

EDIT:Well, done, I have full superuser rights on the reocovery console.
I can't seem to manage to actualy connect to internet from there even when iwtools seems like a stupidly easy tool to use so I am downloading the broken packages using a synaptic script, how could I tell apt-get to fix the packages and use those deb files instead of trying to download them? there doesn't seem to be a way to do that in the man page.
Also, I can't help but note than out of the 75 packages downloaded by [the script]("http://pastebin.com/4En66HT3"), none of them is the libc6 update.
EDIT 2:I just noted "wget -c [http://ar.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/multiarch-support_2.19-0ubuntu6.5_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/multiarch-support_2.19-0ubuntu6.5_i386.deb)", that's libc6, right?

---

