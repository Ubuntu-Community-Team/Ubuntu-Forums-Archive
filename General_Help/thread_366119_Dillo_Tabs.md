---
title: "Dillo Tabs"
date: 2007-02-20
forum: General Help
---

### Post by nlvivar on 2007-02-20
Anyone know how to get tabs working in Dillo?

Thanks.

---

### Post by kerry_s on 2007-02-20
Ive been trying but i can't get it to compile right. I would love to have dillo with tabs, frames all that good stuff. You can grab the dillo source and the patch and give it a try-> [http://teki.jpn.ph/pc/software/index-e.shtml](http://teki.jpn.ph/pc/software/index-e.shtml)
make sure you use check install, so you can get a .deb and maybe share with the rest of us. :)

---

### Post by bodhi.zazen on 2007-02-20
LOL

IMO the best way to get dillo to use tabs is to run fluxbox and add dillo to ~./fluxbox/groups

For some helpful info on how to configure dillo :

[http://community.fluxbuntu.org/index.php?topic=83.0](http://community.fluxbuntu.org/index.php?topic=83.0)

---

### Post by kerry_s on 2007-02-20
> **bodhi.zazen said:**
> LOL

IMO the best way to get dillo to use tabs is to run fluxbox and add dillo to ~./fluxbox/groups

For some helpful info on how to configure dillo :

[http://community.fluxbuntu.org/index.php?topic=83.0](http://community.fluxbuntu.org/index.php?topic=83.0)

Yeah, i know that, but this month i'm using Xubuntu and dang'it i want tabs. Fix it and fix it now, your fired, get out my site. :lolflag:

---

### Post by nlvivar on 2007-02-22
Well, the last distribution that I used was FC5. When I installed Dillo on FC5, it had tabs. I can't figure out if that was something added onto FC, or the Dillo for Ubuntu/Xubuntu is really stripped down...

---

### Post by kerry_s on 2007-02-22
The dillo in the ubuntu repos is the stock dillo with no patches, just like if you grabbed it from the dillo site. The patches is what gives dillo tabs,adblock,ssl,...

---

### Post by chavo on 2007-02-22
I managed to patch and build it here on my feisty box. I also made a deb with checkinstall, but I have no where to upload it.

---

### Post by kerry_s on 2007-02-22
How big is it? You can attach debs with the manage attachments. The 1 in the repo comes out to around 950 and the max size of attachement is "deb  	976.6 KB". You might even be able to reduce it more if you tar or zip it.

---

### Post by chavo on 2007-02-22
Ok now why didn't I think of that?!?! Doh!
Anyway here it is. I never made a .deb before so don't hate me if it skins your cat or something. I didn't include the dependencies because I assume you already have them installed and I'm not sure exactly what they are. 
I just installed it on my laptop, a pretty fresh feisty install.  It wouldn't run because it needed libgtk-1.2, but a quick apt-get install fixed that.

Edit.. It didn't make a menu entry in my KDE menu either. But that's easy to fix.

---

### Post by kerry_s on 2007-02-22
Thanks, but it just keeps crashing, looks like there's a problem with the dpi daemon. I'll play around with it, see if i can get it working. Ohh, and by the way i hate you, my cat doesn't look right without her skin. :lolflag:

---

### Post by nlvivar on 2007-02-22
Sorry if I'm missing something, how does patching work? Is this deb package an extension for my dillo installation or a whole new installation of dillo?

---

### Post by kerry_s on 2007-02-22
> **nlvivar said:**
> Sorry if I'm missing something, how does patching work? Is this deb package an extension for my dillo installation or a whole new installation of dillo?

Whole new installation, your replacing the installed one with one that has been fixed up. Patching makes it do something that wasn't built in or it might be to correct errors, it's basically a rewrite/addon of/to the code.

---

### Post by kerry_s on 2007-02-22
Hey, it works in xubuntu, without crashing. I get tabs, but the bookmarks doesn't work because there's no dpi daemon. No big deal i can live with out bookmarks. 
Thankyou chavo! :)

---

### Post by nlvivar on 2007-02-22
Do you have bookmarks working in your build, Chavo?

---

### Post by kerry_s on 2007-02-22
Yep it has tabs, i just can't get the dpi daemon to work so no bookmarks. Just try it it's easy to install and uninstall and go back to the old one. Pic->

---

### Post by Onyros on 2007-02-22
Heh, I have dillo with tabs for so long now, I don't remember how I did it, but I guess I compiled it from the site mentioned in page one of this thread. Guess I'll have to keep the binary files, just in case!

Lately I'd been having some trouble login into the forum, but I found a (strange) way to make sure it works: I click on the "Forgot your password" button, and THEN login :P (hey, it works)

---

### Post by chavo on 2007-02-23
Ok I figured out the dpi and bookmark thing, there's a script in the build directory you need to run after you build it. For some reason it isn't run by make install so it didn't get included in the .deb. This will install the dpi daemon in your ~/.dillo.


So I tarred up the script and the daemon here. Just extract this cd into dillo-dpi and run the install-dpi-local script.

Edit.. I installed gtk-theme-switch and some gtk-engines and got it looking pretty nice. This is using the thinice engine and my KDE colorscheme. gtk-theme-switch and the gtk-engines are in the repos.

---

### Post by kerry_s on 2007-02-23
All right now it works! You are the man. =D>
I'm guessing dillo uses the older gtk1 themes? Never mind i got it i just need to find a nice black gtk1 theme to match the rest of my set up. :)

---

### Post by kerry_s on 2007-02-23
Man, i only fond 1 theme at xfce-look that has everything. I guess it will do for now.

---

### Post by nlvivar on 2007-02-23
kerry_s: What did you have to do to get your bookmarks working?

---

### Post by kerry_s on 2007-02-23
> **nlvivar said:**
> kerry_s: What did you have to do to get your bookmarks working?

Follow chavo's instructions above, download the dillo-dpi.tar.gz and click on it to unpack it. Then right click on install-dpi-local and select execute. That's it should work after that.

---

### Post by nlvivar on 2007-02-25
Thanks for the heads-up, kerry_s.

This is what I love about Ubuntu: everyone helping out each other and wading through how to do stuff.

---

### Post by nlvivar on 2007-02-25
So, bodhi.zazen, did you install Fluxbuntu, or did you install an "official" Ubuntu variant? And how do you like it?

---

### Post by bodhi.zazen on 2007-02-25
> **nlvivar said:**
> So, bodhi.zazen, did you install Fluxbuntu, or did you install an "official" Ubuntu variant? And how do you like it?

I have 2 versions of Ubuntu installed.

I am using Fluxbuntu as a home server and an quiet happy with it. I should say that I use Fluxbox as a primary window manager and am happy to have a fluxbuntu because it is 100 % compatible with Ubuntu. Although I use it as a server, Fluxbuntu would work equally well as a desktop.

If you would like to see what Fluxbox can do, go ahead and try out Fluxbuntu.

If you would like to see what a properly configured Fluxbox can look like, take a look at Wolvix-hunter.

[http://wolvix.org/node/379](http://wolvix.org/node/379)

My other Ubuntu install is Feisty and I play a little with cutting edge.

If I can be of further assistance, please let me know.

Also kerry_s is knowledgeable with Fluxbox and as you can see quiet helpful.

Note: To both of you.

I downloaded and compiled dillo-i18n from here (patched source code)
[http://teki.jpn.ph/pc/software/index-e.shtml](http://teki.jpn.ph/pc/software/index-e.shtml)

Patched Source [dillo-0.8.6-i18n-misc-20060709.tar.bz2](http://teki.jpn.ph/pc/software/dillo-0.8.6-i18n-misc-20060709.tar.bz2)  592Kbytes
md5sum 5e632d551065abadac320edaa9ead76a

It compiles without errors.

I got errors on make and make install but it seems to run without any problem.

If I have time I will make a .deb

HTH

---

### Post by nlvivar on 2007-04-15
So I finally got around to trying to install the deb package that chavo posted. My install crashes when I open it up.

Oh, well. I'll just stick to the non-tabbed version.

Peace.

---

### Post by bodhi.zazen on 2007-04-15
Well, there is actually an easier way of getting tabs in dilo :twisted:

[http://community.fluxbuntu.org/index.php?&topic=179.0](http://community.fluxbuntu.org/index.php?&topic=179.0)

Works like a charm ;)

---

### Post by nlvivar on 2007-04-16
wow, bodizazen. perfect. works for me. are there any other options to enable on dillo?

and out of curiosity, how is this different from the patched build?.. I was never able to compile that patched build.

Thanks. -Noel

---

### Post by kerry_s on 2007-08-13
dillo patched, no errors

---

### Post by bodhi.zazen on 2007-08-13
Awesome.

For what version of Ubuntu ? All versions ?

---

### Post by kerry_s on 2007-08-13
> **bodhi.zazen said:**
> Awesome.

For what version of Ubuntu ? All versions ?

i built it on etch/lenny, so should be good up to fiesty.
i'm not sure about gutsy, as the last time i ran debian unstable, gtk1.2 was needing rebuild, so i guess it would depend at what snapshot it's currently using.

Try it and let me know. :)

---

