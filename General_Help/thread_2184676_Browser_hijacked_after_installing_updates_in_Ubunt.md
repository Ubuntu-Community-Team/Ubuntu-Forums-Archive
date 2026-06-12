---
title: "Browser hijacked after installing updates in Ubuntu 13.10"
date: 2013-10-30
forum: General Help
---

### Post by glennsmart on 2013-10-30
Today I installed the latest updates for Ubuntu 13.10.  One of optional the updates was a Chinese language pack for Firefox.  I teach English here in China and thought it might be  a useful addition.

When I started the Firefox browser I found that the start page automatically opened at the address [www.daohang114so.cn](www.daohang114so.cn)

I managed to reset the homepage to BBC.co.uk which opens no problem when Firefox is launched.  However, if I click on any link on the BBC's page, or try to go to a different website, or do a Google search, it automatically goes to [www.daohang114so.cn](www.daohang114so.cn)   The same is true of the Opera web browser: it automatically directs to daohang114so.cn

I've used the Ubuntu software centre to uninstall Firefox and then reinstall it. It made no difference. I've looked on Linux forums for advice and followed suggestions.  Nothing has made the slightest difference.  The package manager doesn't list anything that might be associated with ''daohang114so'.  There's nothing in Firefox's settings which indicate what this nuisance is being caused by.

The result is that I've had to borrow a Windows laptop just to get online.  I don't believe for one minute that the downloaded 13.10 updates had anything to do with ..probably more a case of 'something coming in with it' (this is China..).

I'm a complete 60 year old novice with Ubuntu.  I can follow instructions but most of the technical jargon is way above my head.  Is there something that I would be able to do to remove this home-page hijacker, or is a fresh installation of Ubuntu my only hope?
 I

---

### Post by ajgreeny on 2013-10-30
With firefox not running rename your current ~/.mozilla folder with command **mv .mozilla .mozillabak** in a terminal which you can get to with Ctrl+Alt+T, and then restart firefox.

It sounds to me as though you have a corrupted profile.  If that works OK you can copy back your old bookmarks and some other bits and pieces that may be needed, from the original renamed folder to the new one, but let's go one step at a time to see if it works.

---

### Post by glennsmart on 2013-10-30
Thanks for a swift reply. I really do think the Linux community are worth their weight in gold.  However, I solved the problem.

I ran the Clam virus checker which picked up a massive possible 855 threats.  Here in China 'foreign teachers' as they call us, download many Windows based software for students to use.  We also use QQ (a Chinese chat program) which is Windows-based.  To get it to work in Linux  we use Wine/Winetricks or VirtualBox with a Chinese version of XP/Windows 7.  That is to say, whilst using Linux there is also a Windows 'input'.

I simply deleted everything that Clam identified as a possible threat, thinking that if Ubuntu didn't work I could always install a fresh copy.  Well, Ubuntu *did* work after deleting everything picked up by Clam.  Not only that, Firefox and Opera were back to normal..what it was that actually caused the problem

I don't have a clue what it was that actually caused the problem other than calling it a 'Windows nasty'.Virus-malware-trojan whatever. The virus scan results mean nothing to me.
And by coincidence as I write, a Canadian teacher here has just called in on me.. he uses a different version of Ubuntu but he has found he has exactly the same problem as I had...

---

### Post by philinux on 2013-10-30
If it happens again try clearing firefox's cache. Also the addon noscript might be a worthwhile addition. [https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

---

