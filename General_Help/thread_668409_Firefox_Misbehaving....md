---
title: "Firefox Misbehaving..."
date: 2008-01-15
forum: General Help
---

### Post by CAD-MAN on 2008-01-15
Whenever I double click the firefox icon, it tries to start, but the furthest it gets is a tab(?) on the panel which says 'starting firefox'. But it never even opens a firefox window, or gets past the 'starting firefox' stage.

To be honest, Ive no idea whats gone wrong. I can ping google.co.uk in a terminal, and i get pinged back, and programs such as aMSN work perfectly. Other **browsers** are also misbehaving: Firefox 3.0 (alpha 8 ) opens, but will freeze after a couple of minutes (websites load for this small amount of time though). Its the same story with Epiphany.

Im wondering what I might have done :( :mad:, and more importantly - how to fix it!


Any ideas? Anybody else had the same or similar problem? This i sdriving me nuts (Im being forced to write this post in my Vista partition!)

---

### Post by Metaljaz on 2008-01-15
Where you getting a good connection and then all of a sudden lost your connection speed or what?
How are you connected to the internet? If you are wireless and using a router you may want to reset your router so that your computer will obtain a new ip address.

---

### Post by wolfen69 on 2008-01-15
go to administration>system monitor 

go to processes and see if an instance of firefox is running. if yes, stop it. then try opening firefox again.

---

### Post by sowelie on 2008-01-15
I would run firefox from the terminal.

```
firefox
```

This'll will most likely report an error and give you a better idea of what's going on.

---

### Post by CAD-MAN on 2008-01-16
Thanks for all of your replies.


> **Metaljaz said:**
> Where you getting a good connection and then all of a sudden lost your connection speed or what?
How are you connected to the internet? If you are wireless and using a router you may want to reset your router so that your computer will obtain a new ip address.

Yeah, im on a notebook, connecting wirelessly. Ive got a fixed ip address, and my desktop and vista on my notebook both connect fine. Other programs which require an internet connection (such as aMSN) work perfectly on Ubuntu.


> **wolfen69 said:**
> go to administration>system monitor 

go to processes and see if an instance of firefox is running. if yes, stop it. then try opening firefox again.

I'll give it a go, thanks.


> **sowelie said:**
> I would run firefox from the terminal.

```
firefox
```

This'll will most likely report an error and give you a better idea of what's going on.

Tried it already, but no error message was given.

---

### Post by Metaljaz on 2008-01-16
If you have any extensions installed trying disabling them, maybe one at a time and see if it starts. This once happened to me with a theme extension.

---

### Post by Washer on 2008-01-16
Try  
```
firefox -profilemanager
```
Make a new profile & see if it works.

---

### Post by CAD-MAN on 2008-01-19
> **Metaljaz said:**
> If you have any extensions installed trying disabling them, maybe one at a time and see if it starts. This once happened to me with a theme extension.

I tried this by just removing the folders of all of the extensions that i had in /home//me/.mozilla/firefox//profiles/[whatever my profile is called.default]/extensions. I couldn't 'disable' them in the normal sense because I couldnt open firefox in the first place!

> **Washer said:**
> Try  
```
firefox -profilemanager
```
Make a new profile & see if it works.

I took the profile folder of the firefox thats installed on vista, and replaced the profile folder of Ubuntu's firefox. I then changed the profile to use in the profiles.ini file in /home/me/.mozilla/firefox/, but to no avail. I'll try the command line thing that you've suggested when i log back into Ubuntu.


Ive downloaded a firefox tarball from the official website, and im considering just replacing the programs files. Anyone think this could work?

Thanks for all of your tips. Please keep them coming - I hate being inside Vista so much (I barely log into Ubuntu anymore because of the lack of web browsing :( )

---

### Post by CAD-MAN on 2008-01-22
Anyone got an ideas?

---

### Post by ElSimo on 2008-01-22
hey CAD-MAN,

I'm having the same problem in my Gutsy install. As soon as I'm on the wireless connection, no more firefox. Opera works a treat though

---

### Post by CAD-MAN on 2008-01-25
> **ElSimo said:**
> hey CAD-MAN,

I'm having the same problem in my Gutsy install. As soon as I'm on the wireless connection, no more firefox. Opera works a treat though

Thanks ElSimo. Did firefox **ever** work on your gutsy install? It worked brilliantly for me for a couple of months, and suddenly - no more :(

I've tried Firefox 3 (alpha 8), it just freezes after a minute or so of being open (better than firefox - which doesnt open at all!). I've also tried epiphany, which dies after a short while too.

I just think its weird that firefox and epiphany worked fine for months, and now firefox wont even open, and epiphany has a nervous breakdown after a few minutes.

Im considering reinstalling :confused: . If I just copy my home folder onto a usb stick (or DVD), do a fresh install, and copy my home folder back again, I should be ok shouldn't I? I'll just need to reinstall programs...

---

### Post by CAD-MAN on 2008-01-26
Im sorry for the incessant bumping, but I really want to get this fixed :(

---

### Post by CAD-MAN on 2008-02-01
So Im guessing the problem im having is pretty much unheard of...

:(

---

### Post by CAD-MAN on 2008-02-05
Ok, I am now reduced to **begging** for advice :( ...

---

### Post by bilijoe on 2008-04-10
> **Washer said:**
> Try  
```
firefox -profilemanager
```Make a new profile & see if it works.

I tried this.  All it did was open up a new instance of FireFox (on my home page).:confused:

---

### Post by bilijoe on 2008-04-10
For the first time since I have been using ubuntu (4 or 5 months), I have had to reboot in order to clear a problem (shades of Windows, coming back to haunt me).:shock:  While web browsing, FireFox seemed to suddenly become very sluggish when loading pages.  Refreshing the page sometimes returned it to its "normal" speed.  Then it quit responding altogether.  I used the "Force misbehaving application to quit" button, and killed the application (or so I thought).  But, when I went to re-launch it, I got a message saying it was already running, and that I either needed to stop the current session, **OR REBOOT!**:confused:  This is *exactly* why I switched to Linux in the first place--to get away from what I consider to be the consistently buggy performance of Windows:mad: (and because Linux is just an all 'round better OS:)).  I see from the other posts in this thread, that a [very] few people seem to have experienced similar problems, in that FireFox worked just fine for some time, and then, after, in my case, months of [near constant] use, began to misbehave.  Apparently CAD-MAN is becoming desperate to find a solution to this problem.](*,)  I am burdened with a significant anxiety disorder, and sincerely hope I do not find myself slipping into desperation, seeking a solution.:(  Will one of you Top Flight Linux Gurus out there please do CAD-MAN (and me) a favor, and take up this cross.  Please, somebody, see if you can't find out what's going on here, and provide a solution.  I would be truly grateful.:biggrin:

---

### Post by CAD-MAN on 2008-04-13
> **bilijoe said:**
> For the first time since I have been using ubuntu (4 or 5 months), I have had to reboot in order to clear a problem (shades of Windows, coming back to haunt me).:shock:  While web browsing, FireFox seemed to suddenly become very sluggish when loading pages.  Refreshing the page sometimes returned it to its "normal" speed.  Then it quit responding altogether.  I used the "Force misbehaving application to quit" button, and killed the application (or so I thought).  But, when I went to re-launch it, I got a message saying it was already running, and that I either needed to stop the current session, **OR REBOOT!**:confused:  This is *exactly* why I switched to Linux in the first place--to get away from what I consider to be the consistently buggy performance of Windows:mad: (and because Linux is just an all 'round better OS:)).  I see from the other posts in this thread, that a [very] few people seem to have experienced similar problems, in that FireFox worked just fine for some time, and then, after, in my case, months of [near constant] use, began to misbehave.  Apparently CAD-MAN is becoming desperate to find a solution to this problem.](*,)  I am burdened with a significant anxiety disorder, and sincerely hope I do not find myself slipping into desperation, seeking a solution.:(  Will one of you Top Flight Linux Gurus out there please do CAD-MAN (and me) a favor, and take up this cross.  Please, somebody, see if you can't find out what's going on here, and provide a solution.  I would be truly grateful.:biggrin:

Seems very similar to the problem I had (and still have, as far as I know). I have not booted into Ubuntu in months, purely because of this!! Im waiting for Hardy, and then plan a fresh install in the hope that everything will be ok again... Whats the point in using an operating system when you cant get on the web? (Its not just firefox misbehaving, but every web browser, to some degree).

This seems to be a very obscure problem anyway... :confused:

---

