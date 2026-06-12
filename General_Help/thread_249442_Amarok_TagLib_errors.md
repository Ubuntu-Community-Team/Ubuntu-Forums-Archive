---
title: "Amarok TagLib errors"
date: 2006-09-02
forum: General Help
---

### Post by brentrussell on 2006-09-02
I tried to setup my Amrok collection to a maped network drive. It worked fine for the "Sinle_files" folder but when I did it to another mapped folder I get this error message:

Sorry, the collection Scan was aborted, since too many problems were encountered.
Advice: A common source for this problem is a broken 'TagLib' package on your computer. Replacing this package may help fixing the issue.
The Following files caused problems:
/media/music/Full Albums/Doors/Essential Rarities/Doors - Break on Through.mp3
/media/music/Full Albums/Eric Clapton/Slowhand/Eric Clapton - Lay Down Sally.mp3


I removed those files and it just encountered errors with 2 more files, then 2 more, then 2 more and so on. So I searched around and could not find TagLib but I did find libtag. libtag is used by amarok, gnome desktop and many more so I did:
sudo apt-get --reinstall install libtag
which recomended
sudo apt-get --reinstall install libtag1c2a

Still no results.
Any other ideas from the community?

---

### Post by brentrussell on 2006-09-02
I have since reinstalled Amarok but I am still experiencing the same issues

---

### Post by fraco on 2006-09-04
for what it's worth, I have the same problem. 

I also tried the reinstall of taglib. Apparantly, Amarok 1.4.x had some problems with the collection building crashing Amarok, so I suspect that the program now just catches all crashes of that process and just gives a generic problem report.
It may have nothing to do with Taglib...

There must be something out of the ordinary with our setup, because  indeed it is hard to find anything on google about this.

I just reread your mail. My collection is also on a (samba) network drive. Could that be the issue? I'm going to move my files over to the local hard drive and see if that makes a difference. I don't see how it can make a difference...


regards

---

### Post by [h2o] on 2006-09-04
I have the same issue.
Downgrading libtag to 1.4.3 and amarok/amarok-xine to 1.3.9 solved it so now I can at least listen to my music.

---

### Post by fraco on 2006-09-05
I wonder if it has anything to do with this:
[http://amarok.kde.org/amarokwiki/index.php/Samba](http://amarok.kde.org/amarokwiki/index.php/Samba)

---

### Post by bluenova on 2006-09-05
If you feel up to it, I strongly recommend installing amarok from source. There are lots of things that don't work in the kubuntu version, one thing being automatic tagging. It's really not so hard to install from source, especially if you've already installed it via the package as most of the dependencies will already be met.

Check it out here:
[http://amarok.kde.org/wiki/Installation_HowTo#Building_From_Source](http://amarok.kde.org/wiki/Installation_HowTo#Building_From_Source)

:edit:
The only thing you need to do differntly is where it says:
```

    *  cd amarok-x.y.z
    * ./configure --prefix=`kde-config --prefix`
    * make
    * su -c "make install" 

```

Do this instead:

```

    *  cd amarok-x.y.z
    * ./configure --prefix=`kde-config --prefix`
    * sudo make
    * sudo checkinstall 

```

---

### Post by bernied on 2006-09-05
For what it's worth, I had amarok 1.4.1 running flawlessly under kubuntu, but when I upgraded to 1.4.2 (backports), I had the same issue with libtag. It stops updating at 19%, so I moved some music folders, then it stopped at 30%, so I moved some more, then it stopped at 58% and I got fed up.

I also use a samba share for my collection, and have had some trouble accessing it while trying to update the collection db - anything that tries to access the share freezes (konqeror, terminal). 

I also could find nothing from googling, and was waiting for this to appear in the ubuntu forums, as I thought it must be specific to ubuntu, but maybe it's about smbfs.

I will try doing a complete removal, then build from source. Are there any dependencies (like xine) that I should do the same with?

---

### Post by fraco on 2006-09-05
> **bluenova said:**
>  especially if you've already installed it via the package as most of the dependencies will already be met.


just one or two missing dependencies: 
```
sudo apt-get install ruby1.8-dev libmysqlclient14-dev libtunepimp3-dev libtunepimp3-mp3 
sudo apt-get install libtag1-dev libtag-dev libxine-dev kdelibs4-dev checkinstall libqt3-mt-dev libvisual-0.4-plugins 
sudo apt-get install libvisual-0.4-dev postgresql-dev xmms-dev  helix-player libsdl-gfx1.2-dev 

``` 
ok, some of it is optional, but I built with some optional stuff extra :
./configure --prefix=`kde-config --prefix` --enable-postgresql --enable-mysql  --with-helix 

at least half of the extra libraries are mandatory...

the bad news is ... it doesn't fix the failing collection scan

fraco

---

### Post by disciple on 2006-09-05
i got this problem when i switched over to suse.. under kubuntu, never had it..   

tried all sorts of things to remedy , even compiling taglib from scratch ..

funnily enough, when i was googling, i found no one with the same problem .. now i happen upon this thread.. :-)

anyhow, what i did was compile amarok 1.4.3 from source.. apparently, 1.4.3 changes the error threshold from 2 to 20 ( or something so) , so instead of crashing  every 2 failures, it stops at  20, and leaves the collection built so far instead of exiting blank)

( which is better than every 2.. because now i have a better idea of how many mp3s i have to delete, instead of being frustrated by th thought of it goin on ad infinitum)

anyhow, packages for 1.4.3 probably goin to be on kubuntu.org now.. give it a try

---

### Post by cleentrax on 2006-09-05
> **fraco said:**
> I wonder if it has anything to do with this:
[http://amarok.kde.org/amarokwiki/index.php/Samba](http://amarok.kde.org/amarokwiki/index.php/Samba)

fraco, thank you for that link! I was going crazy trying to figure out why Amarok wouldn't index the music on my server.

EDIT: Well, still thanks for the link, but it didn't actually make any difference in the end. Amarok still won't load my music library.

---

### Post by xenoNfluX on 2006-09-07
It looks like I'm in the same boat here. I'm in Ubuntu Dapper and trying to build a collection across a SMB share. I noted that link to a different mount command, but that did not help.

I know the files its failing on are valid files that do play in other players. I've built the same collection within Rhythmbox and Banshee with no problems, so I'm confused as to why Amarok would fail. At any rate, I'm not picky at the moment, so I'll just use Rhythmbox... but I would like to eventually use Amarok as it does appear to be a nicer player.

Any help would be appreciated.

---

### Post by bernied on 2006-09-08
> **xenoNfluX said:**
> I know the files its failing on are valid files that do play in other players.
Not just on other players, also on previous versions of amarok. Mine was superb until the upgrade to 1.4.2 broke it. Still going to try a manual install. Maybe tonight.

Anyone got any other solutions to this? Do we know whether it's a ubuntu specific issue?

---

### Post by xenoNfluX on 2006-09-08
> **bernied said:**
> Not just on other players, also on previous versions of amarok. Mine was superb until the upgrade to 1.4.2 broke it. Still going to try a manual install. Maybe tonight.

Anyone got any other solutions to this? Do we know whether it's a ubuntu specific issue?

Yeah, you're right. For giggles, I forced version on amarok to 1.3.9 in Synaptic, but that didn't help much. It scanned the collection just fine, but after it was done, nothing showed up. I didn't really care to use the older version, though... no last.fm support from what I can tell.

---

### Post by gnoshi on 2006-09-09
By forcing taglib to downgrade to 1.4.3 and upgrading to Amarok 1.4.3, suddenly my tags started to read again, and my collection (on a cifs share) indexed correctly again.

Hurrah!

Still, if you want something more gnomish, it is worth checking out [http://listengnome.free.fr/](http://listengnome.free.fr/)

It isn't there yet methinks but I do like it.

UPDATE: I lied - I realised I missed some of my collection, and when indexing that section of the collection, I got the dreaded '20 error' problem.
The oddity is that those files will load fine if manually selected from the file system - all the tags load, etc. Very odd.

---

### Post by Thund3rstruck on 2006-09-09
Yup, I'm in the same boat as well. I have 70GB on a network share. For the last several months I have been using XBMC (XBOX Media Center) exclusivly but this morning I wanted to stream upstairs to my laptop. Started up amarok and suddenly my database was missing. Rescanning it only serves to dump the tag error. 

I have tried everything imaginable, re-install, remove install, build from source, downgrade, updgrade, flush ~.kde/shared/apps/amarok, and nothing works. Its too bad, I always considered amarok the 'killer app' for linux.

---

### Post by geearf on 2006-09-09
I have the same problem here with 1.4.2 and 1.4.3 in edgy :(

No samba or any other thing in the middle though.

Also anyone knows about the moodbar thing ? it seems it's not fully installed.

---

### Post by geearf on 2006-09-09
I have posted a bug report, but still no answer :(

[https://launchpad.net/distros/ubuntu/+source/amarok/+bug/58613](https://launchpad.net/distros/ubuntu/+source/amarok/+bug/58613)

---

### Post by fraco on 2006-09-14
the issue is discussed on the amarok forums too:
[http://amarok.kde.org/forum/index.php/topic,12916.0.html](http://amarok.kde.org/forum/index.php/topic,12916.0.html)

One interesting suggestion there is to scan the whole collection in small incremental pieces... I'm going to try this and see if it is a workaround

fraco

---

### Post by jms830 on 2006-09-19
I have one folder full of all my artists that I asked amarok to build a collection for, but I was getting the same error of this thread.  So today I went through and checked individual artists, adding them in parts.  So I would check all my artists A through G, and then do Rescan Collection. Then I would continue checking H-M (so that A through M were checked) and click Rescan Collection again. Then I checked N through S, Rescan Collection, then all my artists checked, Rescan Collection.  Then finally, I just checked the folder that contained all of these artists (as I originally wanted to do) and did Rescan Collection.  It took a long time, but for some reason this worked for me.

---

### Post by geearf on 2006-09-20
Well thanks to you I just tried doing that, and I have about everything in my collection still some files are missing but that's okay.

Thanks

---

### Post by fraco on 2006-09-25
switching from samba -> NFS fixed the issue for me. 
As a bonus, NFS is two times faster on the NSLU2 I use in terms of transfer speeds...

---

### Post by web250 on 2006-09-29
That Listen program is really nice. Looks like Rhythmbox, features like Amarok...and i'm using the beta version (.5.1 i think) and it is a little slow...but it works.

---

### Post by nfoti on 2006-09-30
Switching to NFS doesn't solve the problem in my eyes. I have multiple computers in my home, Macs, win boxes, and Dapper and Breezy machines. I don't want to hassle with switching servers and getting NFS support up on the other machines. 
My machine running breezy and amarok 1.3 has no problems building a collection off of my samba shares. The original build of amarok 1.4 on a dapper machine also had no problems. What gives - the last time I checked the bug report thread on the amarok website they claimed to have solved the problem in 1.4.3 - no such luck.

Problem-
Amarok 1.4.3 still doesn't build a collection from my smbfs share. It will build in small increments but it takes forever and a day and my collection is way too large to sit through that. 

Any suggestions to fix the problem?

---

