---
title: "iPhone and Ubuntu"
date: 2007-10-23
forum: General Help
---

### Post by Terc on 2007-10-23
Edit: We have a Wiki!
Go here:[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

also, for information about sycing iPods with Windows VMware guests go here:[http://ubuntuforums.org/showthread.php?t=614208](http://ubuntuforums.org/showthread.php?t=614208)


Original Post:
I've just ditched Windows and moved to Linux this past weekend, I'm loving Ubuntu, and after fighting with audio, I have just one more issue to resolve... iPhone syncing with Banshee [Edit: Don't use Banshee, it wont work with the method discussed on this thread].  Any advice/help would be greatly appreciated.

I just spent about 3 hours learning to mount my iPhone under Ubuntu by using sshfs.  While this *sort of* works with gtkpod, I was hoping someone could point me in the right direction on getting it working with Banshee (they use their own iPod connector) They use [libipoddevice]("http://banshee-project.org/Subprojects/Libipoddevice")  and [ipod-sharp]("http://banshee-project.org/Subprojects/Ipod-sharp")  I currently am mounting my iPhone's /media directory to /media/iPhone and have added a symbolic link called iPod_Control to the iTunes_Control Folder located at %iPhoneIP%/media

This works with gtkPod, but Banshee continues to ignore it.

I have begun the registration process at Banshee's website, but it requires that I wait on an Admin to approve me before i can post.

---

### Post by Kdar on 2007-10-23
[http://www.howardforums.com/showthread.php?t=1249692&page=1&pp=15](http://www.howardforums.com/showthread.php?t=1249692&page=1&pp=15)

Check this site.

Follow instruction to set up your iPhone. (those two videos).  (It will install "package manager" on you iPhone, so you can download them. One of them will be for Linux support)

Just do not unlock your phone, its not necessary. Just stop before he will go into explaining how to unlock the phone.

Here the link to download 1.02 firmware.
[http://appldnld.apple.com.edgesuite.net/content.info.apple.com/iPhone/061-3823.20070821.vormd/iPhone1,1_1.0.2_1C28_Restore.ipsw](http://appldnld.apple.com.edgesuite.net/content.info.apple.com/iPhone/061-3823.20070821.vormd/iPhone1,1_1.0.2_1C28_Restore.ipsw)

oh PS. You got to do it on Windows.

---

### Post by Wiebelhaus on 2007-10-23
Also you could run Itunes in WINE or Codeweavers Crossover.

---

### Post by Terc on 2007-10-23
I currently have iPhone firmware 1.1.1 and I HAVE SSH INSTALLED AND WORKING, with my iPhone mounted at /media/iPhone.

It IS WORKING with libgkpod

I quote:
"I currently am mounting my iPhone's /media directory to /media/iPhone and have added a symbolic link called iPod_Control to the iTunes_Control Folder located at %iPhoneIP%/media"

Also, iTunes 7.4.2 does not work under Wine, also, Wine does not support iPod syncing, much less iPhone syncing.

---

### Post by Terc on 2007-10-24
Alright, I've given up with using Banshee, I'm on Rhythmbox now, and I am syncing with my iPhone from Rhythmbox.

Anyone want a how to?

This should work with iPod Touch also.

---

### Post by Wiebelhaus on 2007-10-24
> **Terc said:**
> Alright, I've given up with using Banshee, I'm on Rhythmbox now, and I am syncing with my iPhone from Rhythmbox.

Anyone want a how to?

This should work with iPod Touch also.

Yes , Please.

---

### Post by XFocus on 2007-10-24
> **Terc said:**
> Alright, I've given up with using Banshee, I'm on Rhythmbox now, and I am syncing with my iPhone from Rhythmbox.

Anyone want a how to?

This should work with iPod Touch also.

YES!  Please, don't tease me... :(

---

### Post by Terc on 2007-10-24
Will do when I get home, sorry for the tease.  Just so you're aware, this requires you to have third party apps on your iPhone or iPod Touch.  You'll need to be able to ssh into your device, sorry if this means you won't be able to sync using my instructions. If this counts you out, there may be hope using a modified dock connector, I have not managed to get that working though.

---

### Post by XFocus on 2007-10-26
Any word on this?

---

### Post by wireless on 2007-10-27
syncing iphone with ubuntu? thats cool i know you can do it with gtkpod. doesnt it wreck your artwork btw?

---

### Post by tribaal on 2007-10-27
Well for a short set of instructions on how to sync your iphone with gutsy's gtkpod (don't know about feisty):

- Install ssh on your iphone. There are many howtos on the internet on how to do this, I'm not going to explain it here (it's pretty long on top of that).

- Install sshfs ("sudo apt-get install sshfs"). This is what lets you mount ssh filesystems, we'll use this to mount our iphone.

- Create a mountpoint. I use /media/ipod. ("sudo mkdir /media/ipod"). Make sure you got read/write access to it ("sudo chown <username> /media/ipod").

- To use sshfs you need to be in the "fuse" user group ("sudo adduser <username> fuse")

- Log out and back in again (this is necessary for your user group to be taken into account).

- Now the fun part. Go to the wifi settings on your iphone. tap the blue arrow next to your SSID, so that you can see your iphone's IP address. Note it down somewhere.

- Go to your general settings and set "auto-lock" to "never" (the iphone closes the wifi connection when it's locked).

- Open a terminal in ubuntu and do "ssh root@<your iphone's ip address>" (default password is "dottie", change it ASAP with the "passwd" command once loged in).

- If you didn't change your password on your iphone, do it now with the "passwd" command.

This is a BSD-like shell. Most of the commands are the same than in ubuntu, but I highly suggest you don't try anything funny if you don't want to brick your phone.

- move to where the iTunes library is: "cd /var/root/Media"
- make a symbolic link to this directory from within itself (weird, but necesserary): "ln -s . iTunes"
- make another symbolic link to the iTunes_Control directory called iPod_Control: "ln -s iTunes_Control iPod_Control"

- Get out of the iphone. "exit"

In ubuntu now, we need to actually perform the mount!

"sshfs root@<iphone's ip address>:/var/root/Media/ /media/ipod/"

Your Iphone should appear in gtkpod! Congratulations! Some errors are displayed, and you need to be root to unmount the iphone ("sudo umount /media/ipod"), but otherwise it works pretty well.

And wifi sync is something you couldn't do with iTunes and a Mac :) It's an extra linux-only feature :)

The only downside is that it doesn't sync the covers (yet?), and that **you have to reboot your iphone** for the tracks to show in the "ipod" appliacation.

Hope this helps :)

- trib'

---

### Post by wireless on 2007-10-27
good tutorial thanks mate, i just have a couple of Qs.
does it work with the fw1.1.1? And i learned the cover artwork issue is solved in the gtkpod svn. I did not managed to install the svn version. Is there any tutorial for that..? 
Thnx

---

### Post by XFocus on 2007-10-27
Thanks Tribaal!  I'll try this tonight and report back

---

### Post by tribaal on 2007-10-27
I didn t upgrade my firmware to 1.1.1 yet, but i guess it s exactly the same.
I ll try to use the svn version see if it fixes the artwork, compiling shouldn t be any harder than the usual apt-get build-dep / ./configure / make / make install i guess ... I ll try that tonight and update the tutorial. I ll also make a cleaner looking wiki page out of this glad it helped :)

---

### Post by Terc on 2007-10-29
Sorry, I ran into issues with this and did not want to post again until I had worked things out.  I am releasing this short tutorial *AS IS* in hopes that someone will be able to help me fix some of the issues.

So far, what I have done is:
   install SSH on your iPhone/iPod Touch
   install sshfs on Ubuntu
   mount your iPhone/iPod Touch with this command: (changing the ip for your pod's IP)
       ```
sudo sshfs root@ip.address.here:Media /media/iPhone -o allow_other
```
   create a link to the iTunes_Control folder and name it iPod_Control, place it in /media/iPhone
   use this command:
      ```
sudo lsusb -v | grep -i iSerial
```
   you should get something that looks like
      ```
iSerial                 3 00fc86a9439637191fec695fa1a643469e27977a
```
   take the first 16 characters (starting at fc, the first two 00's don't count)
   go to iTunes_Control\Device and create a file called SysInfo, paste in FirewireGuid: 0xfc86a9439637191f (using the characters returned for your iSerial port
   launch gtkpod and detect devices, set up your iPhone/iPod touch.

What this does:
   Full access to the iPhone/iPod Touch filesystem
   Device is detected as an iPod, shows up in apps supporting gtkpod
   Songs and playlists can be transfered to the IPhone/iPod touch
   Songs and playlists can be played from the device *wirelessly*

Issues right now:  

songs transfered to the iPhone/iPod Touch DO NOT PLAY EVEN AFTER THEY ARE RECOGNIZED BY THE IPOD APP This is why I am hesitant to release this how-to

you will need to remount your iPhone/iPod Touch with a new command each time its ip changes

you will need to install JohnTool from your iPhone/iPod Touch Installer.app or you will need to set Auto-Lock to Never so that you don't loose a connection when the device locks.

songs transfered to the iPhone/iPod Touch don't show up until the springboard is reloaded (go to iPod, hold down the home button for 5 seconds until it returns to the homescreen)

Album art has not transfered for me (expected from what I had read), my existing album art is still working.



*Blushes*

Thanks for the tutorial tribaal, I just wrote this all up before reading through the rest of the thread.  You're more than welcome to use any of this in your wiki page.  I'm off to try out the latest svn for the cover art fix.

---

### Post by wireless on 2007-10-29
hey terc,  if you manage to install the svn please let us know. I run into some dependencies hell..

---

### Post by tribaal on 2007-10-29
How to install svn gtkpod (Gutsy):
```

sudo apt-get build-deb gtkpod
sudo apt-get install subversion
svn co https://gtkpod.svn.sourceforge.net/svnroot/gtkpod gtkpod
cd gtkpod/libgpod/trunk
./autogen.sh
make
sudo make install
cd ../..
cd gtkpod/gtkpod/trunk
./autogen.sh
make
sudo make install

```

Using "apt-get build-dep" *usually* prevents dependency hell...

Enjoy :)

- trib'

---

### Post by wireless on 2007-10-29
Gr8!!!!!!! Thank You tribaal I will try it as soon as im out of work!
Thank You!

PS
need i uninstall the previous gtkpod installation?
and did it solved the artwork issue?

---

### Post by tribaal on 2007-10-29
Hum no you shouldn't need to uninstall your previous gtkpod installation (changed files will simply be overwritten).

If you wish to make a "cleaner" install (creating a .deb file instead of just overwriting the files) you should:

```

sudo apt-get install checkinstall

```

And use "sudo checkinstall" instead of "sudo make install" in my previous post.
This will create a .deb file on the fly and install it using dpkg. This way you can remove it cleanly with apt-get or synaptic or whatever you use.
The created .deb file isn't really suitable or redistribution though, as it lacks dependancy info (the most important part of a .deb file really).

Hope this helps

- trib'

---

### Post by wireless on 2007-10-29
Excelent !! I'm just gonna overwrite the old files 
Thnx Again mate!

---

### Post by tribaal on 2007-10-29
I started an ubuntu [wiki page]("https://help.ubuntu.com/community/PortableDevices/iPhone") on how to use the iphone with Ubuntu.
It would be nice if we centralized information there (easy to link to, nicer). Maybe Terc you could add some of your stuff there too? You seem to approach things in a slightly different way.

And if someone wants to make the page better-looking please do (I'm very bad with wiki formating as you can tell from looking at the "article").

Cheers

- trib'

---

### Post by wireless on 2007-10-29
Tribaal can you confirm artwork now supported with svn gtkpod?

---

### Post by Terc on 2007-10-29
Tribaal, I read through the wiki, one thing that stuck out was that you DONT have to reboot the iPhone to get the music to show up!  All you have to do is press on the iPod app on your iPhone and then hold down on the home key until you are returned to the springboard.  (this is a quick way to reset the springboard, but has the usefull side effect of reloading your iTunes library).  In fact, if you watch a sync with iTunes, this same animation occurs at the end of the sync.

I had taken a different approach, because i would like to eventually manage to sync through the usb connection.I also hope to script a springboard reset at the end (this would make music show up right away)

---

### Post by wireless on 2007-10-29
OK i just tried the svn guys.. its still does not support artwork and and wreck all the existing covers:(

---

### Post by XFocus on 2007-10-29
I made major changes to the wiki and formatted it accordingly.  Let me know if you see any errors I might've made or if you have any suggestions.  BIG thanks to everyone that posted, particularly Tribaal and Terc for the foundation of this howto!

[iPhone and Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPhone")

---

### Post by Terc on 2007-10-29
If some people could take a look at JohnTool, it may be the prefered method for preventing lost connections while syncing wirelessly.  [http://ericasadun.com/ftp/Misc/JohnTool/]("http://ericasadun.com/ftp/Misc/JohnTool/")

This is working for me right now.  Give it a shot and report back about battery impact.  I've had it installed for a day now and saw very little if any battery impact, contrary to what I expected.

The big advantage here is that if you forget to lock your phone when you stick it in your pocket, your battery wont die powering that ginormous 3.5" screen until you notice it was left on.

---

### Post by Terc on 2007-10-30
I'm going to just a little ahead here and see if anyone has figured out a way to get images onto the iPhone...

I was going to set my wallpaper tonight, and now that I'm on ubuntu only, I have no way to get new wallpaper on my phone!

---

### Post by tribaal on 2007-10-30
Wow brilliant!

Thanks for the reformatting :) It really looks slick. Talk about teamwork :KS
I couldn't make the artwork appear on purpose (even with the svn version), but for some reason a couple of my albums *do* have artwork on the iPhone. I'll investigate to be able to reproduce...

- trib'

---

### Post by wireless on 2007-10-30
what firmware do you have ?

---

### Post by XFocus on 2007-10-30
I have v1.1.1 and I'm experiencing the same thing as Tribaal.  The artwork is intermitent at best.  The coverflow artwork has stayed unscathed, the now playing artwork was wiped out on some of the tracks and remained on others.  Very peculiar.

---

### Post by Terc on 2007-10-30
I am also on firmware 1.1.1
I notice the same issues, although I cannot play music that i synced from Ubuntu (only music that was there from my Windows syncs will actually play.  Music added from Ubuntu will appear after I restart springboard, but when I choose play, it pauses for about 5 seconds and then skips to the next song until it reaches a song synced from Windows)

---

### Post by XFocus on 2007-10-30
The music that I've synced from Ubuntu seems to play fine.  Not sure what I might've done differently.  The wiki/howto is my experience to a "T", from jailbreak to sync.

---

### Post by Terc on 2007-10-31
Alright then.

I'm going to start fresh tomorrow, now that jailbreaking isn't the 30 min long effort it was back when the first tiff exploit was released (I did my jailbreak on 1.1.1 within 30 min of the first beta tiff) I don't mind starting over.

I will follow our wiki exactly and let everyone know how it goes.

---

### Post by wireless on 2007-10-31
have you tried using 'swaptunes' ? That way you can create diff libraries for syncing from windows and ubuntu..this way the artwork stays untouched for the windows sync. It worked for me and I think its a good solution until a final fix will be found for the artwork. In anyway I seems to be able to play songs in any case

---

### Post by ntetreau on 2007-11-01
As for the art album, could this post be part of the solution you are looking for?

[http://www.nabble.com/iPhone-thumbnails-t4386424.html](http://www.nabble.com/iPhone-thumbnails-t4386424.html)

---

### Post by XFocus on 2007-11-01
It looks like they might know what the problem is, which is promising.  Unfortunately the post is 2 months old and there still isn't a way to preserve the album art.

[Edit] Woops!  Didn't see the patch at the bottom!!  I'm gonna try it tonight and report back.

---

### Post by wireless on 2007-11-01
can anyone tell what actually the issue with the artwork? 
at first it looked like the easiest thing.. its only pictures how hard should it be to transfer it to the iphone/ipod.. but i guess its much more than that hey..?:)

---

### Post by ntetreau on 2007-11-01
> **wireless said:**
> can anyone tell what actually the issue with the artwork? 
at first it looked like the easiest thing.. its only pictures how hard should it be to transfer it to the iphone/ipod.. but i guess its much more than that hey..?:)

From what I understand from the post, it seems that with the missing sysinfo, gtkpod gets the wrong impression that the devices doesn't support album art, hence the deletion... 

Nic

---

### Post by Terc on 2007-11-01
I think the first thing is that they're actually stored in a database...

---

### Post by kloy1334 on 2007-11-02
Hello. So I just got an iPhone (1.1.1 / Jailbreakme / AnySIM to Rogers) yesterday. I am not really sure why I bought it, but anyways, I have Gutsy and gtkpod 0.99.10 / libgpod2 0.5.3-svn. I used the instructions from page 1 and the bottom of 2 (the one with iSerial) here in the forums.

So I can transfer the songs to my iPhone using model 'xiphone1,' but none of the music displays on my iPhone. FTW?

Here's a run-through, it if helps.

1. I mount my iphone:
sudo sshfs root@192.168.1.101:Media /media/iPhone

2. I open gtkPod and get:
'Error while mmap'ing /media/iPhone/iPod_Control/Artwork/ArtworkDB: Invalid argument'
But whatevs, right? Since artwork hasn't fully been hacked yet.

3. I add/delete music, click 'Save Changes,' let the database write. And then the dialog box closes, to show that it is 100% complete.

4. Unmount my iPhone using:
sudo umount /media/iPhone

5. Open up 'iPod' on my iPhone to see 'No Music', and then hold down the Home key so it restarts the springboard.

6. Open up 'iPod' again, and still... nothing.

Is there anything that I did wrong, or is there another way or hack to do the music sync?

Thanks much.
-Jeff K.

---

### Post by XFocus on 2007-11-02
Did you try the wiki that was linked to on page 3?  [Try this]("https://help.ubuntu.com/community/PortableDevices/iPhone")

---

### Post by kloy1334 on 2007-11-02
Yes, that was the one I used.

---

### Post by misterbeetz on 2007-11-03
Hey everyone.  For those who want to use or try Amarok with the iphone... I found this site with a quick how-to and it worked great for me.  It was pretty easy too:

[http://blog.adaniels.nl/?p=50](http://blog.adaniels.nl/?p=50)

Hopefully it will be useful for someone.

- misterbeetz

---

### Post by kloy1334 on 2007-11-03
The amarok method worked! Kinda odd how I have to use Amarok, and not gtkPod, but thanks.

Just tried it again, songs don't go on past 10 seconds?

---

### Post by Scimu on 2007-11-03
Thanks for this.. And im gonna use that checkinstall in the future too. Thanks a lot!

---

### Post by misterbeetz on 2007-11-03
> **kloy1334 said:**
> The amarok method worked! Kinda odd how I have to use Amarok, and not gtkPod, but thanks.

Just tried it again, songs don't go on past 10 seconds?

Yeah it was weird for me to use amarok at first as well but I found it served my ipod-syncing needs better than the other music clients I tried.

Songs don't play past the 10 second mark for you on the iphone?  Can you tell me the following?:

- If applicable, have these songs worked fine on another ipod before?

- What file format and bitrate are they?

- What program did you use to encode them if any.

- Do all songs exhibit this behaviour or just some?

The reason I ask is because I have had songs that were encoded using a certain encoder and it seemed to have botched a certain part of my songs a couple seconds into them causing my ipod to choke at that point in the song.

In addition, I do not have this problem for songs synced to my iphone using amarok.  The only thing that dosent carry over for me is the song artwork unfortunately. 

- misterbeetz

---

### Post by misterbeetz on 2007-11-06
Anyways, I have a question of my own.  Does anyone know a way to check free space on the iphone without using itunes?

- misterbeetz

---

### Post by kloy1334 on 2007-11-06
Settings --> General --> About

---

### Post by misterbeetz on 2007-11-06
> **kloy1334 said:**
> Settings --> General --> About

Excellent. Thank you.

- misterbeetz

---

### Post by Terc on 2007-11-08
Is there any support for videos/pictures at all for the iPhone/iPod Touch?  I've been looking and just can't find anything

Also, I'm really missing the ability to synchronize my calendar.


edit:  for calendar/contacts syncing... just go to the next page!  (funambol.com helps!)

---

### Post by Terc on 2007-11-08
[http://my.funambol.com/](http://my.funambol.com/)

Install funambol on your iPhone (just released)

install it on your desktop client of choice

sync



More to come when I get this running!!

---

### Post by sonicborg on 2007-11-09
does any of this stuff stop you getting updates or working service from the phone ?

---

### Post by Terc on 2007-11-11
Each time you update, you will need to re-jailbreak and reinstall ssh and any other third party apps you need to get this stuff working.  Currently, the 1.1.2 update does nothing for US customers other than fix the tiff exploit (which can be fixed on the 1.1.1 firmware with a third party install)  It is a case by case basis.  This does not affect service in any way.

---

### Post by misterbeetz on 2007-11-11
Did anyone catch this article?:

[http://www.tuaw.com/2007/11/11/afp-for-iphone-and-ipod-touch/](http://www.tuaw.com/2007/11/11/afp-for-iphone-and-ipod-touch/)

It allows for full read/write disk access to the iphone (over usb im assuming).

One commenter already brought up how this might help linux clients:

"This should also work with any Linux based client that has access to apple protocol packages. In Ubuntu the package is "netatalk". It makes it real simple to manage the music library on the iPhone with Amarok or any other music manager that hadles the previous iPods." - ES Odin

I really hope this will allow us to sync our iphones with linux clients over usb.  Syncing over wifi is entirely too slow for my liking.

- misterbeetz

---

### Post by Terc on 2007-11-11
Unfortunatly, the instructions require you to get the wifi ip address... so I'm guessing this is not over usb.

---

### Post by superm1 on 2007-11-18
For everyone encountering problems in this thread, I just bought an iPod Touch and sorted out a ton of things with it today.

I've updated the wiki page at 

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

for the new improved support.

I ended up having to build a newer libgpod and amarok which are both now on a PPA (which is listed at [https://edge.launchpad.net/~ipod-touch/+archive/](https://edge.launchpad.net/~ipod-touch/+archive/) for those interested).

You can add this source to your sources.list for it to work for you in gutsy:
```
deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main
```

---

### Post by wireless on 2007-11-19
whats new using your method?

---

### Post by superm1 on 2007-11-19
> **wireless said:**
> whats new using your method?
The serial number discussion is proper on there.  There is a different place that is linked to for the jailbreaking discussion.  I've got package there that won't corrupt the ipod database.  I've got an amarok section.

---

### Post by wireless on 2007-11-19
I understand that artwork is still an issue, correct?

---

### Post by benanzo on 2007-11-20
I've got a little program that does automatic wireless syncing with the iPhone.

[http://code.google.com/p/iphone-usync/](http://code.google.com/p/iphone-usync/)

It uses gnupod for automated syncing and gtkpod for manual syncing.  Artwork and videos are supported by gtkpod but not gnupod (for now.)

---

### Post by superm1 on 2007-11-20
Well I'm not sure where the underlying issue is for me at least with artwork.  The ArtworkDB is not being written out with any warnings even  by Amarok.  Gtkpod complains that it can't mmap the file.

All of the thumbnail files are however being generated and put into the appropriate directories when syncing.

---

### Post by benanzo on 2007-11-20
teuf told me that GTKPod has fixed the mmap() errors (which don't work over sshfs) but it's still never worked for me.  My solution was to only mount the Music directory via sshfs and rsync everything else in iTunes_Control to local then use gtkpod/amarok to make the changes then rsync it back.  I have a script that does it automatically.  Then artwork works normally.

---

### Post by superm1 on 2007-11-20
> **benanzo said:**
> teuf told me that GTKPod has fixed the mmap() errors (which don't work over sshfs) but it's still never worked for me.  My solution was to only mount the Music directory via sshfs and rsync everything else in iTunes_Control to local then use gtkpod/amarok to make the changes then rsync it back.  I have a script that does it automatically.  Then artwork works normally.
Yuck.  There has to be a cleaner way to do this.  I'm wondering if NFS might be more worthwhile exploring than sshfs on the iPhone...

---

### Post by benanzo on 2007-11-20
[Here's]("http://wickedpsyched.com/iphone/") a bunch of tools ported to iPhone.  I tried to get the samba port working but wasn't successful.  You might have more luck.

---

### Post by Terc on 2007-11-21
superm1, benanzo, it's great to have you on board.

I think a native app for the iPhone/iPod Touch may be the best option after seeing usync, however, any work on getting gtkpod up and running is much appreciated!

When I say that a native app would be my choice, the reason is that I am thinking about family members.  Although I have no problem mounting through ssh each time I want to sync, it's a little intimidating for the less adept.  Also, iPhone IPs can change which means they actually need to understand what they're doing, as well as check their IP each time they want to sync.  If the usync project and funambol teamed up, we may see true, complete wifi syncing with just an initial setup involved.

Final question, has anyone managed to sync video yet?  I'm looking for help with getting this working.

---

### Post by superm1 on 2007-11-21
> **Terc said:**
> superm1, benanzo, it's great to have you on board.

I think a native app for the iPhone/iPod Touch may be the best option after seeing usync, however, any work on getting gtkpod up and running is much appreciated!

When I say that a native app would be my choice, the reason is that I am thinking about family members.  Although I have no problem mounting through ssh each time I want to sync, it's a little intimidating for the less adept.  Also, iPhone IPs can change which means they actually need to understand what they're doing, as well as check their IP each time they want to sync.  If the usync project and funambol teamed up, we may see true, complete wifi syncing with just an initial setup involved.

I was thinking about this more, and I really think this can all be handled with some nice mounting tricks and amarok connect and disconnect commands.

If you properly setup SSH pub/priv keys, you can have automatic sshfs mounting and fusermount -u.  I even just got mine as far as restarting MobileMusicPlayer automatically via SSH after syncing.

I'd really like to see a method to have clean artwork writing still.  Here is what i'm thinking:

First off:
This will only work for Amarok (unless gtkpod supports custom mount/unmount commands).

Mount command actions:
1) rsync all but the Music directory over to /media/ipod
2) Mount the Music directory to /media/ipod/Music via sshfs

3) "Transfer the songs"

Unmount command actions:
4) unmount sshfs Music directory
5) rsync the other directories back over
6) issue a killall MobileMusicPlayer via ssh

> 
Final question, has anyone managed to sync video yet?  I'm looking for help with getting this working.
That is on my todo.  Particularly I want to have myth2ipod working, and once I do i'll turn whatever it took to do it into a deb for people to use.  Gtkpod and Amarok claim to be able to do it, just a matter of having video in the right format.

---

### Post by superm1 on 2007-11-21
Also, in terms of iPhone ips always changing....

Get DNS working on your network.  When the iPod touch joins my network, it provides the hostname "ipod" to my dns server when it requests a dhcp address.

So all of my mount commands are always root@ipod

---

### Post by benanzo on 2007-11-21
Video and artwork both work fine in GTKPod.  Artwork should work right away if you rsync the iTunes and Artwork directories then mount the Music dir via sshfs.  Video requires an extra step since the version of libmp4-dev in the Gutsy repos is broken in terms of gtkpod being able to use it.  You must use mpeg4ip instead [http://mpeg4ip.sourceforge.net/](http://mpeg4ip.sourceforge.net/)

As for the DHCP problem, uSync handles that by defining "locations" in the uSync.conf file on the phone so if your computer has a static address then you just define it there, otherwise if it's not defined (if it uses DHCP) or it can't connect to the one that is defined then it will prompt the user for it.  The uSync script that runs on the computer (uSync-Server.sh) doesn't know or care what it's own IP is.  It ONLY knows the iPhone's IP if the iPhone sent it to it (stored in iphone_ip.tmp in the uSync-Server directory.)  The computer will continue to use this IP to connect to the iPhone until it changes, then you just launch uSync on the phone to update the IP address, then everything works again.

uSync uses rsync for everything.  It doesn't mount anything with sshfs.  The reason is because I wanted uSync to allow the iPhone to continue to be "portable" even while syncing.  Using rsync for the music transfer is much safer in that regard than using sshfs since it will safely disconnect if the iPhone drops its connection.  If the phone drops off while transferring over sshfs then you'd be left with a stale sshfs mount on your computer which more often than not will completely lock up nautilus.  Plus rsync has the advantage of being able to resume a previously disconnected transfer when the phone comes back online.  Because uSync transfers the iTunes and Artwork directories back to the phone (or iPod Touch) before the Music directory you can listen to any tracks that have transferred completely even while the rest are still syncing.  All the tracks you're syncing will be listed in the iTunes database, but the ones that haven't transferred (or are still transferring) wont be playable yet.

One primary disadvantage of manipulating a local "copy" the the iTunes_Control directory (stored in LocaliPhone in the uSync-Server dir) is that this directory must be identical to the iTunes_Control directory on the phone.  So if you have 6 GB of music and videos on your phone then they're also stored in the LocaliPhone directory on your computer, which is a rather waste-of-space.  I had to do this because without mounting via sshfs GTKPod would delete anything it didn't find in the Music dir, the so-called "orphaned" files.  So when you sync it would just remove all the entries from iTunesDB (but not the actual tracks).  If anyone has an idea how to do this (and continue to be able to sync with multiple computers) without mounting the Music dir I'd be very interested.

---

### Post by superm1 on 2007-11-22
Okay everyone.

I've added a new package to that PPA entitled ipod-convenience.

It provides 2 new binaries, iphone-mount and iphone-umount

Here's the jist of what it does:
iphone-mount:
        * Creating a mount point
        * Syncing over all but music to your mount point
        * Properly mounting music within your mount point
        * Creation of a Firewire GUID
        * Building the proper directory structure for a 7th generation device

iphone-umount:
        * Unmounting music
        * Syncing over all databases that are used for music and artwork
        * Restarting the Apple Mobile Media Player

So the use case is now this:
1) Turn on iPhone
2) iphone-mount
3) Start gtkpod
4) do $stuff
5) "Save" in gtkpod
6) iphone-umount
7) enjoy

---

### Post by superm1 on 2007-11-22
OK next update.  As for videos:

Got these working too. I pushed a new gtkpod-aac to the PPA.  You can add any h264 videos no trouble.  I just transcoded an episode of something in mythtv into h264 at the right resolution and it appears to have worked.

For those using myth, you need nuvexport to convert your recordings easily. I've also pushed that to the PPA.  Next up is myth2ipod ([www.myth2ipod.com](www.myth2ipod.com)) which creates RSS feeds that you can subscribe to.

---

### Post by jack12387 on 2007-11-22
Superm1, thanks for your work so far. I've been following (and testing) methods described in this thread for a while now. I can see that recent posts from you and Benanzo have really lifted the progress on solving this issue.

I've ran your "use case" from ipod-convenience tonight, but it seems album art is still not working.  On the bright-side gtkpod didn't give any warning messages.  Can you confirm that Album art is working for you?  I'm asking this, because your posts seemed pretty confident :)

My output for iphone-umount is as follows.  It seems your tools does transfer the necessary Artwork files to the iPhone :/  But my iphone album covers are all gray.

> 
iTunes_Control/Artwork/
iTunes_Control/Artwork/ArtworkDB
iTunes_Control/Artwork/F3001_1.ithmb
iTunes_Control/Artwork/F3002_1.ithmb
iTunes_Control/Artwork/F3003_1.ithmb
iTunes_Control/Artwork/F3005_1.ithmb
iTunes_Control/iTunes/iTunesDB
iTunes_Control/iTunes/iTunesDB.ext
iTunes_Control/iTunes/iTunesSD

sent 3457 bytes  received 10192 bytes  3899.71 bytes/sec
total size is 12664981  speedup is 927.91
root@10.0.0.9's password: 
zsh: command not found: killall


On a secondary note, I understand that the MobileMusicPlayer must restart.  And you are using killall to stop this process,  My "killall" error message would not be related to the Album Art not appearing, correct?

FYI, I have been using the following options as alternative to "killall", a) hold the menu button in iPod mode for >5 sec, b) reboot c) use a native app such as SysInfo to kill the process,

Just for clarity:

I apt-get installed gtkpod libgpod3 ipod-convienence from PPA repo.

---

### Post by superm1 on 2007-11-22
> **jack12387 said:**
> Superm1, thanks for your work so far. I've been following (and testing) methods described in this thread for a while now. I can see that recent posts from you and Benanzo have really lifted the progress on solving this issue.

I've ran your "use case" from ipod-convenience tonight, but it seems album art is still not working.  On the bright-side gtkpod didn't give any warning messages.  Can you confirm that Album art is working for you?  I'm asking this, because your posts seemed pretty confident :)

My output for iphone-umount is as follows.  It seems your tools does transfer the necessary Artwork files to the iPhone :/  But my iphone album covers are all gray.



On a secondary note, I understand that the MobileMusicPlayer must restart.  And you are using killall to stop this process,  My "killall" error message would not be related to the Album Art not appearing, correct?

FYI, I have been using the following options as alternative to "killall", a) hold the menu button in iPod mode for >5 sec, b) reboot c) use a native app such as SysInfo to kill the process,

Just for clarity:

I apt-get installed gtkpod libgpod3 ipod-convienence from PPA repo.
Ah killall works for me because i've installed bsdutils from the installer on my ipod touch.  Sysinfo isn't native to the ipod either, neither is pkill.  Any recommendations on other native apps so people don't have to install bsdutils?

I can confirm artwork works for me, the killall MobileMusicPlayer is what restarts the player and then the artwork works.

---

### Post by jack12387 on 2007-11-23
Good news, after I scp'd killall to /usr/bin, Album Art does appear on my iphone :)

Here are couple of medium-level annoyances (they are not show-stopping issues)

1) Upon iphone-umount, You will get a "No matching processes were found" error if MobileMusicPlayer is not started. *Work around*: turn on your iphone/ipod touch's ipod app.

2) Suppose I need to set covers on 10 albums, After the first attempt (iphone-mount->gtkpod->iphone-umount), you will not see any album covers, You shall finally see the covers from the first attempt when adding cover to a 11th album on the next (iphone-mount->gtkpod->iphone-umount) cycle. *Work around*: Do you first (iphone-mount->gtkpod->iphone-umount) cycle of setting covers for your albums. Then perform iphone-mount->gtkpod->bulk edit comments->iphone-umount cycle, All covers should be set properly.

3) Videos lose their "cover" too.  iTunes  puts a preview image as a cover for each video, gtkpod seem to set them as gray art.  I'm not too concerned about this.  Also I haven't tried your gtkpod-aac yet.


For people who don't have killall on their iphone.  I managed to get hold of a bundle which contains it from a unlock 1.1.1. thread at hackint0sh ([http://www.hackint0sh.org/forum/showthread.php?t=12817](http://www.hackint0sh.org/forum/showthread.php?t=12817))

The bundle which contains killall: [http://d.turboupload.com/d/2098918/unlock111.zip.html](http://d.turboupload.com/d/2098918/unlock111.zip.html)

Don't forget to chmod the executable once its on your device.


**If you got it working, can you tell me how big are your ithmb files? For one album I'm getting about 4mbs of thumb files in my Artworks folder!**

---

### Post by prappo on 2007-11-23
Hi, jack12387

2 questions:
 1. what is the version of gtkpod you're using?
 2. what does exactly the "bulk edit comments" mean?

---

### Post by Zorael on 2007-11-23
Is there any way to create and add ringtones on a 1.1.1 phone?

I tried creating an m4a file using faac, then renaming and adding it to the ringtones folder, with varying success. It either doesn't show up in the list or it refuses to play.

---

### Post by jack12387 on 2007-11-23
Your query regarding ringtines is bit off topic but as reference you will need to search for topics regarding a "patched MeCCA" file to make ringtones work for 1.1.1.

Try elite dev team forum. Seek and you shall find

---

### Post by jack12387 on 2007-11-23
Prapo, I'm using gtkpod libgpod3 ipod-convenience from PPA repositary.

Bulk edit comments means highlight all songs, and editting their track info all in one go. In this case Ive changed the comment field. Them all covers appeared.

---

### Post by superm1 on 2007-11-23
Folks, I've got ipod-convenience uploaded to Hardy now too.  Ideally any other improvements that come out of this thread should be directed to launchpad as a bug (once it clears the archive administrators) or at least at me directly.

There is a pending issue with Amarok, that it expects that your top level mount point is where the iPod Touch/iPhone shows up.  I'm going to try to suss it out with upstream to see if a better solution can come up.

---

### Post by XFocus on 2007-11-23
> Is there any way to create and add ringtones on a 1.1.1 phone?

If you use SendSong that is in the Installer.app, you can convert any tune in your library (on the phone) into a ringtone.  So simply add the song to your phone and then use sendsong to convert it.

Also, great work to everyone on this thread.  I'm really excited to try out some of the more recent stuff.  

:-D

---

### Post by jack12387 on 2007-11-24
Hi this might sound noobish but how do I make ipod-convenience NOT depend on libgpod3?

I'm asking this, because I want to use svn version of gtkpod/libgpod :/

---

### Post by superm1 on 2007-11-24
> **jack12387 said:**
> Hi this might sound noobish but how do I make ipod-convenience NOT depend on libgpod3?

I'm asking this, because I want to use svn version of gtkpod/libgpod :/
I'll tell you the proper solution here is to build svn into debs instead so that you don't spew svn made binaries across your system without accounting for where they are being stored or which ones and what not.

---

### Post by medomedo on 2007-11-25
Hi,

Thanks superm1 for your work. I followed the steps in this thread and in here[https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone").

I installed Amarok and ipod-convenience from your repository. I can now SSH to the phone without password.I configured Amarok by going to "Add device" and selecting "Apple ipod media device" and edited mounting location to become "/media/ipod". Then I mounted using "iphone-mount". By now I can see the files correctly mounted into /media/ipod. When I click on "connect" in Amarok, I get this error message:

"Media Device: No mounted iPod found"

I was afraid of permission issues so I have run chmod 777 -R /media/ipod. I also restarted iPhone and tried again but no success.

Can anyone tell me what is wrong?

---

### Post by superm1 on 2007-11-25
> **medomedo said:**
> Hi,

Thanks superm1 for your work. I followed the steps in this thread and in here[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone).

I installed Amarok and ipod-convenience from your repository. I can now SSH to the phone without password.I configured Amarok by going to "Add device" and selecting "Apple ipod media device" and edited mounting location to become "/media/ipod". Then I mounted using "iphone-mount". By now I can see the files correctly mounted into /media/ipod. When I click on "connect" in Amarok, I get this error message:

"Media Device: No mounted iPod found"

I was afraid of permission issues so I have run chmod 777 -R /media/ipod. I also restarted iPhone and tried again but no success.

Can anyone tell me what is wrong?
I fear that this is an unfortunate side effect of doing it this way with Amarok.  It seems to want your mount point to be the top level (/media/ipod rather than /media/ipod/Music).

I talked to Amarok developers and they are open to a patch to change this behavior, but I don't have the time to investigate it in depth right now.

Use gtkpod for now :(

---

### Post by medomedo on 2007-11-25
Hi superm1,

Thanks for clearing this up to me. I will install GTKpod and see if things gets better. I will keep watching this thread because I am using Amarok for music and podcasts for long time now.

Thanks again.

---

### Post by CDNdevil on 2007-11-26
Need help, I have a Ipod touch 1.1.1 jailbreaked, I've been following the wiki, using ipod-convenience PPA, with gtkpod, everything shows up that is on the ipod on gtkpod, so I tried putting some music on, well after what looked like a smooth umount, my ipod shows no music or video, but when I plug in my laptop, a desktop, gtkpod can see the music as well as copy to the computer.
What am I doing wrong?

---

### Post by superm1 on 2007-11-26
> **CDNdevil said:**
> Need help, I have a Ipod touch 1.1.1 jailbreaked, I've been following the wiki, using ipod-convenience PPA, with gtkpod, everything shows up that is on the ipod on gtkpod, so I tried putting some music on, well after what looked like a smooth umount, my ipod shows no music or video, but when I plug in my laptop, a desktop, gtkpod can see the music as well as copy to the computer.
What am I doing wrong?
Try to restart the Music app on the iPod.  Start it and hold down the "home" button and see if this resolves things.

---

### Post by CDNdevil on 2007-11-26
Oh sorry should have mentioned that I do that as well, but new devolpment is that I just got it to work with Amarok following this [http://blog.adaniels.nl/?p=50](http://blog.adaniels.nl/?p=50) problem is, is I don't know how to put video on here with Amorok. Is it possible, or keep trying to get gtkpod working?

---

### Post by superm1 on 2007-11-26
Well slight problem with that.  If you use that method, MobileMusicPlayer won't restart and you can't get artwork onto the iPhone/iPod touch.

---

### Post by nikoPSK on 2007-11-26
> **sx66gns said:**
> Also you could run Itunes in WINE or Codeweavers Crossover.

itunes under wine isn't so hot for me... :(

---

### Post by CDNdevil on 2007-11-26
Well artwork is nice and but more important for me is getting video on here, If I can get gtkpod working then artwork & video.

---

### Post by superm1 on 2007-11-26
> **CDNdevil said:**
> Well artwork is nice and but more important for me is getting video on here, If I can get gtkpod working then artwork & video.
Install gtkpod-aac.  It's on that PPA too.  It lets you add video (i've done it myself)

---

### Post by superm1 on 2007-11-26
> **nikoPSK said:**
> itunes under wine isn't so hot for me... :(
Not to mention the newer version (required for the iPod touch) doesn't work in wine.  Even if it did work in wine, the way that it communicates with the ipod requires the ipod service and/or driver that come with windows to be working too since it doesn't just expose a filesystem.

---

### Post by CDNdevil on 2007-11-26
Ok I have installed gtkpod-aac, what do I do to add videos with it?
Oh and thank you advance for all your help tonight.

---

### Post by superm1 on 2007-11-26
> **CDNdevil said:**
> Ok I have installed gtkpod-aac, what do I do to add videos with it?
Oh and thank you advance for all your help tonight.

I just dragged and dropped myself.

---

### Post by CDNdevil on 2007-11-26
Ok I've got gtkpod working, and sending videos to thank for the help, I going to bed.

---

### Post by adaniels on 2007-11-26
Also have a look at the article 'iPhone + Amarok' on my blog.
[http://blog.adaniels.nl/?p=50](http://blog.adaniels.nl/?p=50)

---

### Post by sirab on 2007-11-26
i keep getting this error

fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option


ive done the passwordless ssh login , iphone-convenience, and set up a guid but i cant mount anymore

---

### Post by sirab on 2007-11-26
never mind... solved it..

---

### Post by nikoPSK on 2007-11-26
good for you!

---

### Post by CDNdevil on 2007-11-26
Ok almost everything is working now, except for album art, which is odd because gtkpod can see the album art off my ipod, but I don't see it on coverflow. I'm using iphone-mount, and iphone-umount, with no errors. I must be doing something wrong again, but not sure what.

---

### Post by superm1 on 2007-11-26
> **CDNdevil said:**
> Ok almost everything is working now, except for album art, which is odd because gtkpod can see the album art off my ipod, but I don't see it on coverflow. I'm using iphone-mount, and iphone-umount, with no errors. I must be doing something wrong again, but not sure what.
Make sure you have the BSD subsystem installed on your ipod.  Try to restart the music player on it too.

---

### Post by CDNdevil on 2007-11-26
BSD subsystems are installed, but something I'm doing is probably causing it, at least thats what I think. I'll try setting up with the media centre again, to see if I screwed up settings on the laptop or something. Oh crap I forgot what do I use to sync photos?

---

### Post by wireless on 2007-11-28
Hey PPL

I followed  superm1 method 
when im issuing ipod-touch-mount and ipod-touch-umount and it looks ok and no errors but than when im openning gtkpod it does nothing. no iphone is detected..

update:
ok i added the iphone manually through "edit repository/ipod options" menu. now it loads the play list but no artwork and also it gives error "Error reading iPod photo database (Photos directory not found: '/media/iphon/iPod_Control/Photos' (or similar).)."
i tried killall MusicMobilePlayer but no avail...
the gtkpod im using the latest from svn.
i also installed libgpod3 (libgpod2 is also installed..should i remove it?)
any hints?
thnx

---

### Post by jack12387 on 2007-11-29
When i had it working, i removed libgpod2 and i used the gtkpod from PPA repo.

Gtkpod didn't show any error message on my machine. I found that i need to save then eject the ipod under gtkpod to see the artwork straight away after iphone-umount.

On a side note I am still concerned with sizes of thumb files. I dont get why they are over 150mbs for 300 songs i have on the iphone. Im currently investigating this.

---

### Post by jack12387 on 2007-11-29
I just saw AFPd server available on installer.app. I understand it has been beta for couple of weeks but this seems to be a working release. It is still a wireless based but at least give us some more things to play with iPhone under ubuntu.

---

### Post by wireless on 2007-11-29
> **jack12387 said:**
> When i had it working, i removed libgpod2 and i used the gtkpod from PPA repo.

Gtkpod didn't show any error message on my machine. I found that i need to save then eject the ipod under gtkpod to see the artwork straight away after iphone-umount.

On a side note I am still concerned with sizes of thumb files. I dont get why they are over 150mbs for 300 songs i have on the iphone. Im currently investigating this.

removing libgpod2 means removing rythmbox . a depend' .  
oh damn . i have lots of mess from the svn version i installed. sorry for the stupid Q but how can i completely remove anything installed from svn?


UPDATE:
ok i cleaned some stuff and now i can see artwork and also the songs i transfer but they wont play. :\
wtf is going on here guys?!

when i issue  ipod-touch-mount command , i get
> receiving file list ... done

sent 31 bytes  received 540 bytes  380.67 bytes/sec
total size is 920910  speedup is 1612.80
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

AND when issueing ipod-touch-umount i get 

> fusermount: entry for /media/iphone/iTunes_Control/Music not found in /etc/mtab
building file list ... done

sent 582 bytes  received 20 bytes  401.33 bytes/sec
total size is 920910  speedup is 1529.75

---

### Post by CDNdevil on 2007-11-29
I'm wondering what I did wrong, because I still can't get album art to work at all, is it because I'm using gtkpod to find the album art? I'm using PPA gtkpod, iphone-mount, and iphone-umount. It doesn't have any errors and still no album art even though if I look at the ipod with gtkpod PPA on my laptop, I see album art, just not on the ipod. I'm convinced I'm screwing up somewhere. But other wise I have tons of music and videos on here now.

---

### Post by wireless on 2007-11-29
> **CDNdevil said:**
> I'm wondering what I did wrong, because I still can't get album art to work at all, is it because I'm using gtkpod to find the album art? I'm using PPA gtkpod, iphone-mount, and iphone-umount. It doesn't have any errors and still no album art even though if I look at the ipod with gtkpod PPA on my laptop, I see album art, just not on the ipod. I'm convinced I'm screwing up somewhere. But other wise I have tons of music and videos on here now.

Its Driving me CRAZY! i dont even have this option to find artwork through gtkpod i have to add it manually , moreover now when i solved all the error. and mounting and unmounting is errorless. i can get songs to the iphone but again no artwork is being generated. before when artwork did apeard the songs wouldnt play!!!

i wanna go haaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

---

### Post by jack12387 on 2007-11-29
@Wireless, and CDN, you are pretty close.  The "intermittent" artwork appearing on your iphone can be solved by (at least worked for me personally) making sure you SAVE then EJECT, then iphone-umount;

What you will expect is when you click Save, there will be a progress bar pop up describing its saving something.  Then, when you right click the iphone and click Eject, you will see the same progress bar pop up describing its saving something again.

Finally, when you run iphone-umount, you should expect to see the contents of Artwork folder to be transferred to your iphone (see my output on Page 8 ).  At this stage, I guess I can say the artwork should be on your iphone.  HTH

---

### Post by CDNdevil on 2007-11-29
But jack I am doing that, that is why I am so confused. By the way anyone know how to put regular pictures on here?
Edit: I see very similar results from using iphone-umount, after I save > eject

---

### Post by nikoPSK on 2007-11-29
I think you can just drag and drop photos.

---

### Post by wireless on 2007-11-29
> **jack12387 said:**
> @Wireless, and CDN, you are pretty close.  The "intermittent" artwork appearing on your iphone can be solved by (at least worked for me personally) making sure you SAVE then EJECT, then iphone-umount;

What you will expect is when you click Save, there will be a progress bar pop up describing its saving something.  Then, when you right click the iphone and click Eject, you will see the same progress bar pop up describing its saving something again.

Finally, when you run iphone-umount, you should expect to see the contents of Artwork folder to be transferred to your iphone (see my output on Page 8 ).  At this stage, I guess I can say the artwork should be on your iphone.  HTH


YES artwork apear on the iphone and yes i follow this exact procedure you describe but im still getting fusermount error when unmounting
>  ipod-touch-umount 
fusermount: entry for /media/iphone/iTunes_Control/Music not found in /etc/mtab

and when mounting 
> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option


the songs and artwork apear but when playing it just keep silent and when trying to fast seek through the song it just skip to the next song and again nothing plays!:(

before it worked for one time i dont know how but when tried to sync more music all the problems  came back :( wierrrrd

---

### Post by nikoPSK on 2007-11-29
have you tried resetting your ipod to factory settings then trying?

---

### Post by wireless on 2007-11-29
> **nikoPSK said:**
> have you tried resetting your ipod to factory settings then trying?

yes! and it worked one time after it! thats it!

what about those fuse errors? is it possible that its somehow related to the issues im having?

---

### Post by nikoPSK on 2007-11-29
well, are you using itunes under wine? it could be your issue there.

---

### Post by wireless on 2007-11-29
> **nikoPSK said:**
> well, are you using itunes under wine? it could be your issue there.

no, no itunes here.

---

### Post by nikoPSK on 2007-11-29
what then, that could be your issue....

---

### Post by CDNdevil on 2007-11-29
Hey wireless, I had that problem at the beginning as well, try deleting all the music off, then save > eject > unmount > mount > open up gtkpod then load > add directory > then save...... I found that I can only add folder at a time or 1 file at a time or similar problem occured.
EDIT: Also try deleting the /media/ipod folder then iphone-mount, will tell you to make /media/ipod, make it again sudo chown username /media/ipod it never hurts to do simple things like that, hell even restarting the comp, just incase something is still mounted and screwing up iphone-mount, also I will keep watching his page to help as best I can

---

### Post by wireless on 2007-11-29
thank you so much for helping cdndevil. i will try what you just suggested.
i have lots of mess becouse before the ipod-convinience and the ppa packages i install gtkpod from svn and i dont know howto completly remove it. now it looks like i have to gtkpod versions the one from ppa and the one from svn, furthermore in /usr/bin there is 
iphone-mount
iphone-umount
ipod-touch-mount
and ipod-touch-umount
i dont know where they all came from but its realllly confusing :\ what a mess
anyway they all give same results.

---

### Post by CDNdevil on 2007-11-29
I know what you mean Wireless, I made a mess on the laptop, then I setup everything on my media centre, after figuring out some problems I had, but what sucks is that I have no album art, and all you have is album art. Strange. But I know we will fix our problems eventually.

---

### Post by wireless on 2007-11-29
> **CDNdevil said:**
> I know what you mean Wireless, I made a mess on the laptop, then I setup everything on my media centre, after figuring out some problems I had, but what sucks is that I have no album art, and all you have is album art. Strange. But I know we will fix our problems eventually.

CDNdevil your suggestions worked thank so much. but its so frigile i allready messed it up again ;p 
i guess more work should be done but we are on the right track!

cheers ;)

ok so after testing twise to be sure deleteing /media/ipod . than recreating it and sudo chown username /media/ipod. works.
and true. its all mather of howto mount, add files, save, EJECT, unmount. miss one of those steps and its all screwed. :)

---

### Post by CDNdevil on 2007-11-29
Alright that's good to here, \\:D/ just curious but does your artwork show up on the ipod/iphone? :-D

---

### Post by wireless on 2007-11-29
yep finally they show up allright!! :)

---

### Post by CDNdevil on 2007-11-29
Good to hear, did you manually download your cover art, or use gtkpod? I cant for the life of me get cover art/album to work. I still need help:confused:

---

### Post by nikoPSK on 2007-11-29
lol, I was going to suggest gtkpod. (if you weren't already using it) is everything resolved?

---

### Post by iiviip3 on 2007-11-29
Hey I'm hoping someone can help with an issue syncing my iPhone. Last week I synced over wi-fi using Amarok but when my album art got all screwed up I decided not to go that route anymore. I followed the directions for GTKPod and I was able to send a few songs over to the iPhone flawlessly but only over USB.

Right now I can't seem to much anything. Here is some proof that I can login without it requiring a pw and that SSH is setup properly. I just can't figure out why it will not mount. Any help would be appreciated...have a good one!

ira@lapper:~$ iphone-mount
ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this.
ssh: ipod: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [receiver=2.6.9]
read: Connection reset by peer
ira@lapper:~$ iphone-mount
ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this.
ssh: ipod: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(454) [receiver=2.6.9]
read: Connection reset by peer
ira@lapper:~$ ssh root@192.168.1.8
Last login: Thu Nov 29 22:59:38 2007 from 192.168.1.10
# ls
Library  Media  bin

---

### Post by CDNdevil on 2007-11-29
When you installed ipod-convience it popped up where type in the IP address for the iphone, it looks like you didn't change that from what I see at least. Only thing I can think of from when I read your post. Hope that helps.

---

### Post by iiviip3 on 2007-11-30
Thanks CDNdevil that was definitely a part of it as it does try to execute now. I've only had Ubuntu for 2.5 weeks but I love it thus far and I've learned a lot through these forumst! Appreciate the help...thanks.

This is what I get at the moment...It hangs at "iTunes_Control/Artwork/F3001_1.ithmb" so a CTRL+C brought forth the rsync error message. 

ira@lapper:~$ iphone-mount
receiving file list ... done
iPod_Control -> iTunes_Control
iTunes -> .
iTunes_Control/
iTunes_Control/iTunes_Control -> iTunes_Control
iTunes_Control/Artwork/
iTunes_Control/Artwork/ArtworkDB
iTunes_Control/Artwork/F2002_1.ithmb
iTunes_Control/Artwork/F2003_1.ithmb
iTunes_Control/Artwork/F3001_1.ithmb
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(271) [receiver=2.6.9]
rsync error: unexplained error (code 130) at rsync.c(271) [generator=2.6.9]

This is what I get on un-mount:
ira@lapper:~$ iphone-umount
fusermount: entry for /media/ipod/iTunes_Control/Music not found in /etc/mtab
building file list ... done
iTunes_Control/
iTunes_Control/Artwork/
iTunes_Control/Artwork/ArtworkDB
iTunes_Control/Device/
iTunes_Control/Device/SysInfo
iTunes_Control/iTunes/
iTunes_Control/iTunes/gtkpod.prefs
iTunes_Control/iTunes/iTunesDB
iTunes_Control/iTunes/iTunesDB.ext
iTunes_Control/iTunes/iTunesSD

sent 1060 bytes  received 464 bytes  1016.00 bytes/sec
total size is 5151  speedup is 3.38

---

### Post by superm1 on 2007-11-30
> **iiviip3 said:**
> Thanks CDNdevil that was definitely a part of it as it does try to execute now. I've only had Ubuntu for 2.5 weeks but I love it thus far and I've learned a lot through these forumst! Appreciate the help...thanks.

This is what I get at the moment...It hangs at "iTunes_Control/Artwork/F3001_1.ithmb" so a CTRL+C brought forth the rsync error message. 

ira@lapper:~$ iphone-mount
receiving file list ... done
iPod_Control -> iTunes_Control
iTunes -> .
iTunes_Control/
iTunes_Control/iTunes_Control -> iTunes_Control
iTunes_Control/Artwork/
iTunes_Control/Artwork/ArtworkDB
iTunes_Control/Artwork/F2002_1.ithmb
iTunes_Control/Artwork/F2003_1.ithmb
iTunes_Control/Artwork/F3001_1.ithmb
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(271) [receiver=2.6.9]
rsync error: unexplained error (code 130) at rsync.c(271) [generator=2.6.9]

This is what I get on un-mount:
ira@lapper:~$ iphone-umount
fusermount: entry for /media/ipod/iTunes_Control/Music not found in /etc/mtab
building file list ... done
iTunes_Control/
iTunes_Control/Artwork/
iTunes_Control/Artwork/ArtworkDB
iTunes_Control/Device/
iTunes_Control/Device/SysInfo
iTunes_Control/iTunes/
iTunes_Control/iTunes/gtkpod.prefs
iTunes_Control/iTunes/iTunesDB
iTunes_Control/iTunes/iTunesDB.ext
iTunes_Control/iTunes/iTunesSD

sent 1060 bytes  received 464 bytes  1016.00 bytes/sec
total size is 5151  speedup is 3.38
ctrl-c'ing out of this cancels the copy....which is a bad idea.  I suspect your ipod went into lock mode or sleep (and turned off wireless) which is probably why it appears to be "hanging"

---

### Post by CDNdevil on 2007-11-30
Some ideas to throw out there, is anyone able to sync with there evolution calender or tomboy notes, or put pictures on here? I just really want to get the most out of this thing that I spent so much money for thats why I keep asking.:)

---

### Post by iiviip3 on 2007-11-30
Well I CTRL+C out because it hung at that line. I set the iPhone so that it wouldn't go into lock mode and it never restart...the screen stayed at the springboard the entire time. After hanging at that line for several minutes I loaded GTKpod to see what happens and when I go to access the phone it gives a message about not finding iPod directory structure in media/ipod. If I didn't CTRL+C it would just hang forever...clearly I have done something wrong here but SSH does work flawlessly and it at least begins the ipod-convenience execution...it's not as though it fails immediately. Any ideas?

---

### Post by superm1 on 2007-11-30
> **CDNdevil said:**
> Some ideas to throw out there, is anyone able to sync with there evolution calender or tomboy notes, or put pictures on here? I just really want to get the most out of this thing that I spent so much money for thats why I keep asking.:)
I'd like to explore these venues at some point, but haven't yet.  You can be the first if you are up to the task :)

---

### Post by CDNdevil on 2007-11-30
Oh I'm up for it:) , but I will wait till I have some time off work next week, I don't wanna screw up the ipod before I go to work.

---

### Post by nikoPSK on 2007-11-30
question: how do I reset my ipod to factory defaults?

---

### Post by jack12387 on 2007-11-30
@NikoPSK, you should go to hackint0sh to ask that question ;).  The correct way to set your iphone back factory involves virginizing your seczone and do a restore to your iphone firmware (using iTunes).  Good luck, you will get more help at [http://www.hackint0sh.org/forum/forumdisplay.php?f=123](http://www.hackint0sh.org/forum/forumdisplay.php?f=123).

Edit, I just saw you wrote ipod.  Does a restore not set it back to factory settings?  I read an interesting article from hackint0sh (again you should really ask people over there), that if you turn off backup, it will do a full restore.  Apparently, USB traces/profiling have (proven?) show that an iTunes restore is in fact a full restore.  As far as a linux tool to restore your ipod-touch/iphone, i think we just have to wait (maybe for a loooooooooooong time) before it happens. -- we are at a stage where "contacts/calendar/notes" is a feature request :)

Reference: [http://www.hackint0sh.org/forum/showthread.php?t=14786](http://www.hackint0sh.org/forum/showthread.php?t=14786)

@iiviip3, you are experiencing the "hanging effect" correct?  I think the whats actually happening is the ithumb files are large and taking a while to transfer.  If you wait you will see it completely transfers.  I don't know why its so slow and why the artwork files are seemingly so large.  But I will spend time this weekend to do some (hopefully fruitful) investigation.

---

### Post by wireless on 2007-11-30
> **superm1 said:**
> I'd like to explore these venues at some point, but haven't yet.  You can be the first if you are up to the task :)

Hey Im wondering if its possible to integrate the ipod-mount and umount scripts into gtkpod?
having a mount and umount buttons in gtkpod can make it all a bit easier.
what do you think?

---

### Post by wireless on 2007-11-30
> **CDNdevil said:**
> Good to hear, did you manually download your cover art, or use gtkpod? I cant for the life of me get cover art/album to work. I still need help:confused:

Im using the get artwork from web thingie. allthough sometimes it does not find the correct one so i add it manually.

---

### Post by wireless on 2007-11-30
Hey I think i found a little bug.
for the second time, when im transefring a large amount of data to the iphone via gtkpod when pressing eject it wont eject. then with no other choise i procceed to issue iphone-umount and it umounts correctly but the data do not apear in the iphone nor in gtkpod when i reopen it.

---

### Post by superm1 on 2007-11-30
Okay folks I discussed things with the libgpod maintainer today.  There is a new workaround in 0.3-0ubuntu1~ppa1 of ipod-convenience that removes rsync from the requirements.

Syncing should be a heck of a lot faster now as the entire ArtworkDB isn't rewritten every single time.

The process should now just be 

iphone-mount
<gtkpod stuff (be sure to save changes)>
iphone-umount.

---

### Post by superm1 on 2007-11-30
Also:

This just gave me another realization.  Since the mount point is now back to the normal area:

You can use iphone-mount and iphone-umount in amarok again.  Amarok can be a complete solution (since it supports connect and disconnect commands).

---

### Post by wireless on 2007-11-30
great news !
are there any special steps that should be taken inorder to setup amarok or just follow the guide in PortableDevices/iPhone page?

---

### Post by nikoPSK on 2007-11-30
whats the great news:confused:

---

### Post by cypher35 on 2007-12-01
Sorry for the newbish questions, but I just started running through a mishmash of tutorials to get my iphone working with Amarok, and I'm a little bit confused.  I originally used the sshfs method, but am now using the iphone-mount method.

My question is this:

Is it currently possible, through Amarok, to get album art to sync along with my music, or do I have to use gtkpod for that?

I took a gander at my "Artwork" directory (*/media/iphone/iTunes_Control/Artwork*) and noticed that although there are two *.ithmb files in there, the ArtworkDB file is 0B.

Also, in Amarok I have set my "iPod Model" to "*Mobile (1) (xmobile1)*".  Is this correct, or should I be trying to trick Amarok into treating it as another iPod model?

---

### Post by wireless on 2007-12-01
yes you seted up amarok correctly. I did not managed to get artwork working with amarok. It works fine with gtkpod though.

---

### Post by jack12387 on 2007-12-01
I can be totally wrong on this but xmobile is actually motorola razr phones with iTunes? (I have this phone actually)

Again this is theortical: artwork is not working because amarok needs libgpod3 too?

---

### Post by Lord Illidan on 2007-12-01
I've read this thread with interest.

I'd like to get an Ipod Touch, but I have no Windows/Itunes whatever in my house..just Ubuntu. I wonder, how have people installed 3rd party apps etc on their Touch, and will any updates brick the touch?

---

### Post by jack12387 on 2007-12-01
@Lord Illidan

What you need is computer-less jailbreak.  The best candidate is (assuming your ipod-touch is firmware 1.1.1) to open ipod-touch safari and visit [http://jailbreakme.com](http://jailbreakme.com),  The site contains a tiff thats been "tweaked/exploited" to allow third party apps to be installed on your device.

I believe it will install necessary packages to get you started (in a series of guided steps). I have done it the manual way through windows.  But just remember that after jailbreak, you patch up the tiff exploit (again from a third party source), so nothing malicious (e.g. [http://link.brightcove.com/services/link/bcpid769469373/bctid1305477927](http://link.brightcove.com/services/link/bcpid769469373/bctid1305477927)) happens to your device.

I don't personally own a ipod touch but I think its reasonably safe (my workmate has done it).  Since you don't have a windows machine, you won't be doing any updates to worry about bricks ;).  However, when you do, you will expect that restore will wipe your device clean anyway.

I've been playing around the homebrew scene with PSP etc for a significant amount of time, and I guess the rule is to "when there is a new firmware, don't update until other people reports its fine" :P

---

### Post by Lord Illidan on 2007-12-01
What if the firmware is not that, and it's been updated by the store?

---

### Post by jack12387 on 2007-12-01
I am 99.9% confident u can downgrade (apple so far has not been as anal about downgrading as what Sony did to PSP updates)

However to downgrade u will definately need a windows/apple machine as iTunes is needed.

Also iPod touch has advantage that its less complicated to downgrade than iphone. I can positively confirm that downgrading iphones are a walking in the park.

You might already know that vmware (virtualbox too) has a bug/incompability with iPhone so virtualization is not usable.

---

### Post by wireless on 2007-12-01
i think you shouldnt be worry to much, there is a way to jailbreak with any fw. Including the latest 1.1.2 . What i dont get is why would someone buy an ipod touch, just a few more bucks and you get the same just with phone capabilities.

---

### Post by Lord Illidan on 2007-12-01
I can't buy an iphone, as it is not sold here in Malta, damn Apple and their contracts.

I was just asking, but I think I won't go ahead with it, I don't want to buy a phone or mp3 player and waste all my time trying to get it to work with my OS of choice. Apple should make it easier for Linux users, it bothers me no end how they ignore Linux users, and pay lipservice to open-ness.

Well, I won't intrude on this thread any longer, but thanks all the same.

---

### Post by wireless on 2007-12-01
I can totaly relate to what you saying mate. But I guess we shouldn't expect to much from apple side. Thank god we have so many talented people on the open source comunity who contribute their time and knowledge to make things work. I wouldn't trade Linux for any other OS in the world. and btw you can get iPhone from ebay. By the time apple will sell iPhone in your country we'll have flying cars .

---

### Post by nikoPSK on 2007-12-01
so wireless, whats up now? I was looking around and spotted this, but apparently there have been problems with it, try it out.

---

### Post by nikoPSK on 2007-12-01
lol, forgot the link:

[http://blog.adaniels.nl/?p=50](http://blog.adaniels.nl/?p=50)

---

### Post by superm1 on 2007-12-01
> **nikoPSK said:**
> lol, forgot the link:

[http://blog.adaniels.nl/?p=50](http://blog.adaniels.nl/?p=50)
Okay so now if instead you use the newer ipod-convenience (0.3 or higher) and have an ssh key saved, you can put in iphone-mount and iphone-umount in those boxes and have artwork work, and it will refresh MobileMusicPlayer and everythign else nice for you.

---

### Post by superm1 on 2007-12-01
Terc:

Since you started this thread first, would you mind editing your first post to point people at the wiki page?  I think that a lot of people will see the length of this discussion and be discouraged to read all of the pages just to find out how to get their iPhone/iPod Touch working.

Also if you can update the thread title to say something about this being relevant to the iPod touch, that would be great too.  Thanks!

---

### Post by cypher35 on 2007-12-01
Just updated amarok and ipod-convenience to the latest version off of adept.

Looks like a newly-added iPhone device option (xiPhone1), and an updated ipod-convenience package.  I'm not sure which did the trick, but album art displays perfectly now!

w00t!  No more iTunes for me!


There is a small thing I would like to mention though...  It appears that when I use iphone-mount it doesn't quit gracefully when the ip address cannot be connected to.  It seems to like placing a bunch of dummy files and symbolic links into the /media/iphone folder even though it couldn't be mounted.  As a result, the iPhone will refuse to mount again until I go in and wipe the directory clean.

It's a bit annoying, but it only happens if I accidentally try to connect to my iPhone while it's at the wrong ip address.


One last little question.  Would it be possible to correct the remaining disk space indicator at the bottom of the devices tab in amarok?  I'm not sure what it is querying to get it's information but I know I don't have a terabyte of free space on my iPhone ;)  It would be nice to know how much space is left so I don't over-fill it.

---

### Post by nikoPSK on 2007-12-01
glad to hear.;)

---

### Post by Terc on 2007-12-01
> **superm1 said:**
> Terc:

Since you started this thread first, would you mind editing your first post to point people at the wiki page?  I think that a lot of people will see the length of this discussion and be discouraged to read all of the pages just to find out how to get their iPhone/iPod Touch working.

Also if you can update the thread title to say something about this being relevant to the iPod touch, that would be great too.  Thanks!

Will Do!

Edit: Is there a way for me to chance the title of the thread when viewed from the search results page?  Title of my post now reads iPhone/iPod Touch syncing with Ubuntu, but the link from the search page is stuck on the previous title.

---

### Post by XFocus on 2007-12-01
> **cypher35 said:**
> Just updated amarok and ipod-convenience to the latest version off of adept.

Looks like a newly-added iPhone device option (xiPhone1), and an updated ipod-convenience package.  I'm not sure which did the trick, but album art displays perfectly now!

w00t!  No more iTunes for me!


I apologize in advance, I'm new to Ubuntu.  :-D

After some hesitation I installed Amarok.  I tried using it before but it was too unstable for me.  In any case, I now get amarok to mount my phone properly but in the process of syncing it has thoroughly destroyed my artwork.  I have the latest version of amarok from synaptic but I don't get the xiPhone1 plugin option.  Am I missing something?

EDIT:  I finally got it to work, however, the album art seems to be corrupt.  What I mean is that the covers are 1) of the wrong artist 2) are garbled/spliced.  It's hard to explain.  This is, however, one step closer to a complete solution.

---

### Post by misterbeetz on 2007-12-02
> **iiviip3 said:**
> Hey I'm hoping someone can help with an issue syncing my iPhone. Last week I synced over wi-fi using Amarok but when my album art got all screwed up I decided not to go that route anymore. I followed the directions for GTKPod and I was able to send a few songs over to the iPhone flawlessly but only over USB.


Please excuse my ignorance, but I was under the impression not too long ago that syncing music to the iphone over usb was not possible. Has there been a breakthrough recently in this regard?

- misterbeetz

---

### Post by Dexter. on 2007-12-02
Hey. When I follow the wiki created from users on this thread I run into a problem. At the part where you have to edit sshd_config, with: "nano /etc/sshd_config" I get a blank file in nano. Like the file doesn't exist and nano is starting with an empty file. The file does exist however, and a "cat /etc/sshd_config" shows the content, which looks normal. What could be wrong? I've tried to use vim and thats shows the content of file when I open it in vim, but from there, editing is difficult and vim won't play nice for some reason. Any help with this is appreciated. -Dexter

---

### Post by wireless on 2007-12-02
I had the same issue anyway I dont like this way of editing files. I find it dificult to use all those shurtcuts and stuff so I go ahead and edited the file with gedit. So its your call you dont have to do it the nano/vim way.

---

### Post by nikoPSK on 2007-12-02
I prefer the default text editor, gedit.:popcorn:

---

### Post by Zorael on 2007-12-02
```
zorael@azrael:~$ ssh root@iphone
Last login: Sun Dec  2 18:35:19 2007 from 192.168.0.3
# cd /etc
# ls -l sshd_config
-rw-r--r-- 1 root wheel 3230 Nov 20 02:43 sshd_config
# kate sshd_config
zsh: command not found: kate
# gedit sshd_config
zsh: command not found: gedit
# echo dern!
dern!
```

I suggested nano in the wiki since GUI editors aren't available in the ssh session, only if you mount it (which, in that part of the procedure, you haven't done yet).

```
# cd /usr/bin
# ls
awk       expand   less     passwd    simulatecrash  tar       vim
banner    false    login    paste     sort           tee       wc
basename  find     logname  pathchk   split          top       which
chgrp     fmt      mesg     pico      srelay         touch     who
cksum     fold     minicom  pr        ssh            tr        whoami
comm      grep     mkfifo   printenv  ssh-add        tsort     xargs
crontab   groups   more     readlink  ssh-agent      tty       yes
csplit    gzip     nano     renice    ssh-keygen     uname
curl      head     nc       rsync     ssh-keyscan    unexpand
cut       hexdump  nice     sar       stat           uniq
dirname   id       nl       scp       su             uptime
ditto     join     nohup    sed       sum            users
env       killall  od       sftp      tail           vi
```

Those are the available, uh, thingies. Applications. You could use vi, but I find it more difficult to use.

As for nano not working, I've no idea what could cause that.

---

### Post by wireless on 2007-12-02
Hey 
I just tried amarok to sync with iphone . i configured amarok as suggested here and also put iphone-mount and umount as the mount and unmount commands in amarok. its syncs allright but no artwork. any hints guys?

OK i was bitch*ng to soon! it works !! yay:)

---

### Post by XFocus on 2007-12-02
> **wireless said:**
> Hey 
I just tried amarok to sync with iphone . i configured amarok as suggested here and also put iphone-mount and umount as the mount and unmount commands in amarok. its syncs allright but no artwork. any hints guys?

OK i was bitch*ng to soon! it works !! yay:)

Did your artwork sync properly?  The first time I synced everything looked like it worked, but when I resynced and updated the album artwork everything went FUBAR (scrambled/wrong artwork).  Any suggestions?

---

### Post by wireless on 2007-12-02
sorry, no idea. im having other straaange (maybe related) issues. some songs i import to iphone using amarok are nameless. no tags whats or ever. when i try to fill-in tags using music brainz it gives me: Tunepimp (MusicBrainz tagging library) returned the following error: "Cannot decode audio file.".

I dont know man. im digging the sh*t out of google to find some answers. will post as soon as im on to something

EDIT: wow my bad. i mistakinly tried adding corrupted files which ment for deletion. haaaaaaaaaa what 9 hours of work can do to you man :|

Edit2: ok so final observation: it works. artwork works perfectly.

> Did your artwork sync properly? The first time I synced everything looked like it worked, but when I resynced and updated the album artwork everything went FUBAR (scrambled/wrong artwork). Any suggestions?

XFocus go through your settings in amarok make sure everything is set correctly
make sure you use the ppa version of amarok. and using the iphone-mount and umount as mounting and umounting commands and all should work!

---

### Post by cypher35 on 2007-12-02
> **Dexter. said:**
> Hey. When I follow the wiki created from users on this thread I run into a problem. At the part where you have to edit sshd_config, with: "nano /etc/sshd_config" I get a blank file in nano. Like the file doesn't exist and nano is starting with an empty file. The file does exist however, and a "cat /etc/sshd_config" shows the content, which looks normal. What could be wrong? I've tried to use vim and thats shows the content of file when I open it in vim, but from there, editing is difficult and vim won't play nice for some reason. Any help with this is appreciated. -Dexter

You have to use pico.  On my iPhone, nano is just an alias for pico, but whenever I run the nano command it fails to pass the correct file parameter to pico, so you need to make sure to call pico directly or you'll get a "new buffer", hence the empty file.

**pico /etc/sshd_config**

---

### Post by XFocus on 2007-12-02
> **wireless said:**
> 
XFocus go through your settings in amarok make sure everything is set correctly
make sure you use the ppa version of amarok. and using the iphone-mount and umount as mounting and umounting commands and all should work!

Well, I've checked and rechecked the settings and everything looks to be set fine.  I'm sure that there's something I'm missing but I'll just have to wait to see if some other solutions pops up or just wait till I garner some more patience :-\

---

### Post by ConfinedSurrealist on 2007-12-03
I am slightly depressed by the iPhone. I want to be able to use SSH access to it, but in order for me to do so I need to downgrade my firmware to 1.1.1, which requires either a mac or windows! Does anyone know how to downgrade the firmware on Ubuntu gutsy, I have a 64 bit windows at home as my gaming machine, but itunes complains about not being properly installed (due to windows be 64 bit as opposed to 32 bit)
I'm like tearing the hair off my head over this.

---

### Post by CDNdevil on 2007-12-03
Hey guys, I was able to find a couple of possible solution for syncing with contact, notes, calender question that I had earlier this week. One is the gtkpod scripts that are available haven't tested yet. Second is SyncEvolution found here [http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)
there is a jailbreak installer repo, and a Ubuntu repo, I installed both, but don't have the time to do the other stuff. It looks like a very promising solution that I really need to test, and maybe need help from people here :) apparently, you need to also use Scheduleworld as say a middle man to have the iPhone/Ipod communicate with comp. It looks very complicated to setup so I'm going to wait till the weekend to continue work on this, so if anybody is interested in this too and wants to help be my guest.

---

### Post by superm1 on 2007-12-04
> **CDNdevil said:**
> Hey guys, I was able to find a couple of possible solution for syncing with contact, notes, calender question that I had earlier this week. One is the gtkpod scripts that are available haven't tested yet. Second is SyncEvolution found here [http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)
there is a jailbreak installer repo, and a Ubuntu repo, I installed both, but don't have the time to do the other stuff. It looks like a very promising solution that I really need to test, and maybe need help from people here :) apparently, you need to also use Scheduleworld as say a middle man to have the iPhone/Ipod communicate with comp. It looks very complicated to setup so I'm going to wait till the weekend to continue work on this, so if anybody is interested in this too and wants to help be my guest.

I tried to set up scheduleworld myself recently, and they can't seem to import my gmail contacts.  Hopefully that's been fixed by now.

---

### Post by superm1 on 2007-12-04
> **ConfinedSurrealist said:**
> I am slightly depressed by the iPhone. I want to be able to use SSH access to it, but in order for me to do so I need to downgrade my firmware to 1.1.1, which requires either a mac or windows! Does anyone know how to downgrade the firmware on Ubuntu gutsy, I have a 64 bit windows at home as my gaming machine, but itunes complains about not being properly installed (due to windows be 64 bit as opposed to 32 bit)
I'm like tearing the hair off my head over this.
I ended up having to use my roomate's windows machine to do it :(

---

### Post by Mateo on 2007-12-04
how the heck are you all getting your videos onto the iphone?  that's what I can't figure out.  I can mount it with sshfs but then what?  I can't copy files to it and even if I could I wouldn't know where to put them. some help please?

---

### Post by superm1 on 2007-12-05
> **Mateo said:**
> how the heck are you all getting your videos onto the iphone?  that's what I can't figure out.  I can mount it with sshfs but then what?  I can't copy files to it and even if I could I wouldn't know where to put them. some help please?
Just drag them into gtkpod's ipod device.

---

### Post by ConfinedSurrealist on 2007-12-05
Do you think if I run a 32 bit windows on VMWare, that I could back up contacts onto that virtual machine and restore my iphone to 1.1.1 and jailbreak it?
Also do you think its smarter to keep it on firmware 1.1.1 or should I upgrade to 1.1.2?

I am aware the first one I could just try doing it, but I can't for another.. 3 hrs, and I will let ya'll know my results when I have at least attempted it.

---

### Post by superm1 on 2007-12-05
> **ConfinedSurrealist said:**
> Do you think if I run a 32 bit windows on VMWare, that I could back up contacts onto that virtual machine and restore my iphone to 1.1.1 and jailbreak it?
Also do you think its smarter to keep it on firmware 1.1.1 or should I upgrade to 1.1.2?

I am aware the first one I could just try doing it, but I can't for another.. 3 hrs, and I will let ya'll know my results when I have at least attempted it.
probably should work, but can't guarantee.  Upgrading to 1.1.2 is not a big deal once you are jailbroken, I don't think there is any incentive though to do it one way or the other.

---

### Post by ntetreau on 2007-12-06
> **ConfinedSurrealist said:**
> Do you think if I run a 32 bit windows on VMWare, that I could back up contacts onto that virtual machine and restore my iphone to 1.1.1 and jailbreak it?
Also do you think its smarter to keep it on firmware 1.1.1 or should I upgrade to 1.1.2?

I am aware the first one I could just try doing it, but I can't for another.. 3 hrs, and I will let ya'll know my results when I have at least attempted it.

Unfortunately, the iphone doesn't work on Windows when installed under vmware or virtualbox.  It seems Apple did something tricky with the USB hub...

[http://communities.vmware.com/thread/91715;jsessionid=E32FA427BE7129CA31EFAFAF64256433?tstart=0&start=90](http://communities.vmware.com/thread/91715;jsessionid=E32FA427BE7129CA31EFAFAF64256433?tstart=0&start=90)

---

### Post by Terc on 2007-12-06
> **ntetreau said:**
> Unfortunately, the iphone doesn't work on Windows when installed under vmware or virtualbox.  It seems Apple did something tricky with the USB hub...

[http://communities.vmware.com/thread/91715;jsessionid=E32FA427BE7129CA31EFAFAF64256433?tstart=0&start=90](http://communities.vmware.com/thread/91715;jsessionid=E32FA427BE7129CA31EFAFAF64256433?tstart=0&start=90)

I hear that there's a patch to enable USB connectivity for iPods under VMware, apparently this is an issue for all the new iPods (with the new USB encryption)  so, 6th gen (classic) iPod Touch and iPhone.

---

### Post by Terc on 2007-12-06
Disk Mode!

[http://www.electronista.com/articles/07/12/06/iphone.113.rumor/](http://www.electronista.com/articles/07/12/06/iphone.113.rumor/)

---

### Post by n0greenfx on 2007-12-07
ok i am using this guide i had previously jailbroken 1.1.1 cuz i have it unlocked also have ssh and bsd subsystem
i am following this guide [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
and i get and error on the second imput line which is this 
ssh-copy-id -i ~/.ssh/id_rsa.pub root@<device ip>

here is wat the terminal looks like

god@god-desktop:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/god/.ssh/id_rsa): 
Created directory '/home/god/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/god/.ssh/id_rsa.
Your public key has been saved in /home/god/.ssh/id_rsa.pub.
The key fingerprint is:
05:75:84:a3:b0:44:6f:ff:14:5b:98:46:62:61:4d:a3 god@god-desktop
god@god-desktop:~$ ssh-copy-id -i ~/.ssh/id_rsa.pub root@<192.168.1.41>
bash: syntax error near unexpected token `newline'
god@god-desktop:~$

---

### Post by wireless on 2007-12-07
Try without < > where you type your ip

---

### Post by wireless on 2007-12-07
> **Terc said:**
> I hear that there's a patch to enable USB connectivity for iPods under VMware, apparently this is an issue for all the new iPods (with the new USB encryption)  so, 6th gen (classic) iPod Touch and iPhone.

where did you got this info? Do u know where to obtain this patch?

---

### Post by n0greenfx on 2007-12-08
still having issues help lol



god@god-desktop:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/god/.ssh/id_rsa): 
/home/god/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/god/.ssh/id_rsa.
Your public key has been saved in /home/god/.ssh/id_rsa.pub.
The key fingerprint is:
7e:81:b6:3c:a3:23:b8:91:31:8e:4b:61:25:3e:a7:9d god@god-desktop
god@god-desktop:~$ ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.41
root@192.168.1.41's password: 
Permission denied, please try again.
root@192.168.1.41's password: 
Permission denied, please try again.
root@192.168.1.41's password: 
Permission denied (publickey,password).

---

### Post by Mateo on 2007-12-08
Anyone have problems with installer.app?  A lot of software I try to install, won't.  Some will though.  It gets through the download and set up process, but once the Install begins, it doesn't do anything for a second or two, then goes back to the main screen.  This happens on probably 60 or 70% of the time.

---

### Post by morky on 2007-12-08
Trying to play the songs on my iphone. but they wont play.
Used gtkpod and rhythmbox to transfer, but they wont play on the iphone.
Help??!!

---

### Post by superm1 on 2007-12-08
> **Mateo said:**
> Anyone have problems with installer.app?  A lot of software I try to install, won't.  Some will though.  It gets through the download and set up process, but once the Install begins, it doesn't do anything for a second or two, then goes back to the main screen.  This happens on probably 60 or 70% of the time.
Try removing summer board.  It's incredibly unstable (for me at least)

---

### Post by xir_ on 2007-12-09
Having a little trouble getting the iphone to work

i've followed the wiki and installed all the relevant packages.

I managed to transfer a half dozen songs but since then i haven't been able to get it to work

```
bennie@bennieboy:~$ sudo iphone-mount
ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this.
read: Connection reset by peer
bennie@bennieboy:~$ 
```


anyone? :(

---

### Post by superm1 on 2007-12-09
> **xir_ said:**
> Having a little trouble getting the iphone to work

i've followed the wiki and installed all the relevant packages.

I managed to transfer a half dozen songs but since then i haven't been able to get it to work

```
bennie@bennieboy:~$ sudo iphone-mount
ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this.
read: Connection reset by peer
bennie@bennieboy:~$ 
```
anyone? :(
First of all, don't use sudo.  You don't need to.  Matter of fact, permissions may get messed up if you do.

Second, does your ipod resolve to the address "ipod"?  If not, then it can't be contacted.  You will need to reconfigure the package with the right info.

```
DEBIAN_FRONTEND=gnome sudo dpkg-reconfigure ipod-convenience
```

---

### Post by xir_ on 2007-12-09
ok redid the IP address

here is what it got

```

bennie@bennieboy:~$ iphone-mount
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
bennie@bennieboy:~$ iphone-umount
fusermount: entry for /media/ipod not found in /etc/mtab
No matching processes were found
bennie@bennieboy:~$ iphone-mount
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

```



edit:
i rooted in and cleared the directory: seems to be ok now

thanks for the reply by the way superm1

---

### Post by ntetreau on 2007-12-10
Hi all, thanks superm1 for your great work producing the ipod-convenience package.  I am trying to get my jailbraked iphone 1.1.2 (came with the 1.1.2 firmware preinstalled in the US).  I have followed the wiki and the transfers are working fine so far.  However, like so many before my, I can't get the artword to work at all.  Once again, the songs transfer fine in both amarok and gtkpod, they play fine on the iphone.  If I delete the SysInfo file ti gets recreated on the next mount.  I also use the iphone-mount and iphone-umount as pre- and post-commands respectively in amarok.  

I'd appreciate if someone could give me a few starting point into debugging the problem.  I have been in linux for a while so I should be able to follow instructions hopefully!

Thanks again!

Nic

---

### Post by superm1 on 2007-12-10
> **ntetreau said:**
> Hi all, thanks superm1 for your great work producing the ipod-convenience package.  I am trying to get my jailbraked iphone 1.1.2 (came with the 1.1.2 firmware preinstalled in the US).  I have followed the wiki and the transfers are working fine so far.  However, like so many before my, I can't get the artword to work at all.  Once again, the songs transfer fine in both amarok and gtkpod, they play fine on the iphone.  If I delete the SysInfo file ti gets recreated on the next mount.  I also use the iphone-mount and iphone-umount as pre- and post-commands respectively in amarok.  

I'd appreciate if someone could give me a few starting point into debugging the problem.  I have been in linux for a while so I should be able to follow instructions hopefully!

Thanks again!

Nic
Nic,

Try to issue the commands from a terminal (iphone-mount and iphone-umount) and see if there is some more information about things that go astray.  Hopefully so.  If not, can you try with gtkpod instead?  I've seen some reports of artwork being fscked in amarok (even with this)

---

### Post by ntetreau on 2007-12-10
Wow, silly mistake, it turns out that I hadn't manually uninstalled gutsy's libgpod before trying to install packages from your repo.  Once I did that, everything seems to work fine.  Sorry to have bothered you with this.  Anyway, thanks for the great work once again (I'm also a user of mythbuntu, so double thanks!)

Nic

---

### Post by ntetreau on 2007-12-14
Hi, I've setup syncevolution on ubuntu and funambol (via Installer.app) after opening a ScheduleWorld account and the sync works perfectly for the contacts.  I also found a small app called genesis that fonctions as a nice gui sitting int he panel for syncing.  If anybody is having problems setting this up, I'd be happy to help.  

syncevolution: [http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)
genesis:  [http://my.opera.com/freedo/blog/2007/12/02/genesis-a-graphical-frontend-for-syncevolution](http://my.opera.com/freedo/blog/2007/12/02/genesis-a-graphical-frontend-for-syncevolution)

By the way, for those interested, gpodder seems to work well with the iphone using te iphone-mount and iphone-umount from ipod-convenience package, thanks again!

---

### Post by 1ino1eum on 2007-12-14
> **ntetreau said:**
> Hi, I've setup syncevolution on ubuntu and funambol (via Installer.app) after opening a ScheduleWorld account and the sync works perfectly for the contacts.  I also found a small app called genesis that fonctions as a nice gui sitting int he panel for syncing.  If anybody is having problems setting this up, I'd be happy to help.  

syncevolution: [http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)
genesis:  [http://my.opera.com/freedo/blog/2007/12/02/genesis-a-graphical-frontend-for-syncevolution](http://my.opera.com/freedo/blog/2007/12/02/genesis-a-graphical-frontend-for-syncevolution)

By the way, for those interested, gpodder seems to work well with the iphone using te iphone-mount and iphone-umount from ipod-convenience package, thanks again!

hello.
Thank you, I would like to have more information :
What should I exactly install on my iphone to be able to sync contact or other kind of information with ubuntu ?
Folowing the website [http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/) , I go finely there : [http://www.estamos.de/download/iphone/](http://www.estamos.de/download/iphone/). They tell I need to go to this adress with safari , but the iphone tells me that it's impossible to download the file.

I found that there is already a funambul application in the list applications. But I dont know if it's the good application.

---

### Post by 1ino1eum on 2007-12-14
I also would like to ask 2 questions about transfering music on the iphone :

- I tried with libgpod3 and gtikpod, and I have the artwork, great ! 
But I tried also with rhythmbox, and I dont have the artworks. Is it possible to have the artworks with rhythmbox, or is it only an amarok/gtkpod feature for the moment?

- Is there another way to transfer music , than with ssh? because it tooks me about 20 minutes to transfer 100 mb of music : /
it's way too long and the network is a campus network so I can't do anything :(.
The usb solution would be the best... Any hope?

thank you for all anyway, you guys are doing a great job.

---

### Post by ntetreau on 2007-12-15
Ok, i'll try to write up a short howto, it can be added to the wiki later once it's polished so try to document the steps that won't work:

Howto sync your contacts with your iphone on Ubuntu:

1. Register with ScheduleWorld.com, note your username id number (e.g. 75370) and your password.  You can play around the preferences window a bit if you'd like to sync your google calendar with evolution for example.

2. Install syncevolution:

add the syncevolution repository to your sources.list:

```

sudo gedit /etc/apt/sources.list

```

add this line:
```
deb http://www.estamos.de/download/apt stable main

```

then
```

sudo apt-get update
sudo aptitude install syncevolution-evolution-2.12

```

the version number refers to your evolution's version number, it is 2.12 in Gutsy.
copy the default.

3. Configure syncevolution [you can skip this step if you want to install the Genesis sync utility]:

```
mkdir -p ~/.sync4j/evolution
cp -r  /usr/share/doc/syncevolution/scheduleworld ~/.sync4j/evolution/
gedit ~/.sync4j/evolution/scheduleworld/spds/syncml/config.txt

```

then, change the deviceId for something that represents your computer, I used my hostname for example:

```

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = sc-api-nat

```
for
```

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = Somethingpersonnal

```

then change the username and password for your ScheduleWorld id:

```
# authorization for the SyncML server
username = your SyncML server account name
password = your SyncML server password

```
# authorization for the SyncML server
username = 75370
password = Password
[/CODE]

save, exit and try in a terminal:

```

syncevolution scheduleword

```

After a few seconds, I get a log of the transaction
```
Synchronization successful.

Changes applied during synchronization:
+-------------------|-------ON CLIENT-------|-------ON SERVER-------|
|                   |   successful / total  |   successful / total  |
|            Source |  NEW  |  MOD  |  DEL  |  NEW  |  MOD  |  DEL  |
+-------------------+-------+-------+-------+-------+-------+-------+
|          calendar |  0/0  |  0/0  |  0/0  |  0/0  |  0/0  |  0/0  |
|              memo |  0/0  |  0/0  |  0/0  |  0/0  |  0/0  |  0/0  |
|       addressbook |  0/0  |  0/0  |  0/0  |  1/1  |  0/0  |  0/0  |
|              todo |  0/0  |  0/0  |  0/0  |  0/0  |  0/0  |  0/0  |
+-------------------+-------+-------+-------+-------+-------+-------+

Changes applied to client during synchronization:
*** calendar ***
no changes
*** memo ***
no changes
*** addressbook ***
no changes
*** todo ***
no changes

```

4. [Not necessary but recommended] Install the [Genesis]("http://my.opera.com/freedo/blog/2007/12/02/genesis-a-graphical-frontend-for-syncevolution") applet

```

sudo aptitude install wget
wget --no-check-certificate https://launchpad.net/genesis-sync/trunk/0.2/+download/genesis-0.2.tar.gz
tar xvzf genesis-0.2.tar.gz
python genesis-0.2/src/genesis.py

```

If you have already configured and tested syncevolution, then you don't need to add a new server. You should be able to left-click on the applet icon next to your clock and it will nicely sync.  If not, right click on the icon and add a new server, choose scheduleworld and give it a name.  Enter your username number and password, then sync.

If you like the applet, you can add it to your session so that it is automatically started when you login Ubuntu.

To do this: System > Preferences > Sessions, then +Add

Name: Genesis
Command: python <Path to genesis-0.2>/src/genesis.py

click ok, you are all set.  You should now have your Evolution address book, task, todo list and calendar in sync with the Scheduleword server.

5. Install the [Funambol]("http://www.funambol.com/solutions/iphone.php") app using Installer.app on your iPhone or use the web based version by sending Safari to: [http://my.funambol.com/iphone](http://my.funambol.com/iphone)
> 
To get the application on the iPhone, you need the following application: Installer.app. Open Installer and install Community Sources under Sources, then select Productivity and install Funambol. It includes SyncEvolution as well (but you need the BSD subsystem to be installed on the iPhone already). Change the settings and you have over-the-air address book sync.


Once installed on your iPhone, start the app and choose "Settings" in the upper left corner.  Change the server URL, username and password:

Server:  [http://sync.scheduleworld.com/funambol/ds](http://sync.scheduleworld.com/funambol/ds)
Username:  75370
Password: Password

Save.

Then Sync All or Contacts.  

For now, only the Contacts can be synced, but I think this is gonna change soon.

---

### Post by Mateo on 2007-12-15
anyone getting cover art to work yet?

---

### Post by ntetreau on 2007-12-15
> **Mateo said:**
> anyone getting cover art to work yet?

Before you wrote this, I was the last one to figure it out.  Make sure you uninstall everything libgpod related before following the wiki (see first post.)

---

### Post by 1ino1eum on 2007-12-15
that's a really nice howto ntetreau, tkx.

Is it possible to have cover art with rhythmbox ? I only get them with gtkpod.

---

### Post by NerdyShinobi on 2007-12-17
Ok, this is a queer little problem, and I bring it up because it is my ONLY problem after following the guides.  Here it is:

Ipod -convenience is constantly showing as an update in Update Manager and Aptitude, no matter how many updates I go through.  Is there a fix for this?  Did I bork the pooch somewhere?

Otherwise, it all works flawlessly.  gtkpod, and gpodder handle all my needs perfectly through ipod-convenience.  Excellent!:guitar:

---

### Post by superm1 on 2007-12-17
> **NerdyShinobi said:**
> Ok, this is a queer little problem, and I bring it up because it is my ONLY problem after following the guides.  Here it is:

Ipod -convenience is constantly showing as an update in Update Manager and Aptitude, no matter how many updates I go through.  Is there a fix for this?  Did I bork the pooch somewhere?

Otherwise, it all works flawlessly.  gtkpod, and gpodder handle all my needs perfectly through ipod-convenience.  Excellent!:guitar:
Not at all your fault.  It's a bug in the PPA system.

[https://bugs.launchpad.net/ipod-convenience/+bug/165230](https://bugs.launchpad.net/ipod-convenience/+bug/165230)

---

### Post by CJ145 on 2007-12-17
I can't seem to get album art working with gtkpod/libgpod.

I'm not on Ubuntu so I think my problem is something to do with the ipod-convenience stuff?

I'm running Gentoo x86_64 with libgpod and gtkpod from svn (as of today).  I cleaned out all left over gtkpod/libgpod stuff from before the svn install.  I made sure to hit eject after saving the changes, but still no artwork.

If anyone could help it would be much appreciated.

---

### Post by superm1 on 2007-12-17
> **CJ145 said:**
> I can't seem to get album art working with gtkpod/libgpod.

I'm not on Ubuntu so I think my problem is something to do with the ipod-convenience stuff?

I'm running Gentoo x86_64 with libgpod and gtkpod from cvs (as of today).  I cleaned out all left over gtkpod/libgpod stuff from before the cvs install.  I made sure to hit eject after saving the changes, but still no artwork.

If anyone could help it would be much appreciated.
ipod-convenience does handle all of this for us.  I would recommend you file a bug with the appropriate places within gentoo to get ipod-convenience as an available ebuild.

---

### Post by CJ145 on 2007-12-17
> **superm1 said:**
> ipod-convenience does handle all of this for us.  I would recommend you file a bug with the appropriate places within gentoo to get ipod-convenience as an available ebuild.

The chance of someone picking this up into portage is slim to none.  I guess I will download the stuff for Ubuntu and figure out how to get it working myself.

Thanks for letting me know that I needed this package.

Edit: Ah it was surprisingly easy to edit.

All I had to do was:

change the /etc/default/ipod-convenience to /etc/ipod-convenience
edit /usr/share/ipod-convenience/mount-unmount to reflect the above change and to change the group "fuse" to "plugdev" (I don't have a fuse group).

Edit2:  Album art works great now, the script fixed it.

---

### Post by Mateo on 2007-12-17
album art only works with the SVN of gtkpod (to my knowledge).

---

### Post by ntetreau on 2007-12-17
> **Mateo said:**
> album art only works with the SVN of gtkpod (to my knowledge).

...and it works with amarok (PPA) and gpodder as well.

---

### Post by KLineD on 2007-12-18
I still can't get album art to work. I'm using iphone-mount and iphone-umount. The mounting works great, I can transfer songs to my iphone using gtkpod or amarok, however when I try to do iphone-umount as a regular user I get fusermount: failed to unmount /media/iphone: Operation not permitted

If I try it with sudo I get:

> mkdir: `/media/iphone': Permission denied
We tried to make your directory /media/iphone, but couldn't.  Please make it yourself and try again.

So to umount I need to do sudo umount /media/iphone. It unmounts the device but I don't get the artwork there, I suppose it's because of the extra stuff that iphone-umount does right?

I already added myself to the fuse group and also I have the following in my /etc/fstab file:

sshfs#root@iphone:/var/root/Media /media/iphone fuse user,noauto 0 0

Also I have the following permissions in /dev/fuse:

crw-rw---- 1 root fuse 10, 229 2007-12-17 21:51 /dev/fuse

Any thoughts on this one? thanks!

---

### Post by superm1 on 2007-12-18
> **KLineD said:**
> I still can't get album art to work. I'm using iphone-mount and iphone-umount. The mounting works great, I can transfer songs to my iphone using gtkpod or amarok, however when I try to do iphone-umount as a regular user I get fusermount: failed to unmount /media/iphone: Operation not permitted

If I try it with sudo I get:



So to umount I need to do sudo umount /media/iphone. It unmounts the device but I don't get the artwork there, I suppose it's because of the extra stuff that iphone-umount does right?

I already added myself to the fuse group and also I have the following in my /etc/fstab file:

sshfs#root@iphone:/var/root/Media /media/iphone fuse user,noauto 0 0

Also I have the following permissions in /dev/fuse:

crw-rw---- 1 root fuse 10, 229 2007-12-17 21:51 /dev/fuse

Any thoughts on this one? thanks!
During ipod-convenience installation, it created the directory and adjusted the permissions.  Are they still intact?

should be root:fuse on /media/iphone, with 775.

---

### Post by superm1 on 2007-12-18
> **KLineD said:**
> I still can't get album art to work. I'm using iphone-mount and iphone-umount. The mounting works great, I can transfer songs to my iphone using gtkpod or amarok, however when I try to do iphone-umount as a regular user I get fusermount: failed to unmount /media/iphone: Operation not permitted

If I try it with sudo I get:



So to umount I need to do sudo umount /media/iphone. It unmounts the device but I don't get the artwork there, I suppose it's because of the extra stuff that iphone-umount does right?

I already added myself to the fuse group and also I have the following in my /etc/fstab file:

sshfs#root@iphone:/var/root/Media /media/iphone fuse user,noauto 0 0

Also I have the following permissions in /dev/fuse:

crw-rw---- 1 root fuse 10, 229 2007-12-17 21:51 /dev/fuse

Any thoughts on this one? thanks!
Additionally, you don't need/want anything in your fstab about this.  It's handled all by iphone-mount.

---

### Post by KLineD on 2007-12-18
> **superm1 said:**
> During ipod-convenience installation, it created the directory and adjusted the permissions.  Are they still intact?

should be root:fuse on /media/iphone, with 775.

No they where not intact, thanks for the tip. Anyway I changed the permissions so it looks like this now:

> drwxrwxr-x  2 root fuse 4096 2007-12-17 22:18 iphone

However I still have problems when unmounting:

> cesar@frodo:/media$ iphone-mount
cesar@frodo:/media$ iphone-umount
fusermount: failed to unmount /media/iphone: Operation not permitted


Thanks for your help.

---

### Post by superm1 on 2007-12-18
> **KLineD said:**
> No they where not intact, thanks for the tip. Anyway I changed the permissions so it looks like this now:



However I still have problems when unmounting:



Thanks for your help.
okay now that permissions are intact, pull out that entry from your fstab, unmount all references to this being mounted, and empty out that directory and try once more.

---

### Post by KLineD on 2007-12-18
Still no go. I don't know if this is relevant, but in order to iphone-mount to work I had to change sshfs permissions to 755 with:

> sudo chmod 4755 /usr/bin/sshfs

If not I would always get Operation not permitted. Maybe something similar but for umount is needed?

---

### Post by superm1 on 2007-12-18
> **KLineD said:**
> Still no go. I don't know if this is relevant, but in order to iphone-mount to work I had to change sshfs permissions to 755 with:



If not I would always get Operation not permitted. Maybe something similar but for umount is needed?
Sounds to me like you didn't log out after adding yourself to the fuse group perhaps?

---

### Post by KLineD on 2007-12-18
> **superm1 said:**
> Sounds to me like you didn't log out after adding yourself to the fuse group perhaps?

Well it's been a while since I added myself to the fuse group. Since then I most definitely have logged out / in, even complete shutdown.

---

### Post by ntetreau on 2007-12-18
Here's another go at a howto... this time to sync google calendar to the iphone calendar.  I have contacted the developer to ask about syncing from the iphone to computer and also to see if he could get on the funambol app... we'll see.  Perhaps this could also be bundled with ipod-convenience?  By the way, if you'd like to sync your evolution calendar instead of google calendar, then find the path to your evolution calendar and substitute it in the howto.

To emphasize, the program is developed by Lucas.  You can check is blog here: [http://wayetender.spawnpoint.com/post/1162/#comments](http://wayetender.spawnpoint.com/post/1162/#comments) and superm1 started a lauchpad repository for development here: [https://code.launchpad.net/ical2sqlite](https://code.launchpad.net/ical2sqlite)

Syncing Google calendar with iphone (google --> computer --> iphone)

1. Install pre-requisites

```
sudo aptitude install build-essential libsqlite3-dev checkinstall
```

install libical:
```
wget http://downloads.sourceforge.net/freeassociation/libical-0.27.tar.gz?modtime=1172565976&big_mirror=0
tar xvjf libical-0.27.tar.gz
cd libical-0.27
./configure --prefix=/usr
make
sudo checkinstall

```

then ical2sqlite-0.1

```

wget http://epowerservices.com/personal/ical2sqlite-0.1.tar.gz
tar xjvf ical2sqlite-0.1.tar.gz
cd ical2sqlite-0.1
./configure --prefix=/usr
make
sudo checkinstall

```

2. Configuration

Obtain the personnal URL for your google calendar page  from the "Settings > Calendars > Your calendar name, bottom of the screen, right click on private ICAL icon and copy link".
From within the ical2sqlite-0.1 folder:

```
gedit updateipod.sh

```

Replace YOURCALENDARHERE by the copied link to your private google calendar.  Alternatively, you can insert the path to your evolution calendar.

Then replace the $1 by your iphone's IP address in:
```
scp Calendar.sqlitedb root@$1:/var/root/Library/Calendar/Calendar.sqlitedb
```

```
sudo cp ipodupdate.sh /usr/local/bin/
sudo chmod +x /usr/local/bin
```

try it!
```
updateipod.sh
```

I actually get a long error message but my Iphone's Calendar is now fully synced anyway!

---

### Post by superm1 on 2007-12-18
> **ntetreau said:**
> Here's another go at a howto... this time to sync google calendar to the iphone calendar.  I have contacted the developper to ask about syncing from the iphone to computer and also to see if he could get on the funambol app... we'll see.  Perhaps this could also be bundled with ipod-convenience?  By the way, if you'd like to sync your evolution calendar instead of google calendar, then find the path to your evolution calendar and substitute it in the howto.

Syncing Google calendar with iphone (google --> computer --> iphone)

1. Install pre-requisites

```
sudo aptitude install build-essential libsqlite3-dev checkinstall
```install libical:
```
wget http://downloads.sourceforge.net/freeassociation/libical-0.27.tar.gz?modtime=1172565976&big_mirror=0
tar xvjf libical-0.27.tar.gz
cd libical-0.27
./configure --prefix=/usr
make
sudo checkinstall

```then ical2sqlite-0.1

```

wget http://epowerservices.com/personal/ical2sqlite-0.1.tar.gz
tar xjvf ical2sqlite-0.1.tar.gz
cd ical2sqlite-0.1
./configure --prefix=/usr
make
sudo checkinstall

```2. Configuration

Obtain the personnal URL for your google calendar page  from the "Settings > Calendars > Your calendar name, bottom of the screen, right click on pricate ICAL icon and copy link".

```
gedit updateipod.sh

```Replace YOURCALENDARHERE by the copied link to your private google calendar.  Alternatively, you can insert the path to your evolution calendar.

Then replace the $1 by your iphone's IP address in:
```
scp Calendar.sqlitedb root@$1:/var/root/Library/Calendar/Calendar.sqlitedb
``````
sudo cp ipodupdate.sh /usr/local/bin/
sudo chmod +x /usr/local/bin
```try it!
```
updateipod.sh
```I actually get a long error message but my Iphone's Calendar is now fully synced anyway!
This looks great, but where is updateipod.sh?
Also, coming from the packaging community, doing stuff like checkinstall isn't ideal, but its functional for now.

---

### Post by Mateo on 2007-12-18
Ok permissions issues.... what I did was, before installing ipod-convenience, I created the /media/iPhone directory.  then I chowned it to my user.  Then after installing ipod-convenience I edited /etc/default/ipod-convenience to reflect the directory I use.  I haven't had any permissions issues since.

---

### Post by ntetreau on 2007-12-18
> **superm1 said:**
> This looks great, but where is updateipod.sh?
Also, coming from the packaging community, doing stuff like checkinstall isn't ideal, but its functional for now.

Hi superm1, sorry I don't know any alternative to checkinstall, i thought that at least it let you use synaptic to remove it later.  I'd welcome an alternate way of installing.  Do you think it would be worth adding these two last howto to the wiki?

By the way, updateipod.sh comes with ical2sqlite so it is in the same directory where you unpacked it. I've edited my post trying to make this clearer.

---

### Post by KLineD on 2007-12-18
> **Mateo said:**
> Ok permissions issues.... what I did was, before installing ipod-convenience, I created the /media/iPhone directory.  then I chowned it to my user.  Then after installing ipod-convenience I edited /etc/default/ipod-convenience to reflect the directory I use.  I haven't had any permissions issues since.

My mount point was owned by root and the fuse group. Since I'm in the fuse group I thought that should work. I'll chown it to myself and give it another go when I go home.

---

### Post by superm1 on 2007-12-19
> **ntetreau said:**
> Hi superm1, sorry I don't know any alternative to checkinstall, i thought that at least it let you use synaptic to remove it later.  I'd welcome an alternate way of installing.  Do you think it would be worth adding these two last howto to the wiki?

By the way, updateipod.sh comes with ical2sqlite so it is in the same directory where you unpacked it. I've edited my post trying to make this clearer.
Okay, i've packaged up both the packages and added them to the PPA.  The libical package was in hardy already, so I backported it temporarily.  The ical2sqlite package I had to package up.  I've submitted it to the PPA and for inclusion in hardy.  See how it works for you.

---

### Post by Will May on 2007-12-21
Hi all

I've recently brought an iPod Touch and have managed to upload music successfully by jailbreaking, etc. The only problem is that only the first album I uploaded shows it's album art correctly.

I think the problem come from the fact that I haven't set the model correctly. I've currently got it set to xiPhone1 (which is the iPhone?) and am reluctant to set it to it's correct one as the Touch says 'Read Only' next to it. Should I be setting it to it's correct one or is there a better choice? Is my problem not related to my choice of model in gtkpod?

---

### Post by superm1 on 2007-12-21
Great news folks.

ical2sqlite was accepted for Hardy.  You should be able to grab both from the PPA for now, and when you upgrade to Hardy they will be available there.

---

### Post by spacetree on 2007-12-24
Hi!

Few days ago, there was an update for amaroK (1.4.8). Before that, artwork in my iPhone worked fine. Now its gone. Any ideas someone?

---

### Post by Harold P on 2007-12-25
I'm having a problem with viewing the music on my ipod touch, unfortunately.

I can see the ipod, mount, and unmount it. But, when it comes to viewing the music on the ipod after being written to by amarok (and I've also tried gtkpod), none of the tracks show up. I make sure that I unmount before I actually check, too.

Anyone have an idea why this would happen? I'm stumped.

---

### Post by elreteipos on 2007-12-25
Tried accessing my iPod touch using gtkpod today. I can read my iPod database, but I can't save the changes I made. How come? I do have full read/write access to my iPod touch.

---

### Post by robowraith on 2007-12-25
Hi,

I installed everything as stated in the wiki (except changing the mountpoint's name and keeping a password for the login).

My setup is Kubuntu Gutsy with Amarok 1.4.8 (2:1.4.8-0ubuntu1~gutsy1), libgpod 0.6 (0.6.0-3~ppa1), GTKPOD 0.99 (0.99.10-2) and ipod-convenience 0.3 (0.3-0ubuntu1~ppa1).


Amarok connects to my iPhone and I can upload music to it. ArtworkDB is not updated and hence I can see no album art. The two files F2002_1.ithmb and F2003_1.ithmb get changed when I upload new albums or ask Amarok to update the artwork, but ArtworkDB stays at 0 bytes.

(GTKPod reports that it is unable to mmap ArtworkDB because of an invalid argument, but I read elsewhere that mmaping is supposed to be impossible via sshfs anyway.)


Any ideas?


rw

---

### Post by superm1 on 2007-12-25
> **robowraith said:**
> Hi,

I installed everything as stated in the wiki (except changing the mountpoint's name and keeping a password for the login).

My setup is Kubuntu Gutsy with Amarok 1.4.8 (2:1.4.8-0ubuntu1~gutsy1), libgpod 0.6 (0.6.0-3~ppa1), GTKPOD 0.99 (0.99.10-2) and ipod-convenience 0.3 (0.3-0ubuntu1~ppa1).


Amarok connects to my iPhone and I can upload music to it. ArtworkDB is not updated and hence I can see no album art. The two files F2002_1.ithmb and F2003_1.ithmb get changed when I upload new albums or ask Amarok to update the artwork, but ArtworkDB stays at 0 bytes.

(GTKPod reports that it is unable to mmap ArtworkDB because of an invalid argument, but I read elsewhere that mmaping is supposed to be impossible via sshfs anyway.)


Any ideas?


rw
Upgrade to the newer amarok on the ppa.

---

### Post by robowraith on 2007-12-25
Thanks superm1!

I upgraded Amarok to the version from ppa. Now the ArtworkDB gets updated but I still see no album art.Tried multiple times to update the artwork, upload new albums, reset the Ipod app, restart the Iphone, even  restarted Kubuntu.

Any (further) ideas? :-)

Thanks.

rw

---

### Post by Harold P on 2007-12-25
> **Harold P said:**
> I'm having a problem with viewing the music on my ipod touch, unfortunately.

I can see the ipod, mount, and unmount it. But, when it comes to viewing the music on the ipod after being written to by amarok (and I've also tried gtkpod), none of the tracks show up. I make sure that I unmount before I actually check, too.

Anyone have an idea why this would happen? I'm stumped.
Wow. What the heck is going on. I was able to put music on my ipod from windows, but when I wrote to it with amarok, all of my music disappeared.

This is getting very frustrating. I'm about ready to pull all of my hair out.

---

### Post by Terc on 2007-12-26
[http://code.google.com/p/t-pot/](http://code.google.com/p/t-pot/)

Wow, I just wrote (from windows) to the iPod Touch through USB 2.0

Is there anyone out there with experience using this with Linux?  This is defiantly my new preferred method of file access on the iPhone/iPod Touch.

---

### Post by jasonrandolph on 2007-12-26
Okay, I checked out the Wiki page, and the jailbreaking page it links to says the method works on the iPod Touch, not the iPhone.  Is this true?  And if so, where can I find out how to jailbreak my iPhone?

---

### Post by robowraith on 2007-12-26
For jailbreak instructions check out [http://www.hackint0sh.org]("http://www.hackint0sh.org")


rw

---

### Post by ntetreau on 2007-12-27
@superm1:  I get a lot of these errors:

> iphone-mount 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option


I usually have to do a 
```
rm -fr /media/iphone/*
```

Is there a better way to do this?  Perhaps one could integrate this "noempty" mount option?

Nic

---

### Post by ntetreau on 2007-12-27
> **superm1 said:**
> Great news folks.

ical2sqlite was accepted for Hardy.  You should be able to grab both from the PPA for now, and when you upgrade to Hardy they will be available there.

Thanks superm1 for packaging ical2sqlite in your PPA and Hardy.  I forgot to mention that the author is Lucas "Wayetender" Waye (his blog: [http://wayetender.spawnpoint.com/archive/2007/](http://wayetender.spawnpoint.com/archive/2007/)).  I will try to contact him to get him to work on the bzr repository with you.  Perhaps it could be possible to get iphone-->evolution/google calendar working?

Thanks.

---

### Post by superm1 on 2007-12-27
> **ntetreau said:**
> @superm1:  I get a lot of these errors:



I usually have to do a 
```
rm -fr /media/iphone/*
```Is there a better way to do this?  Perhaps one could integrate this "noempty" mount option?

Nic
If there are items showing up in /media/iphone, something else is going wrong.  The directory should be empty at all times (otherwise your iphone will likely get out of sync at some point).

Try to describe exactly the order you are doing things to cause this to happen.

---

### Post by superm1 on 2007-12-27
> **ntetreau said:**
> Thanks superm1 for packaging ical2sqlite in your PPA and Hardy.  I forgot to mention that the author is Lucas "Wayetender" Waye (his blog: [http://wayetender.spawnpoint.com/archive/2007/](http://wayetender.spawnpoint.com/archive/2007/)).  I will try to contact him to get him to work on the bzr repository with you.  Perhaps it could be possible to get iphone-->evolution/google calendar working?

Thanks.
Yeah that's the blog I came across when I created the copyright file for his package.  No problem on the packaging, it's the easy part :)

As for working on iphone->evolution/google calendar, we'll see.  I've got lots of other things i'm working on simultaneously.

---

### Post by robowraith on 2007-12-27
@superm1:

My ArtworkDB gets updated now (and is larger than zero bytes), but I can still see no album art. 

Any ideas? Any info that I could provide that might clear things up?

Thank you!

rw

---

### Post by superm1 on 2007-12-27
> **robowraith said:**
> @superm1:

My ArtworkDB gets updated now (and is larger than zero bytes), but I can still see no album art. 

Any ideas? Any info that I could provide that might clear things up?

Thank you!

rw
Are you sure its properly associated in Amarok with the songs?  The DB does grow (even when you don't set artwork) as the song list grows.

---

### Post by ntetreau on 2007-12-27
> **superm1 said:**
> Yeah that's the blog I came across when I created the copyright file for his package.  No problem on the packaging, it's the easy part :)

As for working on iphone->evolution/google calendar, we'll see.  I've got lots of other things i'm working on simultaneously.

Let Lukas and the Funambol/syncevolution sort it out then. 

I'll try to find out how I get the nonempty problem and post about it.

---

### Post by robowraith on 2007-12-27
> **superm1 said:**
> Are you sure its properly associated in Amarok with the songs?  The DB does grow (even when you don't set artwork) as the song list grows.

I guess so. I downloaded the album art in amarok with the cover manager. I don't know how I could change their association with the mp3-files.

Not only does the ArtworkDB grow, but also the two .ithmb files.

Sometimes, when I transfer music or update artwork in amarok, disconnect, umount, start the iPod app, reset it (pressing the home button for five seconds) and try to restart it, it shows me an iPod app with a black background that maybe has black writing on it.

Maybe it tries to read the ArtworkDB and fails?

rw

---

### Post by robowraith on 2007-12-27
And BTW, I also get the problem with leftovers in the media/ipod directory from time to time.

rw

---

### Post by Will May on 2007-12-28
I have had the same problem and with a bit of investigation have discovered that it's okay when setting the artwork on a completely blank iPod, but it doesn't work correctly if you are adding an album with art. It also doesn't add the artwork correctly if you do an rm * in the Artwork directory and then reset all the artwork.

I'm using the latest of gtkpod-aac from ppa.launchpad.net on a 64bit machine. I noted earlier in this thread that it said that you needed to compile gtkpod from svn to get the artwork working; is this still the case?

---

### Post by superm1 on 2007-12-28
> **Will May said:**
> I have had the same problem and with a bit of investigation have discovered that it's okay when setting the artwork on a completely blank iPod, but it doesn't work correctly if you are adding an album with art. It also doesn't add the artwork correctly if you do an rm * in the Artwork directory and then reset all the artwork.

I'm using the latest of gtkpod-aac from ppa.launchpad.net on a 64bit machine. I noted earlier in this thread that it said that you needed to compile gtkpod from svn to get the artwork working; is this still the case?
afaik, there are no improvements in svn (that aren't present in the release of gtkpod on the ppa).  the improvements are all in libgpod3, which has already been added to the ppa.

---

### Post by Will May on 2007-12-28
Damn, already got libgpod3. Looking through the packages in ppa there is a 'libgpod-common'. Should this be installed as well?

---

### Post by ntetreau on 2007-12-28
> **Will May said:**
> Damn, already got libgpod3. Looking through the packages in ppa there is a 'libgpod-common'. Should this be installed as well?

I know I have it installed, so you can at least try it. By the way, make sure you have everything non-ppa purged, just in case you would have two copies of libgpod installed. 

Nic

---

### Post by robowraith on 2007-12-29
Still no album art. 

I have purged all affected packages to make sure that I have no non-ppa versions.

Interestingly, the TuneWiki app shows broken album art (ipod app shows none)

Any help would be greatly appreciated!

rw

---

### Post by Big G on 2007-12-29
Having no luck with Album art either. Am using ipod convenience fom PPA (which the sympatic keeps reporting as having update available.) The iphone-mount control works fine and am able to copy music to the iphone no problem. I can see the artwok in Gtkpod but not on the phone. I do get the following error reported when I use iphone-umount to unmount the phone -"zsh: command not found: killall". I suspect this could have something to do with the problem. An ideas?
Have also tried the manual method of mounting the phone using "sshfs root@192.168.11.100:/var/root/Media/ /media/ipod/". Again this mounts ok and I was using "sudo umount /media/ipod" to unmount the phone. Here it appeared to unmount ok but again no artwork.
I believe I am doing everything in the correct order: mount the phone, lauch gtkpod and copy some files, press save, eject iphone , close gtkpod and unmount the phone. Have also tried using Amarok with no artwork success either.
Any help would be greatly appreciated. Have been working on this for days now!
Cheers :-)

---

### Post by ntetreau on 2007-12-29
> **Big G said:**
> Having no luck with Album art either. Am using ipod convenience fom PPA (which the sympatic keeps reporting as having update available.) The iphone-mount control works fine and am able to copy music to the iphone no problem. I can see the artwok in Gtkpod but not on the phone. I do get the following error reported when I use iphone-umount to unmount the phone -"zsh: command not found: killall". I suspect this could have something to do with the problem. An ideas?
Have also tried the manual method of mounting the phone using "sshfs root@192.168.11.100:/var/root/Media/ /media/ipod/". Again this mounts ok and I was using "sudo umount /media/ipod" to unmount the phone. Here it appeared to unmount ok but again no artwork.
I believe I am doing everything in the correct order: mount the phone, lauch gtkpod and copy some files, press save, eject iphone , close gtkpod and unmount the phone. Have also tried using Amarok with no artwork success either.
Any help would be greatly appreciated. Have been working on this for days now!
Cheers :-)

You might be missing the killall command which, if I remember correctly, is part of the BSD utils.  Please double check that this is indeed installed on your iphone through install.app.

---

### Post by lost123 on 2007-12-29
Hi
Im new to ubuntu and im actually using Linux Mint and am looking to setup my ipod touch with it...Im followung the guide on wiki and Iv done everything on the ipod touch side and was wondering what exactly i would have to do in ubuntu(linux mint)...After i set up the 'passwordless login', do i just install 'ipod-convenience' and then i can setup Amarok?...im asking this as iv already done this before and it kept telling me that i wasnt in the fuse group...after some messing around i mannaged to get it to sync but the album art was all wrong and then latter the album art would all be gone..so iv started off with a fresh install of linux mint and th eipod touch and was just wandering what im ment to do and what i might have done wrond before...Also last time when i did this '# ls -al ~/.ssh' the permmison was not the same as the one listed in the guide :confused: 
someone please help me out...

---

### Post by robowraith on 2007-12-30
IT WORKED!

I have album art now. I tried Gtkpod again after reading the last replies here and noticed that it indeed showed the correct cover art but destroyed it when trying to write to ArtworkDB. I then poked around Amarok and noticed that the version from ppa has additional iPod Models listed. The old version only had "xmobile", but the new version has the Model "xiphone". Now Artwork works!

Thanks guys!

f

P.S.: Who knows how to sync the Contacts with Kontact? :-D

---

### Post by Big G on 2007-12-30
> **jack12387 said:**
> Good news, after I scp'd killall to /usr/bin, Album Art does appear on my iphone :)

Here are couple of medium-level annoyances (they are not show-stopping issues)

1) Upon iphone-umount, You will get a "No matching processes were found" error if MobileMusicPlayer is not started. *Work around*: turn on your iphone/ipod touch's ipod app.

2) Suppose I need to set covers on 10 albums, After the first attempt (iphone-mount->gtkpod->iphone-umount), you will not see any album covers, You shall finally see the covers from the first attempt when adding cover to a 11th album on the next (iphone-mount->gtkpod->iphone-umount) cycle. *Work around*: Do you first (iphone-mount->gtkpod->iphone-umount) cycle of setting covers for your albums. Then perform iphone-mount->gtkpod->bulk edit comments->iphone-umount cycle, All covers should be set properly.

3) Videos lose their "cover" too.  iTunes  puts a preview image as a cover for each video, gtkpod seem to set them as gray art.  I'm not too concerned about this.  Also I haven't tried your gtkpod-aac yet.


For people who don't have killall on their iphone.  I managed to get hold of a bundle which contains it from a unlock 1.1.1. thread at hackint0sh ([http://www.hackint0sh.org/forum/showthread.php?t=12817](http://www.hackint0sh.org/forum/showthread.php?t=12817))

The bundle which contains killall: [http://d.turboupload.com/d/2098918/unlock111.zip.html](http://d.turboupload.com/d/2098918/unlock111.zip.html)

Don't forget to chmod the executable once its on your device.


**If you got it working, can you tell me how big are your ithmb files? For one album I'm getting about 4mbs of thumb files in my Artworks folder!**

Hi Guys
Found the above post. I was missing killall file despite having installed and reinstalled BSD subsystem. I have since found killall file and transfered it to my phone's /usr/bin folder. I set the file permission's to all rwx and now I get no error's on unmount using iphone-umount.-Initially got the "No matching processes were found" error but solved it as above by making sure Ipod app was open on phone before unmounting. I also read note 2) above  about artwork not apprearing straight away. I added 11 albums to the phone using sequence mount->gtkpod->save->eject->unmount. After that I added another album using same sequence mount->gtkpod->save->eject->unmount once more.
Still no artwork on phone though. Any ideas anyone it is getting to be just a little tedious now!!
Cheers
Big G
:-)

---

### Post by ntetreau on 2007-12-30
> **Big G said:**
> Hi Guys
Found the above post. I was missing killall file despite having installed and reinstalled BSD subsystem. I have since found killall file and transfered it to my phone's /usr/bin folder. I set the file permission's to all rwx and now I get no error's on unmount using iphone-umount.-Initially got the "No matching processes were found" error but solved it as above by making sure Ipod app was open on phone before unmounting. I also read note 2) above  about artwork not apprearing straight away. I added 11 albums to the phone using sequence mount->gtkpod->save->eject->unmount. After that I added another album using same sequence mount->gtkpod->save->eject->unmount once more.
Still no artwork on phone though. Any ideas anyone it is getting to be just a little tedious now!!
Cheers
Big G
:-)

I have a tendency to write the obvious but let's try anyway!  I fixed yesterday my own album art problems (it worked flawlessly for the longest time) in Amarok by letting it reload ALL the album art again.  In my case, it started by deleting all of them, then synced them again, that took about an hour for me (full 8gb used).  Check the screenshot to Update Artwork, but in a nutsheel you need to click the little arrows -> iPod -> Update artwork.  While you're there, take a sec to double check that you have indeed selected the iPhone in the list, nothing else.

It will work when all the pieces of this puzzle are in place.  We need to submit bug reports for superm1 to help make a more robust solution.  

Nic

---

### Post by ntetreau on 2007-12-30
Ok superm1, I finally found the cause of my 'nonempy' problem.  This happens when I have the impression that the iphone is connected to the network but isn't (or ssh is down for example).  Then, a directory tree gets created under /media/iphone/*, It includes these newly created folders:
iPod_Control  iTunes  iTunes_Control
I can guess that the folders are getting created when the firewireID is written?  Anyway, it probably should write there before the iphone gets mounted anyway.

The obvious consequence is that next time I try to mount the iphone, I get this error message:

```
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

```

It isn't clear if the problem is a result of a misconfiguration on my part or a misbehaving script but I thought it would be a good habit to start writing proper bug report:
[https://bugs.launchpad.net/ipod-convenience/+bug/179489](https://bugs.launchpad.net/ipod-convenience/+bug/179489)

Nic

---

### Post by ntetreau on 2007-12-30
>  Originally Posted by jack12387  View Post
Good news, after I scp'd killall to /usr/bin, Album Art does appear on my iphone

Here are couple of medium-level annoyances (they are not show-stopping issues)

1) Upon iphone-umount, You will get a "No matching processes were found" error if MobileMusicPlayer is not started. Work around: turn on your iphone/ipod touch's ipod app.

2) Suppose I need to set covers on 10 albums, After the first attempt (iphone-mount->gtkpod->iphone-umount), you will not see any album covers, You shall finally see the covers from the first attempt when adding cover to a 11th album on the next (iphone-mount->gtkpod->iphone-umount) cycle. Work around: Do you first (iphone-mount->gtkpod->iphone-umount) cycle of setting covers for your albums. Then perform iphone-mount->gtkpod->bulk edit comments->iphone-umount cycle, All covers should be set properly.

3) Videos lose their "cover" too. iTunes puts a preview image as a cover for each video, gtkpod seem to set them as gray art. I'm not too concerned about this. Also I haven't tried your gtkpod-aac yet.



1) Let's write it up as a bug report so at least the problems are recorded and progresses on solutions can be followed:
[https://bugs.launchpad.net/ipod-convenience/+bug/179490](https://bugs.launchpad.net/ipod-convenience/+bug/179490)

2) Since I can't remember having been bitten by this bug, and it doesn't affect me yet, I suggest you open a new bug report yourself.  This way you'll be able to give more details.

3)  In my case, I have only synced video podcasts using gpodder, and they had the podcast logo.  Perhaps you can open another bug report for this one and I'll try to reproduce it.

---

### Post by ntetreau on 2008-01-02
Just encoded and transfered my first DVD to the iphone using this guide: 
[http://tombuntu.com/index.php/2008/01/01/convert-dvds-for-your-ipod-touchiphone-with-handbrakegtk/](http://tombuntu.com/index.php/2008/01/01/convert-dvds-for-your-ipod-touchiphone-with-handbrakegtk/)

Worked fine transfering with gtkpod by the way,

---

### Post by superm1 on 2008-01-02
> **ntetreau said:**
> Just encoded and transfered my first DVD to the iphone using this guide: 
[http://tombuntu.com/index.php/2008/01/01/convert-dvds-for-your-ipod-touchiphone-with-handbrakegtk/](http://tombuntu.com/index.php/2008/01/01/convert-dvds-for-your-ipod-touchiphone-with-handbrakegtk/)

Worked fine transfering with gtkpod by the way,
This looks quite promising.  I'll give it a shot later this week hopefully.

---

### Post by superm1 on 2008-01-02
> **ntetreau said:**
> 1) Let's write it up as a bug report so at least the problems are recorded and progresses on solutions can be followed:
[https://bugs.launchpad.net/ipod-convenience/+bug/179490](https://bugs.launchpad.net/ipod-convenience/+bug/179490)

2) Since I can't remember having been bitten by this bug, and it doesn't affect me yet, I suggest you open a new bug report yourself.  This way you'll be able to give more details.

3)  In my case, I have only synced video podcasts using gpodder, and they had the podcast logo.  Perhaps you can open another bug report for this one and I'll try to reproduce it.
Okay i've fixed up those two bugs you filed.  Most appreciated!

---

### Post by Leed on 2008-01-03
Hi guys

Could you please give me a more clear description of how you solved these problems?

I have the issue with not getting any Album Cover art on my ipod touch... tried it on three different Computers, always the same problem. Mounting works perfectly, Transfer from Amarok is perfect, unmounting works. 
Just the Cover Art won't, pretty anoying for it was one of the main reasons I bougth the Ipod Touch.

I know quite a bit on computers and am getting used to ubuntu, but I still can't do much with comments like poking around in amarok and ppa or scp'd killall to /usr/bin... isn't killall just to stop processes from running? Are you doing that on the ipod or the pc... 

Please help, I'd love to get cover art working, been on it since twelve hours

---

### Post by ntetreau on 2008-01-03
> **Leed said:**
> Hi guys

Could you please give me a more clear description of how you solved these problems?

I have the issue with not getting any Album Cover art on my ipod touch... tried it on three different Computers, always the same problem. Mounting works perfectly, Transfer from Amarok is perfect, unmounting works. 
Just the Cover Art won't, pretty anoying for it was one of the main reasons I bougth the Ipod Touch.

I know quite a bit on computers and am getting used to ubuntu, but I still can't do much with comments like poking around in amarok and ppa or scp'd killall to /usr/bin... isn't killall just to stop processes from running? Are you doing that on the ipod or the pc... 

Please help, I'd love to get cover art working, been on it since twelve hours

Hi Leed,  no worries, everyone get it working in the end!  This process is even more streamlined in the next version of Ubuntu, thanks to superm1. 

Since this is your first post in this thread, we'll have to start for... well the start, which is the wiki/guide.  You have to follow exactly all the steps, if one of the step isn't working, write back with as much details as you can gather.  

In a nut shell, you need to REPLACE the amarok, libgpod, gtkpod from ubuntu with the versions within the PPA repository (check the wiki).  You setup amarok or gtkpod for the iphone (check my post three posts up, it has a picture as well).  You setup ssh to login to your iphone.  

Go through  the wiki one step at a time:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by Leed on 2008-01-03
Wicked! You did it ntetreau, my worries of having to try using iTunes are over 
:guitar:

The Link you gave me was exactly the one I've been using all day long, but it's that Picture you sent that made the difference... 
After scanning through all the menus in Amarok I would have never guessed that there is another hidden little one there that makes all the difference. Now even all my Playlists look totally different and the Artwork is there. No additional installs or editing configs and sniffing network protocols necessary.

Thanx a million.

---

### Post by quietthunder on 2008-01-04
Hi All,

I'm able to get everything installed and running to the point where gtkPod/Amarok picks up the ipod touch properly and I'm able to listen to the music.

Unfortunately whenever I do, I end up not being able to play songs on my iPod itself (after running iphone-umount). Somehow something along the lines of an indexing file seems to get corrupted on the iPod if I play a song. If I use the tools to just copy songs, things work fine.

Upon connecting the iPod back to a windows box, it complains about not being able to read the iPod and doesn't give an error code. I've tried restoring the iPod a couple of times but end up with the same issue.

Any help would be great, 
Thanks.

---

### Post by robowraith on 2008-01-04
Hi,

I'm converting videos for the iPhone using avidemux and upload them via the "Transfer file to device" function in Amarok. Unfortunately, the filename is not transfered to the database and so, I can upload only one (nameless) video. If I try to upload another one, Amarok tells me that there is alreasy a file ' ' on the device.

How did you get video upload to work?

rw

---

### Post by ntetreau on 2008-01-04
@quietthunder:  sorry but it isn't clear to me exactly when it is that you can and cannot play your music, when it is that the database gets corrupted and what steps you are taking to achieve this.  Please, give more details.

@robowraith:  I used handbrakegtk to convert my movie, then drag it over entry fro my iphone on the left pane in gtkpod, saved, waited a good long time, then iphone-umount.

---

### Post by lx01 on 2008-01-05
Hi,
> **robowraith said:**
> Hi,

I'm converting videos for the iPhone using avidemux and upload them via the "Transfer file to device" function in Amarok. Unfortunately, the filename is not transfered to the database and so, I can upload only one (nameless) video. If I try to upload another one, Amarok tells me that there is alreasy a file ' ' on the device.

How did you get video upload to work?

rw
I think you need to embed that Information into the video itself. To do so, first upload your file as usual, close amarok and re-connect your phone with gtkpod (amarok didn't work for me here). Then right-click your "empty" file and choose "Edit Track Details". Now you can enter artist-/title-information as you wish. 
These steps at least worked for me...

Another solution would be to encode by command-line with ffmpeg., which has the options "-title" and "-author".

BTW: I did not succeed (yet) encoding video that is playable on my ipod touch when using avidemux. Would you mind to share your settings?

---

### Post by ntetreau on 2008-01-05
Has anybody been able to syncronize nicely video podcast with his iphone?  I've used Amarok and gPodder, they both download the videos (.m4v) and transfer them to the device.  They then appear in the podcast list but they play as audio instead of video.  

If, instead, I drag then on my iphone in gtkpod, they are transfered as well but appear in the video section on the iphone, they then play fine as video file.

The best would be to have Amarok or gPodder deal with the feed as podcasts (they can remove the old ones for example), but somehow add them to the database as videos.

As anybody succeeded in doing so?  How?

Edit:  You can try with this feed if you'd like to give video podcast a shot, it ain't half bad!
[http://www.cbcradio3.com/podcast/video/iTunes/](http://www.cbcradio3.com/podcast/video/iTunes/)

---

### Post by Mateo on 2008-01-05
i have both the newest SVN of libgpod and the newest SVN of gtkpod and STILL can't get album art to work.  i even checked during ./configure that it said that libgpod had album art support.  I can add the album art, then I save and close GTKPOD.  then i unmount the iphone.  Then I "reset" the iphone by holding down on the home button for 5 seconds.  but then I look and bam, no album art. very very frustrating.

---

### Post by superm1 on 2008-01-05
> **Mateo said:**
> i have both the newest SVN of libgpod and the newest SVN of gtkpod and STILL can't get album art to work.  i even checked during ./configure that it said that libgpod had album art support.  I can add the album art, then I save and close GTKPOD.  then i unmount the iphone.  Then I "reset" the iphone by holding down on the home button for 5 seconds.  but then I look and bam, no album art. very very frustrating.
Considering you are opting for SVN versions of these packages rather than pre-packaged versions on the PPA, how are you mounting?

Are you using iphone-mount?

---

### Post by Mateo on 2008-01-05
made my own mount scripts.  mount:

sshfs root@192.168.1.101:/var/root/Media/ /media/iPhone/

unmount:

fusermount /media/iPhone -u

---

### Post by superm1 on 2008-01-06
> **Mateo said:**
> made my own mount scripts.  mount:

sshfs root@192.168.1.101:/var/root/Media/ /media/iPhone/

unmount:

fusermount /media/iPhone -u

You should really look to switching to iPod convenience.  It handles several nice items such as permissions, directory creation, pinging the device to make sure it is responding as well as proper sshfs mount options.

If for some reason you opt not to use it, you should at least look at the sshfs mount options that it uses.

---

### Post by Mateo on 2008-01-06
i appreciate the consideration, but until they fix ipod-conveniences problem of installing every time you run apt-get install upgrade, and they start putting out keys for PPAs, i'm not using it.

Regardless, it has 0 to do with my problem.

---

### Post by superm1 on 2008-01-06
You missed my point entirely.

sshfs mount options is your problem.

sshfs can't mmap the ArtworkDB, so you need the workaround mount option (which is part of ipod-convenience).  This is why i said to at least look at it.

---

### Post by Mateo on 2008-01-06
ok, i'll try it right now and see if that is indeed the problem.

---

### Post by robowraith on 2008-01-06
> **lx01 said:**
> BTW: I did not succeed (yet) encoding video that is playable on my ipod touch when using avidemux. Would you mind to share your settings?

I've just encoded one video with it, maybe it was a blind hit? A encoded a xvid by setting video to x264, audio to faac and format to mp4. It worked.

Edit: just tried it with a second video after I successfully renamed the first one. Converting didn't work this time. The iPhone plays the audio part, but not the video (black screen)

rw

---

### Post by robowraith on 2008-01-06
> **lx01 said:**
> Hi,

I think you need to embed that Information into the video itself. To do so, first upload your file as usual, close amarok and re-connect your phone with gtkpod (amarok didn't work for me here). Then right-click your "empty" file and choose "Edit Track Details". Now you can enter artist-/title-information as you wish. 
These steps at least worked for me...

Another solution would be to encode by command-line with ffmpeg., which has the options "-title" and "-author".


The method works but is a little bit unwieldy. :-) What settings do you use for converting with ffmpeg? Is there a guide somewhere? Maybe one that lists the necessary settings for the iPhone?

Thanks.

rw

---

### Post by Mateo on 2008-01-06
here's my script for converting videos:

```
#!/bin/bash
ffmpeg -i "$1" -r 29.97 -vcodec h264 -s 480x320 -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 80k -ar 48000 -ac 2 "$2"
```

it makes it the perfect size to fit the screen.  you just do it like:

./script SOURCE_FILE DESTINATION_FILE

i don't do anything with titles though, but that does seem easy enough.

---

### Post by robowraith on 2008-01-06
Hm.

Not only does ffmpeg tell me "unknown audio codec aac" (and surprisingly its right, ffmpeg -formats does not list aac) but if I set it to "-acodec copy"  I get "Unsupported codec for output stream #0.0". Stream #0.0 is "Stream #0.0: Video: 0x0000, yuv420p, 480x320, q=10-51, 1000 kb/s, 29.97 fps(c)". I think I installed all codecs known to man, but it seems I missed some.

How do I install aac so that ffmepg will see it? What do I miss so that ffmpeg will be able to generate that output stream? 

Thanks

rw

---

### Post by lx01 on 2008-01-06
> **robowraith said:**
> 
Edit: just tried it with a second video after I successfully renamed the first one. Converting didn't work this time. The iPhone plays the audio part, but not the video (black screen)

Yeah, that's what my problem was.
Anyway, i've just upgraded to Avidemux 2.4. There is now an ipod-preset (using xvid rather than x264), which works just fine...:) (you may have to boost the bitrate to get a good looking video though)

> 
The method works but is a little bit unwieldy. What settings do you use for converting with ffmpeg? Is there a guide somewhere? Maybe one that lists the necessary settings for the iPhone?
I basically used this guide:

[https://help.ubuntu.com/community/iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding")
(Section "H.264 Encoding")

and added the "-title" and "-author" options to the second command.

BTW: What part do you mean by "unwieldy"? Using gtkpod to rename oder using ffmpeg to encode?

> 
How do I install aac so that ffmepg will see it? What do I miss so that ffmpeg will be able to generate that output stream? 
I'm afraid I can't help you here (i'm on Fedora, ffmpeg/aac works out-of-the-box here), but i ithink this is also covered in that guide.

---

### Post by robowraith on 2008-01-06
Great, Thank you.

I'll check that guide out.

I found the prospect of converting Videos, starting amarok, connecting the iPhone, copying them onto the iPhone, diconnecting the iPhone, starting gtkpod, having it reindex the, now changed, iPhone library, remnaming the video, ejecting the iPhone, going to amarok to add a second video ..... a little bit unwieldy. :-)

rw

---

### Post by robowraith on 2008-01-06
ffmpeg didn't recognize aac because the version in official (K)ubuntu wasn't built with the right options. The version from the Medibuntu repository in the guide you posted workd though.

I haven't been able to set the title in a way that the iPhone will recognize. I will experiment further.

Thanks.

rw

---

### Post by danip on 2008-01-06
> **tribaal said:**
> Well for a short set of instructions on how to sync your iphone with gutsy's gtkpod (don't know about feisty):

- Install ssh on your iphone. There are many howtos on the internet on how to do this, I'm not going to explain it here (it's pretty long on top of that).

- Install sshfs ("sudo apt-get install sshfs"). This is what lets you mount ssh filesystems, we'll use this to mount our iphone.

- Create a mountpoint. I use /media/ipod. ("sudo mkdir /media/ipod"). Make sure you got read/write access to it ("sudo chown <username> /media/ipod").

- To use sshfs you need to be in the "fuse" user group ("sudo adduser <username> fuse")

- Log out and back in again (this is necessary for your user group to be taken into account).

- Now the fun part. Go to the wifi settings on your iphone. tap the blue arrow next to your SSID, so that you can see your iphone's IP address. Note it down somewhere.

- Go to your general settings and set "auto-lock" to "never" (the iphone closes the wifi connection when it's locked).

- Open a terminal in ubuntu and do "ssh root@<your iphone's ip address>" (default password is "dottie", change it ASAP with the "passwd" command once loged in).

- If you didn't change your password on your iphone, do it now with the "passwd" command.

This is a BSD-like shell. Most of the commands are the same than in ubuntu, but I highly suggest you don't try anything funny if you don't want to brick your phone.

- move to where the iTunes library is: "cd /var/root/Media"
- make a symbolic link to this directory from within itself (weird, but necesserary): "ln -s . iTunes"
- make another symbolic link to the iTunes_Control directory called iPod_Control: "ln -s iTunes_Control iPod_Control"

- Get out of the iphone. "exit"

In ubuntu now, we need to actually perform the mount!

"sshfs root@<iphone's ip address>:/var/root/Media/ /media/ipod/"

Your Iphone should appear in gtkpod! Congratulations! Some errors are displayed, and you need to be root to unmount the iphone ("sudo umount /media/ipod"), but otherwise it works pretty well.

And wifi sync is something you couldn't do with iTunes and a Mac :) It's an extra linux-only feature :)

The only downside is that it doesn't sync the covers (yet?), and that **you have to reboot your iphone** for the tracks to show in the "ipod" appliacation.

Hope this helps :)

- trib'

ok im trying to work through this.  i get to where it asks for a password.  i try "dottie" but it does not work.  ive tried my username password and nothing.  im not aware of ever passwording my iphone, it doesnt require one ever that ive run into.  whats the deal here?  anyone else had this problem?

---

### Post by Mateo on 2008-01-06
try "alpine".  Dottie was the password for the old version.  Alpine should work.

---

### Post by superm1 on 2008-01-06
additionally you can customize your root passwordby picking openssh on your home screen and putting a new password in.

---

### Post by Suger on 2008-01-07
Sorry if the question has already been asked a million times (or even just one), but I couldn't find anything about that. I have a problem with, I guess, libgpod.

So, after followibng the wiki, I can iimport my music OK in the Iphone, the tags are OK too in the ipod (I checked them with Ex falso), but they end up all garbled, or so it seems, in the iTunesDB, as I have very strange results both for the artists, the albums and the titles in the iPod part of the iPhone : the titles start only at the second letter, are followed by elements of the artist and white squares, like if there was an encoding problem (but I tried both UTF-8 and ISO-8859-15 with the same result. Artists end up looking like albumname (without the first letter) followed by ntrol and then by the path to the file on the iPhone (Emilie Simon's Vegetal album appears, in Artist, as

egetalntrol/Music/F00/gtk...

And I get the same results with the latest svn of libgpod and gtkpod.

Did I do something wrong, should I file a bug in launchpad or directly to gtkpod ?

---

### Post by edwardgel on 2008-01-07
> **Terc said:**
> Alright, I've given up with using Banshee, I'm on Rhythmbox now, and I am syncing with my iPhone from Rhythmbox.

Anyone want a how to?

Yes yes yes!

---

### Post by mrmonkeyman on 2008-01-07
I am connecting to my ipod touch using ipod-convinience. How can I change the ip address that it thinks my ipod has? I use two networks one at home and one at work, and had to set the ip at home on the ipod to a static one so that it would connect but the one at work is completely different. Also, my ipod-convinience package says it is upgradable but will not upgrade or change status. it is on version 0.4 and says new version is 0.4.

---

### Post by Suger on 2008-01-07
The IP address is in /etc/default/ipod-convenience

And for the always upgrading package, its a known PPA/Launchpad bug that is being worked on

[https://bugs.launchpad.net/ipod-convenience/+bug/165230](https://bugs.launchpad.net/ipod-convenience/+bug/165230)

---

### Post by danip on 2008-01-07
> **Mateo said:**
> try "alpine".  Dottie was the password for the old version.  Alpine should work.

```
steve@weronika:~$ ssh root@192.168.104.1
Password:
Password:
Password:
root@192.168.104.1's password: 
Permission denied, please try again.
root@192.168.104.1's password: 
Permission denied, please try again.
root@192.168.104.1's password: 
Permission denied (publickey,password,keyboard-interactive).

```

thats the output when i try the password 'alpine' now. superm1 mentioned changing the password by going into the openssh options but i do not have that on my iphone home screen.  ive gone into the customize area and its not disabled either, it simply doesnt exist.

---

### Post by danip on 2008-01-07
ok just ignore the last post of mine, im an idiot, i was using my routers ip for whatever reason and not the phones, sorry about that.

---

### Post by danip on 2008-01-07
ok now i actually have a problem heres the output

```
steve@weronika:~$ sshfs root@192.168.106.26 /var/root/Media /media/ipod/
missing host
see `sshfs -h' for usage
```

---

### Post by agentjon on 2008-01-07
> **danip said:**
> ok now i actually have a problem heres the output

```
steve@weronika:~$ sshfs root@192.168.106.26 /var/root/Media /media/ipod/
missing host
see `sshfs -h' for usage
```

you need a colon in between the hostname/ip and the folder you want sshfs to mount.

try
```

sshfs root@<ip here>:/var/root/Media /media/ipod/

```

---

### Post by raginghampster on 2008-01-09
Ok here's the thing. I followed the guide/wiki. 

For some strange reason sshd on ipod touch is not 
allowing me to connect with publickey method. I can
log in with manualy typing password. 

I've checked and rechecked, publick rsa keys are the same
on both sides. It comes to the part where client is sending rsa 
key but server is not responding to that. I wanted to see what's
going on on server side but there are no logs to look at altough
syslogd is running.  Go figure. :)

I can mount the device with iphone-mount and iphone-umount.
If I use amarok however it fails to mount it. I presume becouse 
of the keys issue above. And after amarok failure I get some stale
files in /media/ipod which need to be deleted for the next iphone-mount
to succeed.

Ok .. so if I do it manually (iphone-mount) I can connect to the device.
I tried transfering music over to ipod-touch. It went ok but there was no
music on ipod even after reboot. I checked and files were there.
Does it need some special format to recognize them?

part of: ssh -l -vvv root 192.168.254.55
-------------------------------------------
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ivo/.ssh/identity
debug3: no such identity: /home/ivo/.ssh/identity
debug1: Trying private key: /home/ivo/.ssh/id_rsa
debug3: no such identity: /home/ivo/.ssh/id_rsa
debug1: Offering public key: /home/ivo/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
root@192.168.254.55's password: 


How are you guys succeeding in doing this is beyond me. :D

Any help appreciated.

Best regards.

---

### Post by robowraith on 2008-01-09
Hi,

does the maintainer of the PPA repository read this thread?

If so, would it be possible to build Amarok with "--with-mp4v2"? 

As I understand it, then it should be possible to write to the tags of the mp4 videos that you upload to the iphone and not go the route via gtkpod (which btw seems to destroy the album art thumbnails).

Thanks.


rw

---

### Post by ntetreau on 2008-01-10
> **robowraith said:**
> Hi,

does the maintainer of the PPA repository read this thread?

If so, would it be possible to build Amarok with "--with-mp4v2"? 

As I understand it, then it should be possible to write to the tags of the mp4 videos that you upload to the iphone and not go the route via gtkpod (which btw seems to destroy the album art thumbnails).

Thanks.


rw

That would be great but near impossible as libmp4v2-dev is not available in repositories.

---

### Post by robowraith on 2008-01-10
Hm.

That's too bad. Would it then be possible to find out with what build options the Amarok version from PPA was built? Then I could try (and most probably fail :-) ) to build a version for myself.

Thanks 

rw

---

### Post by ntetreau on 2008-01-10
> **robowraith said:**
> Hm.

That's too bad. Would it then be possible to find out with what build options the Amarok version from PPA was built? Then I could try (and most probably fail :-) ) to build a version for myself.

Thanks 

rw

Good luck, I just gave it a few hours of my life and I have nothing to show for it, let's hope Superm1 has the time and reach for this.

---

### Post by markjf on 2008-01-10
> **raginghampster said:**
> Ok here's the thing. I followed the guide/wiki. 

For some strange reason sshd on ipod touch is not 
allowing me to connect with publickey method. I can
log in with manualy typing password. 

...

How are you guys succeeding in doing this is beyond me. :D

Any help appreciated.



it's the old adage in unix "99% of problems are path or permissions".

i've just had your exact problem on my iphone (not being able to use public keys to ssh in, and amarok failing to see the folder because of it), but fixed it.
sshd doesn't like you giving write permissions on the home dir to group/other.

log into your ipod touch and do:
chmod g-w ~/.
chmod o-w ~/.

and retry.

i can't see it giving issues to other processes (not having write permissions), so looks like a pretty safe fix.

hth,
mark

---

### Post by robowraith on 2008-01-10
> **ntetreau said:**
> That would be great but near impossible as libmp4v2-dev is not available in repositories.

Hm. I just had a look. This is what I found:
```
apt-cache showpkg libmp4v2-dev
Package: libmp4v2-dev
Versions:
2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language:
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-i386_Packages
                  MD5: 8104558694dd7a4766bccc161be4e715


Reverse Depends:
  libfaac-dev,libmp4v2-dev
Dependencies:
2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 - libmp4v2-0 (5 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5) libc6-dev (16 (null)) libc-dev (0 (null))
Provides:
2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 -
Reverse Provides:

```

rw

---

### Post by ntetreau on 2008-01-11
> **robowraith said:**
> Hm. I just had a look. This is what I found:
```
apt-cache showpkg libmp4v2-dev
Package: libmp4v2-dev
Versions:
2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language:
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-i386_Packages
                  MD5: 8104558694dd7a4766bccc161be4e715


Reverse Depends:
  libfaac-dev,libmp4v2-dev
Dependencies:
2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 - libmp4v2-0 (5 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5) libc6-dev (16 (null)) libc-dev (0 (null))
Provides:
2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 -
Reverse Provides:

```

rw

But Unfortunately, when you try to install it, you get "No candidate version found for libmp4v2-dev"

---

### Post by robowraith on 2008-01-11
> **ntetreau said:**
> But Unfortunately, when you try to install it, you get "No candidate version found for libmp4v2-dev"

Beg to differ. It was installed on my system already.  Do you want me to send you the deb?

rw

---

### Post by superm1 on 2008-01-11
Well the issue is that library sits in multiverse (libmp4v2-dev), whereas Amarok normally lives in main.  It can be fixed temporarily on the PPA, but then come hardy, it will have to be rebuilt for the PPA in hardy too if you want to keep tagging.

Is there anything more that needs to be done other than just building with that single flag?

---

### Post by bharadwaj on 2008-01-12
songbird wioth iPhone add-on works just the same as iTunes and the best one

---

### Post by robowraith on 2008-01-12
> **superm1 said:**
> Is there anything more that needs to be done other than just building with that single flag?

To be hones, I don't know. :-) This was the only thing I found with regard to mp4 tags in amarok.

rw

---

### Post by Suger on 2008-01-12
Bharadwaj, excuse me, but where did you find the iPhone add-on for Songbird ? I only found the iPod add-on, and it doesn't support the iPhone for lack of disk mode

---

### Post by ODF on 2008-01-12
This is what I get now.

```
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

```

I guess its progress hehe

Fixed : Used rm -rf /media/ipod then i reinstalled ipod convenience

---

### Post by ODF on 2008-01-12
A lot of post helped me in this thread, thx to so many people =)

---

### Post by Terc on 2008-01-13
> **Suger said:**
> Bharadwaj, excuse me, but where did you find the iPhone add-on for Songbird ? I only found the iPod add-on, and it doesn't support the iPhone for lack of disk mode

I'm lost here too, I did lots of googling and I see nothing about iPhone support in Songbird, this would be great, but maybe Bharadwaj could link us someplace?

---

### Post by deathblossom on 2008-01-14
About the album art, gtkpod only shows the art I've synced with iTunes on the first track of the each album. None of the other songs on the albums have them. So when I write to my ipod, in the coverflow section, it looks like I've got art for all of my albums, but when I play songs, I get nothing (unless the song is the first track). Is there a way to get the album art to be on all the songs without having to refind all the art again using gtkpod (which often finds bad quality covers or doesn't find them at all)?

---

### Post by superm1 on 2008-01-14
> **deathblossom said:**
> About the album art, gtkpod only shows the art I've synced with iTunes on the first track of the each album. None of the other songs on the albums have them. So when I write to my ipod, in the coverflow section, it looks like I've got art for all of my albums, but when I play songs, I get nothing (unless the song is the first track). Is there a way to get the album art to be on all the songs without having to refind all the art again using gtkpod (which often finds bad quality covers or doesn't find them at all)?
You can select groups of songs and set the same art for albums that way.

---

### Post by deathblossom on 2008-01-14
> You can select groups of songs and set the same art for albums that way.

In gtkpod? I see that you can use the option "Apply changes to all tracks" when looking for new album art, but that requires me to find the album art with gtkpod first. It won't let me take the what artwork is already on one file and spread it to the other songs. I also can't copy the artwork path because it's embedded by iTunes.

Edit: Okay, I'm experimenting with getting iTunes to actually embed the art on all the tracks and write it to the tags, because it wasn't really doing it on all the tracks before. I tried it on a couple of albums and they've seemed to retain their artwork after syncing with gtkpod.

---

### Post by deathblossom on 2008-01-14
Okay, that didn't work. It's weird, because when I bring the ipod up in gtkpod at first, all the tracks will have the album art (before I embedded it into all the files, it didn't). But, as soon as I write to it, all the tracks except the first track lose it.

---

### Post by ntetreau on 2008-01-15
> **Terc said:**
> I'm lost here too, I did lots of googling and I see nothing about iPhone support in Songbird, this would be great, but maybe Bharadwaj could link us someplace?

I'm not sure if it is supported only in the latest developement release of songbird 0.4, but they indicate on the release page that the iphone is supported using the latest ipod add-on:

[http://www.songbirdnest.com/release-notes/0.4](http://www.songbirdnest.com/release-notes/0.4)

---

### Post by ntetreau on 2008-01-15
> **deathblossom said:**
> Okay, that didn't work. It's weird, because when I bring the ipod up in gtkpod at first, all the tracks will have the album art (before I embedded it into all the files, it didn't). But, as soon as I write to it, all the tracks except the first track lose it.

I have refreshed my whole album art database using Amarok before, you can give it a try.  Also, its album art fetcher is more powerful than the one in gtkpod.

---

### Post by superm1 on 2008-01-15
> **ntetreau said:**
> I'm not sure if it is supported only in the latest developement release of songbird 0.4, but they indicate on the release page that the iphone is supported using the latest ipod add-on:

[http://www.songbirdnest.com/release-notes/0.4](http://www.songbirdnest.com/release-notes/0.4)

It may be a little bit early, but when I read that, it said these were the exception ( iPod touch, iPhone, and second gen shuffle)

well and think about that a little bit closer: if they somehow had support for these newer devices, that would mean that they developed some sort of cross platformdriver that can be used to access these ad USB drives. At this point any 3rd party apps that do this on windows use an iTunes API call to do so.

---

### Post by ntetreau on 2008-01-15
> **superm1 said:**
> It may be a little bit early, but when I read that, it said these were the exception ( iPod touch, iPhone, and second gen shuffle)

well and think about that a little bit closer: if they somehow had support for these newer devices, that would mean that they developed some sort of cross platformdriver that can be used to access these ad USB drives. At this point any 3rd party apps that do this on windows use an iTunes API call to do so.

You're right, it was too early!  Now that you did a better job than my morning coffee to open my eyes, it does say these are NOT supported!  My bad!

---

### Post by DougEdey on 2008-01-16
> **superm1 said:**
> Great news folks.

ical2sqlite was accepted for Hardy.  You should be able to grab both from the PPA for now, and when you upgrade to Hardy they will be available there.

Hey there,

I'm not too sure if it's been done or not, but I found that this was over-writing any custom events on my iPod touch, so I made a minor couple of changes so it pulls the existing calender, and then merges it, I'm working on uploading it to google calendar now.

---

### Post by ntetreau on 2008-01-16
> **DougEdey said:**
> Hey there,

I'm not too sure if it's been done or not, but I found that this was over-writing any custom events on my iPod touch, so I made a minor couple of changes so it pulls the existing calender, and then merges it, I'm working on uploading it to google calendar now.

Sounds great, can you add a bit of details?  Also, are you able to implement sync from ipod --> evolution?  Directly or through funambol and syncevolution?

---

### Post by DougEdey on 2008-01-16
> **ntetreau said:**
> Sounds great, can you add a bit of details?  Also, are you able to implement sync from ipod --> evolution?  Directly or through funambol and syncevolution?

Not yet, it currently doesn't require any extra software, it just gets the Calendar DB off the iPhone via SSH, edits it (the original version over-wrote it) then puts it back.

I'll work on the Two way sync later, but at the moment I have other things on the go. But I will work on it next week or the week after

EDIT: Updated source is here: [http://www.voidedwarranty.co.uk/ipodtouch/ipodcal.tar.gz](http://www.voidedwarranty.co.uk/ipodtouch/ipodcal.tar.gz)

---

### Post by spacetree on 2008-01-16
> **robowraith said:**
> IT WORKED!

I have album art now. I tried Gtkpod again after reading the last replies here and noticed that it indeed showed the correct cover art but destroyed it when trying to write to ArtworkDB. I then poked around Amarok and noticed that the version from ppa has additional iPod Models listed. The old version only had "xmobile", but the new version has the Model "xiphone". Now Artwork works!

Thanks guys!

f

P.S.: Who knows how to sync the Contacts with Kontact? :-D

Hi robowraith, so the solution was:

1.-Checking you have amaroK 1.4.8 with libgpod > 0.6 (ppa)
2-.Checking in amaroK the model of the iPhone (it should be ''xiphone'')

Right?  I really want that artwork

---

### Post by DougEdey on 2008-01-16
> **spacetree said:**
> Hi robowraith, so the solution was:

1.-Checking you have amaroK 1.4.8 with libgpod > 0.6 (ppa)
2-.Checking in amaroK the model of the iPhone (it should be ''xiphone'')

Right?  I really want that artwork

Mine works now too. But I had to manually create the Firewire ID file [http://www.fredemmott.co.uk/blog_121](http://www.fredemmott.co.uk/blog_121)

All the mounting and so on is done using the ipod-convenience tools though.

---

### Post by superm1 on 2008-01-17
> **DougEdey said:**
> Mine works now too. But I had to manually create the Firewire ID file [http://www.fredemmott.co.uk/blog_121](http://www.fredemmott.co.uk/blog_121)

All the mounting and so on is done using the ipod-convenience tools though.
Was the ipod plugged in when you ran iphone-mount?  This is how the script determines that firewire id.

---

### Post by DougEdey on 2008-01-17
> **superm1 said:**
> Was the ipod plugged in when you ran iphone-mount?  This is how the script determines that firewire id.

Yes, but it wasn't created automatically or anything at all by Amarok or iPhone-mount (same with ipod-touch-mount).

All it would do is copy the music across then when completed the ipod-touch would not allow the music software to run at all.

---

### Post by DougEdey on 2008-01-17
Unfortunately only one Artwork cover is active at a time in the artworkDB for some reason. It's random as to which.

EDIT: Manually deleting the ArtworkDB and .ithmb files on the touch, then going to amarok -> devices -> ipod -> update artwork, appears to have fixed this!

---

### Post by Terc on 2008-01-18
> **ntetreau said:**
> I'm not sure if it is supported only in the latest developement release of songbird 0.4, but they indicate on the release page that the iphone is supported using the latest ipod add-on:

[http://www.songbirdnest.com/release-notes/0.4](http://www.songbirdnest.com/release-notes/0.4)

On the contrary, if you read that again, you might be a little dissapointed.

"The latest generation iPods (the 2nd Gen Shuffle/iPod Touch/iPhone an [COLOR="Red"]exception[/COLOR]) are now supported and we have improved the user experience for the iPod including a new iPod Summary Page (requires latest iPod add-on)"

Bad news, I know.  But this looks like they're talking about a fix for the new encryption, not a way to sync with iPods without disk mode.  Too bad, I would have loved to get my younger brothers set up on songbird, they miss the intuitive syncing done with iTunes.

---

### Post by robowraith on 2008-01-19
> **spacetree said:**
> Hi robowraith, so the solution was:

1.-Checking you have amaroK 1.4.8 with libgpod > 0.6 (ppa)
2-.Checking in amaroK the model of the iPhone (it should be ''xiphone'')

Right?  I really want that artwork

Exactly!

rw

---

### Post by spacetree on 2008-01-19
Thanks robowraith.

I have set my model to xiPhone and ligbpod is ok.

Anyway I dont have the ipodconvenience tool installed. Is that really necesary?

Another thing is that when I had artwork working before amarok upgrade i have not determined the firewire id, as it seemed to be necessary only for ipod touch. Any ideas?

EDIT: IT WORKS NOW!

Hi! i put the firewireID, then manually erased the artworkdb, and put in the sshfs premount order the parameter workaround=rename, then uptated the artwork via amarok and voila!!!

Thank guys!

---

### Post by wireless on 2008-01-21
Hello ppl

I restorted my iphone due to some issues, now all is ok i setup amarok and all works wonderfully.
except of the passwordless login. I followed all the steps correctly but it just keep asking for password

permission for the authorized_keys file looks correct
-rw-r--r-- 1 root wheel 392 Jan 21 19:38 authorized_keys
i compared the to key files and they are all in one line with no spaces and match each other.
i rebooted the iphone when neccesary.
offcourse i saved the /etc/sshd_conf file after the changes.

after all that and it still asks for pw.
any ideas??
thnx ppl! ;)

---

### Post by ntetreau on 2008-01-23
> **DougEdey said:**
> Not yet, it currently doesn't require any extra software, it just gets the Calendar DB off the iPhone via SSH, edits it (the original version over-wrote it) then puts it back.

I'll work on the Two way sync later, but at the moment I have other things on the go. But I will work on it next week or the week after

EDIT: Updated source is here: [http://www.voidedwarranty.co.uk/ipodtouch/ipodcal.tar.gz](http://www.voidedwarranty.co.uk/ipodtouch/ipodcal.tar.gz)

This works well for me.  In fact, I will submit a bug report on ical2sqlite to include the changes.  Doug, since the ical file is now updated instead of just copied, what is stopping it from updating the evolution ical file as well?

Thanks again!

EDIT: Unfortunately, ical2sqlite does not use launchpad for bug tracking.  Hopefully, superm1 will read this post and merge the changes.

---

### Post by DougEdey on 2008-01-23
Unfortunately I don't have the time right now to install evolution and test the ical.

---

### Post by ntetreau on 2008-01-23
> **DougEdey said:**
> Unfortunately I don't have the time right now to install evolution and test the ical.

I understand.  But how are you merging the iphone calendar and google-calendar now?  Are you merging them as ics files or as sqlite?  If you are merging as ics, then this file can be reused by evolution or google-calendar i guess.

---

### Post by DougEdey on 2008-01-23
All I did was stop program from truncating the ical file after the script retreives it from the iPhone.

---

### Post by ntetreau on 2008-01-23
> **DougEdey said:**
> All I did was stop program from truncating the ical file after the script retreives it from the iPhone.

I'm not sure how it all happens, so why don't I stop bothering you with this!!! Thanks again.

---

### Post by wireless on 2008-01-23
anyone about my issue ?

---

### Post by Will May on 2008-01-23
Do you get an error message trying to ssh to it via the command line?

Try deleting ~/.ssh/known_hosts as your computer maybe stopping you logging onto your phone as it has stored a copy of the old ssh key and the new one you generated when you wiped your phone doesn't match it.

---

### Post by wireless on 2008-01-23
> **Will May said:**
> Do you get an error message trying to ssh to it via the command line?

Try deleting ~/.ssh/known_hosts as your computer maybe stopping you logging onto your phone as it has stored a copy of the old ssh key and the new one you generated when you wiped your phone doesn't match it.

yeah i cleaned everything up and started over but no avail..
loging in via ssh works fine with no errors. it just asks for pw.. :\

update:
i just went through allll the posts and found this:
chmod g-w ~/.
chmod o-w ~/.
and it workkkkkked! 
but can someone please explained what it just did? it helped but i want to know what just happand 
thnxx:)

---

### Post by CDNdevil on 2008-01-26
Anybody able to get photos on the iphone, or ipod touch in ubuntu?

---

### Post by Mateo on 2008-01-26
> **CDNdevil said:**
> Anybody able to get photos on the iphone, or ipod touch in ubuntu?

depends what you mean.  once you mount your iphone you can go into the filesystem and see your photos.  As far as managing photo albums, I haven't been about to figure this out yet.  Then again, I haven't tried that hard either.

---

### Post by CDNdevil on 2008-01-27
I can't see any pictures, because I can't put them on my ipod touch, so I'm not sure where I can put them when I mount it. I don't know maybe I will just sit tight and wait till someone finds a way to do it.

---

### Post by ntetreau on 2008-01-28
> **CDNdevil said:**
> Anybody able to get photos on the iphone, or ipod touch in ubuntu?

I tried and it is very close to working but isn't.  Once you have the folder /var/root/Media/Photos you will be able to create Photo albums and add picures through gtkpod.  The Albums show up in the Photos software of my iphone and it even shows in bracket next to it the number fo pictures I have added to this album.  Unfortunately, when entering the album, it is empty.

I have posted in the gtkpod-questions mailing list but haven't received any answer.  It would help to get some attention if you were to confirm my post [there]("https://sourceforge.net/mailarchive/forum.php?forum_name=gtkpod-questions").

---

### Post by DougEdey on 2008-01-28
How did you transfer images to begin with? I've created the Photos folder on my iPod but GTKpod doesn't show any options to transfer images?

---

### Post by olavjunior on 2008-01-28
Is there a way of using Exaile to transfer music to iphone?

---

### Post by ntetreau on 2008-01-29
> **DougEdey said:**
> How did you transfer images to begin with? I've created the Photos folder on my iPod but GTKpod doesn't show any options to transfer images?

I don't really remember how it got there but after creating the Photos folder, I get a Photos entry in gtkpod, take a look at the screen shot.

To summarize, I can see pictures taken with the iphone, I can create new albums which shows the right number of pictures in the album list, but nothing once browsing the album.

---

### Post by NerdyShinobi on 2008-01-30
For anyone considering the upgrade to 1.1.3 and jailbreaking:

You might notice that after the upgrade, everything works except Ipod-Convenience.  If you get an error concerning "/var/root/Media does not exist" or some such, here's the fix in a nutshell:  make a symbolic link between where the files were (/var/root/Media) and where the files now ARE (/var/mobile/media).

```
Now for some tasty copy and paste!
```

```
ssh root@your.iphone.ip.address
```

```
ln -s /var/mobile/Media /var/root/Media
```

```
exit
```

Once you've made that link, iphone-mount should work like a charm!

---

### Post by olavjunior on 2008-02-02
> 3. Plug in your iPod Touch or iPhone via USB. This is REQUIRED when you run the next steps for the first time, as the USB connection is used to generate a hash required by the iTunes Database (if this fails to generate properly, see the troubleshooting section below). An added benefit is this also makes sure that your device won't turn the wifi into low power mode, breaking the transfer connection.

After going through step two nothing happens! I plug in the Iphone, but nothing.. I tried ```
iphone-mount
``` wich gave me a fuse-user error, so I added myselfe to fuse group, relogged in, tried it again, but then nothing happened.. just blank, after ```
iphone-mount
```

Also, after installing, it seems the installation never quite finished. The ipod-convenience is marked as an upgrade. I upgraded, but it's still there... Can anybody help me out?

EDIT: It worked out fine after setting ip to dchp somehow..

---

### Post by Kulgan on 2008-02-03
Everything seems fine after following the instructions on the wiki. 

I tranfer music with Rythmbox, and add the album covers with GTKpod. Movies work, though I haven't tried pictures yet. Not my highest priority.

Thanks a lot!

The only issue I have encountered is unrelated to the iPhone, I think. Even though I have installed ipod-convenience, it is always listed as an uprgade "ready to be installed". Any tips on getting rid of it (other than removing the deb line in the apt sources)?
Thanks :D

---

### Post by stefanb on 2008-02-05
> **CDNdevil said:**
> Some ideas to throw out there, is anyone able to sync with there evolution calender or tomboy notes, or put pictures on here? I just really want to get the most out of this thing that I spent so much money for thats why I keep asking.:)

Ok, since no one did it, I just created a little sync tool which for now syncs notes to and from Tomboy to and from the iPhone/iPod touch MobileNotes application. If notes are already there, they won't be overwritten but not merged as well. Something for the future. However, I like it pretty much :)

I just tried launchpad for that, have a look here:
[https://code.launchpad.net/iphone-sync](https://code.launchpad.net/iphone-sync)

---

### Post by ntetreau on 2008-02-06
> **NerdyShinobi said:**
> For anyone considering the upgrade to 1.1.3 and jailbreaking:

You might notice that after the upgrade, everything works except Ipod-Convenience.  If you get an error concerning "/var/root/Media does not exist" or some such, here's the fix in a nutshell:  make a symbolic link between where the files were (/var/root/Media) and where the files now ARE (/var/mobile/media).

```
Now for some tasty copy and paste!
```

```
ssh root@your.iphone.ip.address
```

```
ln -s /var/mobile/Media /var/root/Media
```

```
exit
```

Once you've made that link, iphone-mount should work like a charm!

I wonder if it wouldn' t be better to change the path in iphone-mount instead?

---

### Post by superm1 on 2008-02-06
> **ntetreau said:**
> I wonder if it wouldn' t be better to change the path in iphone-mount instead?
Well the problem is what firmware you are on can't easily be queried.  Do you know of a way to determine this?  I suppose just a quick touch of the mobile user homedirectory would suffice.  This was if it didn't exist, you know its 1.1.1 or 1.1.2, otherwise 1.1.3+.

---

### Post by ntetreau on 2008-02-06
> **superm1 said:**
> Well the problem is what firmware you are on can't easily be queried.  Do you know of a way to determine this?  I suppose just a quick touch of the mobile user homedirectory would suffice.  This was if it didn't exist, you know its 1.1.1 or 1.1.2, otherwise 1.1.3+.

That seems like the best method and I've seen it used elsewhere as well.

Now, I can' t seem to be able to setup the passwordless SSH login, as anybody had any luck first changing the SSH password on 1.1.3 without using passwd (it crashes springboard constantly), and then setting up the the ssh keys properly.  I' m just wondering if some of these files have been moved around.

---

### Post by ntetreau on 2008-02-06
> **stefanb said:**
> Ok, since no one did it, I just created a little sync tool which for now syncs notes to and from Tomboy to and from the iPhone/iPod touch MobileNotes application. If notes are already there, they won't be overwritten but not merged as well. Something for the future. However, I like it pretty much :)

I just tried launchpad for that, have a look here:
[https://code.launchpad.net/iphone-sync](https://code.launchpad.net/iphone-sync)

Hi Stefanb, that looks fantastic, I'll give it a try asap.  Have you thought about integrating your work with "conduit"? I have contacted the main developer already about integrating the calendar sync and his response was very positive, why don' t you do the same? 

Conduit: [http://www.conduit-project.org/](http://www.conduit-project.org/)

---

### Post by nzjrs on 2008-02-07
Hi Stephan,

I had a look over your code. A large part of it is very similar to what Conduit already does wrt sync tomboy notes with existing ipods, etc. 

I will probbably integrate what you have written in the next Conduit version. I would be very interested in working with you to help you do this, if you are interested.

I am always looking for new Conduit developers. Please email me if you are interested in working together.

Thanks a lot

John

---

### Post by ntetreau on 2008-02-07
> **nzjrs said:**
> Hi Stephan,

I had a look over your code. A large part of it is very similar to what Conduit already does wrt sync tomboy notes with existing ipods, etc. 

I will probbably integrate what you have written in the next Conduit version. I would be very interested in working with you to help you do this, if you are interested.

I am always looking for new Conduit developers. Please email me if you are interested in working together.

Thanks a lot

John

Sounds awesome, go Stephan!

---

### Post by ntetreau on 2008-02-07
@ nzjrs:  I gave your note sync a try, it works really well. Do you mind if I give a few ideas?

1. Separate "Sync all" and a "Sync selected" button.  
2. Select multiple Notes and sync only those selected
3. In preference, have the hability to choose a single Tomboy Notebook (a list of notebooks could be queried from Tomboy perhaps?).  After choosing a Notebook, only notes in that Notebook would appear in the gui list for syncing.

All of these, except choosing a single Notebook, become irrelevant if you work within Conduit though.

Thanks for your great app!

EDIT: Very crudely, you get a list of the notebooks used when:  grep "<tag>system:notebook:" .tomboy/*

EDIT2: For those on 1.1.3, open sync.py and change the paths (2 in that file) /var/root/Library/Notes to /var/mobile/Library/Notes

---

### Post by FRuMMaGe on 2008-02-07
> **Kulgan said:**
> Everything seems fine after following the instructions on the wiki. 

I tranfer music with Rythmbox, and add the album covers with GTKpod. Movies work, though I haven't tried pictures yet. Not my highest priority.

Thanks a lot!

The only issue I have encountered is unrelated to the iPhone, I think. Even though I have installed ipod-convenience, it is always listed as an uprgade "ready to be installed". Any tips on getting rid of it (other than removing the deb line in the apt sources)?
Thanks :D

Same here. It's really irritating trying to update to itself!

Also, any news on the photos?

My iPod can see the album and even notice how many photos are in there but it says it is empty when i open it. :(

---

### Post by ntetreau on 2008-02-08
> **FRuMMaGe said:**
> Same here. It's really irritating trying to update to itself!

Also, any news on the photos?

My iPod can see the album and even notice how many photos are in there but it says it is empty when i open it. :(

Same problem here, please confirm my post ont he libgtkpod-question mailing list.  This is probably a bug in libgpod which hasn' t been looked at yet.

---

### Post by Kulgan on 2008-02-09
Don't want to interrupt the thread, just thought I'd inform you all that I took the liberty of adding a small section at the bottom of troubleshooting, regarding the 1.1.3 firmware. Even though it's not really "new" information, it's information none the less, and I thought, since the unlock was released earlier today, that there would be a few people upgrading to 1.1.3 that could make use of it. A point that I didn't add is that though before you didn't have to reboot to see the media you had just transferred (I didn't, at least - iphone-umount would restart Spring/SummerBoard), you now do. So no complaints when the media doesn't turn up :D

---

### Post by nzjrs on 2008-02-09
**This post could be related to an Ubuntu bug filed at**: [http://bugzilla.gnome.org/show_bug.cgi?id=514939](http://bugzilla.gnome.org/show_bug.cgi?id=514939) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A link to the appropriate Conduit bug (for iphone support) is

[http://bugzilla.gnome.org/show_bug.cgi?id=514939](http://bugzilla.gnome.org/show_bug.cgi?id=514939)

John

---

### Post by berardi1111 on 2008-02-11
This is awesome guys... if you can get iPhone sync to be a complete easy to use process, I'm switching to Linux immediately! It's the only thing keeping me cautious about switching =/

---

### Post by Kulgan on 2008-02-11
> **berardi1111 said:**
> This is awesome guys... if you can get iPhone sync to be a complete easy to use process, I'm switching to Linux immediately! It's the only thing keeping me cautious about switching =/

So long as you are aware that the iPhone has to be jailbroken in order to use it:

Switch! 

I personally think using GTKPod is better than using iTunes (I mean, what the hell.. iTunes? Who uses it? It's terrible!) and you get to sync over WiFi - as someone said earlier, "It's a Linux only feature!"

As far as ease of use, here's a little script that saves you having to go into the terminal to mount and unmount the iPhone each time. It uses the default mount point (/media/ipod), which can be changed, and starts GTKPod when the iPhone is mounted. 

I'm not sure how new you are to Linux, but you seem to imply no use (welcome, by the way, and congrats on first post!). If you need help, let us know!

-K

edit: hehe, forgot attachment :D

---

### Post by The Browncoat Cat on 2008-02-15
> **tribaal said:**
> 

- move to where the iTunes library is: "cd /var/root/Media"'

I followed your instructions up to this point, however, on entering this command at the # prompt, I am told that "no such file or directory: /var/root/Media" and cannot continue.  I am using an 8mb ipod touch with jailbroken firmware 1.1.13. Have I misssed something somewhere?

---

### Post by FRuMMaGe on 2008-02-15
> **The Browncoat Cat said:**
> I followed your instructions up to this point, however, on entering this command at the # prompt, I am told that "no such file or directory: /var/root/Media" and cannot continue.  I am using an 8mb ipod touch with jailbroken firmware 1.1.13. Have I misssed something somewhere?

Read the instructions on the Ubuntu wiki.

You must restore to 1.1.1 and then to 1.1.2

---

### Post by Suger on 2008-02-16
Not exactly.

[https://help.ubuntu.com/community/PortableDevices/iPhone#head-2324e37d080ca00c9738c8653562c84872ab4a72](https://help.ubuntu.com/community/PortableDevices/iPhone#head-2324e37d080ca00c9738c8653562c84872ab4a72)

 On 1.1.3, you must create a symlink

```
ln -s /private/var/mobile/Media /private/var/root/Media
```

while logged on the iphone via ssh

---

### Post by The Browncoat Cat on 2008-02-16
> **Suger said:**
> Not exactly.

[https://help.ubuntu.com/community/PortableDevices/iPhone#head-2324e37d080ca00c9738c8653562c84872ab4a72](https://help.ubuntu.com/community/PortableDevices/iPhone#head-2324e37d080ca00c9738c8653562c84872ab4a72)

 On 1.1.3, you must create a symlink

```
ln -s /private/var/mobile/Media /private/var/root/Media
```

while logged on the iphone via ssh

Thank you.

---

### Post by xALEXANDRE on 2008-02-16
Hi guys..
I have a iPhone 1.1.2..
Try [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) but don't mount.
Error: You don't have a Firewire GUID, so we will create one
Thanks.

---

### Post by Suger on 2008-02-16
I got tired of having to resort on non free solutions to get custom ringtones on my iphone, so I wrote a python script (iphone-ringtones) which does the job. I got the m4atags class from here
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/496984](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/496984)

and I use the plist.py library from here

[http://odz.sakura.ne.jp/toys/wiki/python-plist](http://odz.sakura.ne.jp/toys/wiki/python-plist)

And here is the code

```
#! /usr/bin/env python
# -*- coding: utf-8
#This program is distributed under BSD Licence
#Copyright (c) 2008, suger@p2pfr.com

#All rights reserved.

#Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
#Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
#Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
#Neither the name of the p2pfr.com nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

#THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


import sys
import optparse
import os
import shutil
import plist
import struct

FLAGS= CONTAINER, SKIPPER, TAGITEM, IGNORE, NOVERN, XTAGITEM= [2**_ for _ in xrange(6)]

# CONTAINER: datum contains other boxes
# SKIPPER: ignore first 4 bytes of datum
# TAGITEM: "official" tag item
# NOVERN: datum is 8 bytes (2 4-bytes BE integers)
# XTAGITEM: datum is a triplet (I believe) of "mean", "name", "data" items
CALLBACK= TAGITEM | XTAGITEM
FLAGS.append(CALLBACK)

TAGTYPES= (
    ('ftyp', 0),
    ('moov', CONTAINER),
    ('mdat', 0),
    ('udta', CONTAINER),
    ('meta', CONTAINER|SKIPPER),
    ('ilst', CONTAINER),
    ('\xa9ART', TAGITEM),
    ('\xa9nam', TAGITEM),
    ('\xa9too', TAGITEM),
    ('\xa9alb', TAGITEM),
    ('\xa9day', TAGITEM),
    ('\xa9gen', TAGITEM),
    ('\xa9wrt', TAGITEM),
    ('trkn', TAGITEM|NOVERN),
    ('\xa9cmt', TAGITEM),
    ('trak', CONTAINER),
    ('----', XTAGITEM),
    ('mdia', CONTAINER),
    ('minf', CONTAINER),
)

flagged= {}
for flag in FLAGS:
    flagged[flag]= frozenset(_[0] for _ in TAGTYPES if _[1] & flag)

def _xtra(s):
    "Convert '----' atom data into dictionaries"
    offset= 0
    result= {}
    while offset < len(s):
        atomsize= struct.unpack("!i", s[offset:offset+4])[0]
        atomtype= s[offset+4:offset+8]
        if atomtype == "data":
            result[atomtype]= s[offset+16:offset+atomsize]
        else:
            result[atomtype]= s[offset+12:offset+atomsize]
        offset+= atomsize
    return result

def _analyse(fp, offset0, offset1):
    "Walk the atom tree in a mp4 file"
    offset= offset0
    while offset < offset1:
        fp.seek(offset)
        atomsize= struct.unpack("!i", fp.read(4))[0]
        atomtype= fp.read(4)
        if atomtype in flagged[CONTAINER]:
            data= ''
            for reply in _analyse(fp, offset+(atomtype in flagged[SKIPPER] and 12 or 8),
                offset+atomsize):
                yield reply
        else:
            fp.seek(offset+8)
            if atomtype in flagged[TAGITEM]:
                data=fp.read(atomsize-8)[16:]
                if atomtype in flagged[NOVERN]:
                    data= struct.unpack("!ii", data)
            elif atomtype in flagged[XTAGITEM]:
                data= _xtra(fp.read(atomsize-8))
            else:
                data= fp.read(min(atomsize-8, 32))
        if not atomtype in flagged[IGNORE]: yield atomtype, atomsize, data
        offset+= atomsize

def mp4_atoms(pathname):
    fp= open(pathname, "rb")
    fp.seek(0,2)
    size=fp.tell()
    for atom in _analyse(fp, 0, size):
        yield atom
    fp.close()

class M4ATags(dict):
    "An example class reading .m4a tags"
    cvt= {
        'trkn': 'Track',
        '\xa9ART': 'Artist',
        '\xa9nam': 'Title',
        '\xa9alb': 'Album',
        '\xa9day': 'Year',
        '\xa9gen': 'Genre',
        '\xa9cmt': 'Comment',
        '\xa9wrt': 'Writer',
        '\xa9too': 'Tool',
    }
    def __init__(self, pathname=None):
        super(dict, self).__init__()
        if pathname is None: return
        for atomtype, atomsize, atomdata in mp4_atoms(pathname):
            self.atom2tag(atomtype, atomdata)

    def atom2tag(self, atomtype, atomdata):
        "Insert items using descriptive key instead of atomtype"
        if atomtype == "----":
            key= atomdata['name'].title()
            value= atomdata['data'].decode("utf-8")
        else:
            try: key= self.cvt[atomtype]
            except KeyError: return
            if atomtype == "trkn":
                value= atomdata[0]
            else:
                try: value= atomdata.decode("utf-8")
                except AttributeError:
                    print `atomtype`, `atomdata`
                    raise
        self[key]= value


class IphoneRingtone():
    def parserOptions(self):
        self.parser.set_defaults(mountpoint="/media/iphone")
        self.parser.add_option("-l", "--list", help="List the personalized ringtones already installed", action="store_const", const=1, dest="list" )
        self.parser.add_option("-a", "--add", help="Adds ringtone to the personalized ringtones of the iPhone", action="store", type="string", dest="ringtone")
        self.parser.add_option("-m", "--mountpoint", help="Sets the mountpoint of the iPhone. Defaults to /media/iphone", action="store", type="string", dest="mountpoint")

    def parsePlist(self, file):
        dict=plist.parse_plist(file)
        self.ringtones=dict["Ringtones"]

    def testGuid(self):
        self.guid=1
        resultat=0
        while resultat == 0:
            resultat = 1
            for key in self.ringtones:
                try:
                    if (self.guid == int(self.ringtones[key]["GUID"])):
                        self.guid += 1
                        resultat = 0
                except:
                    pass

    def makePlist(self):
        ligne="<?xml version=\"1.0\" encoding=\"UTF-8\"?>" 
        ligne2="<!DOCTYPE plist PUBLIC \"-//Apple Computer//DTD PLIST 1.0//EN\" \"http://www.apple.com/DTDs/PropertyList-1.0.dtd\">"
        ligne3="<plist version=\"1.0\">"
        ligne4="<dict>"
        ligne5="\t<key>Ringtones</key>"
        ligne6="\t<dict>"
        ligne="\n".join((ligne, ligne2, ligne3, ligne4, ligne5, ligne6))
        for key in self.ringtones:
            ligne2=("\t\t<key>%s</key>" % key)
            ligne3="\t\t<dict>"
            ligne="\n".join((ligne, ligne2, ligne3))
            for key2 in self.ringtones[key]:
                ligne2=("\t\t\t<key>%s</key>" % key2)
                if (key2=="Total Time"):
                    ligne3=("\t\t\t<integer>%i</integer>" % self.ringtones[key][key2])
                elif (key2=="GUID"):
                    try:
                        ligne3=("\t\t\t<string>%i</string>" % self.ringtones[key][key2])
                    except:
                        ligne3=("\t\t\t<string>%s</string>" % self.ringtones[key][key2])
                else:
                    ligne3=("\t\t\t<string>%s</string>" % self.ringtones[key][key2])
                ligne="\n".join((ligne, ligne2, ligne3))
            ligne2="\t\t</dict>"
            ligne="\n".join((ligne, ligne2))
        ligne2="\t</dict>"
        ligne3="</dict>"
        ligne4="</plist>\n"
        ligne="\n".join((ligne, ligne2, ligne3, ligne4))
        unicode=ligne.encode("utf-8")
        file=open(os.path.join(self.options.mountpoint, "iTunes_Control/iTunes/Ringtones.plist"), "w")
        file.write(unicode)
        file.close()

    def add(self):
        if os.path.isfile(os.path.join(self.options.mountpoint, "iTunes_Control/iTunes/Ringtones.plist")):
            file=open(os.path.join(self.options.mountpoint, "iTunes_Control/iTunes/Ringtones.plist"), "r")
            self.parsePlist(file)
            file.close
            self.testGuid()
        else:
            print "Ringtones.plist not found. We will create it"
            self.guid=1
        (root,ext)=os.path.splitext(os.path.basename(self.options.ringtone))
        tags=M4ATags(self.options.ringtone)
        name=tags["Title"]
        newkey=(root+".m4r")
        self.ringtones[newkey]={"Name" : name, "GUID" : self.guid}
        self.makePlist()
        shutil.copyfile(self.options.ringtone,os.path.join(self.options.mountpoint, ("iTunes_Control/Ringtones/%s.m4r" % root)))
        os.chown(os.path.join(self.options.mountpoint, ("iTunes_Control/Ringtones/%s.m4r" % root)), 501, 0)
    def list(self):
        if os.path.isfile(os.path.join(self.options.mountpoint, "iTunes_Control/iTunes/Ringtones.plist")):
            file=open(os.path.join(self.options.mountpoint, "iTunes_Control/iTunes/Ringtones.plist"), "r")
        else:
            print "Ringtones.plist not found. Do you have any custom ringtones ?"
            exit()
        self.parsePlist(file)
        file.close
        for key in self.ringtones:
            for key2 in self.ringtones[key]:
                if (key2=="GUID"):
                    try:
                        print ("%s=%i"%(key2, int(self.ringtones[key][key2])))
                    except:
                        print "GUID n'est pas un entier"
                else:
                    print ("%s : %s" % (key2, self.ringtones[key][key2]))
            print ("Filename : %s" % key)
            print

    def testeArgs(self):
        if self.options.list and self.options.ringtone:
            self.parser.error("options -a and -l are mutually exclusive")
        if not os.path.isdir(self.options.mountpoint):
            self.parser.error("The directory "+self.options.mountpoint+" doesn't seem to exist. Are you sure it's your iPhone mountpoint ?")
        elif not os.path.isdir(os.path.join(self.options.mountpoint, "iTunes_Control/iTunes")):
            self.parser.error("No iTunes_Control/iTunes directory. Are you sure the iPhone is mounted ?")
        if (self.options.list == 1):
            self.list()
        elif self.options.ringtone:
            if os.path.isfile(self.options.ringtone):
                (root,ext)=os.path.splitext(self.options.ringtone)
                if (ext==".m4a"):
                    self.add()
                else:
                    self.parser.error("iphone-ringtones only supports aac(m4a).")
            else:
                self.parser.error("Unable to find the file "+self.options.ringtone+". Are you sure it exists ?")
        else:
            self.parser.error("You must specify an action, either list (-l or --list) or add (-a file or --add file)")

    def __init__(self, argv):
        self.parser=optparse.OptionParser()
        self.parserOptions()
        (self.options, self.args) = self.parser.parse_args()
        self.testeArgs()

def main(argv):
    application = IphoneRingtone(argv)

if __name__ == '__main__':
    main(sys.argv[1:])

```

anyone wants to test ? It should work fine under 1.1.2 and 1.1.3 but is only tested here with 1.1.3

---

### Post by Kulgan on 2008-02-17
I'll gladly try it out as soon as I get SSH working. Updating to 1.1.3 seems to have broken it, so I can't do anything until it fixed. Something similar happened last time, as well, but I have no idea as to what I did to fix it. According to the number of " OMG!!!11 HELP!!" posts on hackint0sh, it's quite a common problem. ( does anyone here have a decent solution? )  

But anyway, I'll try it out when I'm alive again :D

- K

---

### Post by Kulgan on 2008-02-17
Ok, Suger.. 
I got SSH working - had to restore and unlock with ziPhone instead of through Installer. Went a lot better, I have to admit, and at least SSH is working now. 
So I wanted to try out this script of yours. But then I realise that I know absolutely nothing whatsoever about python. I copied over the script you posted, save and chmod +x, then run as python scriptname.py, and got a module error. So I download the tarball in the second of those links, untar it, and stick the script in the same directory. It then tells me that "/media/iphone" is an invalid mount point, which I agree with, as the phone is mounted at /media/ipod. But it makes me wonder what it's trying to do. Shouldn't it just convert an mp3, ogg or whatever sound file into a shortened version of the right format, which I then upload - or is it doing that as well?
As I said, I'm clueless when it comes to python, so reading the source isn't helping much :(

Sorry for being such a dumbass...

-K

---

### Post by Suger on 2008-02-18
Don't worry, you're not at all being a dumbass.

First, you got things right, you need to have plist.py in the same directory as the script to get it working. As for the script, you can either chmod +x it and type

```
./iphone-ringtones
```
(if you saved it as iphone-ringtones)
or use 
```
python iphone-ringtones
``` to run it

Now for a few explanations : iphone-ringtones doesn't convert files (yet). It can either give you a list of the ringtones installed by typing

```
./iphone-ringtones -l
```

or add a ringtone to your iphone. This ringtone needs to be already in m4a format. To do that, you type

```
./iphone-ringtones -a /path/to/your/m4a
```

And if your iphone is not mounted in /media/iphone but /media/ipod, you type

```
./iphone-ringtones -m /media/iphone -a /path/to/your/m4a
```

And there you go. Right now, all it does is upload your tune to the Ringtones directory of the iphone and add an entry in the Ringtones playlist.

There are two things on my todo list : adding a preferences file (so that you don't have to use the -m switch) and adding support for other music file formats.

Is this clearer ?

---

### Post by Kulgan on 2008-02-18
It does! Thanks! 
No errors any more. No list either, but I take it that that's because I haven't actually added any ringtones :D

Do you have any suggestions as to what I should be using to convert the files to m4a? I have ConvertIT installed, but I can't figure out how to get it to convert TO m4a...

Great work... if only I could understand it :(

-K

---

### Post by Suger on 2008-02-19
Well, I must confess I always did it by hand, using the appropriate decoder to transform a file in wav format, then using faac to encode in aac

here is the faac part (for ringtones, the only important tag is the title)

```
faac --title TitleOfYourSong -b 256 -w -o "${file%.*}.m4a" "${file%.*}.wav"
```

The program to use to extract the wav depends on the format of the file

---

### Post by Kulgan on 2008-02-19
Great :D

It works perfectly. Didn't even have to reboot the phone for it to work. 
Converted it to wav with mplayer:
```
mplayer -ao pcm:file=outfile infile
```
Then to m4a with the code you sent. 

I presume that python is similar to PHP in that it has a command that allows you to execute code directly to the OS. That should work, then, shouldn't it?

Thanks a lot!

edit:
Everything transfers correctly, apparently, but the phone won't actually use it as a ringtone. It's in the list when you select, and it plays when I tap it, but not when I'm actually receivve a call. I can set other ringtones, just not the one I added. It is shown when I use the -l switch in your script. 
Is there a certain length it has to be under for the iPhone to let you use it? I just tested with a random MP3...

---

### Post by stillingen on 2008-02-22
Hi.

Thanks for the wiki. I just got my Iphone, exited to get it up and running:) 
I've followed this wiki and the device mounts ok. I can copy music from my laptop to my iphone.
However I do have issues with music not showing on my device, although it's showing in both Amarok and gtpod. . I have a 16GB iphone 1.1.3(I used ziphone to jailbrake and unlock), so I've made the symlink as described in the wiki. I've also verified that the mp3 files are indeed on the iphone using commandline;

haakon@tiptop:/media$ find /media/iphone -name "*.mp3"

/media/iphone/iTunes_Control/Music/F01/kpod0392501.mp3

/media/iphone/iTunes_Control/Music/F04/gtkpod288467.mp3


My problem is described to be related to Firewire GUID, but this applies only to Ipod Touch.
**Are there other measures one should take if this problem is on a Iphone?**

I tried anyhow, and made the changes to the SysInfo file using the command;
[I]
sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16 | xargs printf "FirewireGuid: 0x%sn" > SysInfo[/I]

Bellow is the content of SysInfo before and after:

Before:
ModelNumStr: xiPhone1

FirewireGuid: 0xaa517f107cff1df4

After:

FirewireGuid: 0xaa517f107cff1df4n

**It did not make any difference. Could there be other issues that's not related to FirewireGuid, that make the music not appear on my iphone?** In Amraok the Iphone capacity shows as 1GB, which is a bit strange..

---

### Post by ntetreau on 2008-02-22
Hi Stillingen, good to have you on board.  I'm only gonna write a few quick things because I am running out of battery on my laptop.  First, double check the GuID as there is some difference between before and after (extra "n"?), there shouldn't be.  You can remove the file anyway, plugin your iphone with USB and run iphone-mount, the right sysinfo file will be automatically created for you.

In order for the ipod to show your new synced music, you also need to restart the ipod program.  This is normally done when you unmount your iphone but for some reason, since I've upgraded to 1.1.3, I find myself having to do this manually.  Do to that, you either have to restart the whole iphone, or while in the ipod program, press and hold the Home button until it exits back to the springboard.  

For this to work though, you need to have the right sysinfo (let the iphone-mount do it for you), then you need to explicitely choose the xiPhone model in gtkpod and Amarok before syncing.

As for the 1gb capacity shown in Amarok, it shows 1000gb for me! Must be a bug.

---

### Post by ScottSatkin on 2008-02-25
Stillingen:  I have been having the same issue as you (I am able to transfer music to the iPhone, however, it does not show up in the media player).

I have tried amarok, gtkpod and rhythmbox.  The music is definitely on the iPhone.  My guess is that the iPhone music database (iTunesDB) is not be updated.

Have you had any success yet?

---

### Post by lopagof on 2008-02-25
Any way to remove the symbolic links so my 1.1.3 ipod works with ipod convenience?

every time I use ipod-touch- mount I get this:
```
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
mkdir: `/media/ipod/iTunes_Control/Music': Too many levels of symbolic links
ln: accessing `/media/ipod/iPod_Control': Too many levels of symbolic links
You don't have a Firewire GUID, so we will create one
mkdir: `/media/ipod/iTunes_Control/Device': Too many levels of symbolic links
/usr/bin/ipod-touch-mount: 98: cannot create /media/ipod/iTunes_Control/Device/SysInfo: Too many levels of symbolic links
```

any help??:confused:

---

### Post by ntetreau on 2008-02-25
@Scottsatkin & Stillingen:  Check in synaptic and tell me what version of libgpod, gtkpod and amarok you have.

---

### Post by ntetreau on 2008-02-25
> **lopagof said:**
> Any way to remove the symbolic links so my 1.1.3 ipod works with ipod convenience?

every time I use ipod-touch- mount I get this:
```
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
mkdir: `/media/ipod/iTunes_Control/Music': Too many levels of symbolic links
ln: accessing `/media/ipod/iPod_Control': Too many levels of symbolic links
You don't have a Firewire GUID, so we will create one
mkdir: `/media/ipod/iTunes_Control/Device': Too many levels of symbolic links
/usr/bin/ipod-touch-mount: 98: cannot create /media/ipod/iTunes_Control/Device/SysInfo: Too many levels of symbolic links
```

any help??:confused:

Did you create some symbolic links yourself?  If so, which one.  Please disconnect your iphone from your network or turn it off completely then try this:

```
rm -fr /media/ipod/*
```

Then reconnect and try again.  Follow the part on the wiki about the 1.1.3 firmware.  Let us know if that works.

---

### Post by ScottSatkin on 2008-02-25
> **ntetreau said:**
> @Scottsatkin & Stillingen:  Check in synaptic and tell me what version of libgpod, gtkpod and amarok you have.

Amarok:  1.4.8-0
libgpod2:  0.5.2-2
libgpod3:  0.6.0-3
gtkpod: 0.99.12-0

---

### Post by ntetreau on 2008-02-25
There you go, just uninstall completely libgpod2 which is being used instead of the latest libgpod3, then reinstall libgpod3 for good luck.  Make sure you've followed all the other instructions from the wiki.  We should add on the wiki that you need to uninstall libgpod2 before installing the newer version.

---

### Post by ScottSatkin on 2008-02-26
Alright, I have finally my music synced from Amarok to show up on my iPhone.

I used the method described on this page:

[http://blog.adaniels.nl/articles/iphone-amarok]("http://blog.adaniels.nl/articles/iphone-amarok")

Be sure to replace "/var/root/Media" with "/var/mobile/Media".

I still have not gotten the CD cover artwork to appear.

Let me know if anyone has gotten artwork to appear syncing their iPhone with Amarok.

---

### Post by ntetreau on 2008-02-26
Yes, artwork has been working for most since last November, so keep pushing it will work in the end.  Make sure you only have the latest libgpod3 (version > 0.6), amarok and gtkpod installed from the PPA repository and that Amarok and gtkpod are setup up for the iPhone model (check wiki for this).

Also, you need to restart the iphone media player after transfering, this can be done by holding the Home button for a few seconds until it closes.

Also, there is virtually no difference bewteen the method you linked to and using the ipod-convenience package and script, except one is... less convenient!

---

### Post by stillingen on 2008-02-27
> **ntetreau said:**
> Hi Stillingen, good to have you on board.  I'm only gonna write a few quick things because I am running out of battery on my laptop.  First, double check the GuID as there is some difference between before and after (extra "n"?), there shouldn't be.  You can remove the file anyway, plugin your iphone with USB and run iphone-mount, the right sysinfo file will be automatically created for you.

In order for the ipod to show your new synced music, you also need to restart the ipod program.  This is normally done when you unmount your iphone but for some reason, since I've upgraded to 1.1.3, I find myself having to do this manually.  Do to that, you either have to restart the whole iphone, or while in the ipod program, press and hold the Home button until it exits back to the springboard.  

For this to work though, you need to have the right sysinfo (let the iphone-mount do it for you), then you need to explicitely choose the xiPhone model in gtkpod and Amarok before syncing.

As for the 1gb capacity shown in Amarok, it shows 1000gb for me! Must be a bug.

Got it! Many thanks ntetreau! I removed the sysinfo file, and did the steps in the order described in the wiki. I had to restart the ipod "player" on my iphone as you mentioned. 

I have the following;
 
libgpod2 0.5.2.2
gtkpod 0.99.12
amarok 2.1.4.8.0

---

### Post by FRuMMaGe on 2008-02-27
> **ntetreau said:**
> Hi Stillingen, good to have you on board.  I'm only gonna write a few quick things because I am running out of battery on my laptop.  First, double check the GuID as there is some difference between before and after (extra "n"?), there shouldn't be.  You can remove the file anyway, plugin your iphone with USB and run iphone-mount, the right sysinfo file will be automatically created for you.

In order for the ipod to show your new synced music, you also need to restart the ipod program.  This is normally done when you unmount your iphone but for some reason, since I've upgraded to 1.1.3, I find myself having to do this manually.  Do to that, you either have to restart the whole iphone, or while in the ipod program, press and hold the Home button until it exits back to the springboard.  

For this to work though, you need to have the right sysinfo (let the iphone-mount do it for you), then you need to explicitely choose the xiPhone model in gtkpod and Amarok before syncing.

**As for the 1gb capacity shown in Amarok, it shows 1000gb for me! Must be a bug.**

Same here

Also, is there really no way to do this wired? My router takes aaaaaages to send all the info to my ipod :(

---

### Post by Will May on 2008-02-27
There is no way to do this wired.

With the previous versions of the iPod, you could access the disks on them directly (by-passing iTunes). With the iPhone/iPod Touch, disk access has been displayed (presumably because the disk inside is HFS+ only, rather than HFS+ or FAT32 with the previous versions).

I guess that as Windows doesn't support HFS+, Apple decided to disable disc access mode completely rather than have a Mac-only feature.

---

### Post by lopagof on 2008-02-27
thanks, sorry I was just being dumb. I have a occasionally do that.
I figured it out right before I got to read your question.

---

### Post by lopagof on 2008-02-27
sorry for the double post, accidentally clicked enter  im having a killer day 
thanks for the courtesy to post

---

### Post by FRuMMaGe on 2008-02-27
I deleted libgpod2 and then reinstalled libgpod3 but it still seems to think my ipod is 1000GB

Obviously it doesn't matter too much, but I would like it to be fixed

---

### Post by benanzo on 2008-02-29
For those of you wondering if we'll ever get an iPhone kernel module that allows syncing via USB, George Hotz posted on his blog a few weeks ago that he's been tinkering with it a bit.  It doesn't do much yet, but at least the effort is there.

[http://iphonejtag.blogspot.com/2008/01/113-unlock-and-linux-driver.html](http://iphonejtag.blogspot.com/2008/01/113-unlock-and-linux-driver.html)

Hopefully this goes somewhere.  It seems what we really need is a UMS kext on the phone so we can expose the filesystem out via USB, then we could just mount it as a USB mass storage device like normal.  This might be quite a ways off though...

---

### Post by robowraith on 2008-03-01
> **Kulgan said:**
> Great :D

It works perfectly. Didn't even have to reboot the phone for it to work. 
Converted it to wav with mplayer:
```
mplayer -ao pcm:file=outfile infile
```
Then to m4a with the code you sent. 

I presume that python is similar to PHP in that it has a command that allows you to execute code directly to the OS. That should work, then, shouldn't it?

Thanks a lot!

edit:
Everything transfers correctly, apparently, but the phone won't actually use it as a ringtone. It's in the list when you select, and it plays when I tap it, but not when I'm actually receivve a call. I can set other ringtones, just not the one I added. It is shown when I use the -l switch in your script. 
Is there a certain length it has to be under for the iPhone to let you use it? I just tested with a random MP3...


Maybe a stupid question, but did you rename it to .m4r? As far as I know, the ringtones are named *.m4r and not *.m4a.

rw

---

### Post by Suger on 2008-03-02
Renaming to .m4r is one of the things the script does (sorry for not replying earlier, I was in vacation). What is your version of the firmware ?

---

### Post by Mateo on 2008-03-03
so has ANYONE been able to sync gtkpod with 1.1.3 or 1.1.4?  i'm starting to regret ever upgrading from 1.1.1

---

### Post by ntetreau on 2008-03-04
> **Mateo said:**
> so has ANYONE been able to sync gtkpod with 1.1.3 or 1.1.4?  i'm starting to regret ever upgrading from 1.1.1

Hi Mateo, sorry to hear you are having difficulties.  Yes, I have been running 1.1.3 since it got out and other than to have to make a few small changes (see at the bottom of the wiki for 1.1.3), it all works fine.  The latest version of ipod-convenience should even take care of 1.1.3-1.1.4 automatically (0.7) but I'm having some issue with it at the moment.  

Please try to follow the part of the wiki on 1.1.3, then give us more details on what works and what doesn't.

---

### Post by ntetreau on 2008-03-04
I can confirm there is a bug in the latest ipod-convenience 0.7 ([bug 198139]("https://bugs.launchpad.net/ipod-convenience/+bug/198139"))

I found a workaround i think (please confirm).  In iphone-mount :

```

sudo gedit /usr/bin/iphone-mount

```

Change line 66 from:

```

    if ssh root@192.168.6.136 test -d /var/mobile; then

```

to

```

    if ssh root@$IPADDRESS test -d /var/mobile; then

```

I still get the "ssh: : Name or service not known" message but it mounts fine for me.

EDIT:  I have attached the 0.5 deb file for those who'd like to downgrade.  If you do so, remember to edit teh iphone-mout.sh file and change the music directory from /var/root/ to /var/mobile

---

### Post by FRuMMaGe on 2008-03-04
Anyone successfully synced photos to their iPhone or iPod Touch yet?

I have tried the latest svn relaese of gtkpod but to no avail.

I can add the pictures to the iPod and it even sees that they are there and tells me how many I have, but when I open the particular photo library it says "no photos"

---

### Post by Azumangaman on 2008-03-04
So I've recently istalled Ubunutu and I'm loving it. Of course, I'm trying to get my ipod touch working. Its jailbroken and eveything, but I'm having problems connecting I get this message: 
>  ipod-touch-mount
ping: unknown host ipod192.168.1.115
iPod is not responding to pings at ipod192.168.1.115.
Please set the environment variable IGNOREPING if you want to ignore this.
 
Anybody know how to fix this?
Thanks guys!

---

### Post by FRuMMaGe on 2008-03-04
> **Azumangaman said:**
> So I've recently istalled Ubunutu and I'm loving it. Of course, I'm trying to get my ipod touch working. Its jailbroken and eveything, but I'm having problems connecting I get this message: 

Anybody know how to fix this?
Thanks guys!

Is it connected to your router?

Have you set it to use a static ip?

---

### Post by Azumangaman on 2008-03-04
> **FRuMMaGe said:**
> Is it connected to your router?

Have you set it to use a static ip?
Yes its connected to the internet and it has a static ip.

---

### Post by Will May on 2008-03-05
Why does the IP address have the word ipod in front of it? From the looks of things, you set the IP address incorrectly (it should only be the address of the ipod and nothing else)

---

### Post by ntetreau on 2008-03-06
> **Will May said:**
> Why does the IP address have the word ipod in front of it? From the looks of things, you set the IP address incorrectly (it should only be the address of the ipod and nothing else)

Will May is right, run 
```
sudo dpkg-reconfigure ipod-convenience
```
and enter the right IP address

---

### Post by ntetreau on 2008-03-06
Quick message to say that I attached the 0.5 deb of ipod-convenience to my post at the top of this page regarding a bug in 0.7

---

### Post by FRuMMaGe on 2008-03-09
[SIZE="5"]For all those trying to sync photos/pictures![/SIZE]

Currently I have found no way of doing it. However, I have found a great alternative!

It is an app called iComic.

Here is complete instructions on how to install it:

> Installing icomic on your itouch/phone

To Install icomic v 0.7 from the repo.

1) Open up the installer application from the itouch/phone’s springboard.

2) Go to the 'install' tab and select 'all applications' - search for icomic and if it's there install it. If not, then go to the ‘Sources’ tab, press the ‘edit’ button it the top right corner and then press the ‘Add’ button in the top left corner. Add the source:
Code:

hpcgi3.nifty.com/moyashi/ipodtouch/repository.cgi

3) Go to the install tab again, find the icomic application and install it.

To install icomic v 0.9-2
1. download the latest icomic version, 0.9-2. from here:
Code:

[http://iphonecomic.googlecode.com/files/iComic009-2.zip](http://iphonecomic.googlecode.com/files/iComic009-2.zip)

2. Unzip and SSH either the icomic app in the 1.1.1 folder (for firmware 1.1.1 and 1.1.2) or 1.1.3 folder (for firmware 1.1.3) into the applications directory on your iphone/touch.

3. Set permissions to 755 for all files in the icomic directory.

If you now open icomic from the springboard you will see that, for the moment, menus are in Japanese. We’ll change that to English language (or other language) in the next section.

**To change the language to English**

To change the icomic application’s menu language from Japanese to English, navigate to the <root>/applications/icomic.app directory and delete the japanese.lproj directory completely (which will change all parts of icomic menus, bar the buttons, to English) and to further change the buttons to English, copy the "info.plist" file (using WinSCP) from the icomic.app directory to your desktop, open it up in notepad and change the "ja" in the following line to "en" or "english". Save it and then overwrite the old file on your iphone/touch.

i.e. from:
Code:

	<key>CFBundleDevelopmentRegion</key>
	<string>ja</string>

to:

Code:

	<key>CFBundleDevelopmentRegion</key>
	<string>en</string>

To change icomic to another itouch/phone supported language:

i. to change the buttons you must amend the CFBundleDevelopmentRegion string (as shown above) to your language, e.g. "ru" or "Russian" for Russian language buttons.

ii. to change the menu texts to a different language you will have to edit the two "localizable strings" files in the japanese.lproj directory - copy the files to your desktop, open up in Wordpad, change the Japanese translation of the English text into your own language, save the two files and copy back over the original localizable strings files on your itouch/phone (if you do this can you please post your amended files here so we can provide links to them for other international icomic users).

Russian localizable strings (thanks Mariarty)

Adding Comics

either simply:

Unpack .cbr files using Winrar and repack as .zip format. Rename .cbz files to .zip by editing the filename extension (cbr - rar compression, cbz - zip comression fyi).

or, to optimse and ensure faster page turns and load times or for repacking large comic runs (thanks lvlln)

1. Unpack the comic jpegs from your .cbr or .cbz file into a folder. You could use a file renamer here for batch renaming of .cbr to .rar and .cbz to .zip and then unpack all in one shot using WinRAR.
2. Download XnView.
3. Use XnView to batch resize your jpegs to a height of 800 pixels.
4. Repack your new optimised jpegs to a .zip file. Again you could use a batch zip utility for this.

Uploading to iphone/touch

Drag and drop your comics to the <root>/private/var/root/Media/Comic directory if you are on firmware 1.1.1. or 1.1.2 or to <root>/private/var/media/Media/Comic/ if you are on 1.1.3 (if the "Comic" directory does not exist then create it by right clicking in the itouch/phone's explorer window under WinSCP and selecting New -> Directory). A file transfer window will pop up to copy your comic to your device and you should ensure you press the 'preset' button in bottom left hand corner and select 'binary' mode before pressing the 'copy' button to copy across.

All being well you should now be able to view your comics page by page on your itouch/phone.

Note that you can add folders in the <root>/private/var/root/Media/Comic directory to better organise your comics (thanks volandkit). The addition of folders or having folders within your zip files will not affect page load times or performance.

(Adapted from Windows installation instructions)

---

### Post by scabanga on 2008-03-09
> **ntetreau said:**
> I can confirm there is a bug in the latest ipod-convenience 0.7 ([bug 198139]("https://bugs.launchpad.net/ipod-convenience/+bug/198139"))

I found a workaround i think (please confirm).  In iphone-mount :

```

sudo gedit /usr/bin/iphone-mount

```

Change line 66 from:

```

    if ssh root@192.168.6.136 test -d /var/mobile; then

```

to

```

    if ssh root@$IPADDRESS test -d /var/mobile; then

```

I still get the "ssh: : Name or service not known" message but it mounts fine for me.

EDIT:  I have attached the 0.5 deb file for those who'd like to downgrade.  If you do so, remember to edit teh iphone-mout.sh file and change the music directory from /var/root/ to /var/mobile

There's another error in the script that causes the "ssh: :Name or service not know" message ...

in line 62 or so, there's an error in the ssh root@.... command ... change IPDADDRESS to IPADDRESS and the message goes away -- or delete the whole line, it's not needed anyway ....

works fine after that

rgds
Scabanga

---

### Post by Naddiseo on 2008-03-10
Does anyone know the default ssh password for 1.1.4? "alpine" (without quotes)isn't working for me.


Edit:never mind.. it seems it just asks me 3 times, even though it succeeds.

---

### Post by Shrynn on 2008-03-10
Okay I'm having some trouble with the iphone-mount command. My Ubuntu doesn't seem to like the ssh command. Here is my output....

```
shrynn@shrynn-Linux:/usr/bin$ iphone-mount
iPod is not responding to pings at 192.168.0.7.
Please set the environment variable IGNOREPING if you want to ignore this.
ssh: connect to host 192.168.0.7 port 22: No route to host
ssh: connect to host 192.168.0.7 port 22: No route to host
read: Connection reset by peer

```

I CAN run sshfs root@IPADDRESS:/var/mobile /media/iphone
no problems there. I can login a see directory structure. 

If I use the instructions at [http://blog.adaniels.nl/?p=50]("http://blog.adaniels.nl/?p=50")] I can see and transfer mp3s to the iphone. Album art doesn't work and currently no sound from the mp3s on the iPhone (though sound did work at one point).

So I decided to go the ipod-convenience route. Any idea on why ssh and ping can't see the iphone? 

Amarok 1.4.8
libgpod3
Gutsy
iPhone 1.1.4 firmware

UPDATE: Checked my router and saw that my iPhones IP address was in the DHCP range. I moved it out of the DHCP range and everything works great now. Not sure why that matters... but working now.

---

### Post by Azumangaman on 2008-03-12
Ok, so I realized I had to get rid of the "ipod" in the IP address. Whoops. BUt my iPod messed up, so I had to restore and re-jailbreak it. Now when I do the earler step on the first post of page 2, I get this:

```
azumangaman@azumangaman-desktop:~$ ssh root@192.168.1.115
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
3a:07:ef:f6:e4:a2:63:d7:ed:f2:11:04:22:ef:ce:85.
Please contact your system administrator.
Add correct host key in /home/azumangaman/.ssh/known_hosts to get rid of this message.
Offending key in /home/azumangaman/.ssh/known_hosts:1
RSA host key for 192.168.1.115 has changed and you have requested strict checking.
Host key verification failed.

```

---

### Post by FRuMMaGe on 2008-03-12
> **Azumangaman said:**
> Ok, so I realized I had to get rid of the "ipod" in the IP address. Whoops. BUt my iPod messed up, so I had to restore and re-jailbreak it. Now when I do the earler step on the first post of page 2, I get this:

```
azumangaman@azumangaman-desktop:~$ ssh root@192.168.1.115
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
3a:07:ef:f6:e4:a2:63:d7:ed:f2:11:04:22:ef:ce:85.
Please contact your system administrator.
Add correct host key in /home/azumangaman/.ssh/known_hosts to get rid of this message.
Offending key in /home/azumangaman/.ssh/known_hosts:1
RSA host key for 192.168.1.115 has changed and you have requested strict checking.
Host key verification failed.

```

Mine did this. It still has the hosts file from the other. Just type in the terminal:

rm .ssh/known_hosts

Hope this helps :)

---

### Post by Azumangaman on 2008-03-12
Thanks, that seemed to work. New problem (yaay):
When I try to follow the steps:
> 
- move to where the iTunes library is: "cd /var/root/Media"
- make a symbolic link to this directory from within itself (weird, but necesserary): "ln -s . iTunes"
- make another symbolic link to the iTunes_Control directory called iPod_Control: "ln -s iTunes_Control iPod_Control"


And I get:

```

# cd /var/root/Media
cd: no such file or directory: /var/root/Media

```

---

### Post by FRuMMaGe on 2008-03-12
> **Azumangaman said:**
> Thanks, that seemed to work. New problem (yaay):
When I try to follow the steps:


And I get:

```

# cd /var/root/Media
cd: no such file or directory: /var/root/Media

```

In that firmware, it will be:

cd /var/mobile/Media

---

### Post by tomislavmedak on 2008-03-12
I didn't see this problem and solution being posted earlier in this thread - if so, please excuse redundancy. I'd be happy to learn if there was an easier solution.

The problem was that after upgrading my iPhone to 1.1.4 from 1.1.1 I couldn't get the iPhone to play my music files. Using the ipod-convenience I've upgraded to ver. 0.8 and Amarok, I managed to write files and find them subsequently in the iPhone music folders, however I couldn't get my iPhone to read them.

After mucking around I discovered that Amarok wrote changes to an iTunesDB file in a different folder than the one used to store music. While my music was written to:

*/var/mobile/Media/iTunes_Control*

the iTunesDB was written to:

*/var/mobile/Media/iPod_Control*

To solve the problem I discovered that I need to do the following: after my Amarok finishes transferring music files and I disconnect the iPhone, I log onto the iPhone and manually replace the iTunesDB file that iPhone reads from:
[I]
/var/mobile/Media/iTunes_Control/iTunes/iTunesDB[/I]

with the iTunesDB that Amarok used to write the database into:
[I]
/var/mobile/Media/iPod_Control/iTunes/iTunesDB[/I]

All works fine now. It's a dirty hack though. I guess symlinking the two files could solve this easier. But I guess the real reason and solution for this strange behaviour should be found in the mount-umount script in the */usr/share/ipod-convenience/*.

---

### Post by Azumangaman on 2008-03-12
> **FRuMMaGe said:**
> In that firmware, it will be:

cd /var/mobile/Media

So I did that and put in the other 2 things and it came out like this:
```

# cd /var/mobile/Media
# ln -s . iTunes
# ln -s iTunes_Control iPod_Contro

```
Nothing showed up or anything extra, so I just exited. 
Whats the command to use for mounting?


Thanks,
Azumangaman

---

### Post by xjgnsdof on 2008-03-13
Ubuntu screwed up some of my artwork when I synched my iPod Touch through gtkpod. When I tried it with Amarok, it screwed up all of my artwork. Now, I can see artwork in iTunes (when I try to synch in Windows), but not on the iPod Touch. Anyone else have this problem and know how to fix it?

---

### Post by darkkith on 2008-03-13
You probably corrupted the artworkdb.  ssh into your ipod and look for a file called ArtworkDB..  there may also be a folder related to it.. rm -rf all of that stuff, then resynch with windows/itunes

---

### Post by ntetreau on 2008-03-13
> **elgilicious said:**
> Ubuntu screwed up some of my artwork when I synched my iPod Touch through gtkpod. When I tried it with Amarok, it screwed up all of my artwork. Now, I can see artwork in iTunes (when I try to synch in Windows), but not on the iPod Touch. Anyone else have this problem and know how to fix it?

You could also let amarok resync all the artwork. After connecting the iphone in Amarok, click on iPod and Update Artwork.

---

### Post by ntetreau on 2008-03-13
> **tomislavmedak said:**
> I didn't see this problem and solution being posted earlier in this thread - if so, please excuse redundancy. I'd be happy to learn if there was an easier solution.

The problem was that after upgrading my iPhone to 1.1.4 from 1.1.1 I couldn't get the iPhone to play my music files. Using the ipod-convenience I've upgraded to ver. 0.8 and Amarok, I managed to write files and find them subsequently in the iPhone music folders, however I couldn't get my iPhone to read them.

After mucking around I discovered that Amarok wrote changes to an iTunesDB file in a different folder than the one used to store music. While my music was written to:

*/var/mobile/Media/iTunes_Control*

the iTunesDB was written to:

*/var/mobile/Media/iPod_Control*

To solve the problem I discovered that I need to do the following: after my Amarok finishes transferring music files and I disconnect the iPhone, I log onto the iPhone and manually replace the iTunesDB file that iPhone reads from:
[I]
/var/mobile/Media/iTunes_Control/iTunes/iTunesDB[/I]

with the iTunesDB that Amarok used to write the database into:
[I]
/var/mobile/Media/iPod_Control/iTunes/iTunesDB[/I]

All works fine now. It's a dirty hack though. I guess symlinking the two files could solve this easier. But I guess the real reason and solution for this strange behaviour should be found in the mount-umount script in the */usr/share/ipod-convenience/*.

I'm on 1.1.3, I let ipod-convenience script (iphone-mount) create all the relevant folders and links.  Here's what I have:

```
# pwd
/var/mobile/Media
# ls -l
total 24
drwxr-xr-x   4 mobile  wheel  136 Feb 27 22:35 DCIM
drwxr-xr-x   2 mobile  wheel  136 Mar  7 09:27 MxTube
drwxr-xr-x   3 root    wheel  136 Mar  8 14:28 Photos
-rw-r--r--   1 mobile  wheel    0 Feb 22 21:24 com.apple.itunes.lock_sync
lrwxr-xr-x   1 root    wheel   14 Feb 22 21:02 iPod_Control -> iTunes_Control
lrwxr-xr-x   1 root    wheel    1 Feb 22 21:02 iTunes -> .
-rw-r--r--   1 mobile  wheel  969 Mar  7 21:26 iTunesOnTheGoPlaylist.plist
drwxr-xr-x   6 root    wheel  204 Feb 22 21:20 iTunes_Control

```

With these simlinks, you can see that amarok saves the database in the right folder as iPod_Control links to iTunes_Control

---

### Post by xjgnsdof on 2008-03-13
@darkkith
That's exactly how I rectified this matter. I deleted the Artwork folder (which is in the iPod_Control folder) that contained the artworkdb file. I then reconnected to iTunes, deleted all my media from the iPod, and resynched with my music and video libraries.

@ ntetreau
I have had luck playing music in Rhythmbox. When I use gtkpod and amarok for that purpose, I get screwy artwork again. Maybe when I have the patience, I will try to play AND synch media in Ubuntu. Until then, I will resort to iTunes.

---

### Post by ookadoo on 2008-03-22
I have a very strange problem and it doesn't seem to matter if I use gtkpod, amarok or rhythmbox.  I can mount, sync new music, and unmount without any errors but when I restart the iPhone and attempt to play the music, most tracks play but some only play 2-4 seconds of silence then it skips to the next track.

Has anyone else experienced this?

I have firmware 1.1.4 and used ZiPhone to jailbreak my iPhone.  Then I did the following
- Installed BSD subsystem
- Installed OpenSSH server
- Installed ipod convenience on gutsy and 99.12 gtkpod

---

### Post by Suger on 2008-03-24
Well yes, I have the same problem here and I have been having it with both 1.1.2 and 1.1.3. Just testing now with 1.1.4

---

### Post by Kulgan on 2008-03-24
Just thought I'd notify those who haven't upgraded yet:

Hardy doesn't find the pictures automatically when you stick the iPhone in the charger. You have to use SSH to get them out of the folder (/var/mobile/Media/DCIM/100APPLE for the camera roll) and GTKpod doesn't find them when you start it as usual. 

Other than that, everything seems fine.

To those who don't get any music playing when transferring from ubuntu:
Have you tried clicking the "Save changes" button again once the media has already been transferred? I don't know why, but that worked for me the first time. After that it has been operating normally. I just restarted the media player rather than the whole phone, but the effect should be the same.

---

### Post by ookadoo on 2008-03-24
> **Kulgan said:**
> 
To those who don't get any music playing when transferring from ubuntu:
Have you tried clicking the "Save changes" button again once the media has already been transferred? I don't know why, but that worked for me the first time. After that it has been operating normally. I just restarted the media player rather than the whole phone, but the effect should be the same.

Yes I do choose "Save Changes" after I add an album.  I've tried several times and each time the tracks that do not play will be different.  I do the following each time I sync music.

1. iphone-mount, enter password
2. run gtkpod
3. add folder
4. select "Save Changes" and it shows the progress bar, wait for it to complete then wait a few minutes longer
5. close gtkpod
6. iphone-unmount (successful)
7. restart phone


An example of the track inconsistency:

- 1st sync, tracks 2,8,9,12 do not play (silence, track time does not advance)
- delete album, restart phone
- 2nd sync (same album as before), tracks 4,8 do not play

It's very irritating especially when it skips songs I like :(

---

### Post by Kulgan on 2008-03-24
Odd that they alternately drop out. That is definitely an issue of not being able to enter the songs' locations into the database. 

What kind of wireless connection are you using? Encrypted? How strong is the signal?

---

### Post by ookadoo on 2008-03-24
> **Kulgan said:**
> Odd that they alternately drop out. That is definitely an issue of not being able to enter the songs' locations into the database. 

What kind of wireless connection are you using? Encrypted? How strong is the signal?

It is very odd.  I do have WPA encryption on the wireless, and the iPhone is about 1 foot away from the router.

I forgot to mention that I can play the songs in gtkpod from the iPhone.  I'm assuming it's playing it wirelessly from the phone so I think that validates your idea that it's a database issue and not that the mp3 files are missing.

---

### Post by stillingen on 2008-03-25
I've been using my iPhone with Amarok now for just over a month, and everything has work perfectly. After I connected my iPhone to Win PC and synced with iTunes I deleted all my music as a had no music on the Win PC (not very smart I know). Know back on Amarok I also have the issue with Artwork. I've deleted the ArtworkDB and .ithmb files that are in the Artwork directory. When I connect and update via Amarok I can see the ArtworkDB and the .ithmb getting created, but there is no artwork showing on my iPhone. The ArworkDB file is 0kb btw, and contains nothing. 
What is typical content of this file, and could it be that the permission are not set correct?

---

### Post by Kulgan on 2008-03-25
O.o 
is this stillingen from trap17? My apologies if I'm wrong...

Here's my artwork folder's contents and permissions, anyway:
```

# ls -la /var/root/Media/iPod_Control/Artwork
total 344992
drwxr-xr-x   2 root    wheel       306 Mar 24 23:05 .
drwxr-xr-x   7 mobile  wheel       272 Mar 24 01:13 ..
-rw-r--r--   1 root    wheel    492192 Mar 24 23:05 ArtworkDB
-rw-r--r--   1 root    wheel  56623104 Mar 24 23:05 F3001_1.ithmb
-rw-r--r--   1 root    wheel  14155776 Mar 24 23:05 F3002_1.ithmb
-rw-r--r--   1 root    wheel   3538944 Mar 24 23:05 F3003_1.ithmb
-rw-r--r--   1 root    wheel  88473600 Mar 24 23:05 F3005_1.ithmb
-rw-r--r--   1 root    wheel   4000256 Mar 24 16:19 F3006_1.ithmb
-rw-r--r--   1 root    wheel   9343844 Mar 24 16:19 F3007_1.ithmb

```

The first songs I transferred were from Rhythmbox, which seemed to work fine so long as RB itself knew what the cover file was..

---

### Post by Romu on 2008-03-26
Dear all,
I've just read the 43 pages of this thread, thanks for all !!

I've just also seen the ml-iPod plugin for Winamp is making some progresses to bring iTouch/iPhone support to winamp:
[http://mlipod.sourceforge.net/](http://mlipod.sourceforge.net/)

Is there any way to "port" or to share the works to accelerate this work on Ubuntu?

---

### Post by President_Thor on 2008-03-26
Unlike the poster before me, I'm too lazy to read all of it. I read several pages, and my problem is still unfixed.

I'm using Filezilla for my SSH, but I know that the problem is not coming from the program, because I've also had the problem in WinSCP. 

The problem is that I have a really hard time getting connected to the phone, and when I do, I lose the connection after I go through about the second folder. It's a pain, and I can't get anything done. I'm running 1.1.4 on my phone, and I'm running Ubuntu 7.10 on my computer. Is there an alternative to the method I'm using? Is there a fix for the constant disconnections? 

I'd really appreciate some help.

---

### Post by stillingen on 2008-03-27
> **Kulgan said:**
> O.o 
is this stillingen from trap17? My apologies if I'm wrong...


Yes, that's me:)

I've connected my iPhone to ITunes and updated the Artwork, everything worked fine. Artwork DB, was no longer 0Kb either. Now, back on Ubuntu and Amarok, I've added a new album and did a transfere. The problem returns, no Artwork on my iPhone and ArtworkDB back to 0Kb.


```

haakon@tiptop:/media/iphone/iTunes_Control/Artwork$ ls -lah
total 1.7M
drwxr-xr-x 1 root root  170 2008-03-27 19:32 .
drwxr-xr-x 1  501 root  238 2008-03-27 19:16 ..
-rw-r--r-- 1 root root    0 2008-03-27 19:32 ArtworkDB
-rw-r--r-- 1 root root 171K 2008-03-27 19:32 F2002_1.ithmb
-rw-r--r-- 1 root root 1.6M 2008-03-27 19:32 F2003_1.ithmb
haakon@tiptop:/media/iphone/iTunes_Control/Artwork$ 

```


Is the ArtworkDB sesitive to owner and moderator? I tried to change owner to 501, but that didn't solve the problem. 

I tried connecting using gtkpod, and I get this message:

Could not open "(null)" for reading extended info.
Extended info will not be used.
Error while mmap'ing /media/iphone/iPod_Control/Artwork/ArtworkDB: Invalid argument
Error reading iPod photo database (Photos directory not found: '/media/iphone/iPod_Control/Photos' (or similar).).

I deleted the Artwork Folder, and started gtkpod again. Added an album and saved the changes. Now ArtworkDB is 1,5Kb byte, but I don't now how to add Artwork in gtkpod, so I'm a bit stuck, but at least the ArtworkDB it not 0Kb. 

Could this be a Amarokproblem? This started happening after I connected my iPhone to iTunes and synced music. What is the difference in the way that iTunes write data, and the iPod convinience script write data that could cause such a problem?

---

### Post by ntetreau on 2008-03-27
For all those who are having problems with artwork, here's a few things I tried myself after updating to 1.1.4 and finally got me going.

Check in Synaptic that you only have libgpod3 installed, if you also have libgpod2 installed as well, purge it.

Then, delete the ArtworkDB file, you've done this a few times already, do it again.

Then fire up Amarok and press the connect button.  Once connected, double check that Amarok is still setup for the xiPhone type of ipod.  This setting doesn't always seem to stick for me, especially after update amarok.

Then, choose: Sync Artwork.  This can take ages if you have a lot of music.  You can monitor the transfer through the System monitor.  If nothing gets transfered, something else is wrong.  

When it's done, take a look at your ArtworkDB file again, it should be big (I'm at work, so can't check the size of mine!).  Restart the iphone MediaPlayer by holding the Home button 6 seconds.  Hopefully, you'll see your artwork.

To recap, the two important steps here is to double check that the right libgpod is installed and used, then make sure Amarok is configured specifically for the iphone.

If that doesn't work, go back to the wiki, and double check the the Firewire ID was transfered correctly to the device.  If not, delete it, plug in the iphone through USB and iphone-mount it.

Good luck

---

### Post by ntetreau on 2008-03-27
> **President_Thor said:**
> Unlike the poster before me, I'm too lazy to read all of it. I read several pages, and my problem is still unfixed.

I'm using Filezilla for my SSH, but I know that the problem is not coming from the program, because I've also had the problem in WinSCP. 

The problem is that I have a really hard time getting connected to the phone, and when I do, I lose the connection after I go through about the second folder. It's a pain, and I can't get anything done. I'm running 1.1.4 on my phone, and I'm running Ubuntu 7.10 on my computer. Is there an alternative to the method I'm using? Is there a fix for the constant disconnections? 

I'd really appreciate some help.

is it only SSH that disconnects or the iphone looses the wifi connection altogether?  Are your other devices in your house also affected by this?  From the same computer, can you SSH another computer/device than the iphone and stay connected?  If you can, try to connect via DHCP on the iphone instead of a static address.  To change the IP address in ipod-convenience, do a 

```
sudo dpkg-reconfigure ipod-convenience
```
and enter the new dynamic IP.  See if that kind of connection is more stable.  If you have the same SSH problem with other devices, you could be having some issues with your router, and this is better solved by posting to the general networking forum.

---

### Post by stillingen on 2008-03-27
> **ntetreau said:**
> 
Check in Synaptic that you only have libgpod3 installed, if you also have libgpod2 installed as well, purge it.


Hi ntetreau. If I purge libgpod2, I also remove amarok. Is there a workaround?

---

### Post by ntetreau on 2008-03-27
> **stillingen said:**
> Hi ntetreau. If I purge libgpod2, I also remove amarok. Is there a workaround?

At least, we found the culprit!  Indeed, purge ligpod2 and amarok, there are the wrong versions.

Please refer to the wiki : [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) in the "Setup Ubuntu" section and add the PPA repository, update and reinstall libgpod (now version libgpod3), amarok, gtkpod again.  Keep following the wiki to the letter, setting up amarok properly, including the part on setting up the type of ipod as the xiPhone.  After that, it should work.

This may fix the problems encountered by ookadoo and kulgan as well.

---

### Post by Kulgan on 2008-03-27
I'm on Hardy. Version 3 is installed by default. However, I may originally have had version 2 installed on Gutsy - but everything seemed to work fine (except that I could never access photos through gtkpod. 

But I don't think it would be a bad idea to upgrade if you haven't. :D

---

### Post by stillingen on 2008-03-27
> **ntetreau said:**
> At least, we found the culprit!  Indeed, purge ligpod2 and amarok, there are the wrong versions.


Thanks again, but I'm still missing something here. The repo for ipod-convenience is correct, but with the other [repos]("http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories") I'm using it's not possible to install Amarok without installing libgpod2.


Which repo are you fetching Amarok from?

---

### Post by ntetreau on 2008-03-28
> **stillingen said:**
> Thanks again, but I'm still missing something here. The repo for ipod-convenience is correct, but with the other [repos]("http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories") I'm using it's not possible to install Amarok without installing libgpod2.


Which repo are you fetching Amarok from?

I'm on hardy so there is no need for a separate repo for libgpod and amarok.  However, you can probably fire up synaptic, click on "Origin" in the lower left corner and choose the PPA repo.  You should see the PPA amarok version there and install it together with the right libgpod3.

---

### Post by HilliBilly on 2008-03-29
hi,

i cannot mount my iphone. please help. this is my error message:

:/media$ **iphone-mount **
root@192.168.1.25's password: 
root@192.168.1.25's password: 
root@192.168.1.25:/var/mobile/Media: No such file or directory

'No such directory' is correct because

:~$ **ssh -l root 192.168.1.25**
root@192.168.1.25's password: 
Last login: Sat Mar 29 19:19:47 2008 from 192.168.1.16
# **ls /var/mobile **
.forward        Library
#** ls /var/root  **
Library Media
# 

i am on gutsy (2.6.22-14-generic), iphone 1.0.2, gtkpod 0.99.10, ipod-convenience 0.9

btw ...why is it asking twice for the root password?

---

### Post by Kulgan on 2008-03-30
Not to sure what exactly the problem is, but it has to do with links to the media folder (I assume you are on firmware 1.1.4?). 
For reference, the same stuff looks like this for me:
```
$ ssh root@iphone
Last login: Sun Mar 30 12:54:22 2008 from 192.168.0.101
# ls -la /var/mobile 
total 8
drwxr-xr-x    4 mobile  wheel  170 Feb 17 19:15 .
drwxr-xr-x   16 root    wheel  612 Feb 17 19:10 ..
-r--r--r--    1 mobile  wheel   10 Dec 12 08:39 .forward
drwxr-xr-x   20 mobile  wheel  816 Mar 28 21:13 Library
drwxr-x---    8 mobile  wheel  408 Mar 30 00:41 Media
# ls -la /var/root 
total 8
drwxr-xr-x    4 root  wheel  170 Mar 29 15:29 .
drwxr-xr-x   16 root  wheel  612 Feb 17 19:10 ..
drwx------    2 root  wheel  136 Mar 29 15:34 .ssh
drwxrwxrwx    5 root  wheel  170 Feb 17 18:59 Library
lrwxr-xr-x    1 root  wheel   25 Feb 17 19:14 Media -> /private/var/mobile/Media

```

Your /var/mobile/Media folder does not seem to exist... try doing 
```
ln -s /var/root/Media /var/mobile/Media
```
reboot and try again.

To prevent having to enter the password all the time, follow the section in the wiki:
[https://help.ubuntu.com/community/PortableDevices/iPhone#head-42c6360c46112bf20f0e2ab9c52059202821d821](https://help.ubuntu.com/community/PortableDevices/iPhone#head-42c6360c46112bf20f0e2ab9c52059202821d821)

---

### Post by HilliBilly on 2008-03-30
hi,

it's me again. i don't know how but i did a real big mess. all my images and all my musicfiles on the iphone seems to be deleted. how is this possible by using this one command 'iphone-mount'? 
> 
xyz@centaur4:~$ ssh -l root 192.168.1.25
root@192.168.1.25's password: 
Last login: Sun Mar 30 12:35:08 2008 from 192.168.1.16
# ls -la /var/mobile 
total 8
drwxr-x---    3 mobile  wheel  136 May 23  2007 .
drwxr-xr-x   14 root    wheel  544 Jan 30 00:26 ..
-r--r--r--    1 mobile  wheel   10 May 23  2007 .forward
drwx------    3 mobile  wheel  136 May 23  2007 Library
# ls -la /var/root  
total 0
drwxrwxrwx    4 root  wheel  136 Sep 11  2007 .
drwxr-xr-x   14 root  wheel  544 Jan 30 00:26 ..
drwxrwxrwx   25 root  wheel  884 Mar 29 16:18 Library
drwxr-x---    3 1000  106    136 Mar 30 13:24 Media
# 
# ls -la /var/root/Media 
total 0
drwxr-x---   3 1000  106    136 Mar 30 13:24 .
drwxrwxrwx   4 root  wheel  136 Sep 11  2007 ..
-rw-r--r--   1 root  106      0 Mar 30 12:36 com.apple.itunes.lock_sync
# 
[COLOR="Red"](here should be more directories, like DCIM ...)[/COLOR]


there is another thing i do not understand:

xyz@centaur4:/usr/share/ipod-convenience$ cd /media/ipod/
xyz@centaur4:/media/ipod$ ls
iPod_Control  iTunes  iTunes_Control
xyz@centaur4:/media/ipod$ ls -ltr
total 4
drwxr-xr-x 4 xyz xyz 4096 2008-03-29 22:21 iTunes_Control
lrwxrwxrwx 1 xyz xyz    1 2008-03-29 22:21 iTunes -> .
lrwxrwxrwx 1 xyz xyz   14 2008-03-29 22:21 iPod_Control -> iTunes_Control
**xyz@centaur4:/media/ipod$ cd iTunes**
xyz@centaur4:/media/ipod/iTunes$ ls -ltr
total 4
drwxr-xr-x 4 xyz xyz 4096 2008-03-29 22:21 iTunes_Control
lrwxrwxrwx 1 xyz xyz    1 2008-03-29 22:21 iTunes -> .
lrwxrwxrwx 1 xyz xyz   14 2008-03-29 22:21 iPod_Control -> iTunes_Control
**xyz@centaur4:/media/ipod/iTunes$ cd iTunes**
xyz@centaur4:/media/ipod/iTunes/iTunes$ ls -ltr
total 4
drwxr-xr-x 4 xyz xyz 4096 2008-03-29 22:21 iTunes_Control
lrwxrwxrwx 1 xyz xyz    1 2008-03-29 22:21 iTunes -> .
lrwxrwxrwx 1 xyz xyz   14 2008-03-29 22:21 iPod_Control -> iTunes_Control
**xyz@centaur4:/media/ipod/iTunes/iTunes$ cd iTunes**
xyz@centaur4:/media/ipod/iTunes/iTunes/iTunes$ ls -ltr
total 4
drwxr-xr-x 4 xyz xyz 4096 2008-03-29 22:21 iTunes_Control
lrwxrwxrwx 1 xyz xyz    1 2008-03-29 22:21 iTunes -> .
lrwxrwxrwx 1 xyz xyz   14 2008-03-29 22:21 iPod_Control -> iTunes_Control
xyz@centaur4:/media/ipod/iTunes/iTunes/iTunes$


@Kulgan: i'm on firmware 1.0.2.

---

### Post by Xpyd3r on 2008-03-30
Would this be like a passive link to my computer? like, could I still get updates and get those extra things and still be able to use it on my linux computer to upload music and what not? I want to get one but not if I can only use itunes, or if I give up those extra features to use it on linux...

---

### Post by ntetreau on 2008-03-30
hillibilly,
looking at your directory tree, it seems to be on your computer and not on your iphone.  Turn off your iphone, or at least make sure it is not connected to your network.  Then rm the direectories in /media/ipod:

```
rm -fr /media/ipod/*
```

Reconnect to your network with ipod, then remount it.  check the directory tree now.

---

### Post by Kulgan on 2008-03-30
@HilliBilly
try getting rid of the folders on your computer, then mount the phone again. Make sure to turn the phone completely off before deleting everythin in /media/ipod. 

@Xpyd3r
Pretty much everything works the same way. Ie, you can plug it into a windows PC/Mac and sync with iTunes. Then you can SSH into it from your Linux box and sync from Linux. You have to jailbreak it for that, though. See the [wiki]("https://help.ubuntu.com/community/PortableDevices/iPhone") for more details.
The one thing that will not work the same way is firmware updates on the phone. You shouldn't update the firmware via iTunes unless you know it's safe - this is related to the jailbreaking and unlocking, though, no Ubuntu. 
I would recommend getting one. It's fun :3

-K

---

### Post by Xpyd3r on 2008-03-30
So I can still play on the internet, check my email, use google earth, and whatever other nifty features they have right?  I mostly want it to be half internet email and half music and movies, but I'd like to play with whatever other features they have too...

---

### Post by HilliBilly on 2008-03-30
@ntetreau & Kulgan

thanks for your answers! in the meantime i got everything working. i'm quite sure that i didn't disconnect resp. unmount my iphone when executing the 'rm -fr /media/ipod/*' (what i had to do because at one point the mount command complained that the mountpoint wasn't empty) and this deleted all media files on my iphone. i didn't have a backup of my images, i.e. i learned it the hard way *smile*.

btw ... i'm using gtkpod (version 0.99.12) and i have a little problem with the artwork:

i can manually add the cover art into gtkpod and then write it to the iphone. but i would prefer if gtkpod would automatically reads it from somewhere but it doesn't. i checkboxed the 'read coverart from embedded apic data' in gtkpod's preferences but this doesn't do it. any ideas what is wrong?

---

### Post by Caldur06 on 2008-03-31
I've been having trouble getting ubuntu to sync with my iPod Touch. I've followed the tutorials, and music is getting on my iPod, as I can find the files using the application Squid on my Touch. However, when I open the music app on my Touch, it doesn't find the music I synced to it. I've tried everything I can think of and have looked on google for countless hours. The only thing I can think of that I can do now is to either delete all the songs on my iPod or restore my ipod (which I really don't want to do).

My SysInfo has my GUID for the record.

Is my database file corrupted or something? I was using gtkpod 99.10 at the very beginning and then I read to use 99.12 so I upgraded. Could that have screwed up my DB file? And if so, how can I fix it?

Or just any ideas in general? I've been trying for so long to get this to work.. As far as I can tell, the music is on my iPod, it's just not getting recognized..

---

### Post by Kulgan on 2008-03-31
Are you using the "find on web" option or "select from file" to add it manually?

@Caldur06:
I take it you've rebooted the phone at least once since transfering the music. Is it that the phone can't find the files, or that  they aren't playing properly. We've had a few issues of that...

---

### Post by Caldur06 on 2008-03-31
Yeah, I've been trying about everything I can think of, and I usually unmount and reboot my ipod to make sure. And they're just not showing up on my ipod at all.

---

### Post by Kulgan on 2008-03-31
does the music appear when you connect to itunes? ( careful about that, though... Any music that isn't in iTunes will be deleted if yu sync.

---

### Post by ntetreau on 2008-03-31
@Caldur06:  Please check in synaptics that you have only one version of libgpod installed, it has to be libgpod3, not libgod2.  Also, try to set up amarok, at least for testing purposes.  In both gtkpod and amarok, you need to specify that your ipod is a touch (or alternatively an xiPhone, both are the same for libgpod if I remember correctly).  Once connected in amarok, you should see the music that's on your ipod, if not, click on the little arrows next to Connect, iPod, Stale and orphaned, it will find the music files not in the database and you can then right click on the bunch and add them to the database. Amarok will also automatically sync your artwork, provided it found them prior to syncing.

---

### Post by ntetreau on 2008-03-31
> **Xpyd3r said:**
> So I can still play on the internet, check my email, use google earth, and whatever other nifty features they have right?  I mostly want it to be half internet email and half music and movies, but I'd like to play with whatever other features they have too...

Yes, everything else including the internet will still work.

---

### Post by Romu on 2008-03-31
Hi all,
I'm coming back with my idea to port the ml_ipod code to Ubuntu. ml_ipod bring the iTouch/iPhone support to winamp as described here:
[http://mlipod.sourceforge.net/wiki/IPhone_and_iPod_touch_support](http://mlipod.sourceforge.net/wiki/IPhone_and_iPod_touch_support)

Any chance this to be useful for Ubuntu?

---

### Post by dbrice3 on 2008-03-31
I'm having the problem that my music doesn't show up in the iPhone's iPod program .

The music transfers onto the phone at 
/var/mobile/Media/iTunes_Controll/Music/

But, my other media on the phone is at 
/var/root/Media/iTunes_Control/Music

If it isn't obvious, I'm on iPhone firmware 1.12.

I have the Hardy beta.

Thanks for your help.  Just making this post has given me a better idea of my problem.

---

### Post by Caldur06 on 2008-03-31
Thanks for the responses!

I checked, and I did have two versions of libgpod (2 and 3). I uninstalled 2, but it seems I'm having the exact same problem still. To clarify:

When my iPod is mounted, I can see the music that I synced to it from Linux from Amarok, gtkpod, and RhythmBox. They all show that the music is on my iPod. However, none of these programs show the music that is already on my iPod (synced from iTunes on Windows).

And when I open the Music app on my iPod, it still doesn't find the music. I've tried fiddling with both Amarok and gtkpod with the exact same results.

Oh, and my music is getting synced to the same place as the last poster's like this:

/var/mobile/Media/iTunes_Controll/Music/

When the iTunes put the music here:

/var/root/Media/iTunes_Control/Music

Is that normal? I have 1.1.1 firmware and am running Gutsy.

Any more ideas? I figured uninstalling libgpod2 would have worked.. but it didn't. :(

---

### Post by Caldur06 on 2008-03-31
To the first page we go.

---

### Post by Q-ro on 2008-03-31
Well i'm kind of new in all of this, but i; having some problemes with my iphone, i changed form indows vista ( suck a lot ,)to ubuntu gutsy, and everything have gone fine, till now, i got an iphone, and i cannot upload music to it, well, i can, but i does not play at all, its like, 2 o 3 min of absolute silence, and no possibility to listen to it at all on my iphone, i have already convert the mp3 file yo an m4a that is the one the iphone use... so, any one with a good idea ?? ( or do i have to go back to MICRO$OFT or Mac OS ?? :S ) ..

PD: i tried using wine and itunes, but i cannot put music on it unless i errase all the music i have on my iphone, i i have no way to backup it, when i put all the music on the iphone i erase it couse i needed some space...

so any idea ?? :confused:

---

### Post by dbrice3 on 2008-03-31
I retried the procedure, this time with gtkPod.  

Unfortunately, ultimately I end up with the same results.

When loading the iPhone for the first time, after asking gtkPod to create the file structure/directories for the iPod, I receive this message.

Could not open "(null)" for reading extended info.
Extended info will not be used.

Amarok continues to fail me at transferring data, although I can say for certain, the music gets onto the phone.

Any help would be much appreciated.  I'd be glad to give more error messages or config file readings if there's something you think might be the problem.

---

### Post by Q-ro on 2008-03-31
> **dbrice3 said:**
> I retried the procedure, this time with gtkPod.  

Unfortunately, ultimately I end up with the same results.

When loading the iPhone for the first time, after asking gtkPod to create the file structure/directories for the iPod, I receive this message.

Could not open "(null)" for reading extended info.
Extended info will not be used.

Amarok continues to fail me at transferring data, although I can say for certain, the music gets onto the phone.

Any help would be much appreciated.  I'd be glad to give more error messages or config file readings if there's something you think might be the problem.

i have done it with Rhythmbox 0.11.2, till now i can listen to any song in my iphone, but first i did all that they say here :

[http://www.fsckin.com/2007/10/10/how-to-stream-music-from-the-iphone-in-ubuntu/#comments](http://www.fsckin.com/2007/10/10/how-to-stream-music-from-the-iphone-in-ubuntu/#comments)

For me it worked perfectly, i can reproduce any song of my iphone with Rhythmbox, but cannot put music on it ( well i can, but it does not play ._. )

---

### Post by Caldur06 on 2008-04-01
I upgraded to a jailbroken 1.1.2 firmware to see if that would solve any problems--it didn't. I'm getting the same exact results.

Amarok 1.4.8
libgpod3 0.6.0-3~ppa1
Ubuntu Gutsy

Would deleting all of my songs in iTunes help? I figured when I upgraded to 1.1.2 that my Music would all be deleted, but it stayed. I wonder if that database file is just our of whack.

I've been trying to get this to work for way too long.. Please help someone!

---

### Post by dbrice3 on 2008-04-02
Looks like it's just you and me on this one.

Maybe we'll have to threaten switching to Windows before the support comes flooding.

I had similar thoughts about upgrading my iPhone, went ahead up to 1.1.4, but continued to run into the same problems.  

At this point, I think I'm going to drop it back down to 1.1.1, jailbreak it and try again.

Good luck and let me know if you have any success.

---

### Post by Kulgan on 2008-04-02
You can now jailbreak directly from 1.1.3 (and as far as I know, 1.1.4 as well). Check out [http://www.iclarified.com](http://www.iclarified.com) for tuts. You need windows if you don't want to go all the way back to the 1.1.1 tiff exploit, though.

---

### Post by Caldur06 on 2008-04-02
Heh, good idea! I'm going back to windows, guys! Just kidding.

I think the only thing left to try is to completely restore the iPod back to factory settings, then jailbreak it again. If that doesn't work, it has to be some step or setting on ubuntu that we're missing. I'm about out of patience with it, though.

---

### Post by ntetreau on 2008-04-07
> **Caldur06 said:**
> Thanks for the responses!

I checked, and I did have two versions of libgpod (2 and 3). I uninstalled 2, but it seems I'm having the exact same problem still. To clarify:

When my iPod is mounted, I can see the music that I synced to it from Linux from Amarok, gtkpod, and RhythmBox. They all show that the music is on my iPod. However, none of these programs show the music that is already on my iPod (synced from iTunes on Windows).

And when I open the Music app on my iPod, it still doesn't find the music. I've tried fiddling with both Amarok and gtkpod with the exact same results.

Oh, and my music is getting synced to the same place as the last poster's like this:

/var/mobile/Media/iTunes_Controll/Music/

When the iTunes put the music here:

/var/root/Media/iTunes_Control/Music

Is that normal? I have 1.1.1 firmware and am running Gutsy.

Any more ideas? I figured uninstalling libgpod2 would have worked.. but it didn't. :(

You guys are having the same problem where the music is put in the wrong directory. 

This is a weird failure I guess from ipod-convenience, please file a bug.  Since you are on firmware <1.1.2 and not on 1.1.3 or higher, iphone-mount should not mount the non-existent /var/mobile directory.  If you are 100% sure that you are on firmware 1.1.2 or lower, you can safely delete the /var/mobile directory.  Next time you mount using iphone-mount, it will mount to /var/root and put the music files in the right directory.  Hopefully, that will be the end of your problems.

---

### Post by Caldur06 on 2008-04-08
> **ntetreau said:**
> You guys are having the same problem where the music is put in the wrong directory. 

This is a weird failure I guess from ipod-convenience, please file a bug.  Since you are on firmware <1.1.2 and not on 1.1.3 or higher, iphone-mount should not mount the non-existent /var/mobile directory.  If you are 100% sure that you are on firmware 1.1.2 or lower, you can safely delete the /var/mobile directory.  Next time you mount using iphone-mount, it will mount to /var/root and put the music files in the right directory.  Hopefully, that will be the end of your problems.

Delete /var/mobile on the actual iPod? Well, I need that directory for an application I use (the NES application puts ROMS in that directory for some reason). Would upgrading to 1.1.3 fix this? Or could I just manually change the ipod-touch-mount and ipod-touch-umount commands to point to the right directory?

And just to make sure, when this is working properly, the music that I sync from Amarok (or whichever app) should be in the same folder with the music that I synced from iTunes, correct?

---

### Post by ntetreau on 2008-04-08
@Caldur06:
That's the real problem i guess.  Since you have other applications (NES) that created the /var/mobile directory, then it is fooling iphone-mount into believing that you are on firmware 1.1.3 or higher. 

With that said, you are on to something with the solutions you propose.  One of them is to upgrade to 1.1.3 or 1.1.4 (may as well go to 1.1.4 in my opinion).  The only draw back is that you will loose stuff on your iphone which you will need to reinstall.  Also, you can make a soft link from /var/mobile/Media/iTunes_Controll/Music to /var/root/Media/iTunes_Controll/Music on your device.  The easiest solution would probably be to gedit iphone-mount and replace all /var/mobile for /var/root  .  If you do this, you should lock the ipod-convenience package version so it doesn't get upgraded without your consent.

---

### Post by stevensonfire on 2008-04-08
i keep getting 
"ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this"

i jailbroke mine using ziphone 1.1.4 but on amps i can't install anything or uninstall...
**** man im giving up.. on itouch..

---

### Post by Caldur06 on 2008-04-08
stevensonfire: Are you sure you're trying to connect to the right IP address?

ntetreau: I'm so close! Instead of upgrading to 1.1.3 or 1.1.4 just yet, I decided to modify ipod-convenience so that it puts it in /var/root instead of /var/mobile. Now, whenever I open Amarok and connect, all of my music that was already on my iPod shows up! That didn't happen before. I synced some music to my iphone, and it shows up just fine in Amarok. It's getting put in the same folders as my music that's already in there. I can disconnect and reconnect with Amarok and all the music (everything synced with iTunes and the stuff I just synced) shows up.

But when I look for it in my iPod, it's not there. I've restarted my iPod several times. I've restarted my Music app several times. I don't get what's wrong with it now. It's in the right folder. Amarok says that flushing the information for the database goes well, etc.

Any ideas? It seems so close to working.

---

### Post by ntetreau on 2008-04-09
> **Caldur06 said:**
> stevensonfire: Are you sure you're trying to connect to the right IP address?

ntetreau: I'm so close! Instead of upgrading to 1.1.3 or 1.1.4 just yet, I decided to modify ipod-convenience so that it puts it in /var/root instead of /var/mobile. Now, whenever I open Amarok and connect, all of my music that was already on my iPod shows up! That didn't happen before. I synced some music to my iphone, and it shows up just fine in Amarok. It's getting put in the same folders as my music that's already in there. I can disconnect and reconnect with Amarok and all the music (everything synced with iTunes and the stuff I just synced) shows up.

But when I look for it in my iPod, it's not there. I've restarted my iPod several times. I've restarted my Music app several times. I don't get what's wrong with it now. It's in the right folder. Amarok says that flushing the information for the database goes well, etc.

Any ideas? It seems so close to working.

@Caldur06:  Now, double check again that you have configured Amarok properly for the "xiPhone" type of iPod.  Also, once you've connected your iphone with Amarok, go in the same menu as for the type of ipod, and click "stale or orphaned".  It will look for files that are thre but not added to the database.  If it finds some, you will be able to add them to the database.  Please take another look at the wiki, step by step, check the firewireid for example, etc.

@stevensonfire:  Don't give up just yet!  you need to connect your touch to your network, preferable with a static IP address, let's say 192.168.1.6 .  Then reconfigure ipod-convenience:

```
sudo dpkg-reconfigure ipod-convenience
```

it will ask you for the directory, normally /media/ipod, and the IP address where to find it, use the static IP address where your ipod is connected instead of "ipod".

---

### Post by dbrice3 on 2008-04-11
I've managed to get GtkPod to sync wirelessly with my iPhone, but I still cannot get it to work for Amarok.

I really just did the same procedure that I had been trying all along, so I'm sorry to report, I don't have the cure for those still struggling.

But don't give up, as I won't give up on the Amarok sync option.  

For the record, I'm on the Hardy, with a jail-broken(obviously) 1.1.4 iPhone.

Thanks forum for the help.

---

### Post by Xpyd3r on 2008-04-12
Okay, I got my Touch to mount. its a 1.1.2.  everything appears to work fine until I transfer a song onto my Ipod.  I just pick a random song and put it in the queue, then hit transfer.  When I go to my Ipod, and touch the music app, nothing works.  I can't go to playlists or artist, it just acts as though its frozen.  This is the 3rd time it happened.  Each time so far I figured maybe I had done something wrong so restored, etc etc.  But now its obvious that it wasn't just an error if it happened 3 times.  Any ideas of why I cant transfer? or if it actually did transfer, why is my Player not working at all?  Any help is Greatly appreciated Thanks guys.

---

### Post by Xpyd3r on 2008-04-13
Solved my problem.  I have no idea what it was, but still... I restored then updated like normal, once I got to 1.1.2 I soft updated to 1.1.4, tried it again, and it worked.  Haha, I'm a happy camper now... Well, until I give videos and pictures a shot at least, haha.

---

### Post by Xpyd3r on 2008-04-13
Nope, found the culprit.  Amarok screws it up... I can only use gtkpod...

---

### Post by wireless on 2008-04-16
I wonder if anyone getting same issue as i get with Amarok.
After i setup the iphone in amarok it all goes well and syncs correctly. if Amarok is closed. next time I'll run amarok it forgets the device setup. BUT if i try to re-add the device it give the following error: > Sorry, you cannot define two devices with the same name and mountpoint!

Anyone?

***HAAA Nevermind, It seems to have been solved with the latest update in hardy :)

---

### Post by quini on 2008-04-16
> **wireless said:**
> I wonder if anyone getting same issue as i get with Amarok.
After i setup the iphone in amarok it all goes well and syncs correctly. if Amarok is closed. next time I'll run amarok it forgets the device setup. BUT if i try to re-add the device it give the following error: 

Anyone?

***HAAA Nevermind, It seems to have been solved with the latest update in hardy :)

Hi!

Same problem here... let's wait until someone finds a solution...

Mine is not a good one: I rename the ~/.kde/share/config/amarokrc to a different name, then open amarok as if it was the 1st time...

:popcorn:

---

### Post by wireless on 2008-04-16
hey quini. if you on hardy just update. it look like the issue solved.

---

### Post by Kulgan on 2008-04-16
yup. And the f-spot import tool now starts as soon as the phone is connected. Yay!

---

### Post by quini on 2008-04-17
Hi!  Thanks for the information, I'll check that myself later  ;)

I still have one more question: have you been able to transfer videos to the iPhone?  I've been succesful using amarok, but the iPhone says they aren't playable.

What (linux) program do you use to convert the videos?  What settings do you use?

TIA  :popcorn:

---

### Post by Kulgan on 2008-04-17
have been able to watch movies on the iphone. Converting took far too long to be worth it, so I don't do that any more. Used mplayer, I can't remember what settings. There are scripts that do it for you, though. I think podencoded works well?

---

### Post by alex_sh on 2008-04-17
Hi all,

I got iPod Touch (1.1.1) working quite well with gtkpod (sshfs over wifi, mounting via ipod-convenience scripts).

However, I'm interested if there's any way to manage the music database without using gtkpod (through a command line interface).
You see, with ipod shuffle I could just copy the files using mc or similar and then run the rebuild_db program right from it, generating the database from the directory structure directly.

I'd love to have that functionality with ipod touch. You know, just copy the files (over sshfs or whatever), and run some program to automatically do the rest.
Oh, and keeping the original track filenames would be cool too.
So, is there any way to do this? I mean, the code is there (in gtkpod at least), right?

Thanks in advance

---

### Post by abuakel on 2008-04-27
Has anyone figured out a practical way to get the album art synced in gtkpod or Amarok.. preferably Amarok
It's killing me because it's soo boring without the art ;-)

Edit: For some weird reason, Amarok is transferring my album art when it didn't before. All I did was wipe all the songs and start again.. now cover flow is beautiful! :D

Edit 2: God, I love Amarok.. it totally kills iTunes! \\:D/

---

### Post by ntetreau on 2008-04-29
Has anybody been able to transfer and view pictures so far?

---

### Post by abuakel on 2008-04-29
> **ntetreau said:**
> Has anybody been able to transfer and view pictures so far?

Yes, that would be a fabulous thing because, as I believe, the bluetooth feature in the iPhone only works with 'special' Apple products :(

God, they're frustrating! :confused:

---

### Post by Kulgan on 2008-04-29
The problem with bluetooth is not that it is selective (well, it is, but that's not the only problem), but that there is only support for a few of the bluetooth standards: 

[http://www.iphonebuzz.com/iphones-bluetooth-is-dumb-purposely-crippled-or-both-151188.php](http://www.iphonebuzz.com/iphones-bluetooth-is-dumb-purposely-crippled-or-both-151188.php)

There should be a way of getting round that, but it would be on firmware level. I doubt there would be enough interest to get the devs working on a solution. 

For now, I guess we have to plug it in O.o

---

### Post by abuakel on 2008-04-29
> **Kulgan said:**
> For now, I guess we have to plug it in O.o

Plugging in would be perfectly fine if I knew how to transfer photos to the iPhone :)

---

### Post by Kulgan on 2008-04-29
I get a pop-up as soon as I plug it in... 

Try running "f-spot-import" in the command line while the phone is plugged in.

In any case, you should be able to find the files if you dig through the folder you mount the phone to. It's in a folder called DMCA/APPLE100 or something odd like that. For some reason my phone just relocked itself, so I can't check right now. Restoring...

Edit:
I'm sorry - misread your post. 
Thought you were saying that you couldn't get them to your computer, not the other way round. 
There should be a way of doing that via GTKPod. What version of Ubuntu are you using?

---

### Post by abuakel on 2008-04-29
> **Kulgan said:**
> There should be a way of doing that via GTKPod. What version of Ubuntu are you using?

Latest one :biggrin: 8.04

I had Amarok working with the wireless transfers but now, in addition to my photo problem, my wifi won't work anymore. I think I'm going to restore and unlock the whole thing again.

What are you using to jailbreak your phone?

---

### Post by Kulgan on 2008-04-30
I've done it a grand total of three times. Once with the 1.1.1 tiff exploit, (jailbreakme.com style), once with ZiPhone and once with iLiberty+. 

Apparently it's not a good idea to use ZiPhone any more, due to some WiFi issues (he hard-coded a mac address or something), but I am hating iLiberty+ because it installed Cydia instead of Installer, and Cydia does not have SummerBoard (seriously.. it must be the most insalled app ever..).

I'm also planning on doing it again, again with iLiberty+, but this time select to install Installer instead of Cydia. Unless I can find some way to install SummerBoard...

---

### Post by abuakel on 2008-05-02
Thanks, I got some stuff to work. :)

but now I've got another problem.. I ended up restoring my iPhone to start anew.
But now, when I try to follow the wiki, the WI-FI Networks page in the iPhone (the one that tells you the DHCP, BootP, and Static) gives me blanks for the IP Address, Subnet Mask, Router, DNS, etc. So I make up the last one or two numbers of the IP Address that I figured out in Ubuntu. I used that address in the ipod-convenience and pulled up the terminal for iphone-mount and I get this:

```
laptop:~$ iphone-mount
iPod is not responding to pings at 192.168.2.23.
Please set the environment variable IGNOREPING if you want to ignore this.
```

I do it again:

```
laptop:~$ iphone-mount
The authenticity of host '192.168.2.23 (192.168.2.23)' can't be established.
RSA key fingerprint is 7e:af:a0:39:7a:61:5e:49:5e:68:75:3a:44:f0:2f:3f.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.2.23' (RSA) to the list of known hosts.
root@192.168.2.23's password: 
root@192.168.2.23's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
```

It's a belkin router that's not connected to the internet.. it's just plugged in. I might have made up a wrong IP Address. idk :confused:

So, next, I try the router that's has WLAN access and wireless internet. As the wiki says, I re-installed ipod-convenience and give it the IP Address that was under Static in my iPhone (it says I need to change it to an address that's outside the dynamically assigned range of my network.. I never did that before I restored my iPhone and it worked, but I might have to do it now). However, when I plug the phone into the usb and bring up the terminal to type in iphone-mount, I get this return:

```
laptop:~$ iphone-mount
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
******************************************
Please contact your system administrator.
Add correct host key in /home/abuakel/.ssh/known_hosts to get rid of this message.
Offending key in /home/abuakel/.ssh/known_hosts:1
RSA host key for 192.168.0.194 has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer
```


please help lol :(

Edit: I'd rather use the router that's not connected to the internet.. the belkin
but the other one is fine if the belkin is a lost cause

---

### Post by ntetreau on 2008-05-03
> **abuakel said:**
> Thanks, I got some stuff to work. :)

but now I've got another problem.. I ended up restoring my iPhone to start anew.
But now, when I try to follow the wiki, the WI-FI Networks page in the iPhone (the one that tells you the DHCP, BootP, and Static) gives me blanks for the IP Address, Subnet Mask, Router, DNS, etc. So I make up the last one or two numbers of the IP Address that I figured out in Ubuntu. I used that address in the ipod-convenience and pulled up the terminal for iphone-mount and I get this:

```
laptop:~$ iphone-mount
iPod is not responding to pings at 192.168.2.23.
Please set the environment variable IGNOREPING if you want to ignore this.
```

I do it again:

```
laptop:~$ iphone-mount
The authenticity of host '192.168.2.23 (192.168.2.23)' can't be established.
RSA key fingerprint is 7e:af:a0:39:7a:61:5e:49:5e:68:75:3a:44:f0:2f:3f.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.2.23' (RSA) to the list of known hosts.
root@192.168.2.23's password: 
root@192.168.2.23's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
```

It's a belkin router that's not connected to the internet.. it's just plugged in. I might have made up a wrong IP Address. idk :confused:

So, next, I try the router that's has WLAN access and wireless internet. As the wiki says, I re-installed ipod-convenience and give it the IP Address that was under Static in my iPhone (it says I need to change it to an address that's outside the dynamically assigned range of my network.. I never did that before I restored my iPhone and it worked, but I might have to do it now). However, when I plug the phone into the usb and bring up the terminal to type in iphone-mount, I get this return:

```
laptop:~$ iphone-mount
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
******************************************
Please contact your system administrator.
Add correct host key in /home/abuakel/.ssh/known_hosts to get rid of this message.
Offending key in /home/abuakel/.ssh/known_hosts:1
RSA host key for 192.168.0.194 has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer
```


please help lol :(

Edit: I'd rather use the router that's not connected to the internet.. the belkin
but the other one is fine if the belkin is a lost cause

Not sure about the first router and im a bit tight with time right now.  Nevertheless, just to get you going, use the second one with the static address, open the file:

```
gedit /home/abuakel/.ssh/known_hosts
``` 

in properties, turn line numbering on, delete line 1, close and try again.  Say yes when asked if you want to accept the new RSA key.  

Finally, if you get the nonempty error, turn off your iphone and enter this command:

```
rm -fr /media/iphone/* 
```

---

### Post by abuakel on 2008-05-03
The gedit didn't work and the 
```
rm -fr /media/iphone/*
```
results in the same thing:
```
laptop:~$ rm -fr /media/iphone/*
laptop:~$ iphone-mount
root@192.168.0.194's password: 
root@192.168.0.194's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
laptop:~$ rm -fr /media/iphone/*
laptop:~$ iphone-mount
root@192.168.0.194's password: 
root@192.168.0.194's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
```

Am I supposed to replug my iPhone back in with the USB when I turn it back on after the "rm -fr /media/iphone/*"?

---

### Post by Kulgan on 2008-05-04
You shouldn't have to plug it in at all, since you are connecting over SSH. Try changing the directory that iphone-mount is using, if that's a problem. 
```
sudo gedit /etc/default/ipod-convenience
```
Change the line 
```
MOUNTPOINT="/media/iphone"
```
to 
```
MOUNTPOINT="/media/ipod"
```
or something. 
You will of course also have to make that directory..
```
sudo mkdir /media/ipod
```

Then make sure that the IP address below is the same one that is assigned to you the iphone. You might want to test that IP before you run iphone-mount, just in case iphone-mount tries something odd. 
```
ping 192.168.0.102
```
Or whatever IP you have assigned. 

Hope you get it working.

---

### Post by besada on 2008-05-14
You can install installer from within cydia, then use installer and cydia in parallel. I tend to use cydia if the program I want is available, as I am accustomed to terminal commands (apt-get ...) if something goes wrong.

Also, iLiberty advanced parameters allow you to install installer in the jailbreaking process.

Quite often I need to obtain the programs from installer, and I had no mayor problems using both (just 3 weeks since I got my iphone).

---

### Post by Kulgan on 2008-05-14
> You can install installer from within cydia, then use installer and cydia in parallel. 
Do you have to enable any specific sources in Cydia? I can't find it in cydia or from apt-get in the terminal. Would really like to get Installer back (for SummerBoard) without re-jailbreaking the phone.

---

### Post by scotiobade on 2008-05-15
Hi i have an ipod touch 32gigs it connects fine and all but i try using it in amarok and i can't upload any files to it. this is my second time doing this ive already just rejailbroken my ipod. Can anyone help?

---

### Post by franky_88 on 2008-05-17
I recently had troubles with my Iphone so I restored it with itunes and then jailbreak with ziphone to firmware v.1.1.4 . I used to be able to connect my iphone to ubuntu, but now even if I do what it says here:[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) in the terminal it gives me this error message: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
(I will no post the RSA Key) Please contact your system administrator.
Add correct host key in /home/francis/.ssh/known_hosts to get rid of this message.
Offending key in /home/francis/.ssh/known_hosts:1
RSA host key for 192.168.1.110 has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer

Any help would be really appreciated,

Frank

---

### Post by abuakel on 2008-05-17
> **franky_88 said:**
> I recently had troubles with my Iphone so I restored it with itunes and then jailbreak with ziphone to firmware v.1.1.4 . I used to be able to connect my iphone to ubuntu, but now even if I do what it says here:[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) in the terminal it gives me this error message: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
(I will no post the RSA Key) Please contact your system administrator.
Add correct host key in /home/francis/.ssh/known_hosts to get rid of this message.
Offending key in /home/francis/.ssh/known_hosts:1
RSA host key for 192.168.1.110 has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer

Any help would be really appreciated,

Frank

I've been having the same problem.. Everything I've tried hasn't worked. Out of desperation, I've just been syncing with iTunes and Windows :mad:

---

### Post by franky_88 on 2008-05-17
Okay so I have finally been able to get this error message off. But when i try to mount it it gives me this error : fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option. 
What should I do?


Thank you,


Frank

---

### Post by ntetreau on 2008-05-17
> **franky_88 said:**
> Okay so I have finally been able to get this error message off. But when i try to mount it it gives me this error : fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option. 
What should I do?


Thank you,


Frank

To clear up the error message about the wrong RSA key, just open the file in .ssh/known_hosts and delete the offending line, you get the line number from the error message

```
Add correct host key in /home/francis/.ssh/known_hosts to get rid of this message.
Offending key in /home/francis/.ssh/known_hosts:1
```

which is line 1. Delete it, then with your iPhone NOT CONNECTED, delete the folders which have been created in /media/iphone/* by error:

```
rm -fr /media/iphone*
```

try again. Make sure you follow the rest of the wiki precisely.

---

### Post by ntetreau on 2008-05-17
> **scotiobade said:**
> Hi i have an ipod touch 32gigs it connects fine and all but i try using it in amarok and i can't upload any files to it. this is my second time doing this ive already just rejailbroken my ipod. Can anyone help?

Hi Scotiobade,
try to follow the guide on how to connect the iPhone/Touch found here: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

if you have difficulties, post your problems here, most problems have already been encountered though and you'll probably find a solution already explained in this thread.

---

### Post by franky_88 on 2008-05-17
Okay so I was able to mount my iphone in ubuntu but Amarok doesn`t see it. It gives me the error "can`t mount device. Device not found" I did everything the help document for iphone, even the Pre-connect" iphone-mount and after-connect: iphone-umount. I just don`t know what to do anymore.


Any help would be greatly appreciated,


Frank

---

### Post by bcmiller on 2008-05-18
I thought I would share my experience with the iPhone in case it was useful to anyone.

Being a fan of Free Software, and a Ubuntu GNU/Linux user I was not 100% comfortable getting the iPhone.  However, when I read about all of the things hackers had accomplished with the phone it was too cool to pass up.  

I got the phone and I switched to AT&T. In order to get the music on there I used iLiberty and installed BSD Subsystem and openSSH.  It worked like a charm.  I was installing all sorts of novelty items, like ifartz, and some really useful tools like Wiki2Touch.  

One night, I used Amarok to remove about 200 songs from the iPhone wirelessly and when I was done the screen was DEAD!!!  I was not totally out of the doghouse from buying the phone (with my wife that is) so I was frantically on the forums here and at ModMyiFone.com looking for a solution.  I found nothing useful. 

I learned that I could reboot by holding in the two buttons at the same time for a few seconds and that I could hold the select button while it was connected to the computer to get it into recovery mode.  I reinstalled the default 1.1.4 software twice and the screen stayed dead.  

I also learned that many people had similar issues and not all of those people "jailbroke" their phones.  

I was a bit worried about going into the Apple Store with a jailbroken iPhone.  Turns out that fear was justified, more on that later.  Since I was able to restore the phone the jailbreak issue was a moot point.  

The next morning I went to AT&T, where I bought the phone and I was turned away.  They refer you to Apple Stores for repairs and exchanges.  I went to the nearest Apple Store at lunch but I didn't have an appointment.  They were very nice and they gave me an appointment that was going to have me there about 2 hours.  I was helpless and agreed to wait or come back.  However, they took pity on me and I had a seat at the "Genius Bar" (how pretentious) in a few minutes.

They verified my account and I had a new iPhone in 20 minutes.  

I do not think that jailbreaking led to the screen dying, since I saw limited dead screen help associated with jailbreaking and dead phone complaint away from the jailbreaking sites.  But, I'd be lying if I didn't say I was nervous when I jailbroke the phone that very night.  It's been a few days and no problems.  This time I opted for Cydia instead of Installer but I added Installer later when I realized that I couldn't get SummerBoard or a few other good apps I wanted.  (It's possible that I could add a repo in Cydia, didn't look into that).  Cydia seemed like a better choice for a Linux user since it uses APT and a better openSSH.  

Warning: 
While I was at the Apple Store a guy came in with his iPhone that had a hardware problem.  His phone didn't have the SIM card or an AT&T account associated with it.  He had some lame story that the Genius behind the bar didn't buy either.  He was told they couldn't help him without an AT&T account or a SIM card.  They could also not help you if you brought the phone in jailbroke.  Just a word of warning.  

I read somewhere else where a kid got an AT&T account for a few days for the exchange of his iPhone and then canceled the account.  It may work, but I don't see the harm in just having the AT&T account.  Unless you just wanted an iPod Touch with a mic attached.

---

### Post by iiviip3 on 2008-05-19
I was following the guide but Amarok does not come up for me in the PPA repos at all. I added Project Neon which does show up as Amarok-nightly but it gets a 404 error trying to get 3 of the files. Anyone else having this issue?

Amarok comes up requiring libgpod2 if I don't use the PPA as the origin naturally, but Amarok doesn't come up at all other than the Project Neon nightly so I am currently stuck. Thanks...

---

### Post by ntetreau on 2008-05-20
> **iiviip3 said:**
> I was following the guide but Amarok does not come up for me in the PPA repos at all. I added Project Neon which does show up as Amarok-nightly but it gets a 404 error trying to get 3 of the files. Anyone else having this issue?

Amarok comes up requiring libgpod2 if I don't use the PPA as the origin naturally, but Amarok doesn't come up at all other than the Project Neon nightly so I am currently stuck. Thanks...

Are you on Hardy?  If so, you can just install the stock libgpod and Amarok, if not, then make sure to reload the sources after adding the PPA, you can also browse by repositories directly in synaptic, this way you are sure to find amarok and libgpod3 (make sure to uninstall libgpod2!)

---

### Post by PeteZA on 2008-05-25
Ok so I have followed the wiki guide, and everything seems to be fine until I try to mount my ipod touch. i get the following:

```
peter@peter-laptop:~$ ipod-touch-mount
root@10.0.0.10's password: 
root@10.0.0.10's password: 
root@10.0.0.10:/var/mobile/Media: No such file or directory
You don't have a Firewire GUID, so we will create one

```

I have cleared the /media/ipod directory a couple of times 'cause that seems to be the general suggestion, but to no avail. BTW I am on 1.1.1, any other ideas?

---

### Post by Kulgan on 2008-05-25
I assume you have also followed the section for setting the GUID correctly in:
[https://help.ubuntu.com/community/PortableDevices/iPhone#head-9f7139ac4a88f2e29bcc9c3e6ea78c9433960fe4](https://help.ubuntu.com/community/PortableDevices/iPhone#head-9f7139ac4a88f2e29bcc9c3e6ea78c9433960fe4)
?

---

### Post by StaceyRVC on 2008-05-26
I have tried all of this several times and still stuck at a stand still :( I setup the FireGUID as per the instructions and followed everything line by line. I can't even get the itouch to unmount... [http://stace.pastebin.ca/1029572](http://stace.pastebin.ca/1029572)

When I go into amarok and try connecting I get "Media Device: No mounted iPod found".

I am able to copy to the itouch in term. 

Very very lost ](*,)

---

### Post by Kulgan on 2008-05-26
Turn off the iPod Touch, remove all the directories in /media/ipod, then give us the output of ipod-touch-mount after having turned it on and connected it with the USB cable.

---

### Post by FRuMMaGe on 2008-05-26
> **PeteZA said:**
> Ok so I have followed the wiki guide, and everything seems to be fine until I try to mount my ipod touch. i get the following:

```
peter@peter-laptop:~$ ipod-touch-mount
root@10.0.0.10's password: 
root@10.0.0.10's password: 
root@10.0.0.10:/var/mobile/Media: No such file or directory
You don't have a Firewire GUID, so we will create one

```

I have cleared the /media/ipod directory a couple of times 'cause that seems to be the general suggestion, but to no avail. BTW I am on 1.1.1, any other ideas?

This is simple to fix. It is caused because you are using the latest version of ipod-convenience but not the latest iPod firmware.

Either upgrade to 1.1.4 on your iPod or (much easier) downgrade ipod-convenience to version 0.5.

Make sure you uninstall ipod-convenience before installing the older version.

I have attached the older version of ipod-convenience. Once it's installed, delete the repository from the Software Sources to stop it upgrading.

I hope I have helped you. :)

---

### Post by FRuMMaGe on 2008-05-26
> **franky_88 said:**
> I recently had troubles with my Iphone so I restored it with itunes and then jailbreak with ziphone to firmware v.1.1.4 . I used to be able to connect my iphone to ubuntu, but now even if I do what it says here:[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) in the terminal it gives me this error message: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
(I will no post the RSA Key) Please contact your system administrator.
Add correct host key in /home/francis/.ssh/known_hosts to get rid of this message.
Offending key in /home/francis/.ssh/known_hosts:1
RSA host key for 192.168.1.110 has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer

Any help would be really appreciated,

Frank
Easy to fix!

Navigate to your home folder and press Ctrl+H to make hidden folders appear.

Open up the folder named .ssh and delete all the contents.

Voila

---

### Post by PeteZA on 2008-05-26
Thanks FRuMMaGe! Worked like a charm

---

### Post by Tripero on 2008-05-31
Hi, I've been surfing the web to find any guide about managing photo albums. Reading this thread I've found that may be gtkpod could be the propper solution, but couldn't really make it work (as I read at page 35, only empty albums).
I've also read here that there is a wiki or a startup guide, could anyone paste the link for me to start all over again?
Thanks!

---

### Post by letired on 2008-06-09
Okay, I give up. A couple of days ago I accidentally upgraded to ipod-convenience 0.9.0.whatever from 0.5.something. How the hell do I remove that **** from the update mgr in order to stop this from recurring?
Having downgraded, I am now struggling to regain control of my iphone, and have retraced my steps from last time, and it's worked, barely. I'm on 1.1.3 so I've been working around a bunch of 1.1.3-specific issues successfully but now I end up at

> iphone-mount
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

/media/ipod/ is empty. I remember 'fixing' this the last time around, but it was more of a luck shot than anything else - I did something and suddenly **** just started working. I've rebooted everything a dozen times, rm -f'ed /media/ipod/ again and again.. I don't know what to do. And by the way, how do I even use this 'nonempty' **** option?

Many thanks in advance anyhow, to anyone who saves me from this rage.

---

### Post by regua on 2008-06-13
Hey,

I'm having problems with transferring videos and photos to my iPhone. I can copy all the music using AmaroK, but gtkpod doesn't seem to be working for me - it says the photos directory doesn't exist (I haven't deleted anything), and when I try to transfer a movie (in the .mov format) it displays the progress bar and stops at 0%.

Any ideas? Thanks.

---

### Post by FRuMMaGe on 2008-06-13
> **regua said:**
> Hey,

I'm having problems with transferring videos and photos to my iPhone. I can copy all the music using AmaroK, but gtkpod doesn't seem to be working for me - it says the photos directory doesn't exist (I haven't deleted anything), and when I try to transfer a movie (in the .mov format) it displays the progress bar and stops at 0%.

Any ideas? Thanks.

Nothing is wrong. Photos don't work anyway. The reason why it stops at 0% is because it cannot determine how much of the file has been transferred. Just wait for a while and it will suddenly jump to 100%.

---

### Post by regua on 2008-06-13
> **FRuMMaGe said:**
> Nothing is wrong. Photos don't work anyway. The reason why it stops at 0% is because it cannot determine how much of the file has been transferred. Just wait for a while and it will suddenly jump to 100%.
Wow... thanks... I wouldn't have thought it was so simple.

But... how do I copy the photos to and from the iPhone, then?

---

### Post by otaviofcs on 2008-06-13
gtkpod seems to implement this feature, but the ubuntu/iphone documentation says that it just don't work. See:

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) 

I didn't test it yet but I've tested the video upload with amarok and it works as fine as the music.

---

### Post by FRuMMaGe on 2008-06-15
Photos do not work. You can transfer them and the iPod will recognize them but it always says that they don't exist.

---

### Post by regua on 2008-06-17
Okay, thanks guys.

One more question, though: AmaroK seems not to cope with getting lyrics to work on the iPhone. I've even tried editing the mp3 files' ID3 tags and changing the USLT tag manually, but it doesn't work...

How does iTunes store the lyrics in the music files? And how can I get AmaroK, gtkpod or any other Linux application to do the same?

Thanks.

---

### Post by toupeiro on 2008-06-18
I didn't see this mentioned anywhere else in this thread but I just learned something truly frustrating thats not mentioned in ubuntu's guide.

In regards to artwork, if you have followed the guides steps to create a firewireGUID, then later on follow the guide about syncing artwork, particularly where it tells you to choose your correct iPod model from the list, this **overwrites** the FirewireGUID you create with the guide and will give you a lot of heartache with your artwork.  I've seen two things happen for me:

1) the artwork I already had on the iPod disappears once the firewireGuid is changed

2) none of my music is accessible by the iPod touch, but Amarok can still see all the music.

How to fix these things:

1)  The firewireGuid that Amarok generates has two entries.  An entry that identifies the hardware model of your iPod, and the GUID itself.  The guid differs only in the fact that it doesn't have *yourid@yourhostname* at the end of it, whereas the one that ipod-touch-mount creates already includes this.  What I did to correct my problem is I added *myid@myhostname*at the very end of the FirewireGUID line with no spaces, then saved the file.  I then made the SysInfo file read-only.  > chmod u-w /media/ipod/iPod_Control/Device/SysInfo (change this path so it reflects the path to your SysInfo file if necessary.)

2)  Now, to getting your music and artwork usable on the phone.  You now have a FirewireGUID which Amarok likes, so what I did is I happened to save all the songs on my iPod as a playlist in Amarok, so I simply re-transferred the playlist.  Since all the files still physically exist on the iPod, this takes seconds to complete, but once you restart the music.app on your iPod touch, everything will be available again.  Now your artwork may not be there, if the FirewireGUID you had set when you uploaded the artwork is not the same as you have now.  Simply tell Amarok to resync the pictures .. and prepare to wait.  Thats the one thing that frustrates me.  That particular action seems to be activated on a scheduler because sometimes it takes a few minutes for it to even start.


Anyway, so I feel the guide should be updated in regards to the FirewireGUID and steps to take in amarok to sync pictures because if you do things in the order of the guide, your FirewireGUID gets overwritten and it can make things frustrating.

Hope this helps someone out. :)

---

### Post by Camuso21 on 2008-06-26
I've followed the guide as best I could and am stuck, I can not get my ipod-touch to mount. ```
jfc@jfc-laptop:~$ ipod-touch-mount
connect: Invalid argument
iPod is not responding to pings at 000.168.1.8.
Please set the environment variable IGNOREPING if you want to ignore this.
jfc@jfc-laptop:~$ 

```
What do I do!

---

### Post by darkkith on 2008-06-26
000.168.1.8 is not a valid ip address... try
192.168.1.8

---

### Post by Camuso21 on 2008-06-28
Yeah I had already tried that, in one of the steps it says to change your IP to one outside the normal ranger, thus the 000.

---

### Post by daveb272 on 2008-06-28
+1    almost 3 weeks of messing with this.
> **letired said:**
> Okay, I give up. A couple of days ago I accidentally upgraded to ipod-convenience 0.9.0.whatever from 0.5.something. How the hell do I remove that **** from the update mgr in order to stop this from recurring?
Having downgraded, I am now struggling to regain control of my iphone, and have retraced my steps from last time, and it's worked, barely. I'm on 1.1.3 so I've been working around a bunch of 1.1.3-specific issues successfully but now I end up at



/media/ipod/ is empty. I remember 'fixing' this the last time around, but it was more of a luck shot than anything else - I did something and suddenly **** just started working. I've rebooted everything a dozen times, rm -f'ed /media/ipod/ again and again.. I don't know what to do. And by the way, how do I even use this 'nonempty' **** option?

Many thanks in advance anyhow, to anyone who saves me from this rage.

daveb272@ubuntu:~$ ipod-touch-mount
root@192.168.1.102's password: 
root@192.168.1.102's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
daveb272@ubuntu:~$

---

### Post by ntetreau on 2008-07-01
I'm sure you've tried this already but try once more just for my own benefit!  Turn your iphone off, then do

```
ls /media/ipod
```

obvisouly, it should be empty.  If not, then empty it with rm -fr /media/ipod/*  

Also, reconfigure ipod-convenience to make sure that the mount point and the IP address match (check the IP of your iphone first).

---

### Post by ntetreau on 2008-07-01
> **letired said:**
> Okay, I give up. A couple of days ago I accidentally upgraded to ipod-convenience 0.9.0.whatever from 0.5.something. How the hell do I remove that **** from the update mgr in order to stop this from recurring?
Having downgraded, I am now struggling to regain control of my iphone, and have retraced my steps from last time, and it's worked, barely. I'm on 1.1.3 so I've been working around a bunch of 1.1.3-specific issues successfully but now I end up at



/media/ipod/ is empty. I remember 'fixing' this the last time around, but it was more of a luck shot than anything else - I did something and suddenly **** just started working. I've rebooted everything a dozen times, rm -f'ed /media/ipod/ again and again.. I don't know what to do. And by the way, how do I even use this 'nonempty' **** option?

Many thanks in advance anyhow, to anyone who saves me from this rage.

Just uninstall ipod-convenience using synaptic, then download 0.5 again (two posts up before yours), double click it and install.

---

### Post by travelinman81 on 2008-07-03
when you change your IP to something outside the range it has to remain in the same subnetting structure I think. Something like 192.168.1.356 or something like that would be better I used 192.168.0.126 for mine my router is a Dlink

---

### Post by abuakel on 2008-07-10
Is there a way to correct the order of my artists on my iPhone?
The artists with the word 'the' before their main name (such as The Verve or "The Juliana Theory") end up being placed where the 'T' section should be.. and then, within the 'T' section, the artists are organized by the word after 'The'

Here is a curtailed example:
**A**
Anberlin
Audioslave
**B**
Blink 182
Buckcherry
**C**
Chris Cornell
Coldplay
.
.
.
**R**
Radiohead
Red Hot Chili Peppers
**S**
Semisonic
Snow Patrol
**T**
*B*
The Beatles
*C*
The Calling
*D*
The Dandy Warhols
The Diving Comedy
*F*
The Fray

^^ and you get the point

---

### Post by wireless on 2008-07-12
hey ppl.

I'm having dificulties with getting passwordless access to work. I'm using Ste's OpenSSH package and went through everything in the guide. nothing works. also tried > chmod g-w ~/.
chmod o-w ~/., which worked for me before but now it doesnt.
I'm running iphone 1.1.4.

I took a look at the output of > ssh -vvv and found this, it might be helpfull
> debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/username/.ssh/identity
debug3: no such identity: /home/username/.ssh/identity
debug1: Trying private key: /home/username/.ssh/id_rsa
debug3: no such identity: /home/username/.ssh/id_rsa
debug1: Trying private key: /home/username/.ssh/id_dsa
debug3: no such identity: /home/username/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password


thnx in advance

---

### Post by Tripero on 2008-07-13
Any luck managing photos? Still getting the same result when using gtkpod: I can create albums, upload photos, but the browsing photo albums on the iphone I just see the correct photo counts, but no photos!
Seems to be a simple problem with the photo database, but I can't find anything about it neither on the web nor here.
I'd really apreciate if anyone can help with this issue. Thanks!

---

### Post by abuakel on 2008-07-14
Is anyone having trouble with viewing lyrics in the iPhone? I know that Amarok doesn't actually write ID3 tags, so I was wondering if there was anyway of getting the lyrics generated by Amarok to appear in the iPhone.

---

### Post by coco banderos on 2008-07-20
Does anyone know if amarok/gtkpod support iphone 2.0 firmware (iphone 3g)?  I've tried for hours now to put music on my new iphone, but I think the iTunesDB isn't being created correctly for this version.  When I start iTunes on my phone, it tells me that there is "No Content".  I can put music on with iTunes under VMWare, but neither amarok nor gtkpod are doing it for me.

I've tried the FirewireGuid code from the Ubuntu Forums tutorial, to no avail.  tried both 

'sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16 | xargs printf "FirewireGuid: 0x%sn" > SysInfo'

and

'/usr/sbin/ioreg -n IOIpodUSBDevice -w 0 | grep DeviceConfiguration | cut -d '"' -f 44 | cut -c 1-16 '

anyone have any ideas?

Thanks.

---

### Post by jorns on 2008-07-21
Hi.

I have also the same problem with my iPhone 3G and Amarok.

I have also tried the trikcs from the ubuntu wiki pages but with no luck.

There is no porblems with transfering files to the iPhone, but the phone refuse to list them, it wouldnt even list the files i have uploaded with iTunes.

Maybe there is a new filestructure or something. I have also tested out the latest release of  ipod-convenience (0.10) but i have the same problem.

Lets hope someone solve thuis soon, i am tired of restoring my iphone, becuase after every attempt in Amarok iTunes refuse sync with my iPhone becuase of some files are edited or something so i have to restore my iPhone everytime. 5th time now AFAIR. :-)

---

### Post by coco banderos on 2008-07-21
You don't need to restore each time.  SSH into the phone as root

ssh [email]root@<ip.for.iphone[/email]>
cd /var/mobile/
mkdir tmp
# backup all the old stuff
mv Media/* tmp/.

now connect to iphone to itunes.  You will have to re-assign a name for the phone, but itunes will recognize it.  all data will be lost, but it's a lot faster than restoring.

when you're sure it works, ssh into the iphone again.

# delete all the old stuff
/bin/rm -r /var/mobile/tmp

hope this helps.

i'm also looking forward to progress for 3g iphone with linux.

---

