---
title: "google earth fly to not working in 13.04"
date: 2013-06-29
forum: General Help
---

### Post by harlie on 2013-06-29
I have been using google earth 6.0.3.2197 in ubuntu 13.04 but suddenly it will not fly to I get a box saying   UNABLE TO PERFORM
INVALID HTTP REQUEST  this is a 64 bit pc and on my wifes 32 bit pc the same thing has happened. things worked well on both pc's till msot recent updates. If I need a newer version of google earth do I first need to remove the current one? I see that version 7.-- is available. 

thanks for any help 

Harlie            ps everything else in GE works fine even now.

---

### Post by Michael Craig on 2013-06-30
I noticed the same problem today: "invalid HTTP request".  Actually, *none* of the Search options  - Fly To; Search Businesses; Directions -  works; each throws up the same error.  I've used this install of G.E. on this install of Ubuntu for more than a year, and I never experienced this problem before.  The 3 most recent Ubuntu update installs were done on 6/22, 6/26, and 6/28.  I am not certain about when I last used G.E. before this morning, but I feel it was very likely less than two weeks ago.    Ubuntu **12.04 LTS** Google Earth **6.2.2.6613**

---

### Post by harlie on 2013-07-01
Sounds the same as my error. So must be due to a recent update, in only the last week. The other searches for places do not work either, as in find business etc, asstated in response #1.

Harlie

---

### Post by rusta on 2013-07-04
Xubuntu 13.04 64 bits

Me too, with GE V6 "invalid HTTP request" and with GE V7 no pics with panoramio.

I decided to uninstall all of google-earth and make a sudo apt-get autoremove, who remove all ia32libs that GE use on 64 bits.

Then I copied the /opt/google/ from my arch 64 bits distro to my xubuntu 13.04 HOME and run google/earth/free/googleearth.

Everything is right. I was really surprised!.

if you want I publish the link to my pacakge here but dunno if I can do that. There is no problem with google-earth license but, perhaps, links to packages with binaries are not allowed here. The package is the result of a compilation from AUR on 64 bits, not the last, it's the GE version 7.0.2 8415

Sorry for my bad english

---

### Post by marcia on 2013-07-05
I have the exact problem as all of you do after the latest updates for my dreamstudio 64 and dreamstudio 32. Rusta, you said you fixed it  and I wonder how that fix can be applied to the latest google earth for ubuntu 64 and 32. Any thoughts are welcome. 

I have been researching this for the past 5 days since I discovered the problem. Someone mentioned that the problem is with the libqtwebkit libraries and they need to be the latest since the ones google earth supplies have a problem. I think this was in google groups and mainly applying to the panoramio photos are blank issue.

I hope someone gets a solution soon. I use google earth all of the time.

Sincerely,

marcia

---

### Post by harlie on 2013-07-05
I removed the problem G. E. and installed the newer G. E. 7.--- from NoobsLabs and it works properly except you can not open any photos on the displayed view. I hope this is a minor glitch which can be fixed by seeking help from NoobsLabs. I didn't have time to do this yet. stay tuned for the latest developments.


Harlie

---

### Post by Handssolow on 2013-07-05
Being unable to fly to a chosen location on Google Earth occurred here too recently. I've just removed GE 6 and downloaded GE 7 from Google which I installed using Ubuntu Software centre.

As experienced by harlie, Search/fly to is back but photos aren't showing, just a white window.

OS Ubuntu 12.04 32bit

---

### Post by rusta on 2013-07-06
This is my solution for xubuntu 13.04, raring,  64 bits

Uninstall GE. After that do 'sudo apt-get autoremove'.

Extract my *package where you want

[http://ubuntuone.com/2k9LzFzucXy16X5NnROXSW](http://ubuntuone.com/2k9LzFzucXy16X5NnROXSW)

run 'google/earth/free/googleearth'


*this package is a copy from /opt/google..    , compiled from AUR, arch linux 64 bits
Google Earth 7.0.2.8415

---

### Post by Rebelli0us on 2013-07-06
Yep same problem here, worked fine before, a recent update must have borked it.

So, I downloaded and installed 7.1 from Google. Search works now but clicking on some popup elements crashes the app.  Will this version auto-update?

---

### Post by marcia on 2013-07-10
Thanks for this package. My distro is 32bit so I need a 32bit googleearth. Hopefully there is a way to get 32bit googleearth working totally.

Thanks again.

marcia

---

