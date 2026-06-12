---
title: "ipod-touch 1.1.3, Amarok mp3's no longer recognized"
date: 2008-02-01
forum: General Help
---

### Post by Leed on 2008-02-01
Just updated to 1.1.3 using "Official 1.1.3 Upgrader" from conceited Software

After some minor strains the device itself is working pretty well... only the music & Pictures bit is a bit frustrating. All Music was deleted during upgrade and the ipod refuses to recognize any new songs, even tho Amarok loads them onto the device (worked superb in 1.1.1/1.1.2). 

Wasted some hours looking for solutions, but the update is new and I can't find anyone with the same problem. I gave up after trying around with the FirewireGUID stuff, did'nt fully understand it tho. 

Did anyone get Amarok to work with a 1.1.3 iphone/ipod-touch yet? Would love to have it working again.

---

### Post by Leed on 2008-02-02
Also I can't get Passwordless login to work anymore, I didn't use the passwd command because of the new bug in BSD subsystem... but I'd think it should work without



--------------Update---------------

I found a temporary fix for those with the same problem... not nice, but it works

Apple has changed the location of the Files from the usual Linux mount point "/var/root/Media" to "/var/mobile/Media" I hope there's some update soon that can deal with this (make an Alias or something, I'm not smart enough to figure that out)

What I did was connect the ipod to a Windows machine and put 1-2 Songs on it using iTunes, that then creates the new folder 

-Then opened a folder on the Linux mount point, where Amarok puts all my music
 
-parallel to that opened a Network Folder (Gnome: Places -> Network) and opened the SSH Share of the ipod, where I found the iTunes new Destination  "/var/mobile/Media"

-Then simply copied the files of the linux mount "/media/ipod/iTunes_Control" (akka /var/root/Media/iTunes_Control) to the new Destination  "/var/mobile/Media"

>>>>>>>>>>>Warning<<<<<<<<<
This only shows the Files in the iPod, it doesn't let you play them



***********Update 2, Music now plays (in case anyone is interested)********************

1. Transfer 1 Song from iTunes to the ipod, then disconnect and get back to using linux ;)

2. using SSH connect to the iPod (can be done in Gnome under "Places->Network")

3. on the iPod copy the file "/var/mobile/Media/com.apple.itunes.lock_sync" into the Folder "/var/root/Media"

4. Now delete the folder "var/mobile/Media" on the iPod

5. Connect via SSH using the Terminal using ```
ssh root@<your ipods ip>
```

6. create a symbolic link on the iPod using ```
ln -s /var/root/Media /var/mobile/Media
```

7. disconnect and respring your ipod-touch / iphone... after this Amarok should work fine again


8. -->Find a way to get the pictures working and post here

---

