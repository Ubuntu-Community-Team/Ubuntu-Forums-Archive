---
title: "new ipod classic 80gig music transfer"
date: 2007-09-09
forum: General Help
---

### Post by rlklee on 2007-09-09
I just brought home a new iPod 80 gig classic today and have been attempting to transfer music over to it.  It mounts fine, amarok connects to it fine, and it seems to transfer the files fine.  (BTW, I've tried all this in gtkpod and rhythmbox as well).  It also unmounts without a problem.  However, afterwards none of the music is showing up on the iPod, it claims its library is empty.  I do know for a fact that the data is there somewhere and the iPod itself shows that it has less space available.  When I reconnect to amarok or gtkpod or whatnot all the files are there as far as those programs are concerned.  I've been looking around for similar problems with other people but haven't found any.  Here is the relevant dmesg output:

[ 5073.904000] usb-storage: device found at 13
[ 5073.904000] usb-storage: waiting for device to settle before scanning
[ 5078.904000] usb-storage: device scan complete
[ 5078.912000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5078.912000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 5078.916000] sda: Write Protect is off
[ 5078.916000] sda: Mode Sense: 68 00 00 08
[ 5078.916000] sda: assuming drive cache: write through
[ 5078.916000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 5078.916000] sda: Write Protect is off
[ 5078.916000] sda: Mode Sense: 68 00 00 08
[ 5078.916000] sda: assuming drive cache: write through
[ 5078.916000]  sda: sda1

-Ryan

---

### Post by jnorthr on 2007-09-09
dmesg for my 1gb nano is almost identical to yours; my gtkpod appears to copy over everything too, there is no 'library' menu entry on the nano, just music,photos, songs,genres, extras,settings and no obvious issues but the music is dumped under 'music' on my nano.

---

### Post by rlklee on 2007-09-09
I didn't mean to suggest that there was a "library" menu entry, just that in Music -> Albums, Artists, etc. there is nothing showing up.

---

### Post by rlklee on 2007-09-09
Could this just be a problem of it being such a new device?  Only released 4 days ago now.  I have been trying to find other's experiences on linux with the new ipod lines, but haven't found anything.   Anyone?

---

### Post by nonewmsgs on 2007-09-09
> **rlklee said:**
> Could this just be a problem of it being such a new device?  Only released 4 days ago now.  I have been trying to find other's experiences on linux with the new ipod lines, but haven't found anything.   Anyone?

i have a 60gb one and i have never had a problem with it (ok well once it wasn't being detected and i had to reboot)

---

### Post by mmilburn on 2007-09-09
I have been unable to transfer anything with my machine as well.  I set the new device up on my friends Windows XP machine and transferred several songs.  When I had finished that, I plugged in the same iPod to my machine (Feisty) and transferred a few songs with Amarok (which just worked on my 60gb video).  When I unplugged the iPod I was unable to see any of the songs (even the ones from the Windows machine.)

---

### Post by sprinkles on 2007-09-09
> **nonewmsgs said:**
> i have a 60gb one and i have never had a problem with it (ok well once it wasn't being detected and i had to reboot)

The thread is referring to the new iPod Classics.

---

### Post by rlklee on 2007-09-10
Right: 80gig and 160, released Sept. 5.

---

### Post by dent_a on 2007-09-10
I am having the same problem,  sync music to the Ipod 80GB classic and no music is displayed.  when I rehook up the Ipod Rythmbox displays what is on the ipod and it can play them for the Ipod, same with Amarok.  I have GTKPOD and have the same issue.  As near as I can tell the new IPod uses some different database structure and it gets corrupt with libgtkpod (the libary set that allows for the syncing).
Hope this gets fixed soon cause I really do not like ITunes.
Also here is a link to the discussion on the error at the GTKPOD developer forum:

[http://sourceforge.net/mailarchive/forum.php?thread_name=12574654.post%40talk.nabble.com&forum_name=gtkpod-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=12574654.post%40talk.nabble.com&forum_name=gtkpod-devel)

---

### Post by rlklee on 2007-09-10
Have you heard anything anywhere about a possible workaround?  I must say, although understandable, this is very frustrating.  I don't own any windows machines w/ which to use iTunes.  Thanks for the link to the gtkpod thread.  It's at least encouraging that the problem has been recognized; I'd imagine a solution will not be long in coming.

-R

---

### Post by nwcowboysfan on 2007-09-14
Any news on this problem yet? I had just purchased a 30g Ipod that was working great with Amarok, but they gave me a free upgrade when they released their new product line. So now, like others in this post, my new 80g classic shows no music files present. Although it does show 10g of "other" file types. I have a ton of music files stored on a central linux server and am terrified what will happen if I try and point Itunes to this database. 

I know people are working on this and hope that a resolution comes before I have to go down the Itunes route! Just in case, does anyone know of any windows music file managers that don't have all the Itunes security "features"? I know there are a ton out there (anapod, media monkey, etc.), but curious if anyone has tried these.

---

### Post by UponFirstListen on 2007-09-14
via Digg: [http://ipodminusitunes.blogspot.com/](http://ipodminusitunes.blogspot.com/)

---

### Post by russo.mic on 2007-09-14
I think the problem your having is that Apple has once again resisted support for anything but i-Tunes and changed the way the database works.  Amarok or whatever else is trying to write a database that is probably just in a different place on the IPod itself.  I would think yoiu just need to give it some time for someone to write a new ipod driver.

---

### Post by UponFirstListen on 2007-09-16
via Digg (again): [http://amarok.kde.org/blog/archives/496-iPod-Classic-Will-Be-Supported.html](http://amarok.kde.org/blog/archives/496-iPod-Classic-Will-Be-Supported.html)

---

### Post by janko on 2007-09-19
Does anyone know if this workaround works also for new gen Nanos? I'm asking 'cause probably it's going to be my next buy.

Janko

---

### Post by StevieS on 2007-09-19
As far as I know there are people working on a fix for the problem which will eventually make it into libgpod.  The main problem is that in order to generate the checksum a "firewire ID" is needed and there is no easy way to get it automatically at the moment.

Once this problem is solved it will work for both iPod Classics and iPod Nanos, I have an iPod Classic working with gtkpod (using libgpod) and I have heard of people with Nanos that have managed to get these working too.  Currently the fix is far too fiddly and manual to make it into an official release, though. Hopefully it won't be too long before the firewire ID problem is resolved.

---

### Post by ryanxdurst on 2007-09-19
i just got my new ipod classic (80gb) yesterday and i'm having the same problem...     just to let you know.

---

### Post by Ladybug_309 on 2007-09-19
> **StevieS said:**
> As far as I know there are people working on a fix for the problem which will eventually make it into libgpod.  The main problem is that in order to generate the checksum a "firewire ID" is needed and there is no easy way to get it automatically at the moment.

Once this problem is solved it will work for both iPod Classics and iPod Nanos, I have an iPod Classic working with gtkpod (using libgpod) and I have heard of people with Nanos that have managed to get these working too.  Currently the fix is far too fiddly and manual to make it into an official release, though. Hopefully it won't be too long before the firewire ID problem is resolved.

Do you mind outlining exactly what you did to make your Classic work?  You are one of the few users who's said they've has success (and maybe I'm just missing something really simple...)

---

### Post by StevieS on 2007-09-19
I believe that there is a fix in the cvs version of GNUPod (not gtkpod) for this.  I haven't tried it myself, but people have reported that it is working.  

[http://www.gnu.org/software/gnupod/](http://www.gnu.org/software/gnupod/)

Remember that you will have to check out the source from cvs, found here

[http://cvs.savannah.gnu.org/viewvc/?root=gnupod](http://cvs.savannah.gnu.org/viewvc/?root=gnupod)

and build it yourselves.

As I say, I haven't tried it, so if you have any problems then I can outline my method, however, if you have trouble compiling GNUPod, then it is very unlikely that you will find my method any easier.

---

### Post by StevieS on 2007-09-19
Sorry, it turns out that GNUPod is actally a bunch of perl scripts, there are usage instructions in the FAQ file.  You will have to supply the fw guid which can be found by running

```
$ cat /proc/bus/usb/devices |grep -i serialnumber
```

and looking for the serial number that is 16 hex characters long.

If you manage to get this working then make sure you post here to let others know how you did it.

---

### Post by raijinsetsu on 2007-09-19
I read on /. that this was a purposeful design on Apple's part. Right now, you can only update the new iPods libraries through iTunes. So, until they come out with a way to hack the new hash system Apple is using, you're out of luck.

Personally: I'd return the iPod and get one of the many other non-restrictive MP3 players. :)

*edit*

guess it's already been cracked:
[http://amarok.kde.org/blog/archives/496-iPod-Classic-Will-Be-Supported.html](http://amarok.kde.org/blog/archives/496-iPod-Classic-Will-Be-Supported.html)

---

### Post by StevieS on 2007-09-19
Well if you look above you will see that it has already been resolved.  It's unlikely that this was designed to lock other apps out, it's a hash created for the iTunesDB file that means that iTunes, or any other app for that matter, can tell if the file has been corrupted.

There's been a lot of nonsense talked about this on a lot of sites, personally I no longer believe anything I read and try to make my own mind up.

---

### Post by raijinsetsu on 2007-09-19
Right... And unless the hash can be recreated, then you can't make an iTunes DB, and therefore can't use anything but iTunes to download to your iPod(and have it work).
The "new and improved" hash does not protect the iPod from corruption any better than the old one. It was simply meant to make it more difficult to reverse engineer the hash.
If the hash wasn't meant to keep third-parties out, then why didn't apple use a standard hash??

---

### Post by wonkycyber on 2007-09-27
yo, kids, I've compiled the libgpod svn, but I don't really know what to do from there.

according to the backdot site,  ineed to put the fwid into a sysinfoextended file?

but i see no such file
nor would i know where to put it

amarok doesn't seem to want to recognize the device at all
and says it isn't mounted
libgtkpod says there's no database

---

### Post by StevieS on 2007-09-29
To get the svn version of libgpod and gtkpod working correctly you need to find a file in iPod_Control/Device called SysInfo, if it doesn't exist then you should be able to create it yourself.  Add a line to this file containing your Firewire Guid as follows

```
FirewireGuid: XXXXXXXXXXXXXXXX
```

replacing the "X"s with your Firewire Guid.

If you need to find your Firewire Guid then connect the iPod and run this command

```
$ sudo lsusb -v | grep -i Serial
``` 

and look for the number which is 16 characters long.

Once you have done this when you try to sync an "error" mesage will appear displaying the SHA1 hash which has been written to your iPod.  Nothing else needs to be done here, just close gtkpod, eject your iPod and you should see all of the music on it.

Currently artwork is not supported, but I believe support is being worked on, so it should be added soon.  Keep checking the svn repository for updates.

---

### Post by neoaddict on 2007-10-01
Cover art is now semi-supported as of SVN revision 1714.

---

### Post by ChrisQ on 2007-10-02
[http://thefunkcorner.blogspot.com/](http://thefunkcorner.blogspot.com/)
packages available here^

---

### Post by kmccutcheon on 2007-10-31
Ok, I'm still a little new to this, I've read a few different posts about downloading this or that file, compiling, manually editing files, inserting hash mods, and all I've done is gotten frustrated.
I'm using 7.04 still, and could really use a guide that is a little more specific. I saw one, but it was for 7.10. I tried to follow it anyway, but I had dependency issues.
I am not interested in upgrading to 7.10 (yet...)

Thanks for the help!

---

### Post by jtreach on 2007-11-13
I have just spent close to an hour searching the web for a simple how-to on how to sync the new ipod classics in linux or ubuntu and I simply cannot find one. Seriously this player has been out a fair while now. How come there are absolutely no definitive guides.

Can someone do one? Pleeeeeeaaaaassssseeee.

Or can someone suggest a 50gb+ HDD player with video support, that syncs to linux, plays flac and looks as good as the iPod?

---

### Post by frame45 on 2007-11-14
> **rlklee said:**
> I just brought home a new iPod 80 gig classic today and have been attempting to transfer music over to it.  It mounts fine, amarok connects to it fine, and it seems to transfer the files fine.  (BTW, I've tried all this in gtkpod and rhythmbox as well).  It also unmounts without a problem.  However, afterwards none of the music is showing up on the iPod, it claims its library is empty.  I do know for a fact that the data is there somewhere and the iPod itself shows that it has less space available.  When I reconnect to amarok or gtkpod or whatnot all the files are there as far as those programs are concerned.  I've been looking around for similar problems with other people but haven't found any.  Here is the relevant dmesg output:

[ 5073.904000] usb-storage: device found at 13
[ 5073.904000] usb-storage: waiting for device to settle before scanning
[ 5078.904000] usb-storage: device scan complete
[ 5078.912000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5078.912000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 5078.916000] sda: Write Protect is off
[ 5078.916000] sda: Mode Sense: 68 00 00 08
[ 5078.916000] sda: assuming drive cache: write through
[ 5078.916000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 5078.916000] sda: Write Protect is off
[ 5078.916000] sda: Mode Sense: 68 00 00 08
[ 5078.916000] sda: assuming drive cache: write through
[ 5078.916000]  sda: sda1

-Ryan



I have an iPod Calssic (160GB) silver model and It has done exactly as your has. I had to reload around 100GB worth of music and movies after i restored it using iTunes in WinXP. So I haven't want to even plug it into Linux again.

Does anyone know how to fix this?? Also is there a program out there that will play music and videos from a library like iTunes?? Rythmbox and Banshee won't play videos for me. 

I am running 7.10

---

### Post by exodunix on 2007-11-26
> **frame45 said:**
> I have an iPod Calssic (160GB) silver model and It has done exactly as your has. I had to reload around 100GB worth of music and movies after i restored it using iTunes in WinXP. So I haven't want to even plug it into Linux again.

Does anyone know how to fix this?? Also is there a program out there that will play music and videos from a library like iTunes?? Rythmbox and Banshee won't play videos for me. 

I am running 7.10
same thing happened to me today. good thing i still have a computer with windows around. my comp only has ubuntu, so i guess i would have been screwed..

---

### Post by djdjules on 2007-12-07
Is the fix going to work with Feisty?
I understand that Amarok 1.4.8 is necesary along with libgpod 0.6.0
Will there be a release of Amarok 1.4.8 in the Feisty repos?

I got that info from:
[http://amarok.kde.org/wiki/Media_Device:IPod#Supported_Devices](http://amarok.kde.org/wiki/Media_Device:IPod#Supported_Devices)

---

