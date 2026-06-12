---
title: "Hardy, Firefox 3 &amp; Google Toolbar"
date: 2008-06-21
forum: General Help
---

### Post by Munk3y on 2008-06-21
Hey everyone,

I've seen a ton of threads on the forum about this but none I've found have a solution for me. The problem is that Google Toolbar shows "Downloading Bookmarks" forever. Back in Gutsy, the answer was just to install Libstdc++5 and disable/re-enable Google Toolbar. Well, that's not working for me here and I'm unable to find any answers. I've done "rm -rf .mozilla" with Firefox closed to reset Firefox and reinstalled Google Toolbar right away with no luck as well. The only clue I can find is that Firefox reports this in the Error Console:

```

Error: Cc['@google.com/toolbar/bookmark-wrapper;1'] is undefined
Source File: file:///home/monkey/.mozilla/firefox/lcygwos8.default/extensions/%7B3112ca9c-de6d-4884-a869-9855de68056c%7D/components/bootstrap.js -> file:///home/monkey/.mozilla/firefox/lcygwos8.default/extensions/%7B3112ca9c-de6d-4884-a869-9855de68056c%7D/lib/toolbar.js
Line: 150

```

I could use GMarks (Which is a nice addon BTW) or another option but the truth is that I like Google Toolbar and would love to start using it. Does anyone have an idea or at least a lead of what the problem could be? Here's some of my system info below, any help would be much appreciated.

-Ubuntu 8.04 (Hardy Heron) i386 - Fresh Install w/ALL Updates
-Verified that I meet the requirements of Google Toolbar listed [[COLOR="Red"]Here[/COLOR]](http://www.google.com/support/firefox/bin/answer.py?answer=53937&hl=en) (Except I use the Firefox that came with Hardy)

---

### Post by Munk3y on 2008-06-21
Forgot to mention that I am using Google Toolbar that's compatible with Firefox 3. It's version 3.1.20080605L.

---

### Post by shellmich on 2008-06-22
I can confirm the same problem. I created a launchpad bug entry (see: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/242153]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/242153")).

---

### Post by Munk3y on 2008-06-22
Good idea, thanks!

---

### Post by mhoney on 2008-06-25
I am having the same poblem.

---

### Post by jimv on 2008-06-25
Ditto.  I never used GoogleToolbar before, but I cannot make bookmarks.  The windows just doesn't do anything once I hit OK.

Perhaps a connectivity issue?

---

### Post by hoverX on 2008-06-26
same problem for me. Also,  Firefox would always crash when trying to open a 3rd window, after is uninstalled google toolbar the crashing problem stopped.

---

### Post by Munk3y on 2008-06-30
Absolutely no response on Launchpad. There's also a reply there implying that the Ubuntu devs don't really care about this issue and that they shouldn't support it. The type of response here so far has been no less than frustrating for something as simple as a Toolbar that works on every other platform I've tested it on.

---

### Post by webwzrd on 2008-07-01
Until this gets worked out. Here's an easy work around: [https://addons.mozilla.org/en-US/firefox/addon/2448](https://addons.mozilla.org/en-US/firefox/addon/2448)

---

### Post by bmatthew1 on 2008-07-01
I did the following to solve the Google Toolbar bookmarks - Firefox 3 issue.

In a terminal type...

```
sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6
```

Then reinstall Google toolbar.

I also posted the above information on [_launchpad_](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/242153) earlier this morning.

---

### Post by BeanBagKing on 2008-07-01
Confirm both the problem and the fix.

Also, confirm the problem with the 3 or more windows and FF crashes. The fix for the bookmarks doesn't seem to fix this, honestly not sure if it's related, but I don't remember having it before I installed the toolbar. Anyone know if this one has been reported to launchpad yet, or have a solution for it?

---

### Post by Munk3y on 2008-07-01
Bmatt, you rock. Thanks alot!

---

### Post by Jivicin on 2008-07-01
That didn't do it for me. ](*,)

When I ran that command I got:

```
sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++5 is already the newest version.
libstdc++6 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxul-dev: Depends: libmozjs-dev (>= 1.8.1.13+nobinonly-0ubuntu1) but it is not going to be installed
              Depends: libnspr4-dev but it is not going to be installed
              Depends: libnss3-dev but it is not going to be installed
E: Broken packages

```

No bueno.

---

### Post by Munk3y on 2008-07-01
It looks like you have some other issues going on there. I'm sure if you resolved those and managed to install the package, the fix would work for you.

---

### Post by bmatthew1 on 2008-07-02
Yeah Munk3y might be right Jivicin, try the following ...

```
sudo apt-get install libmozjs-dev libnspr4-dev libnss3-dev
```

Then enter this...

```
sudo apt-get install libxul-dev gcc-4.1
```

---

### Post by shellmich on 2008-07-03
bmatthew1 thanks a lot for this solution. I can confirm that it did work for me. I only made this small adjustment:

I only installed libxul-dev via the Synaptic Package Manager (I  installed also the depending packages Synaptic recommended e.g. libmozjs-dev, libnspr4-dev, libnss3-dev).

Afterwards I uninstalled the Google toolbar, restarted firefox, installed the Google toolbar again and after another restart the toolbar bookmarks feature worked as it should.

I dind't install libstdc++5 and libstdc++6 because they were already installed on my machine.

I didn't install gcc-4.1 because the newer version (gcc-4.2) was already installed. This newer version seem to be also OK for the toolbar bookmark feature working.

---

### Post by jmasondotnet on 2008-07-03
Thank you, Thank You, Thank You. I have been missing this feature for a while now. Your fix worked like a charm.

---

### Post by aBitLater on 2008-07-08
hello all,

I'm curious, are you all using the beta version 10 adobe flash player?

I reverted from 10 to 9 to fix vuze (azureus), and now my bookmarks are back in google toolbar...

If you install version 9 again, you may need to first delete the version 10 shared library /home/your_account/.mozilla/plugins/libflashplayer.so

If this works for you, please respond here so we can nail this down.

---

### Post by Jivicin on 2008-07-08
Alright, tried the latest and got:

```
sudo apt-get install libmozjs-dev libnspr4-dev libnss3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libnspr4-dev: Depends: libnspr4-0d (<= 4.7.1~beta2-0ubuntu1.1~) but 4.7.1+1.9-0ubuntu0.8.04.1 is to be installed
  libnss3-dev: Depends: libnss3-1d (< 3.12.0~beta3-0ubuntu1.1~) but 3.12.0.2+1.9-0ubuntu0.8.04.1 is to be installed
E: Broken packages

```

Is there something broken with package naming for this stuff?

I'm using Beta 10 for the flash player...

---

### Post by bmatthew1 on 2008-07-09
Okay, well as for the version of Flash I'm using it's v9.0 r124. I did have the newest beta version installed but I also use Opera which I don't believe is compatible with it.

Jivicin, I've got both of those files already installed. So I suggest you enter the following in a Terminal before you try to install the other libraries.

```
sudo apt-get install libnspr4-0d libnss3-1d
```

---

### Post by jroon on 2008-07-11
Shellmich's approach worked for me, although I uninstalled the toolbar first.  I then used Synaptic to install libxul-dev, and accepted the seven additional files that came with it. I reinstalled the toolbar and now I have bookmarks.

---

### Post by bgiannes on 2008-07-16
Thanx lots!

the "sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6" worked!

---

### Post by erythrocyte on 2008-07-18
> **bgiannes said:**
> Thanx lots!

the "sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6" worked!

I've noticed that of the above mentioned packages, only libstdc++6 need be installed in addition to libnspr4-dev and libmozjs-dev. Make sure to uninstall google toolbar before installing the packages and then go ahead and reinstall the toolbar.

---

### Post by fachex on 2008-07-27
Thanks a lot! It worked for me

---

### Post by zeddock on 2008-10-08
> **bmatthew1 said:**
> I did the following to solve the Google Toolbar bookmarks - Firefox 3 issue.

In a terminal type...

```
sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6
```

Then reinstall Google toolbar.

I also posted the above information on [_launchpad_](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/242153) earlier this morning.

In the end I got the latest beta of the bar and it seems to work great!
[http://www.google.com/tools/firefox/toolbar/FT5/intl/en/](http://www.google.com/tools/firefox/toolbar/FT5/intl/en/)

zeddock

---

### Post by Calculon64 on 2008-11-09
> **zeddock said:**
> In the end I got the latest beta of the bar and it seems to work great!
[http://www.google.com/tools/firefox/toolbar/FT5/intl/en/](http://www.google.com/tools/firefox/toolbar/FT5/intl/en/)

zeddock

W00t thx that worked on the first try thx :)

---

