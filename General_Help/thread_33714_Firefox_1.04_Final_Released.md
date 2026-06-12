---
title: "Firefox 1.04 Final Released"
date: 2005-05-11
forum: General Help
---

### Post by the_clown on 2005-05-11
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/)

Are the patches in 1.04 going to be added to ubuntu soon?

---

### Post by bored2k on 2005-05-11
[QUOTE=the_clown][ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/)

Are the patches in 1.04 going to be added to ubuntu soon?[/QUOTE]
 Funny how yesterday I upgraded Firefox from ubuntu repositories and it crashes my extension installs... They just stay in "save as".

---

### Post by nocturn on 2005-05-12
[QUOTE=the_clown][ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/)

Are the patches in 1.04 going to be added to ubuntu soon?[/QUOTE]

I think it might take a while.  This time it is not so bad though because the holes where no longer exploitable.

---

### Post by ubuntu UsER on 2005-05-12
[QUOTE=the_clown][ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/linux-i686/en-US/)

Are the patches in 1.04 going to be added to ubuntu soon?[/QUOTE]

This is very good question. I have FF 1.0.2 on Hoary and it would be good to have all security holes fixed ;-)

---

### Post by bored2k on 2005-05-12
[QUOTE=ubuntu UsER]This is very good question. I have FF 1.0.2 on Hoary and it would be good to have all security holes fixed ;-)[/QUOTE]
 I believe you already have all the holes fixed. Why? well, when your Fox is not updated and you go to their site, you get a "download .3/.4 now!". Yesterday I updated, and to me it isn't there anymore. I know we at least have .3 updates..

---

### Post by gil-galad on 2005-05-12
Firefox just updated for me from the security updates.  It still says 1.02, but I assume it has the security issues fixed.

---

### Post by gmc on 2005-05-12
[QUOTE=bored2k]Funny how yesterday I upgraded Firefox from ubuntu repositories and it crashes my extension installs... They just stay in "save as".[/QUOTE]

The Mozilla team disabled automatic extention installation due to the 2 holes that were recently discovered. If you look at the top of the webpage (addons.mozilla.org) there is a howto that explains why they've disabled the feature and manually install extensions.

G.

P.S. I just tried to get the the extensions page, but it appears to be down right now (12/May.05)

---

### Post by kyle01 on 2005-05-12
Apparently, the favicon thing still works in firefox 1.0.2-0ubuntu5.2 (just installed the latest updates on my hoary system via synaptics). For example, you can use the demo exploit at heisec.de:

[http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml)

It creates and executes ~/browsercheck.sh (runs ls ... ) as soon as you click on "Test ausführen"

Does this only work on my system? I hope there will be a new security update soon...

---

### Post by alt236 on 2005-05-12
Nope, works for me as well (with the latest update from synaptics)....

I can envision a small shell script that attempts to erase all contents of your home dir...

At least it is only proof of concept until now :-)

---

### Post by tread on 2005-05-12
Well, you chaps are brave to test it out anyway :) I wouldn't click on something that is going to exploit my system .. even if its just for testing purposes. I mean .. what reason do you have to trust this guy?

---

### Post by kyle01 on 2005-05-12
The site belongs to a renowned german computer mag.. 
<paranoia>
but then you never know... 
</paranoia>

p.s. the issue seems to be fixed in ff 1.0.4 at least the windows version didn't execute anything (the above demo exploit is designed for both win and linux)

---

### Post by DutchLau on 2005-05-12
"If it ain't broke, don't fix it!"  :grin: 

Ciao,


DutchLau

---

### Post by tread on 2005-05-12
If you don't fix it, the next break could be a severe one :)

---

### Post by XDevHald on 2005-05-12
[QUOTE=tread]If you don't fix it, the next break could be a severe one :)[/QUOTE]
 Oh brother, if it's not fixed then I'm sure either I or someone else sometime this weekend will :p

---

### Post by DutchLau on 2005-05-12
[QUOTE=BB]Oh brother, if it's not fixed then I'm sure either I or someone else sometime this weekend will :p[/QUOTE]
Yes indeed,  :razz: 

*I'm* not the one fixing bugs in Firefox. The only reason I might update is because of these &!#%%$@@#$! crashes that come out of the middle of nowhere and just close Firefox down! I was just posting a beautiful message in the forums to help someone out and the %!$&*&#% program just crashed! I wasn't even on a Java, or Vid plugin site, just the forums! (I still love firefox though, beats Opera and blows away I.E.  :grin: )

DutchLau

---

### Post by 23meg on 2005-05-13
[QUOTE=bored2k]I believe you already have all the holes fixed. Why? well, when your Fox is not updated and you go to their site, you get a "download .3/.4 now!". Yesterday I updated, and to me it isn't there anymore. I know we at least have .3 updates..[/QUOTE]

i've just installed the backported 1.0.3 and i still can't get extensions; it tells me to update to 1.0.4. i couldn't get them with the security fixed 1.0.2 either. any ideas why this is the case?

---

### Post by shakin on 2005-05-13
[QUOTE=23meg]i've just installed the backported 1.0.3 and i still can't get extensions; it tells me to update to 1.0.4. i couldn't get them with the security fixed 1.0.2 either. any ideas why this is the case?[/QUOTE]

Somebody's going to start yelling at me for spamming the board in a second, but...

I have compiled Firefox 1.0.4 from source and made a deb. If somebody can host it for me we can all use it. It installs into /opt/firefox so you don't have to worry about it mucking up your ubuntu install... it's considered a new package.

[url=http://ubuntuforums.org/showthread.php?t=33904]Here's my post about it[/url

---

### Post by XDevHald on 2005-05-13
[QUOTE=shakin]Somebody's going to start yelling at me for spamming the board in a second, but...

I have compiled Firefox 1.0.4 from source and made a deb. If somebody can host it for me we can all use it. It installs into /opt/firefox so you don't have to worry about it mucking up your ubuntu install... it's considered a new package.

[url=http://ubuntuforums.org/showthread.php?t=33904]Here's my post about it[/url[/QUOTE]

Post your request for this to be added to the Repositories in the 3rd Party Projects forum and jdong will get to it once he views it, also note that since you already have the compiled .bz2, put that in there as well so he can see what he wants to do with it from that point.

---

### Post by nuopus on 2005-05-22
I guess this is the reason I switched from Ubuntu in the first place ... but anyway, ive re-installed it and nothing has changed.

Basically, what is in Hoary is what we get ... no upgrades. If 1.02 came in Hoary, that is the version we will get until the next release ... they will just incorporate new security fixes.

Thing is ... Firefox 1.1 is due out soon with some new features and tons of bug fixes. Ubuntu will most likely only encorporate the security fixes and leave us waiting for the next Ubuntu release. This is sad because a distro that works as great as Ubuntu could at least give us up to date software.

But I guess this is the way of the Debian world ... *sigh*

---

### Post by nuopus on 2005-05-22
Well I just found the Ubuntu backports project which gives you newer software in Ubuntu. Now we have a greate distro with newer software .... this is perfect.

For anyone who has never heard of this, go to:

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

