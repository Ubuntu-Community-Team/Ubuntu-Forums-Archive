---
title: "[SOLVED] Google Earth - where did EARTH go..???"
date: 2008-07-10
forum: General Help
---

### Post by Thanh-BKK on 2008-07-10
Hello :)

Now for the first time i actually NEEDED Google Earth to find a way across a stupid traffic system and now it doesn't work anymore! Aaaargh. 

So i start the program, it opens, but - i'm looking at space, there's lots of stars etc but no earth. Where did that go?? The "fly to" brings me nowhere, all my way points or what they are called have disappeared.... but there is activity, because when i click in space and move the mouse, space rotates accordingly.

I tried to reinstall it and then found it's "not there" - at least via Synaptic, so i installed the version from the repo (and THEN remembered that my version was a straight download....) so i had TWO of them - and NEITHER worked.

So i uninstalled ("completely remove") the one from the repo and still have the first one - which still didn't find earth again.

Please, how can i get that to work again??

By the way - nothing to do with my graphics card or internet, Google Earth was working all the time but i only used it to "play around with" and set way points all over my city.

I appreciate any help..... Thanks in advance :)

Thanh

PS starting it from terminal yields no difference, also no output in the terminal.

---

### Post by roquefilipe on 2008-07-10
try remove .googleearth/ or rename it something else.

---

### Post by sdennie on 2008-07-10
It looks like you are using compiz.  The last time I tried Google Earth with an intel graphics card with compiz turned on, what you are describing happened.  Before starting Google Earth hit Alt-F2 and type "metacity --replace".  To get back to compiz hit Alt-F2 and type "compiz --replace".

---

### Post by ibuclaw on 2008-07-10
Hmm... looks like it has been destroyed to make way for an intergalactic highway ;)

On a serious note, though. I agree with Vor, compiz does strange things to intense 3D apps.

Regards
Iain

---

### Post by Jeffa on 2008-07-10
I just installed Google Earth in Ubuntu for the first time and i am having a similar problem. I'm getting the following error when I initialize:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77228&stc=1&d=1215738996[/IMG]

I am definitely connected to the internet and I shut down Firestarter. Maybe their servers are down? unlikely though.

---

### Post by Thanh-BKK on 2008-07-11
Hello :)

Thank you all for replying, i appreciate it. As i mentioned in the original post, i am sure i can safely rule out a problem with the graphics (including Compiz) as it was working fine all the time without me changing anything.

BUT i remember what i did - i installed some add-on which allowed to see and "drive" the new Singapore F1 circuit. That was the last thing i did in Google Earth. Maybe that screwed something up? (it never really worked the way it was supposed to, the add-on i mean). 

I will try the "try remove .googleearth/ or rename it something else." first and see if it works - if not i will attempt tio reinstall my original downloaded one (still got that .bin file somewhere). If that doesn't work i start messing with Compiz/Metacity (will the dock still work with Compiz off??)

My graphic card is an Nvidia by the way, with the proper "restricted driver" from the repo.

Best regards.....

Thanh

---

### Post by bettabert on 2008-07-11
I have the same problem.. here is what happened to me:

1. installed a fresh copy of ubuntu 8
2. Installed google earth. Worked great. 
3. Updated the system with reccommended updates.
4. rebooted
5. Started Google earth... no earth, only stars

I'm thinking the update broke something.. perhaps broke something with the network connectivity with the google servers??

I'm planning to reinstall google earth later today to see if that will fix the problem.

---

### Post by Thanh-BKK on 2008-07-11
Hello :)

Now i did: Rename the .googleearth folder - no change. Deleted that folder - no change (Google Earth just re-generates it).

Reinstalled it from the .bin file - STILL not working.

Finally did the "metacity" one - AWN disappeared and everything looked a bit plain, but still - Google Earth minus earth.

So what can i try next?

Many thanks in advance for advice.....

Thanh

---

### Post by roquefilipe on 2008-07-11
that is quite weird. 

try this. remove googleearth and .googleearth folder and install again by using [medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by bettabert on 2008-07-11
This is what I found.. 

When I re-install google earth from the GoogleEarthLinux.bin then click the run button from the installer GUI I get an earth.. If I run it from the Applications>internet>Google Earth.. I don't get an Earth

If I open a console then cd to /usr/local/google-earth/ directory then type
./googleearth  
 
I get NO earth

but if I type
sudo ./googleearth

I do get an earth.. 

I'm not sure why this occurs.... I believe I ran GoogleEarthLinux.bin using sudo.. perhaps this is my problem.

---

### Post by Thanh-BKK on 2008-07-12
Hi :)

in my case it was in /opt...... and could not be deleted. So i uninstalled it completely (sudo ./uninstall) and it was gone. 

I then reinstalled it thru the repo, and guess what?

NO EARTH!

Regardless how i start it.

I just give up on it and use Google Maps instead. Too much stress to get a single application to work.

Best regards....

Thanh

---

### Post by Thanh-BKK on 2008-07-12
Ok got it!

Did not give up just yet - used Google on the problem, and it brought me right back here (Ubuntu forums ROCK!)

This did the trick:

 Re: Google Earth - No Earth - No Error
was having the same problem.
fixed it by removing the Google directory on my .config folder (you may need to be root).

You HAVE to be root, i.e. navigate there via terminal, then remove the folder using "sudo".

Now i've got my earth back.

Beat regards.....

Thanh

---

### Post by mutzinet on 2008-07-14
This still doesn't work for me :( Or, it worked, but now it doesn't anymore. Just did:
```
sudo rm -r ~/.googleearth/
sudo rm -r ~/.config/Google/
```

And still no earth, even with a fresh install of the latest 4.3 version.


[EDIT]I tried "gksudo googleearth" and... earth was back (I had tried before with "sudo googleearth", but it hadn't worked). After that, "googleearth" as normal user worked as well. It looks like a deep mystery to me. [/EDIT]

---

