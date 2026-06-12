---
title: "iTunes?"
date: 2004-10-15
forum: General Help
---

### Post by Infatuated_iPod on 2004-10-15
Does anyone know if iPod and/or iTunes will ever be compatible with linux? As my user name may suggest i am in love with my ipod, is there any way to bring the ipod along on my linux adventure?

---

### Post by bpmckie on 2004-10-15
I dont know if Ubuntu will support the ipod, but Mepis allready does. I believe its a program called gtkpod. I hear most people have had good luck with it. I personally couldnt get it to work but I later traced it down to a firewire problem. So if you use usb to sync you would probably be fine.

B.

---

### Post by water on 2004-10-16
rythmbox has experimental ipod support as of version 0.80. i've conneced my ipod successfully under ubuntu but it did not show up in rythbox. i haven't follows it up or tried in any way to get it to work, but it should be possible.

:water

---

### Post by mattyh on 2004-11-08
I'm actually going to be spending the late afternoon/early evening trying to set my ipod up.  As I understand it, Crossover Office is going to have support for iTunes in the next version, and they said something about having given that code to the regular wine source, so itunes should be quite runnable.  I would only use it for iTunes Music Store and my iPod, but that would be sweet.

---

### Post by dubdubdub on 2004-11-08
This is why I have a G4 sharing desk real-estate with my ubunutu machine :)

---

### Post by jrhardie on 2004-11-08
First post. New Ubuntu user and so far I like what I see. Thanks to all.

As for the iPod question, gtkPod works very well although it's a little kludgy to setup. 

Amarok 1.1 also has support for it and it is almost effortless. 

The most difficult part (at least for me) is getting the fstab statement correct so the drive is "seen". 

Mandrake was the easiest using Hard Drake. Never did get it to work with SUSE and only occasionaly with Yoper. 
 
I haven't tried it yet under Ubuntu, but I will. 
 Of course, even when it doesn't work, you still end up learning something from trying. 

Jim

---

### Post by mattyh on 2004-11-08
I got it working under gtkpod, but I haven't done too much with it.

---

### Post by natefish on 2004-11-09
jrhardie

Care to share a how to for what you did to set up gtkpod on Ubuntu, I would imagine others, like myself would appreciate it. I was able to install gtkpod, and when the pod is plugged in it says knows its connected and it exists under devices but GTKPod doesn't seem to be able to access and use it.

---

### Post by moon2js on 2004-11-10
I got gtkpod working, but I didn't  test it thoroughly. I could access everything  on the iPod and  play things, but I didn't  test if all the syncing worked correctly.

But it's really easy to setup. Just get it via synaptic/apt-get. I believe it's in the universe repo.

Then plug in your iPod, and it should show up automatically on your desktop. Now run your newly installed gtkpod (you may want to make icons for it on the panel).

You do have to change the mount point in the Preferences of gtkpod. I can't recall what it was for me, but it was something like /media/sda2 or something like that.

---

### Post by dishkuvek on 2004-12-09
In order to get Rythmbox working with the iPod you must recompile it with the "--enable-ipod=YES" configure flag.  Also, I think it looks for /mnt/ipod

---

### Post by nuopus on 2004-12-10
[QUOTE=Infatuated_iPod]Does anyone know if iPod and/or iTunes will ever be compatible with linux? As my user name may suggest i am in love with my ipod, is there any way to bring the ipod along on my linux adventure?[/QUOTE] 
 The real iTunes from Apple works with the new Crossover Office by Codeweavers. Why don't you give that a go?

---

### Post by TravisNewman on 2004-12-11
It doesn't work well. At all. The interface is so freakin' slow, for me at least.

---

### Post by talkingwires on 2004-12-11
Crossover officially doesn't offically support using an iPod with iTunes yet. Take a look at their [instructions](http://www.codeweavers.com/site/compatibility/browse/name?app_id=974;tips=1) that may or may not get it working. The first line is, "This is a long and fairly technically difficult process," and it goes downhill from there.

It kinda sucks, because I recently acquired an iPod, but there aren't any good Linux apps for managing it. Before anyone mentions it, yeah, I tried gtkpod. My question to you is, "Have you used Smart Playlists with your iPod? If so, guess the iTunes/iPod killer feature gtkpod doesn't support!"

---

### Post by Swab on 2004-12-11
> **talkingwires]Crossover officially doesn't offically support using an iPod with iTunes yet. Take a look at their [URL=http://www.codeweavers.com/site/compatibility/browse/name?app_id=974 said:**
> instructions[/URL] that may or may not get it working. The first line is, "This is a long and fairly technically difficult process," and it goes downhill from there.

It kinda sucks, because I recently acquired an iPod, but there aren't any good Linux apps for managing it. Before anyone mentions it, yeah, I tried gtkpod. My question to you is, "Have you used Smart Playlists with your iPod? If so, guess the iTunes/iPod killer feature gtkpod doesn't support!"

That's because the developer has not received enough donations to buy a 3rd or 4th generation Ipod to experiment with smart playlists.  I made a $20 donation myself, hope to see it implemented one day.

---

### Post by poofyhairguy on 2004-12-11
> **talkingwires]Crossover officially doesn't offically support using an iPod with iTunes yet. Take a look at their [URL=http://www.codeweavers.com/site/compatibility/browse/name?app_id=974 said:**
> instructions[/URL] that may or may not get it working. The first line is, "This is a long and fairly technically difficult process," and it goes downhill from there.


Worked for me very well. It even downloaded the file, its was very easy to do.

---

### Post by chrisw on 2005-03-12
Using crossover it just hangs on the install for me with the lastest version...... it gets to the same place everytime.

InstallShield gets to installing the IDriver.exe and then hangs.  It makes no diffrence if I let Crossover download the install exe or download it myself and then try installing hmmmm

Think this will be one all best left for the windows box to run !!

---

### Post by comradevik on 2005-10-11
I was able to set my ipod to work with gtk right away and then i clicked on add ipod directories and they were added then i opened amarok and i'm able to update my files right from there. the only problem .. amarok wants to open KMAIL right after it sends the file to ipod and since i'm using gnome it crashes it...why would it want to open kmaill.. and how od i desable that

---

### Post by chapeaurouge on 2005-10-16
[QUOTE=natefish]jrhardie

Care to share a how to for what you did to set up gtkpod on Ubuntu, I would imagine others, like myself would appreciate it. I was able to install gtkpod, and when the pod is plugged in it says knows its connected and it exists under devices but GTKPod doesn't seem to be able to access and use it.[/QUOTE]

in gtkpod, go under your Edit > Preferences and change the ipod mountpoint.

You may have to change the symlink under /media, which points to /media/iPod by default. For example, my iPod was named IPOD. So it didn't work. I did, while the ipod is not mounted.

```
sudo rm /media/ipod
sudo mkdir /media/IPOD
sudo ln -s /media/IPOD /media/ipod

```

---

### Post by Mgcross on 2005-10-19
> **talkingwires]Crossover officially doesn't offically support using an iPod with iTunes yet. Take a look at their [URL=http://www.codeweavers.com/site/compatibility/browse/name?app_id=974 said:**
> instructions[/URL] that may or may not get it working. The first line is, "This is a long and fairly technically difficult process," and it goes downhill from there.

It kinda sucks, because I recently acquired an iPod, but there aren't any good Linux apps for managing it. Before anyone mentions it, yeah, I tried gtkpod. My question to you is, "Have you used Smart Playlists with your iPod? If so, guess the iTunes/iPod killer feature gtkpod doesn't support!"

Have you tried YamIpod...small simple and works great!

---

### Post by lx73 on 2005-10-19
speaking of iTunes store support for 5.10, I just downloaded the new sharpmusique .deb and I can now preview and purchase iTunes from the Apple iTunes store!

I was so happy with it I donated $10 to the developers right away.

Get yours here:

[http://www.nanocrew.net/software/sharpmusique]("http://www.nanocrew.net/software/sharpmusique")

---

### Post by Samuel on 2005-10-19
[QUOTE=Mgcross]Have you tried YamIpod...small simple and works great![/QUOTE]

tried gtkpod and yamipod, gtkpod told me if i continued to sync i would most likely loose all my data on my ipod so i got too scared to run it but yamipod was ok, just wish apple would let us have real itunes, i didnt like it under windows but now i miss it for its ease of use

---

### Post by imnotrich on 2007-08-20
I have battled gtkpod, rhythmbox and several other programs and they just don't measure up. 

How hard can it be to port itunes to Ubuntu? Isn't it written for the Unix based MAC OS? 

C'mon Apple. Spend a couple bucks to include Ubuntu fans and increase your market share.

---

### Post by strabes on 2007-08-20
> **comradevik said:**
> I was able to set my ipod to work with gtk right away and then i clicked on add ipod directories and they were added then i opened amarok and i'm able to update my files right from there. the only problem .. amarok wants to open KMAIL right after it sends the file to ipod and since i'm using gnome it crashes it...why would it want to open kmaill.. and how od i desable that

Try installing kde-core```
sudo aptitude install kde-core
```

You want to use aptitude for this one because it will make it a ton easier to remove it later.

Anyway, iTunes is a terrible piece of software. Slow, bloated, and written by apple. I have an iPod which I bought three years ago before I knew about apple's shady business practices, DRM, ridiculous prices, linux, and all of the superior players with more features that exist.

Anyway, amarok supports ipods out of the box. GKTpod works great too.

---

### Post by ScottyBoyNow on 2007-10-22
This thread is three years old!

I suggest songbird, it basically is iTunes, with Mozilla back end, cross-platform, even works with my iPod. songbirdnest.com

---

### Post by UK-Wobbie on 2007-10-22
I had iTunes working by Wine!

And your iPod will instill it self... So all you need to do is click on the drive icon :)

---

### Post by ropers on 2007-12-15
How did you install it? When I attempt to install it on 7.10, the installer fails and complains that it needs XP or Vista.

---

### Post by wesswei on 2008-01-04
Just wishful thinking, and I know the predicament that this places as it would mean proprietary software run under linux, (not that my ati graphics card drivers are free anyway) BUT here is an iTunes for Ubuntu petition. 


[http://www.petitiononline.com/eb221998/petition.html](http://www.petitiononline.com/eb221998/petition.html)

I personally would rather use a ready-to-go out of box program like rhythmbox or gtk-tunes. None of which I can get figured out. I've finally got video and desktop effects how i want them to stay, now dvd ripping and burning. then maybe ipod and itunes content.

---

### Post by inaety on 2008-01-04
amaroK supports transferring and uploading files from an iPod.  It's very easy to set up the device under settings, just hit "Media Device" - "Add Device" - and then the drop down to an iPod, and it oughta work after that.

---

### Post by fr0sty on 2008-02-09
Hey. Um I got itunes to install on my computer using wine. It is Ubuntu 7.10 and the itunes was on a cd that came with my sisters ipod in 2005. I got itunes to fully install only I am having troubles when it comes to updating and how the heck can I get music into itunes. I do not recomend putting itunes on a comp that is less than a year old cause mine is just under 12 months and itunes is sorta slow. I am a newb to ubuntu as I am dualbooting between vista home premium (64-bit) and ubuntu 7.10. Is there anyway I could actually get this wo work better?

---

### Post by Meox on 2008-02-22
have you looked into Banshee music player.. it has great ipod support :D **hint hint look in synaptic or add/remove for banshee**

---

### Post by UK-Wobbie on 2008-02-22
> **Infatuated_iPod said:**
> Does anyone know if iPod and/or iTunes will ever be compatible with linux? As my user name may suggest i am in love with my ipod, is there any way to bring the ipod along on my linux adventure?

I have had iTunes working in Wine one time :lolflag:
It worked OK, But the CD burning tool in it did not work and when i re loaded iTunes it will some times show a error sign showing up about the burning tool is missing some file.

But thats a old version of iTunes.
The new one will not work at all in Wine, But may be one day hey? :lolflag:

---

### Post by vbman11 on 2008-03-13
I have itunes installed under WINE.  Everything _but_ iPod syncing works. It's the new version!

---

### Post by mobiryder on 2008-05-03
bump for current info... 

thx

---

### Post by IHATEDLINK on 2008-05-07
Ya, iTunes
Check out the iTunes Linux Project for HOWTO's for running iTunes on Linux, alternatives, and a way to make an Linux version of iTunes (Link on my signature).

---

### Post by revjtanton on 2008-07-16
Check out [http://www.yamipod.com/main/modules/home/]("http://www.yamipod.com/main/modules/home/") for a great app to manage yer ipod in linux...or really anything.  I've used yamipod (no, I'm not on a dev team for them) on Windows and Ubuntu flawlessly.  Its a little jittery on Windows.

---

