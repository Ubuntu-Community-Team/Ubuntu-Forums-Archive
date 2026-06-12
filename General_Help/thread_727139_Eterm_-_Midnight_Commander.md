---
title: "Eterm - Midnight Commander"
date: 2008-03-17
forum: General Help
---

### Post by The Avatar of Time on 2008-03-17
Hello, I am using Eterm, which I like real well overall. It is the only Terminal that I can get the transparency and border-less things to work on. The trouble I am having with it is that Midnight Commander and Finch and probably a few other things I don't remember right now display rather odd in Eterm. Midnight Commander works just fine in Xterm, but in Eterm and Aterm it has weird characters where the divider lines should be, ie. where there should be a | in between Name and Size there is an a with a carrot over it and to squares after it. In Xterm I get the | which looks nice and neat but Eterm is just to cluttered to use MC in. Finch does the same type of thing where the scroll bars should be. It displays them right part of the time but part of the time I get weird characters instead. Even the contact names in my buddy list get messed up, I have on that appears 'shsh' when it should be 'josh'. If I go to buddy list and highlight the contact it will be fixed for a while. Any help would be appreciated. If I can get MC to work in Eterm okay I would also like to get rid of the color and have it transparent as well. Thanks.

---

### Post by The Avatar of Time on 2008-04-03
Anyone  know how to make Eterm display Midnight Commander properly?

---

### Post by kerry_s on 2008-04-03
most terms suck with mc. look in the repo for "roxterm" it does transparency and all that other stuff eterm can do.

transparent mc> mc -b

i think your out of luck with roxterm, i only see it in hardy->
[http://packages.ubuntu.com/hardy/x11/roxterm](http://packages.ubuntu.com/hardy/x11/roxterm)

---

### Post by kerry_s on 2008-04-11
hey did you ever figure this out?

the fix is to edit your /etc/environment
put or change

```
LANG="en_US"
LC_ALL="C"
LANGUAGES="en_US"
```

also you can do you own colors for mc, add these 2 lines to the bottom of ~/.mc/ini
```

[Colors]
base_color=normal=white,default:marked=,default:selected=red,default:markselect=yellow,default:errors=yellow,default:input=white,default:gauge=,default:reverse=red,default:menu=white,default:menusel=red,default:menuhot=,default:menuhotsel=,default:dnormal=yellow,default:dfocus=yellow,default:dhotnormal=,default:dhotfocus=,default:helpnormal=white,default:helpitalic=white,default:helpbold=white,default:helplink=,default:helpslink=,default:viewunderline=,default:executable=,default:directory=,default:link=,default:stalelink=,default:device=,default:special=,default:core=,default:editnormal=,default:editbold=,default:editmarked=yellow,default

```

that line is what i'm using, adjust the colors to your needs.pic->

---

### Post by The Avatar of Time on 2008-04-13
Thank you for the response, however I did what you suggested to /etc/environment and it did not help. I have included a screen shot of what my mc still looks like. 

Here is my /etc/environment:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US"
LC_ALL="C"
LANGUAGES="en_US"

So any idea what I am missing?

Not worried about it being blue, I think I have the color thing under control now. Just those 'weird' symbols.

---

### Post by kerry_s on 2008-04-13
> **The Avatar of Time said:**
> Thank you for the response, however I did what you suggested to /etc/environment and it did not help. I have included a screen shot of what my mc still looks like. 

Here is my /etc/environment:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US"
LC_ALL="C"
LANGUAGES="en_US"

So any idea what I am missing?

Not worried about it being blue, I think I have the color thing under control now. Just those 'weird' symbols.

have you rebooted yet? mine didn't kick in till after a restart.
type> locale
in term to see what it's still on.

---

### Post by The Avatar of Time on 2008-04-13
Okay I restarted now (should have thought of that) and it helped but it did not completely fix the problem. It is much better though. I included screen shots of how it looks depending on which pane you are in. 

Here is my locale:

```

LANG=en_US.UTF-8
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C

```



And here is the /etc/environment again to show that it has not changed:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US"
LC_ALL="C"
LANGUAGES="en_US"

```

I find it odd that LANG="en_US" in /etc/environment but LANG=en_US.UTF-8 when I type locale. Not sure where to go from here. Thanks.

---

### Post by kerry_s on 2008-04-13
hmm, interesting. try running->
sudo dpkg-reconfigure locales

select the 3 en_US, on the next screen select en_US for the default.

i did this long before i did /etc/environment, so not sure if it will help or not.
it wasn't till i changed environment, that mc looks perfect on any term, even the simple xvt term. i've done so much tweaking, i can't remember most of it. :(

also try> mc -a
that makes it use the old style lines.

also, can you look in synaptic and see what version mc your running, that looks like the older version, that had scroll bars.
mines 1:4.6.2~pre1~7, i'm using debian etch/lenny.

at least it's more usable. :)

---

### Post by The Avatar of Time on 2008-04-13
Okay I gave the sudo dpkg-reconfigure locales a try and this is what it does:
```

Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date

```

But it gives me no option to select anything. 

The mc -a does change to the old lines but it still has those weird symbols.

My version of mc is 1:4.6.1-7ubuntu2 which is also listed as the latest version.

Yes it definitely looks much better than it did. It's completely usable now, just a touch odd to look at. I have not restarted yet since using the sudo dpkg-reconfigure locales, since it did not give me options to change anything. Soon as I finish the work I am doing I will see if that helps.

I plan to upgrade to Hardy here as soon as it comes out which might end up helping as well. If you have any other ideas that would be great, and if not thank you very much for your help, it is much nicer now.

---

### Post by kerry_s on 2008-04-13
ohh, that might have been the wrong command then, sorry i'm going off memory and my memory sucks.
let me look it up and get back to you.

hmm, that's funny, that is the right command.
[http://www.ubuntugeek.com/how-to-select-and-generate-locales-on-ubuntu.html](http://www.ubuntugeek.com/how-to-select-and-generate-locales-on-ubuntu.html)
when i run it i get a choice, see pic->

---

### Post by kerry_s on 2008-04-13
i'm out of ideas, sorry. the new version don't have the scroll, so you should be fine when you move up to hardy. it just might not be fixable with the old version, could be why they removed the scroll area in the new version.

anyway's sorry couldn't get it 100%, i'll keep a eye out if i spot anything that might help you with the current install. 
i'm still messing around with mine, been looking for a way to remove the lines altogether, which would also help you. :)

---

### Post by The Avatar of Time on 2008-04-13
Okay I followed that link and added the three locales that you have in your screen shot (well I added two and one was already there) and then ran sudo dpkg-reconfigure locales again. Then I restarted the computer. No change though, mc still looks the same.

```

Generating locales...
en_AU.UTF-8... up-to-date
en_BW.UTF-8... up-to-date
en_CA.UTF-8... up-to-date
en_DK.UTF-8... up-to-date
en_GB.UTF-8... up-to-date
en_HK.UTF-8... up-to-date
en_IE.UTF-8... up-to-date
en_IN.UTF-8... up-to-date 
en_NZ.UTF-8... up-to-date
en_PH.UTF-8... up-to-date
en_SG.UTF-8... up-to-date
en_US.ISO-8859-1... up-to-date
en_US.ISO-8859-15... up-to-date
en_US.UTF-8... up-to-date
en_ZA.UTF-8... up-to-date
en_ZW.UTF-8... up-to-date
Generation complete.

```
That is the output I get now when I run dpkg-reconfigure locales. I wonder if perhaps the problem is just that I have an older version of mc? I suppose I could try to download and compile a newer version. Oh well, Hardy will be out rather soon so I might just wait till then to mess with it more. Thanks for your help though, least I can use it in Eterm now.

---

