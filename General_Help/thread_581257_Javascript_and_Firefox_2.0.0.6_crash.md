---
title: "Javascript and Firefox 2.0.0.6 crash"
date: 2007-10-19
forum: General Help
---

### Post by in_flu_ence on 2007-10-19
Hi,

   There seems to be a problem when I try to view pages by clicking links with javascript:// ...

Whenever I do so, firefox will stall and take up all the CPU power and I have to force quit to release the CPU.

I have seen somewhere that it might be a bug of firefox but I can't find many people that discuss about it. Any help somewhere?

I tried using opera to view the same page with the same machine and have no problem.

Lastly, it was working perfectly in feisty but somehow it fails after upgrading to gutsy.

I have ensured that javascript is enable with all the options checked.

Advice please.

Thanks

---

### Post by in_flu_ence on 2007-10-19
Some extra info that I have found.

If I install the Firefox-3.0, it works perfectly except that all my plugin (google bar) are missing due to incompatibility.

I have previously installed a firefox32 in my 64bit box. It works perfectly while firefox (64bit) doesn't work.

I assume something to do with the location/lib that it read on which cause the javascript issue. Any help?

---

### Post by celsdogg on 2007-10-25
does anyone have a fix for this? its getting quite annoying.

is anyone else having this problem? i have two ubuntu machines that were fine before i upgraded them to gutsy. now they both lookup when javascript needs to be used.

---

### Post by in_flu_ence on 2007-10-25
I didn't fix it but it seems to be gone for no reason.

Now i have Firefox 2.0.0.8 though and Sun java 6 & Icedtea if that is of any use

---

### Post by celsdogg on 2007-10-26
yeah, the problem seems to have gone away in my laptop, but not in my desktop.

---

### Post by in_flu_ence on 2007-10-26
did you try to reinstall via sympatic?

I think i tried that. but hope it will help u further.

---

### Post by celsdogg on 2007-10-26
^^^ thanks.

i marked all the javascript and even the java packages as reinstalls. didnt work still.

then i did the same with firefox. still doesnt work. :( 

is no one else having these probs?

---

### Post by celsdogg on 2007-10-29
i finally fixed it.

i downloaded firefox for linux from the firefox website. the i followed these instructions loosely:

[http://www.brunolinux.com/03-Installing_Software/Installing_Firefox_in_Linux.html](http://www.brunolinux.com/03-Installing_Software/Installing_Firefox_in_Linux.html)

however, the firefox files are actually kept at /usr/lib/firefox in ubuntu. i made a tar of these files for backup, then i just untared the files i downloaded into this folder and it works perfectly now.

---

### Post by tnilsson on 2007-10-31
I have the same problem with firefox 2.0.0.8, eating up all my CPU.
Yes it seems to be connected to javascripts.

I have never experienced such problems in previous versions of Ubuntu.

---

### Post by Oxydius on 2007-11-03
I upgraded to Firefox 2.0.0.8 in Gutsy amd64 and also have that problem. Visiting finance.google.com with Javascript enabled causes Firefox to lockup forever.

---

### Post by mnbzxcf on 2007-12-28
I have been experiencing this ever since upgrading to a Gutsy RC release.  It happens on all four of my Gutsy boxes.  My machine with Feisty on it does not have this problem.  I finally had some time to play a game of elimination today.  For me, it got narrowed down to the googlebar plugin from Google.  Further, if I open the settings, go to 'More' and change 'Button Text Labels' from 'Selective text only' to 'Icons', I can no longer reproduce the issue.  As soon as I change back to 'Selective text only', I get 100% cpu and firefox is hosed.

To reproduce the problem 100% of the time, I had one browser window open to msnbc.com and a second open to finance.google.com.  The only plugin I had installed was googlebar with default settings.  From within the finance.google.com site, if I right clicked a link and selected 'open in new window', I would get 100% cpu and firefox would no longer respond.  After making the above googlebar configuration change, these steps no longer cause the behavior.  This one configuration change also appears to have resolved my issue in my normal browser profile with several other plugins installed.

Now it's time to spend a week or so browsing and see if this truly resolves my problems.

---

