---
title: "Ubuntu / Firefox problem"
date: 2014-05-23
forum: General Help
---

### Post by arborhil on 2014-05-23
This is a very specialized problem which ONLY AFFECTS Firefox in Ubuntu releases 12.04, 14.04.  Firefox is NOT affected in Kubuntu 14.04.  Debian 7.5 with Konqueror is not affected.  IN FACT NO LINUX OS or Web browser is affected with this problem only Ubuntu 12.04 (and later) with Firefox 28 or newer.  I have posted my question on the [Firefox forum here]("https://support.mozilla.org/en-US/questions/997912") with the problem, pictures, and comments.

It is definitely NOT a Firefox problem.  From everything I have been able to research, it is strictly an UBUNTU problem with ITS OWN Firefox.  EVEN KUBUNTU 14.04 with Firefox 28 is NOT AFFECTED.

It has to do with the rendering of the home page (and only the home page) of my website: [http://emblemagic.com](http://emblemagic.com)  I can not figure out WHY this is happening.  But it only occurs in Ubuntu's Firefox.  Not in Windows, not in Chrome, Not in Opera, NOWHERE ELSE! It's been going on since Ubuntu 12.04 to my knowledge.  I have Ubuntu 10.04 on one machine and it is NOT happening there either. 

Unfortunately there were practically no replies on the Firefox forum from Ubuntu users.  I am hoping I get help (or at least some acknowledgement) here. :)

---

### Post by javierrivera on 2014-05-23
> **arborhil said:**
> It is definitely NOT a Firefox problem.  From everything I have been able to research, it is strictly an UBUNTU problem with ITS OWN Firefox.  EVEN KUBUNTU 14.04 with Firefox 28 is NOT AFFECTED.

Kubuntu and Ubuntu Firefox are the same. I mean that they are exactly the same binary, there's not a thing like a Ubuntu Firefox and a Kubuntu Firefox, so that problem can only be caused by a configuration difference (the default settings are indeed different).

Ubuntu install a couple of extensions but disabling them doesn't seem to help. The most likely cause to me is the default font as Ubuntu uses a different default font than most other OSes.

If you expect from Ubuntu developers to fix it I believe that it is going to be very difficult for you to make a case that this is a Ubuntu problem: your site is invalid HTML, and if it finally the problem is font related then it's likely your fault (web developer should specify a font or cope with font variations). Anyway you can try to fill a bug, but expect it to be closed.

EDIT: The problems seem caused by the search form, if I remove it the page works.

EDIT2: The problem is exactly in the input box in the advanced search box, it has a size=40 attribute. A size of 40 characters is too big in Firefox and makes the form grow to wide, if you put a smaller value here it will work. The problem is indeed caused by different default font size.

---

### Post by arborhil on 2014-05-23
javierrivera you are AWESOME!!  You have no idea how crazy this problem was making me!  I couldn't bear to have my website look distorted on **Ubuntu**, even though it was the only OS/browser combo where it was happening.  You were exactly right about the problem too.  I changed the size of the search input text and that made everything fall into place.  I am going to give you credit over on the Firefox forum too!  Again, a THOUSAND THANKS!!!  And a THOUSAND reps too.   +++++++++++++++++++++++

---

