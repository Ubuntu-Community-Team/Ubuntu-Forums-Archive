---
title: "Webpage works on Firefox/Windows but not Firefox/ubuntu"
date: 2007-09-14
forum: General Help
---

### Post by Razi on 2007-09-14
I have a website that does some sort of check for browser version and says that my version of Firefox is not supported.  The same website works on windows using both Firefox 1.5 or 2.0.  Under puppy, ubuntu or xubuntu I get this same 'browser unsupported' error.  The owners of the site say they do not support linux, but a browser is a browser is a browser, right?  

Is there a way to change the installation to [falsely] report to the website that I am using a valid version of Firefox?  

I am not sure that changing the version number from 2.0.0.2 to 2.0.0.6 will do it (i think that is in firefox.js). I need to look at the sites "aspx" code to see what about firefox is saying to them that they don't like.  It's rather frustrating.

---

### Post by Lord Illidan on 2007-09-14
Can you give us a link to this website to check?

---

### Post by Lord Illidan on 2007-09-14
Otherwise, this might help : [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by Razi on 2007-09-14
> **Lord Illidan said:**
> Can you give us a link to this website to check?

The website is time4learning.com however you need an account to get to the part where it tells you that your browser is not supported.  There is one link that you're supposed to be able to run the check without logging in but that link is broken.  

I'm at work and don't have access to my linux installation so I can't get to the screen where it says I failed.  Otherwise I could look at the code and present more info. My gut tells me they are checking more then "mozilla" or "firefox" versions and the code checks OS.  It is aspx which means that is microsoft, and it may just be linux unfriendly (out of spite - gotta love the .net stuff sometimes)... 

If you click on "help->about" under windows it says for example "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.6) Gecko/20070725 Firefox/2.0.0.6".  The "Firefox/2.0.0.6" is generated in "firefox.js" but I have not found where the "Windows;" bit comes from.  I don't mind making Firefox lie and say "Windows;" instead of "Linux" (or whatever it says - again I am not home), but I need to figure out where that is generated.  Just spoofing that should let me into the website - it may not work for some other reason - but I'll deal with that if that is the case.  My gut says that it will work if I can get past the browser-check.  

Frankly, this PC is an old one designed for windows 98 that I have put on xubuntu on because it works better on linux then windows 98 or ME (not to mention security concerns with old microsoft).  The ONLY thing this old PC is going to be used for is home-schooling via this web site... I don't really care if I break the browser for other web sites.

---

### Post by Vadi on 2007-09-14
Yeah, your browser does report what your OS is (see my "what OS visits your site" thread...).

Pretty stupid of the designers to specifically exclude Linux.

---

### Post by Razi on 2007-09-14
> **Vadi said:**
> Yeah, your browser does report what your OS is (see my "what OS visits your site" thread...).

Pretty stupid of the designers to specifically exclude Linux.

I read your thread, but what I need to know is HOW the browser derives that information.  Most of Firefox is just "js" scripts.  Which one reports the OS?  It should be a simple matter of telling it to not run whatever command it is running to retrieve the information from the registry or some os command or whatever... and replacing it with a hard coded string supplying the name of an accepted OS.

---

### Post by Vadi on 2007-09-14
I'll try the plugin that Ilidan suggested, momento.

---

### Post by Vadi on 2007-09-14
Heh, yep the plugin does work. In tools - User Agent Switcher - and voila, pick your browser's new identity.

---

### Post by Razi on 2007-09-14
> **Vadi said:**
> Heh, yep the plugin does work. In tools - User Agent Switcher - and voila, pick your browser's new identity.


:lolflag: it looks like this could be a solution.  I can't wait to get home from work, add this plugin, and test the site.  Thanks Lord Illidan!!  What a way to make firefox :---)

I'll report back to this thread one way or another =D>

---

### Post by fragos on 2007-09-14
Error messages on web sites reflect what the designer understands.  If the designer is Microsoft limited there will frequently be things that work with Linux.  If you look at a good HTML book you'll see a command explained in perhaps one page and the next four or more pages dealing with non-standard implementation like from our friends in Redmond.  Shame on that web site for not understanding their craft.

---

### Post by FuturePilot on 2007-09-14
I hate when websites only support Firefox on one platform. i.e. Windows. They need to realize that a cross platform browser is the same no matter the platform. *sigh*](*,)

---

### Post by jasncab on 2008-07-10
I got this to work with one slight modification for my daughter. I had to edit the Netscape 4.8 (Windows Vista) user agent to 5.1 - 4.8 isn't supported. the IE one made the links not work due to JS differences when rendered I presume.

[http://huberstyle.com/viewblog.aspx?blogid=288](http://huberstyle.com/viewblog.aspx?blogid=288)

Thanks for the tip and awesome plugin for this sort of thing! Ubuntu and FF (FTW).

---

