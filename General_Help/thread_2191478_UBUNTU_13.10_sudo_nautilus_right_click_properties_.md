---
title: "UBUNTU 13.10 sudo nautilus right click properties crash (have searched for this)"
date: 2013-12-02
forum: General Help
---

### Post by musicboy on 2013-12-02
This happened before and then randomly stopped, then started doing it again. Where in root as nautilus ie sudo nautilus, then right click on any file or folder, nautilus crashes but the error on screen disappears as it completely crashes back to leaving you with the terminal not in nautilus any longer as root and its to quick to read most of it I tried screen shots, nothing worked.
So I took a screen record and then paused it and read this following error:


Sorry, could not change the owner of //*name of folder or file*//. Specified owner '//*name of owner*//' doesn't exist

Note: where //* anything between the first forward slash and the last forward slash is replaced with folder or file name *//

I then used sudo chown and that worked when going back just with your usual nautilus into the home folder of which is where i changed the permission of the folder and files so I know that works.

When I installed UBUNTU I have

Your Name:
Your computers name:
Pick a username:

all 3 are obviously present and there is obviously something odd going on here that I can't quite figure out.

Can anyone please help??

Thanks

---

### Post by CatKiller on 2013-12-03
I don't know if it's the cause of your problem, but you should use gksudo (or the new one that I can't remember) with graphical applications like Nautilus. Using sudo causes ownership problems.

---

### Post by musicboy on 2013-12-03
Hi

Thanks for the reply CatKiller. I can confirm that this issue still happens with gksudo nautilus the exact same thing happens. What is the new gksudo you talk of? Up to 12.10 I just used sudo nautilus, no problems, I knew exactly what was going on, was very stable, crashed once in a blue moon! If something happened I could fix it no problem!!
I am re downloading 12.10 at the moment as if I do not get to the root of this (pardon the pun!) then I am reverting to 12.10 and not upgrading until I know the problem has been resolved!

Can you or anyone else out there point me to this new gksudo?

Thanks

---

### Post by Frogs Hair on 2013-12-03
Gksudo is not new and has been recommended opening graphical applications as root for a long time. As written above using sudo can cause the type of permission problems you are experiencing . This is not a common problem ,but does happen. 

[http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus](http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus)  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by philinux on 2013-12-03
Not seen this at all. But if I need to edit a system file I use sudo nano filename.

---

### Post by mc4man on 2013-12-03
> **musicboy said:**
> Hi

Thanks for the reply CatKiller. I can confirm that this issue still happens with gksudo nautilus the exact same thing happens. What is the new gksudo you talk of? Up to 12.10 I just used sudo nautilus, no problems, I knew exactly what was going on, was very stable, crashed once in a blue moon! If something happened I could fix it no problem!!
I am re downloading 12.10 at the moment as if I do not get to the root of this (pardon the pun!) then I am reverting to 12.10 and not upgrading until I know the problem has been resolved!

Can you or anyone else out there point me to this new gksudo?

Thanks
You never should of been opening a root nautilus with sudo in the past, certainly with newer releases, 13.04+,  it's a worse idea.
The "problem has been resolved!" isn't going to happen, gnome/nautilus devs don't support the use of a root nautilus browser.

While in the past sudo gedit was ok, as of 13.10 also a poor idea. (maybe also 13.04, forget)
 You can easily check this by setting your user gedit to use a non default color scheme. sudo gedit will open a gedit window with that color scheme which is clearly wrong.

nautilus can be switched over to pkexec manually, I've a post on it somewhere, at this point I just include it in ppa builds along with some other changes so haven't done manually in some time.
gedit can also be switched to pkexec, though in 13.10  dev  there where some issues so I haven't re-checked lately & just use sudo nano here.

---

### Post by CatKiller on 2013-12-04
> **musicboy said:**
> What is the new gksudo you talk of? 

It's not a new gksudo as such, it's the pkexec already mentioned that uses PolicyKit rather than sudo to handle permissions. I haven't looked into it in any detail, but I'm aware that it's a thing.

---

### Post by musicboy on 2013-12-05
[COLOR=#000000]pkexec and policykit I will look into using this and learning about it etc. Up until 12.10 that I was using, sudo nautilus was acceptable and all the the tutorials and know how around would just state using sudo nautilus and going to a certain file and editing it manually I PROFFERED doing that using nano you have to have this long drawn out process of creating new files!! I create a method of installing a generic KVM USB switch I posted on here I was told I WOULD NEVER succeed in getting to work at full res of monitors!! I succeeded and I ALWAYS did it this way, up until 12.10 when I had bought a dual screen more expensive well known brand etc version of a KVM switch but worked fine!! Everything worked fine!! No problems really the most stable release of UBUNTU I have ever had running 12.10!! After that, PROBLEMS sudo nautilus causes ownership problems = well THEN THAT IS WRONG!! Because up until 12.10 that was FINE I never had one single problem ever, not any!! NONE!
[/COLOR]
I will have to look into this new method but I hear even that is unstable WHAT is going on here??!!

---

### Post by musicboy on 2013-12-05
Right basically reading through all that you shouldn't use sudo nautilus to create any files in your home folder directory BUT editing any system files where you WANT them to be owned by root to run udev or similar etc xorg / x11 etc etc then basically that to mean is fine, that wont create any problems, but using it in your root folder creates problems! 
SO using gksudo nautilus for home folder or gksudo nano for home folder would be more correct and use sudo nautilus for system files owned by root. o_0 complicated!! 12.10 was much easier to use!!

---

### Post by mc4man on 2013-12-05
> **musicboy said:**
> Right basically reading through all that you shouldn't use sudo nautilus to create any files in your home folder directory BUT editing any system files where you WANT them to be owned by root to run udev or similar etc xorg / x11 etc etc then basically that to mean is fine, that wont create any problems, but using it in your root folder creates problems! 
SO using gksudo nautilus for home folder or gksudo nano for home folder would be more correct and use sudo nautilus for system files owned by root. o_0 complicated!! 12.10 was much easier to use!!
No, use gksudo at all times, don't see what the resistance to typing 2 extra letters is. Or use gksu & you can stick with 4

or go (**2 separate commands**
sudo -i
nautilus

Or create pkexec support for either..

---

### Post by musicboy on 2013-12-05
Right well OK but 12.10 worked fine............... why change something that works well?

---

### Post by CatKiller on 2013-12-06
> **musicboy said:**
> Right well OK but 12.10 worked fine............... why change something that works well?

Sudo's always behaved that way. That would be one of the things (along with fine-grained control of permissions being a pain in the ****) that PolicyKit is designed to fix.

---

### Post by musicboy on 2013-12-06
Thanks Cat Killer. Yeah I am going to be doing some reading about [COLOR=#000000]PolicyKit. BUt lol right up to 12.10 I had NOOOOOOOOOOOOOOOO issues doing things sudo nautilus, gksudo nutilus, gksu nautilus, gksudo nano, gksuo nano............ to be quite frank nano just annoyed/annoys me doing it that way!! Just the standard gksudo / gksu - nautilus etc is an acceptable way yeah, but I have yet to see technically WHY this happens and why it never happened to me ever before up until upgrading to 13.04 and then straight after 13.10 which is buggy as heck!!
The date on the calender wont shift the days but I am trying to fix that. Seems that every time i test to see if the UBUNTU distro update works, I end up having to re install a fresh version starting with UBUNTU studio, tweak it, install some desk tops I use re instate a back up, re instate saved PPA's app list etc manual re install some stuff and then go from there. BUT I am fighting it!
You would have thought they would have ironed that out by now, I submit enough error reports!![/COLOR]

---

### Post by luv-laff-lern on 2014-07-24
I switched from 12.04 to 14.04 and found the same problem. Here's what that works.
Open the teminal.
Type;
 sudo chown -R <USERNAME:GROUPNAME> </FILE-FOLDER-DRIVE/LOCATION>
EXAMPLE **sudo chown -R hope:Me /media/hal/Castle**

---

