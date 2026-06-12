---
title: "reccomendations for server-client setup"
date: 2007-01-01
forum: General Help
---

### Post by thechris on 2007-01-01
==background (not overly important)==
Now that my long standing curse with hardware has been lifted and my fileserver stands partially built, I am looking to make a choice between gentoo and ubuntu.

In the past, i'd largely used gentoo, which is a very turbulent distro at times.  overall, i liked that gentoo actually had packages that I used, and that the packages typically worked.  stability was overall good.  

I had also tried various Ubuntu and Kubuntu's in the past with limited sucess.  generally, the installer would have issues with hardware and software.  typically the system would crash at the login screen after install, and i would have critical virtual packages missing.  X11 was typically less stable as well, possibly due to my typical use.


So i'd always go back to gentoo.  but compiling packages and updates were tedious, and often updates would fail or break other packages.  finally i gave up updates, leading to my 1 year old un-updated system.  I don't mind this too much, but someday it would be nice to update without hours of hassel.


==Requirements==
I am looking for an easy to update system.  one that can be cleanly updated every 6-12 months.  I don't want the system to complain about missing packages, packages that have the wrong settings, ect...  i don't want to reconfigure apache on every update, nor do I want it to suddenly break.

this applies to both my server and my desktop.

the system should have the software I use, and shouldn't break on each update. 

==Desktop==
for the desktop, i prefer KDE.  At times I had been reccomeneded to install ubuntu, then apt-get KDE from there.

the desktop is a 64-bit x86 box.  Is there any reason to go with amd64 vs i386 distrobutions from a software standpoint?  I am aware some 3rd party binaries are 32-bit only, but beyond these, is there a lack of packages for amd64 in the reps?

My main uses are web surfing, mathmatical simulation, media viewing, and games.  I am looking primarily for:
firefox/opera, octave+koctave, geda, pcb, gcc, flex/bison, python, mplayer/vlc, cedega, and kgtk or equivilent.

Do suitable packages exist in the main package line, or will I be forced to use 3rd party reps?  how stable are 3rd party reps?

I am mainly trying to determine if I should get ubuntu or kubuntu, and if packages for my uses exist.  

==Server==
The server also has some uses and packages that I'd want, as well as some requirements.  I need to be able to use software RAID5 for my main array (960GB).  I need xfs support as there is data on the array at this time, on an existing XFS partition.

The server needs apache, sql, svn, dav, mediawiki, nfs, and rsync.  I would guess that this shouldn't be too hard to get packages for.

my main question is:  should I get the LTS distro, or the current distro? 



Thank you for any help you might provide.  feel free to give me any insights or suggestions as well.

---

### Post by adaptr on 2007-01-01
> **thechris said:**
> ==background (not overly important)==
Now that my long standing curse with hardware has been lifted and my fileserver stands partially built, I am looking to make a choice between gentoo and ubuntu.

<gentoo-ubuntu wars snipped>

==Requirements==
I am looking for an easy to update system. 
Ubuntu.

>  one that can be cleanly updated every 6-12 months.You erm.. don't - you *update* security patches and bugfixes as soon and as often as needed, and you **upgrade** - which may be what you actually meant - when it is both prudent and safe to do so.
If you install the Ubuntu Server version, get 6.06LTS (Long Term Support); this will be supported for a minimum of 3 years - which is the way a server should be maintained.

> I don't want the system to complain about missing packages, packages that have the wrong settings, ect...  i don't want to reconfigure apache on every update, nor do I want it to suddenly break.Then you have to make intelligent decisions about when or whether to upgrade a certain package - again, we are talking about **upgrading** here; updates generally do not introduce new versions of software.

> ==Desktop==
for the desktop, i prefer KDE.  At times I had been reccomeneded to install ubuntu, then apt-get KDE from there.Since **kubuntu** has been around for quite some time now, I cannot imagine why anybody would recommend that.

>  the desktop is a 64-bit x86 box.  Is there any reason to go with amd64 vs i386 distrobutions from a software standpoint?  There are many reasons **not** to use amd64 - especially if you intend to do all the multimedia-things one might be used to on Windows.

> I am aware some 3rd party binaries are 32-bit only, but beyond these, is there a lack of packages for amd64 in the reps?Erm.. yes.

>  My main uses are web surfing, mathmatical simulation, media viewing, and games.  I am looking primarily for:
firefox/opera, octave+koctave, geda, pcb, gcc, flex/bison, python, mplayer/vlc, cedega, and kgtk or equivilent.

Do suitable packages exist in the main package line, or will I be forced to use 3rd party reps?  how stable are 3rd party reps?Yes, a great many packages exist, nobody forces you to use anything, many 3rd party repositories are of generally high quality.
I challenge you to find any globally used applications that Debian offers that are not available for Ubuntu.
It's getting better every day, too :)

> I am mainly trying to determine if I should get ubuntu or kubuntu, and if packages for my uses exist.If you want KDE, then obviously you want kubuntu - what is the problem?
The repositories are exactly the same.
**[http://packages.ubuntu.com](http://packages.ubuntu.com)** answers any and all questions about package availability.

>  ==Server==
The server also has some uses and packages that I'd want, as well as some requirements.  I need to be able to use software RAID5 for my main array (960GB).  I need xfs support as there is data on the array at this time, on an existing XFS partition.Not a problem.

>  The server needs apache, sql, svn, dav, mediawiki, nfs, and rsync.  I would guess that this shouldn't be too hard to get packages for.
You sound like you think you're asking difficult questions, but any distribution I've used over the last year or 2 had absolutely no issues with any of the above.

> my main question is:  should I get the LTS distro, or the current distro? 
Ubuntu server 6.06LTS.
Period.

> Thank you for any help you might provide.  feel free to give me any insights or suggestions as well.I'm not sure... many of the things you say about Gentoo (which is dying) and Ubuntu (which is not) in the first paragraph suggest you have not tried either in at least a year.. a lot has changed.

I have run Gentoo servers for about 2 years, and am now in the process of moving everything over to Ubuntu, since that *just works*, and does not require me to fiddle with arcane system scripts on a daily basis - [B]without getting anything in return.
[/B]Really, Gentoo has done in for me in a big way - too complex, don't have the time, doesn't put me all that far ahead of the curvefor all its technical prowess.

---

### Post by thechris on 2007-01-01
i wasn't thinking the questions were overly difficult.  just looking for some advice on specifics relating to ubuntu.  

i have not tried ubuntu or gentoo for about 1 year.  a year ago i put gentoo on my desktop, and decided that it was working, and from there I just left things run.  I had more important schoolwork to do and didn't want to risk breaking my computer.  now that I have a job, I have largely lost the desire to break my system on a regular basis.

i wasn't expecting issues with the server software, but i've had issue with software availability in debian/ubuntu in the past.  I had tried to set up mythtv on ubunutu a while back with no luck -- no packages and the 3rd party repositories were broken.

i guess i'll use "upgrade" over "update" on these forums.

---

### Post by thechris on 2007-01-03
ok, finally got kubuntu-6.10 on my desktop.  not sure if it'll last or not.  so far i've found:
1.)  the gui-installer has bugs.  specifically, you cannot put / on xfs.  you _can_, but it just tells you to put /boot on non-xfs.  unfortunantly, it doesn't detect if /boot is on non-xfs, and the install stops.  further, there is no reason not to put /boot on xfs.  reiserfs wasn't even listed as an option...
2.)  no packages are supported.  everything is in universe and multiverse.
3.)  i've already had to seek out packages that aren't in multiverse/universe.
4.)  kgtk and vlc don't mix.
5.)  adept is still buggy.

i'm somewhat worried from the warning that the majority of packages I will use are in universe/multiverse.

so far stability is fine.  i'm not sure the lack of packages is that big of a deal.  i'm debating going all gentoo or all kubuntu about equally at this point.  portage is turbulent and slow, but i don't have to re-learn anything, and the packages i use are in portage already.  kubuntu is promising, but i'm a huge fan of having distro support for all my packages.

---

