---
title: "Upgrade evolution/ximian exchange connector"
date: 2005-06-17
forum: General Help
---

### Post by RikoW on 2005-06-17
Dear all,

I recently moved from Suse to Ubuntu and have to say, I like it very much and I'm quite impressed by the developments, which have happened since the (fairly) old version of Suse I was running. My question might be related to the fact that I'm still not very familiar with agt-get etc.

Ubuntu 5.04 comes with evolution-exchange 2.2.1cvs, which is not the current stable one from Novel. I have problems connecting to our Exchange Server which I suspect is due to a bug (found a bug report which goes into that direction). So, I'm looking for a way to upgrade evolution/evolution-exchange to a higher version, however I'm not able to find a debian package for it on the mirrors I tried.

I did add new repositories to sources.list, for example the backports:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

also tried other repositories which I found mentioned, but whenever I updated sources.list, ran 
     apt-get update

and searched with synaptic I never found a more recent evolution package.

Am I missing something?

Thanks and cheers,
                 Riko

---

### Post by RikoW on 2005-06-17
Hi again,

I figured it out myself, so I thought I share it with everybody. I added the *debian* repositories to my *sources.lis*t file and commented all *hoary* repositories out:

[I]deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) testing main contrib non-free
[/I]

after running *apt-get update* I started synaptic again. Under *Settings -> Preferences -> Distribution* I can select *Prefer version from* a particular distribution, here *stable, unstable, testing*. Doing that, I could check which versions of evolution and ximian-connector were included.

I removed the installed (hoary) version of the two packages and then installed the desired one from the debian repositories. I actually downgraded to 2.04 since I knew that one works.

After doing that, I locked the package versions (*Package -> Lock Version*) to avoid a upgrade after going back to the hoary repositories.

I hope, I didn't break anything in doing that ... so far no indication, though  O:) 

Are there any consequences I should worry about, when a new Ubuntu release comes out and I want to upgrade?

Cheers,

      Riko

---

### Post by ounn on 2005-06-19
Hi.

I also had a problem with the default hoary version of evolution. Always crash with some kind of mails, i think it was because something related with the caracter encoding in html mails.
Yesterday i add breezy repositories to synaptic and upgrade evolution to version 2.3.3. Had no problems yet :p

Forgot to say : My problems with evolution are gone. \\:D/    

ounn

---

### Post by RikoW on 2005-06-20
I tried so many things to get evo+connector to work, I don't remember exactly if I also trued an upgrade! :)
However, since your problem was a different one than mine, I'm reluctant to screw around with it again. I think, for now I will stick with the 2.0.4 package which runs quite reliably. Nevertheless, it's interesting to know, that the upgrade from Breezy works without problems.

Cheers,
                Riko

---

