---
title: "Apps verrry slow"
date: 2005-03-22
forum: General Help
---

### Post by Fintan on 2005-03-22
hi everyone,
Okay i know this is not he fastest machine:
PII 450Mhz
296 Ram
398 Swap

But every thing from evolution, firefox, OO, to even the home directory takes ages to load.
Under firefox even after tweaking the about:cofig here:
network.http.pipelining                       set to true
network.http.pipelining.maxrequests  set to 40
network.http.pipelining.maxrequests  set to true
network.http.proxy.pipelining              set to true

It still takes about a minute or even two to load a normal site like ubuntu

my bandwidth under synaptic or apt-get is somewhere around 160-190kbs
so its not the network connection.

Even on my PIV with 2.6GHz
1GB Ram
Thae same happens, albight not QUITE as slow.

Any ideas would be helpfull.

Thanks and greets
Fintan

---

### Post by ember on 2005-03-22
Have you tried you pinging a site with it's IP address?

There are some people that had issues with DNS when using DHCP. Maybe that's the case for you, too.

---

### Post by Fintan on 2005-03-23
Okay was this just a stupid question?
Ifd so then maybe one of the 27 nonresponing viewers can tell me why.
I want to learn, thats why i ask these kind of questions.
Okay?

---

### Post by rykel on 2005-03-23
Hi,

Did you upgrade your system using the repositories?

My spanky, new Ubuntu Hoary preview was lightning fast... UNTIL! I dist-upgrade the whole thing...

Well, nothing broke, except that applications now take time to start, load plugins etc.

eg. Firefox 1.0 was fast - but 1.0.1 is DRAAAAGGGGY.

So I guess it is coz my system is more bloated now, that's why it's slower...



Best Regards,

Rykel

---

### Post by Fintan on 2005-03-23
Thanks rykel,
I know that happened to me as well and not just on this distro.
Maybe it is bloating, altough it shoudnt, upgrad should (i think:)))9
just repöace existing apps. with newer versions.

I read something after long searching about prelinking. I'll try that and let you know.
Cherrs
F

---

### Post by rykel on 2005-03-23
fintan,

thanks bro!!

i am trying everyday to make my linux firefox run like mine in windows xp, whereby it's not draggy, and it doesn't take 5-6 secs just to drop down a website menu, and where the autoscroll/smooth scroll actually doesn't jerk the page!!

on the other hand, linux the operating system is blazing like hell. (ok, at least a brand new installed distro)


best regards,

rykel
singapore

---

### Post by Fintan on 2005-03-24
Hi rykel,

For FF:

First go Type about:config in the adress field you will then find a list odf stuff you can configure in Firefox:
Find the following lines and chanhe thier state to true by doubleclicking on them.
network.http.pipelining set to true
network.http.pipelining.maxrequests set to true
network.http.proxy.pipelining set to true

Then Change this line:
network.http.pipelining.maxrequests set to 2 to:
network.http.pipelining.maxrequests set to 100

Then rightclick on an empty space and go to new: Integer
and fill in the field with:
nglayout.initialpaint.delay and set the value to 0
That loads the pics faster.

The find:
network.dns.disableIPv6 -> Change the Value to true (Double click)

That should work.
At least it's a bit faster in loading pages. The app itself still takes time to laod.

I tried prelinking it owrks great.
This is how you do that:
Prelink is in universe. I use it on my Ubuntu system without issues, but do google about Prelink and do your research before trying it out.

How to enable prelink:

1. Activate Ubuntu universe sources. The procedure is well-documented by Ubuntu.
2. use apt-get or synaptic to install prelink.
3. Open /etc/default/prelink with your favorite editor, as sudo/root.
4. Change PRELINKING=unknown from unknown to yes.
5. Adjust the other options if you know what the heck you're doing. Defaults work well.
6. To start the first prelink (the longest one!), run sudo /etc/cron.daily/prelink

In the future, prelink performs a quick prelink (a less-than-1-minute procedure on most systems) daily, usually at midnight. Every 14 days, or whatever you changed it to be, a full prelink will run.

If you just did a major apt-get upgrade that changed systemwide libraries (i.e. libc6, glibc, major gnome/X libs, etc etc etc) and experience cryptic errors about libs, rerun step 6.

To undo prelink, change step 4 from yes to no, then rerun step 6.Prelink is in universe. I use it on my Ubuntu system without issues, but do google about Prelink and do your research before trying it out.

Or go to:
[http://www.ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://www.ubuntuforums.org/showthread.php?t=1971&highlight=prelink)

I hope this works for you. As for Upgrades, I don't know why it slows things down and nobody gives me a descent answer.

Cheers and enjoy

---

