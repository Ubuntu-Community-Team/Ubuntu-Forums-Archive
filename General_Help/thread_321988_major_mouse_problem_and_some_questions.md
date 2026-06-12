---
title: "major mouse problem and some questions"
date: 2006-12-19
forum: General Help
---

### Post by mrgreaper on 2006-12-19
hi 
i was persuaded to try linux by  a few mates
i tried linux xp (which was horrible)
linspire (which was no were near s user friendly as it pretended to be and wanted money)
suse 10 (my linux box runs that though it took two weeks to get the thing working right)

so i came to ubuntu 6.10 so far its better then the others but i am still not impressed since people tell me linux is better then xp i must be doing something wrong so i am hoping i can ask you a few questions 
for your info (i am using a laptop=toshiba equium l20-197([http://www.pricerunner.co.uk/computing/computers/laptops/521607/details](http://www.pricerunner.co.uk/computing/computers/laptops/521607/details)) stats as listed except its 1gb of ram
1) (most important) my usb mouse works for about 8 or 9 seconds after boot then dies themouse works on all my other pc`s and has alwys worked on the laptop (i did try plugging my phone into usb it detected the laptop and went into mass storage mode but linux didnt want to let me browse the storage device or even show it in "my computer" so its possibly not just a mouse problem ubuntu may of messed up my usb ports fullstop (by messed up i dont mean to offend but cant think of how to word it)

2) i cant seem to find the linux drivers for my graphics card ?   	ATI Radeon Xpress 200M

3) i must be doing something wrong i need to be able to watch dvds and divx files but all i can find on the net is lists and lists of instructions when all i want is a video player and codec pack , for that matter all linux software is a nightmere to install i cant believe it is ment to be this hard i am guessing i have stumpled on the advanced way of doing the things when i need help to find the normal download and double click method

4) for some reason it is not regonising exe files or allowing me to install the most basic of games this is not a major problem though evemon and eve both wont install is annoying i was told i need to get a third party download to run the exes any advice on that would be most helpful

5) any advice for me ? 

im sorry if this all seems like a flame i wont lie i am dissapointed with linux it is not the easy going helpful os i was expecting but i think i may just be set in my windows ways and need some assistence getting this to work (avoiding the terminal screen if at all possible reminds me of my dos days and seems like a step back in tech)

---

### Post by hikaricore on 2006-12-19
Since I noticed no on has been able to repond to your post.  I'm going to do my best to provide as many answers to you as I am able to, please bear with me as I slowly type lots of text.  lol

---

### Post by hikaricore on 2006-12-19
> **mrgreaper said:**
>  
1) (most important) my usb mouse works for about 8 or 9 seconds after boot then dies themouse works on all my other pc`s and has alwys worked on the laptop (i did try plugging my phone into usb it detected the laptop and went into mass storage mode but linux didnt want to let me browse the storage device or even show it in "my computer" so its possibly not just a mouse problem ubuntu may of messed up my usb ports fullstop (by messed up i dont mean to offend but cant think of how to word it)

I'm afraid I can't help with the mouse issue, you'll need to search around the forums for "USB mouse" and see if anyone has had a similar issue.  Some pieces of hardware just don't work, and others require simple tweaks to get them working perfectly.

> **mrgreaper said:**
>  
2) i cant seem to find the linux drivers for my graphics card ?   	ATI Radeon Xpress 200M

Well I found installation instructions on your specific card, but this may not be useful to you unless you're on a 64 bit system.  I'm posting just incase.
[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=install+ATI+drivers](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=install+ATI+drivers)

This is the official ubuntu wiki on installing ATI drivers (it may or may not help):
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I don't own an ATI card myself I'm just trying to provide you some reference you can look into and see how it may or may not be possible to get your card working at it's best.

> **mrgreaper said:**
>  
3) i must be doing something wrong i need to be able to watch dvds and divx files but all i can find on the net is lists and lists of instructions when all i want is a video player and codec pack , for that matter all linux software is a nightmere to install i cant believe it is ment to be this hard i am guessing i have stumpled on the advanced way of doing the things when i need help to find the normal download and double click method

Your best bet as a new linux user wanting "non-free" video support would be Automatix:
[http://getautomatix.com/wiki](http://getautomatix.com/wiki)

Installation instructions here: [http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

Follow the instructions to install and set it up and it will give you easy access to install dvd support and all video codecs that are available through repos.

> **mrgreaper said:**
>  
4) for some reason it is not regonising exe files or allowing me to install the most basic of games this is not a major problem though evemon and eve both wont install is annoying i was told i need to get a third party download to run the exes any advice on that would be most helpful

For windows based applications you will need to install WINE:
[http://www.winehq.org](http://www.winehq.org)

Automatix as I mentioned in the previous response can also install this software, tho your results may vary, you may want to look at this section of WINE's website to see if running your particular games and applications is even possible:
[http://appdb.winehq.org](http://appdb.winehq.org)

You can search and find user experiences, tips, and work arounds for getting many applications running in linux.

If you have need of dos based applications I suggest you search the forums for DOSbox. :)

> **mrgreaper said:**
>  
5) any advice for me ? 

im sorry if this all seems like a flame i wont lie i am dissapointed with linux it is not the easy going helpful os i was expecting but i think i may just be set in my windows ways and need some assistence getting this to work (avoiding the terminal screen if at all possible reminds me of my dos days and seems like a step back in tech)

It's quite alright to be overwhelmed at first, linux isn't for everyone, but if you can get most or all of what you need your computer to be used for working, it's a nice breath of free fresh air away from the Micorsoft Borg Collective.

---

### Post by mrgreaper on 2006-12-19
thank you for the advice im now searching through it all lol
feeling overwhelmed? i feel like a ant just asked to go to the top of everest lol

i do have a rather pressing problem i cant access my network 
internet works which goes through the router
i can ping the other pc`s so its connected to the network but if i go to network 
then windows network
i see davesnet (my network) but its a blank sheet if i double click it i get"cannot display "smb:///davesnet" "    

any ideas would be most helpful



hmmmmm it fixed itself  i`m gussing since this ubuntu is free and new that there are stabilitie issues (no such thing as a free lunch) but perservering managed to get vlc installed and divx movie working yay 

took look at ati instal instructions ....it cant be right can it? imean windows download double click ...linux type this type that get this edit that edit that type this arghhhhhhhhhhhhhhhh i refuse to believe it is that complicated

---

### Post by hikaricore on 2006-12-19
I've had issues with windows networking in edgy, often the solution I have is hitting F5 to reload the nautilus window
(i'm assuming you're using gnome here) after a few times the blank sheet becomes an icon.

I'm not sure why this is but it might work.

I believe this may be a bug with nautilus, but I didn't realize anyone else was experiencing it til possibly now.

---

### Post by hikaricore on 2006-12-19
Are you seeing something like this?

Before:
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/junk/Screenshot-WindowsNetwork-FileBrows.png[/IMG]

After hitting F5 (once or a couple times slowly):
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/junk/Screenshot-WindowsNetwork-FileBr-1.png[/IMG]



Before:
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/junk/Screenshot-WindowsNetworkpluronplur.png[/IMG]

After hitting F5 (once or a couple times slowly):
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/junk/Screenshot-WindowsNetworkpluronp-1.png[/IMG]

---

### Post by mrgreaper on 2006-12-19
yes the f5 key is an immediate assist here thank you 

still cant fix mouse (touch padhow i hate it) i tried the mouse on my linux box (running suse 10) worked fine nd on my windows box`s again wored and it works on ubuntu for 5 seconds wierd since its nearly 4 am gonna google it all 2morro got to be a solution somewhere

---

### Post by hikaricore on 2006-12-19
> **mrgreaper said:**
> 
took look at ati instal instructions ....it cant be right can it? imean windows download double click ...linux type this type that get this edit that edit that type this arghhhhhhhhhhhhhhhh i refuse to believe it is that complicated

Until standard ATI drivers are released that work well with X as nvidia has done, I'm afraid it is a little bit complicated to get it setup.  I know there's an easier way to do some of it, but I didn't have a whole lot of time to look into the issue.  I've seen dozens of ATI driver howto's in the howto section of the forum, maybe searching around a little bit in there might pay off for you.  It all depends on what card you're using, if anyone has done it before you, and sometimes a little bit of luck.

---

### Post by hikaricore on 2006-12-19
> **mrgreaper said:**
> yes the f5 key is an immediate assist here thank you

Alright it does appear that this is a bug with nautilus in edgy, it was supposed to be fixed but wasn't, and will (maybe) be corrected in fiesty.

Thread about the issue:
[http://ubuntuforums.org/showthread.php?t=286528&page=5](http://ubuntuforums.org/showthread.php?t=286528&page=5)

Launchpad bug report:
[https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277](https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277)

Possible solution:
[http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons](http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons)

Basicly what the solution tells you to do is launch gconf-editor, so hit Alt+F2 (to bring up a gnome launcher box) then type:

```
gconf-editor
```

Once Gconf-editor is running you will notice this is a big like the windows registry.  Goto:

System, smb, and double click on "workgroup"

If you type the exact name of your network (which needs to be set for windows as well as ubuntu).  Then close gconf-editor, hit Alt+F2 again and type in the launch box:

```
killall nautilus
```

Now when loading up your network window you should see both machines (or just one if you have no samba shares on your ubuntu system) and the name of your network in the window.  :)  Worked for me, and just goes to prove you help yourself by helping others.  Or some crap like that which optimistic people say entirely too much.  :P

---

