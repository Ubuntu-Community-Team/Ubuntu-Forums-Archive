---
title: "Help Stupid Mistake"
date: 2007-06-11
forum: General Help
---

### Post by borahshadow on 2007-06-11
Help I just accidently did a ```
sudo rm -r /bin
``` :cry:

I was trying to delete a directory named bin in a different foler and accidently typed /bin instead I don't know what to do from what I have read on google just now when you rm something its gone no easy way to undelete it:x:!::cry:

So how could I recover /bin?
What all is stored in bin does /bin store most programs or just the basic ones like cp rm mv ls etc
If it only stores the basic ones can I just copy a /bin from one of my other ubuntu boxes

I am running Feisty and have another Feisty box available and an edgy box

I just barely installed this and would like to not have to reinstall but I can backup ard reinstall if I HAVE to

I'm still in shock that I made such a Noobish mistake:(
I feel totally lost:cry:
Please help

---

### Post by merlinus on 2007-06-11
My /bin has 104 items.

Probably best to backup data, and re-install.

The power of sudo....

FWIW, did you look in your trash folder, and root's as well?

-merlin

---

### Post by borahshadow on 2007-06-11
from what I read rm does not use trash at all it deletes it completely
I looked at my other feisty machine's /bin and all the programs looked generic(like not a program that could be installed or removed) It looks like I can just copy over my /bin from that comp that thing I worried about was if bin held all the programs that I installed (through synaptic) but everything seems like generic unix programs ls mv cp chmod su login etc
So I think I'll try that

---

### Post by tgalati4 on 2007-06-11
If you haven't rebooted yet (don't) and you have networking to the other Feisty machine, there should be no problem copying the files from one machine to another.  Print out the list of /bin on the other machine so you can see what commands you may have problems with.

Good luck.

---

### Post by borahshadow on 2007-06-12
I was smart enough to not reboot and also not close anything (just incase I coulden't reopen it because I didn;t know what binaries wher in /bin) how would you reccomend copying them temporaraly sharing /bin with samba or nfs or would you put them in like a tar archive and burn them to cd/dvd?

---

### Post by borahshadow on 2007-06-12
ok I copied it over and made sure the permissions were correct I just hope when I reboot everything works

---

### Post by tgalati4 on 2007-06-12
I wouldn't reboot yet.  I would keep your system running as long as practical.  Wait until you have an update that forces your reboot.

That way you can see if anything is broken or acting weird in your current runtime environment.  That will give you a clue if a reinstall is necessary.

I use rm -ri .  The -i is the interactive or inquiry switch and it will ask you "Do you really want to delete /bin?"  That gives you a few seconds to think about it.

---

### Post by borahshadow on 2007-06-12
well I did decide to just use it for a while before I rebooted (I had not seen your post yet) which turned out to be a good thing I had copide the files with konqueror and using the smb: protocol I had not mounted them and it turns out that several of the files in /bin are sym links and the smb: protocol copied them not as a link but the thing that they link to
so I mounted it (with cifs not smbfs as it would do the same thing) and copied it again over writing the old /bin

I noticed something was wierd when I tried to do a kdesu konqueror I was getting wierd errors and had to risk a sudo konqueror
I also noticed that acroread(adobe acrobat reader) would not load 
after I recopied using cifs which preserver the sym links everything worked fine
I gtg2 bed I'll leave it on over night and try to keep it on for as long as possible but it is my laptop so I will have to shut it down soon

---

### Post by tgalati4 on 2007-06-12
I usually put my laptop on standby, so I get uptimes of several months at a time before I really need to reboot.  Good tip on the symbolic links, that's critical.  You can always reinstall Acrobat Reader using the commercial installer that they provide.  It will (hopefully) put all the required files in the right place.

As you have discovered, real Linux learning occurs when you break stuff.

---

### Post by borahshadow on 2007-06-12
Well unfortunately suspend and hybernate don't work on my laptop (averatec 2370)
Acrobat Reader works fine after I fixed the sym links

My laptop actually hybernated itself overnight (got to figure out why) so that forced me to reboot and everything seemed to work fine I didn't have anything strange so I think I'm good to go
> As you have discovered, real Linux learning occurs when you break stuff.
So true I've actually used linux for probably 2 years now (I'm not sure exactly how long)
I started on debian dual booting and just 8 months ago I trashed my windows partition along with a move to (k)ubuntu and then 6 months ago I got this laptop

especially on debian I don't think I could cont that number of times I broke things

Thanks for all your help

---

