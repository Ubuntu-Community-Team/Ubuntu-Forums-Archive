---
title: "[SOLVED] How do I block pop-ups in Firefox without extensions?"
date: 2007-10-04
forum: General Help
---

### Post by aysiu on 2007-10-04
**Note:** Please don't question my desire to use Firefox. I've tried just about every major browser there is: Opera, Kaza...(sp?), Galeon, Epiphany, Konqueror, Lynx, Dillo, SeaMonkey, Swiftfox. I don't need browser recommendations. I like Firefox.

That said, I have generally found Firefox to be fastest when I don't load up extensions. I realize to many people the appeal of Firefox is the ability to add extensions, but I actually like vanilla Firefox. I also know that a lot of people here *say* Swiftfox is faster than Firefox--on my computer, that is not the case; I see no difference between Swiftfox and Firefox, performance-wise.

Still, I do have one problem with Firefox without extensions: pop-ups. With NoScript, it's pretty easy to block pop-ups. But without extensions, is there an easy way (in about:config, for example) to block pop-ups? The built-in pop-up blocker in Firefox doesn't allow you to specify *blocked* exceptions, only *allowed* exceptions.

Any tips?

---

### Post by yabbadabbadont on 2007-10-04
Disable Java and JavaScript...  You didn't specify *good* tips.  ;)

Although that is how I run FF.  I only have one extension installed, Tab Mix Plus.  I've got it configured for Single Window Mode and it forces all pop-ups into new tabs, which makes things a little better.  Of course, that only happens when I have JavaScript enabled and the built-in blocker fails to catch something.  (A pretty rare occurrence for me.)

---

### Post by aysiu on 2007-10-04
Thanks, anyway. I knew I could do that, but, unfortunately, many of the sites I use employ Javascript.

---

### Post by p_quarles on 2007-10-04
[This]("http://www.agileprogrammer.com/dotnetguy/archive/2005/04/18/4791.aspx") might help. Change the privacy.popups.disable_from_plugins value to 2. According to the link, doing that fixed that person's problem with popups getting through the built-in popup blocker. 

That said, it appears to be the default value at least in my copy of Swiftfox, so there might not be anything to change.

---

### Post by aysiu on 2007-10-04
No, that's not it. 2 means the "block pop-up windows" is checked and 1 means it's not checked. So that's no different what I have now. Thanks for looking into that, though.

---

### Post by kerry_s on 2007-10-04
have you tried using a hosts block list?
i'm sure you know how to copy and paste, so here's a list i use, when not using extensions->
your-editor /etc/hosts

[http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

---

### Post by kerry_s on 2007-10-04
aysiu, did you try it yet?

you only need the address's you can cut out the other crap.
the easy way is to "save page as" then delete the parts you don't need, then select all and paste it into your hosts file.

top and bottom of mine->

---

### Post by aysiu on 2007-10-04
Slow down a second.

So I add the sites I want to *block* to my /etc/hosts file? That seems weird. Right now my /etc/hosts file has *localhost*, which is my computer, which is something I don't want to block.

---

### Post by kerry_s on 2007-10-04
> **aysiu said:**
> Slow down a second.

So I add the sites I want to *block* to my /etc/hosts file? That seems weird. Right now my /etc/hosts file has *localhost*, which is my computer, which is something I don't want to block.

you add it below that, see my pics.
maybe you should read about it-> [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

---

### Post by aysiu on 2007-10-04
Thanks for the link. So 127.0.0.1 means *block this site*?

That may work, but I have a sneaky suspicion that some of the pop-ups I see are actually coming from the site itself and not necessarily from some third party (with a few exceptions, of course).

We'll see. Thanks for letting me know about that option, kerry_s.

---

### Post by p_quarles on 2007-10-04
When I looked up this issue, the impression I got was that the popups that get past the built-in blocker are all based on client-side scripting of some sort (whether js, xss or Flash). If you think these are included locallly in the sites that you're visiting, I'd guess it would be very difficult to disable the popups without getting something like NoScript. 

An easy way to confirm your suspicion, though, would be to get NoScript, visit the sites in question, and enable javascript from those sites. If you get popups, you'll know that the scripts are local to the site. I know you don't want plugins, but installing one temporarily would at least help diagnose the source of the problem.

---

### Post by aysiu on 2007-10-04
> **p_quarles said:**
> When I looked up this issue, the impression I got was that the popups that get past the built-in blocker are all based on client-side scripting of some sort (whether js, xss or Flash). If you think these are included locallly in the sites that you're visiting, I'd guess it would be very difficult to disable the popups without getting something like NoScript. 

An easy way to confirm your suspicion, though, would be to get NoScript, visit the sites in question, and enable javascript from those sites. If you get popups, you'll know that the scripts are local to the site. I know you don't want plugins, but installing one temporarily would at least help diagnose the source of the problem.
Thanks, p_quarles. That sounds like a good plan.

To be honest, I don't get pop-ups that often, but the fact that they appear at all ever is a bit jarring (I've only recently got off extensions).

---

### Post by kerry_s on 2007-10-04
> **aysiu said:**
> Thanks for the link. So 127.0.0.1 means *block this site*?

That may work, but I have a sneaky suspicion that some of the pop-ups I see are actually coming from the site itself and not necessarily from some third party (with a few exceptions, of course).

We'll see. Thanks for letting me know about that option, kerry_s.

if the pop up is from the site you can still get. just check the properties and add the full path with 127.0.0.1.
example:
127.0.0.1 google.com/this/opens/a/pop/up

the hosts file is dynamic, you can add/remove entries and it will take effect, you just reload the page.

i also use noscript, so you might want to go with p_quarles suggestion. noscript is the only extension i have.
the host file will catch most things on any browser you use.

---

### Post by aysiu on 2007-10-06
So /etc/hosts appears to work, but just reloading the page doesn't appear to work for me. Even restarting the browser doesn't. I actually had to reboot my computer to have the changes take effect.

Is that weird? Could something be wrong with my computer?

**Edit**: Maybe it is something wrong with my computer (desktop). On my other computer (laptop) has the changes take effect immediately (after a page reload) and doesn't require a reboot.

---

### Post by bodhi.zazen on 2007-10-06
> **aysiu said:**
> So /etc/hosts appears to work, but just reloading the page doesn't appear to work for me. Even restarting the browser doesn't. I actually had to reboot my computer to have the changes take effect.

Is that weird? Could something be wrong with my computer?

**Edit**: Maybe it is something wrong with my computer (desktop). On my other computer (laptop) has the changes take effect immediately (after a page reload) and doesn't require a reboot.

Aysiu, please allow me to try to shed some light on the subject :

I think you are fine, my guess is the page in question was still in your cache and thus there was no change when you re-loaded the page (and the cache was then cleared with a re-boot).

A few comments on the host file, if I may.

First, I think of the hosts file as a local (or personal) address book. Whey you enter site.com in your browser your computer first checks the hosts file, then with your Internet Provider, then on the broader internet for the (IP) address.

The hosts file is most often used to define other computers on your LAN (so you can ssh <mom> to connect to your mom' s box rather then ssh 192.168.0.234).

OK, so if you look at your hosts file, among other things you will see :

> 127.0.0.1       localhost 
127.0.0.1 <your_host_name>

So, 127.0.0.1 == localhost == your computer 

==============
Intermission
==============

Ok now the (mis) use of /etc/hosts as adblock (or so the purists say ...)

The advantage of using your hosts file is it protects not just firefox (the way adblock plus would) but any browser and in fact your whole computer (On windows it would keep malware from phoning home as well)

OK, now there is a script, maintained by the same folks who maintain the listing in the Friefox Adblock extension, to keep you up to date :

download (save) **updatehosts.sh.txt** from here :

[http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)

```
sudo aptitude install tofrodos
sudo cp /etc/hosts /etc/hosts.org #.org for original
chmod a+x updatehosts.sh.txt
sudo ./updatehosts.sh.txt
```

You can run updatehosts.sh.txt any time you like to update your adblock (it seems the list is updated ? weekly, I am not sure).

==============
Intermission
==============

OK, now for icing on the cake ?

Change your adblock from 127.0.0.1 to 0.0.0.0

0.0.0.0 = nowhere

This will speed up your browsing as you will not have to wait for your computer to time out the connection to 127.0.0.1.

This is done in two easy steps :

[list=number][*]A simple sed :```
sudo sed -i -e 's_127.0.0.1_0.0.0.0_g' /etc/hosts
```
[*]Now edit /etc/hosts (I would use nano or vim as gedit will take a *long time* to load your engorged hosts file) and change the references at the top of the file , pointing to your computer, back from 0.0.0.0 to 127.0.0.1 (usually this is the first two lines in /etc/hosts).[/list]

To make it easy, list those lines with ;

sudo grep localhost /etc/hosts
sudo grep <your_hostname> /etc/hosts

---

### Post by aysiu on 2007-10-06
Thanks, bodhi.zazen. That's helpful info! I'm learning a lot here.

---

