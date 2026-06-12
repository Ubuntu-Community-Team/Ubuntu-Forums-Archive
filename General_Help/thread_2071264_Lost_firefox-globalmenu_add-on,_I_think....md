---
title: "Lost firefox-globalmenu add-on, I think..."
date: 2012-10-15
forum: General Help
---

### Post by JamesTheAwesomeDude on 2012-10-15
I use the Firefox Nightly build for my daily use, and it works fine, except for one little annoyance: the Menu Bar doesn't merge with the taskbar like it does in every single application in Ubuntu. (well, excepting those started by gksu, of course.)

If my problem doesn't quite make sense, here's a screenshot:
[IMG]http://i.imgur.com/Xogbs.png[/IMG]
see how the options File, Edit, View, etc., are not beautifully merged with the taskbar like they should be? Does anybody have any ideas on how to fix this?
My suspicion is that I lost the add-on that is supposed to do that, but I'm not quite sure whether that's the problem, or where to find the .xpi file. At askubuntu.com, [somebody had accidentally lost his Global Menu Bar Integration add-on]("http://askubuntu.com/questions/191260/i-lost-the-global-menu-bar-integration-firefox-addon"), but the only answer that had what I needed contained a dead link. [I asked about my problem]("http://askubuntu.com/questions/201105/firefox-nighty-19-0a1-doesnt-integrate-with-the-global-menu-bar-12-04"), but my question was too specific, and was locked. I now turn to you, the Ubuntu Forums, to see what you can do.

---

### Post by jokerdino on 2012-10-15
As I commented in your Ask Ubuntu question, use the PPA. 

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by JamesTheAwesomeDude on 2012-10-15
> **jokerdino said:**
> As I commented in your Ask Ubuntu question, use the PPA. 

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)Nope; didn't fix it. After I added the repository, I did _sudo apt-get update_ and _sudo apt-get upgrade_, but it just had a single update for Opera. NOTHING else.

---

### Post by jokerdino on 2012-10-15
Install firefox-trunk from the PPA and remove your Firefox installed from the tarball.

---

### Post by tupfzom on 2012-10-15
I have the same problem with Firefox 17. I installed Firefox from [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu). Is there anyone using an "unstable" Firefox version who does not have the problem?

---

### Post by jokerdino on 2012-10-16
Just installed firefox-trunk and I can confirm the issue. The global menu is broken and the global menu addon no longer shows up in the addon manager. Would have to file a bug report regarding this.

---

### Post by JamesTheAwesomeDude on 2012-10-16
Okay, so so far this bug is confirmed in the Nightly (version 19,) and Aurora. Correct?
I've confirmed that said bug doesn't appear in Beta, although, if anybody spots it, please let us know here.

P.S., Just curious: what are all the PPA's for the different Firefox release channels?
As far as I know, it's like so:

[LIST]
[*]Beta: [FONT=Courier New]ppa:mozillateam/firefox-next[/FONT]
[*]Aurora: [FONT=Courier New]ppa:ubuntu-mozilla-daily/firefox-aurora[/FONT]
[*]Nightly: [FONT=Courier New]ppa:ubuntu-mozilla-daily/ppa[/FONT] (comes bundled with Thunderbird Nightly/Daily)
[*][COLOR=DarkSlateGray](The stable build PPA has been abandoned. [{source}]("http://www.iloveubuntu.net/firefox-stable-ppa-abandoned-rapid-release-cycle-adopted-ubuntu-1004-and"))[/COLOR]
[/LIST]
Let me know if this is all correct, or if I have gotten something wrong.

---

### Post by tupfzom on 2012-10-17
I'm experiencing this problem with Beta (version 17) and Ubuntu 11.10.

---

### Post by tupfzom on 2012-10-30
There's still no change to the situation, is there?  (At least not for me.)

---

### Post by SantaFe on 2012-10-30
Have you looked in /usr/lib/firefox/extensions ?

I'm using Xfce, but every time I get Firefox updated through the Update Manager, it always updates Firefox-Globalmenu.  So I looked & found it there.  Just for fun I did copy the folder from there to my firefox profile in home/santafe/.mozilla/firefox/xoryqh45.default/extensions and started it and darned if it didn't pop up in my Add-Ons extension list.  

Hope that helps, hopefully it'll be in the same place. ;)

The reason I had to copy it to my home directory is I'm using a compiled Firefox, and wanted to make sure it saw it.

---

### Post by Frogs Hair on 2012-10-30
I had the same problem with Nightly and the Nasa Night Launch theme. The problem was resolved with an update. I know to get that theme to work on Nightly you have to force compatibility (not recommended) and so was not surprised when the problem occurred.

---

### Post by jokerdino on 2012-10-30
> **tupfzom said:**
> There's still no change to the situation, is there?  (At least not for me.)
The recent updates for Firefox Nightly has long fixed the problems for me. Make sure you are using the PPA and have also updated your computer.

---

### Post by tupfzom on 2012-11-08
> **jokerdino said:**
> The recent updates for Firefox Nightly has long fixed the problems for me. Make sure you are using the PPA and have also updated your computer.

Yes, the problem is gone. Everything back to normal!

---

### Post by JamesTheAwesomeDude on 2012-11-09
> **Frogs Hair said:**
> I had the same problem with Nightly and the Nasa Night Launch theme. The problem was resolved with an update. I know to get that theme to work on Nightly you have to force compatibility (not recommended) and so was not surprised when the problem occurred.
Well, the problem's fixed already, but I use the NASA Night Launch theme, too. It says that "This Add-on is not compatible with your version of Firefox," but the developer himself says that he tries to keep up with the Nightlies, and, in fact, encourages users to use it:
> **IMPORTANT NOTE - 2012-10-20**

AMO is stating "not available  for Firefox 19.0" -- referring to the latest Firefox nightly, meaning it  will presumably also state "not available for  Firefox 20.0" and so on  as nightly Firefox version numbers are bumped up -- but in fact we are  compatible with nightly builds, including Firefox 19.0.  I'm using NNL  with nightly Firefox for my everyday browsing, and if you're willing to  use work-in-progress versions of Firefox, which nightlies are, then you  can also use this theme with them.  Just ignore the "not available"  message and click on through to install.  

Thanks to everyone who, like me, is using NNL with nightlies and for reporting any problems you may find.I'm using that theme with the Nightly builds, but I have one last question: the tabs look too Windows-ish. Would it be possible for somebody to whip up some slightly more Ubuntu-ish tab sprites? I have a pretty good idea of how to customize themes on Linux, as I've done it on Windows...

---

### Post by tupfzom on 2012-11-10
Interesting, the problem returned after the last update (Firefox 17)...

---

### Post by JamesTheAwesomeDude on 2012-11-10
> **tupfzom said:**
> Interesting, the problem returned after the last update (Firefox 17)...
That's strange. I'm using the Nightly build, which is currently at 19.0a1, and I don't have that problem anymore.
Perhaps it was a version 17 issue that never got fixed, and now it's hitting the stable release channels. That would be strange, but perhaps possible.

---

### Post by tupfzom on 2012-11-11
> **JamesTheAwesomeDude said:**
> I'm using the Nightly build, which is currently at 19.0a1, and I don't have that problem anymore.
Perhaps it was a version 17 issue that never got fixed, and now it's hitting the stable release channels.

I'm using the Beta channel. There was an update yesterday (I believe) "within" version 17. Before the update, it worked, but now it doesn't.

---

### Post by JamesTheAwesomeDude on 2013-01-15
Ah-ha.

```
sudo apt-get install firefox-globalmenu
```
...and for Nightly:
```
sudo apt-get install firefox-trunk-globalmenu
```

---

