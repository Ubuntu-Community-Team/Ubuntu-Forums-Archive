---
title: "What's with Wine?"
date: 2005-07-18
forum: General Help
---

### Post by SpEcIeS on 2005-07-18
About two days ago I removed wine which comes with Ubuntu and compiled and installed 20050628. When it comes to installing anything, failure. Age of Empires 2 installed, but does not run; Simcity 2000, which worked on my SuSE 8.1 distro, will not even install, kicks out after asking for directory to install to; Internet Explorer 6.0sp1..  not even. Wine Tools will not do the trick. Sidnet and another attempt which escapes my mind, might be the Patrick Mackinlay method. Nothing.

Having these experiences, and others, I decided to try out cedega, this was a failure too. This all seems too strange.

What could be happening here?  :neutral: Has anyone actually had wine work properly, or could this be a poor version. Perhaps downgrading to an older version is needed, like 20041019?

---

### Post by evilghost on 2005-07-18
The newer versions from what I understand are defunct, as are those in the repository last time I checked.

I'm using this version, and have IE6Sp1 installed without issue.
```

luser@400sc:~$ wine --version
Wine 20050524

Winetools 2.1.1

```

---

### Post by SpEcIeS on 2005-07-18
[QUOTE=evilghost]The newer versions from what I understand are defunct, as are those in the repository last time I checked.

I'm using this version, and have IE6Sp1 installed without issue.
```

luser@400sc:~$ wine --version
Wine 20050524

Winetools 2.1.1

```[/QUOTE]
Hey thanks a lot. :) This is good to know, and now I have somewhere to start.  :D

_Update_:
Well that really did the trick, and it is nice to see internet explorer again. Just for testing webpages. Age of Empires II still does not work, but this has been a great improvement. Thanks again. :)

---

### Post by evilghost on 2005-07-19
Hey no problem, glad I could help :)

---

### Post by pablito on 2005-08-14
Hi,

I just recently tried installing version 20050725. Using winetools to install IE fails. Well actually, I tried manually (command line> wine iesetup.exe) installing it also and that was no different. The Windows install complains that "Setup was unable to download the required components. Please make sure you are connected to the Internet or try to run Setup again later."

Anyway, would like to try the version you refer to above. How can I go about getting ahold of this older ubuntu deb package? 

Cheers,
Paul

---

### Post by SpEcIeS on 2005-08-14
In Synaptic use the force version. Downgrade from there. :)

---

### Post by pablito on 2005-08-14
Yeah I saw that suggested in a post elsewhere, but the only options available are:
[list]
[*]0.0.20050725-winehq-1 (now)
[*]0.0.20050310-1.1 (hoary)
[/list]
I presume that the force option can only offer what is available in the repositories or on the local machine. As the version I am after is no longer in either... well back to my original question: Where can I get a hold of older debs? They must be archived somewhere no?! :)

Cheers,
Paul

---

### Post by crane on 2005-08-14
I found 20041019 I had saved from a while back. I installed the .deb using dpkg and all is well. I originally tried the version in the repositories but it was still busted.

Try searching for old .debs of wine and install one of them.

---

### Post by SpEcIeS on 2005-08-14
I am currently using 0.0.20050524-winehq-1 and it works very well. In fact, after my journey of wine testing, I have locked into this version, and I am not letting it go until I know that the newest version, whatever that is, is stable. Or better yet, complete.

I do not know if you have the WineHQ repos in your sources.list, but if not here they are:

[b]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/b]

Apply these lines in your _*sources.list*_, usually located under /etc/apt then sudo apt-get update. Using Synaptic you should be able to downgrade, or install the 0.0.20050524-winehq-1 version.

Hopefully this will help you out. :)

---

### Post by pablito on 2005-08-14
Added it to my sources. Although I now see the sourceforge repo, I still don't have the option of installing 20050524. Only available options are still the same 2 as above (except that now 20050725 has "wine.sourceforge.net" in brakets next to it). Thanks anyway!

Cheers,
Paul

---

### Post by Scunizi on 2006-03-16
I was having all kinds of problems trying to get IE6 installed under Wine .9.9.  It just wasn't happening until I discovered IES4Linux ([http://www.tatanka.com.br/ies4linux/)](http://www.tatanka.com.br/ies4linux/)).  Worked like a champ.  My litmus test is to log into my local MLS and do a home search.  Fonts are a little different but everything functions.  This was a very painless install and gives you a choice between different versions of IE or all of them.

---

