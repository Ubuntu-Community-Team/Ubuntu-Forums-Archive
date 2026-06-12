---
title: "Firefox 89 - looking for the page actions menu."
date: 2021-06-03
forum: General Help
---

### Post by Dennis N on 2021-06-03
I have been looking for a while to locate what happened to the useful Firefox "Page Actions" menu that appeared at the right end of the address bar as three dots (see screenshot from previous Firefox version). It seems to have vanished and resists my efforts to locate. I just may not be seeing it. Does anyone know where this menu can be found? Thanks.

---

### Post by &amp;KyT$0P# on 2021-06-03
It has been removed in Firefox 89.

---

### Post by Dennis N on 2021-06-03
> **halogen2 said:**
> It has been removed in Firefox 89.

Well, that's unfortunate.:sad:
...... [ATTACH=CONFIG]288601[/ATTACH].......
*Page Actions Menu*

---

### Post by Frogs Hair on 2021-06-03
I have installed Firefox ESR from the mozilla ppa and the menu is included. Thanks for the tip about the snap package in a different thread , but I choose the ppa instead.

---

### Post by poorguy on 2021-06-03
Well about all I can say about **Firefox 89** is that it's different and gonna take a bit to get used to.

I had to disable **hardware acceleration** because it created issues with streaming Youtube videos.

It seems to work OK so I'll see how I like it the more I get use to using it and what it has to offer now.

---

### Post by Autodave on 2021-06-04
My FF just updated and I still have that menu......

---

### Post by Holger_Gehrke on 2021-06-04
Disabling 'browser.proton.enabled' in 'about:config' brought that menu back on my Firefox (which isn't the reason I did it; the changes to the look of the tabs were just too disruptive for me).

Holger

---

### Post by ajgreeny on 2021-06-04
> **Holger_Gehrke said:**
> Disabling 'browser.proton.enabled' in 'about:config' brought that menu back on my Firefox (which isn't the reason I did it; the changes to the look of the tabs were just too disruptive for me).

Holger
There have been many complaints about the FF 89 GUI and many ways already available to overcome at least some of those changes.
See [https://ubuntuforums.org/showthread.php?t=2463077&highlight=firefox+89](https://ubuntuforums.org/showthread.php?t=2463077&highlight=firefox+89)

I have a personalised userChrome.css file that I have edited to get the layout and GUI that I want, as shown in a screenshot in that thread, and which I have also now included here.
Disabling proton by toggling browser.proton.enabled in ***about:config*** will also get rid of a lot of whitespace in the menus and bookmarks that I use a lot from the bookmarks icon in the toolbar; with proton enabled none of the menus fitted on my screen height as there was so much wasted space between each line, very annoying.

I like my tabs right at the top of the window but using the css that I currently have, it is possible to move them to beneath the navigation bar or even to the very bottom of the screen, it's your choice, by simply removing the commenting (/*) from the appropriate line that you wish to use.

---

### Post by dddman on 2021-06-04
All this talk about ff89, I had to see it for myself.

Well it's different for sure and I was liking the shortcut screen, then I noticed...It took away my fat scroll bar.  I guess the css can be altered, but much easier just to run ESR.

ESR + LTS = Good stuff

---

### Post by ajgreeny on 2021-06-04
You should be able to get your scrollbar width back to something more usable, though still without the steppers at top and bottom, by editing your FF configuration in ***about:config***.

Find ***widget.non-native-theme.scrollbar.size*** and change the size, which was 12 on my system, to a larger size, 30 in my case.
It works for me; may do for you too!

EDIT:
I have just found that you can also get back the steppers at top and bottom of the scrollbar by finding and toggling ***widget.non-native-theme.gtk.scrollbar.allow-buttons*** from false to true.
Job done!

---

### Post by dddman on 2021-06-05
Thanks! 
Now I will keep both versions installed.

---

### Post by CharlesA on 2021-06-05
> **ajgreeny said:**
> There have been many complaints about the FF 89 GUI and many ways already available to overcome at least some of those changes.
See [https://ubuntuforums.org/showthread.php?t=2463077&highlight=firefox+89](https://ubuntuforums.org/showthread.php?t=2463077&highlight=firefox+89)

I have a personalised userChrome.css file that I have edited to get the layout and GUI that I want, as shown in a screenshot in that thread, and which I have also now included here.
Disabling proton by toggling browser.proton.enabled in ***about:config*** will also get rid of a lot of whitespace in the menus and bookmarks that I use a lot from the bookmarks icon in the toolbar; with proton enabled none of the menus fitted on my screen height as there was so much wasted space between each line, very annoying.

I like my tabs right at the top of the window but using the css that I currently have, it is possible to move them to beneath the navigation bar or even to the very bottom of the screen, it's your choice, by simply removing the commenting (/*) from the appropriate line that you wish to use.

Not to mention the about:config settings will be "removed in a later release." Just like they did with the fallback options for the last GUI change they did (massive ::focus URL bar, etc).

I do not like the lack of delimiters between my tabs, so I guess I'll be going the css route.

---

### Post by walts48 on 2021-06-05
> **Dennis N said:**
> I have been looking for a while to locate what happened to the useful Firefox "Page Actions" menu that appeared at the right end of the address bar as three dots (see screenshot from previous Firefox version). It seems to have vanished and resists my efforts to locate. I just may not be seeing it. Does anyone know where this menu can be found? Thanks.

What items did you use from the page actions menu?

Email Link and others are now in the Customize widget and can be added to a toolbar.

To copy a link just highlight it, right-click and Copy, or use the Ctrl+L, then Ctrl+C key combinations.

---

### Post by Dennis N on 2021-06-05
> What items did you use from the page actions menu?
All actions can be done using the 'old ways' that we used before this little menu even existed. So the removed actions menu is basically a convenience one got used to reaching for, and then it's gone.

A two step technique for copy the URL from the address bar is Alt+D followed by Ctrl+C.

---

### Post by TheFu on 2021-06-05
Had all sorts of issues with FF89 after patching this morning. 
Tabs wouldn't load, pages were empty, clicking links wouldn't click.

There were a number of conflicts with firejail - which isn't THAT odd.  Tried some different settings, had some crashes, and limited the virtual memory that it was claiming. I get tired of seeing 37G used in top.  Chromium is just as bad on the virtual memory.
Had to use the firejail PPA which has both the latest firejail and the updated firejail-profiles.
```
$ dpkg -l firejail*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  firejail       0.9.64.4-1~0 amd64        sandbox to restrict the applicati
ii  firejail-profi 0.9.64.4-1~0 all          profiles for the firejail applica

```

~/bin/firefox.sh 
```
#!/bin/bash
FJ_OPTS="--join-or-start=browserNormal --dns=172.22.22.80 \
         --rlimit-as=4096000000 --ignore=seccomp --ignore=protocol"
FF_OPTS="-no-remote "

# limit RAM VSS to 4G
PID=$(/usr/bin/firejail $FJ_OPTS /usr/bin/firefox $FF_OPTS )

```

FF only sees 4G address space.  I couldn't get the --name= firejail option working.  Having a namespace means when I forget that a file needed isn't available, I can push or grab it inside that jail. Without a name, that isn't possible.

Don't consider that script golden yet.  It has only been a few hours of stability.  Tabs open fine, no empty pages, links that click work - unless they are blocked by the local DNS server. We filter a bunch.

I hate the tabs across the top. Been using "Tree Style Tabs" for a very, very, long time. Can't live without it.  Puts tabs on the left side. Can "pin" some as just icons.  I do that for these forums, nextcloud, wallabag, darksky, and the pihole web-gui.

---

### Post by TheFu on 2021-06-05
> **walts48 said:**
>  
To copy a link just highlight it, right-click and Copy, or use the Ctrl+L, then Ctrl+C key combinations.

No need.

In X11, select with the left-mouse button, then paste into any text location in any window on the system using the middle-mouse button.  Select-paste has worked in X11 since before I started using Unix in the early 1990s.  No need to touch the keyboard to get text.  The xbuffer is great.

---

### Post by ajgreeny on 2021-06-05
I did not even realise until this thread appeared that there even was a Page Actions menu as I had never noticed it or used it.
I simply single-click in the addressbar and its content is highlighted immediately with no need to drag the cursor along its length.  I think I recall making that change somehow in the past as previously I used to drag the cursor to highlight the URL, but I can not remember how I made that change; it's far too long ago.  Having highlighted the URL with that single click I also use the middle mouse button to paste straight from the buffer; that is one of the useful things that I keep trying to do when I occasionally have to use Windows, and I have to remind myself that it doesn't work on that platform.

I am beginning to get the impression the Mozilla is moving in the same direction as gnome, ie, making it more and more difficult, if not impossible, to make changes to the GUI that the developers believe are not needed or wanted by users.

Are they wrong about that?  I think they are, perhaps more so for we Linux users who are so used to making GUI changes that we want and not being locked into whatever someone else decides is the "correct" way to do things.

---

### Post by TheFu on 2021-06-05
Single-click selects something.
Double-click selects a word.
Triple-click selects an entire line.

Middle-mouse button pastes.

Mozilla can screw with the selection sometimes, so I normally just triple-click for URLs. I dislike when programmers go OUT-OF-THEIR-WAY to defeat platform capabilities.  As an old X/Windows programmer, I know that the xbuffers and behavior is automatic. The program has to go out of its way to prevent it.

The magic of X11 for 30+ yrs.  Can't wait for Wayland to catch up.

---

### Post by dddman on 2021-06-06
I redid FF and now have ff89 plus ESR PPA installed.  Both were freshly installed.  I now have weirdness going on (on both).

[ATTACH=CONFIG]288616[/ATTACH]

---

### Post by poorguy on 2021-06-06
> **dddman said:**
> I redid FF and now have ff89 plus ESR PPA installed.  Both were freshly installed.  I now have weirdness going on (on both).


I've always heard that you could run one or the other but not both because one may conflict with the other.

---

### Post by &amp;KyT$0P# on 2021-06-06
> **TheFu said:**
> Having a namespace means when I forget that a file needed isn't available, I can push or grab it inside that jail. Without a name, that isn't possible.

:confused:
It's possible for me, I've always done this by pid of the main firejail process and I do it a lot.

---

### Post by dddman on 2021-06-06
> **poorguy said:**
> I've always heard that you could run one or the other but not both because one may conflict with the other.
I was reading that dual install is supported.

I now have two directories in /.mozilla.  FF and FF-ESR

I shall play with them today.  If they will not play nice, I'll nuke them both.

-------------_***EDIT***_------------
I am going to change this up.  Run FF snap package with ESR-PPA.  The original article that I read made no mention of using a snap package, but this makes sense.

---

### Post by TheFu on 2021-06-06
> **halogen2 said:**
> :confused:
It's possible for me, I've always done this by pid of the main firejail process and I do it a lot.

With **firejail --private** mode?

---

### Post by &amp;KyT$0P# on 2021-06-06
> **TheFu said:**
> With **firejail --private** mode?

I use [FONT=Courier New]--overlay-tmpfs[/FONT] .  But I just tested grabbing a file out of a nameless [FONT=Courier New]firejail --private bash[/FONT] sandbox, and my usual method works there too.

---

### Post by poorguy on 2021-06-06
> **dddman said:**
> I redid FF and now have ff89 plus ESR PPA  installed.  Both were freshly installed.  I now have weirdness going on  (on both).

[ATTACH=CONFIG]288616[/ATTACH]

> **poorguy said:**
> I've always heard that you could run one or the other but not both because one may conflict with the other.

> **dddman said:**
> I was reading that dual install is supported.

I now have two directories in /.mozilla.  FF and FF-ESR

I shall play with them today.  If they will not play nice, I'll nuke them both.

Perhaps so and I may be wrong about having 2 versions of Firefox installed running so yeah see what happens.

---

### Post by dddman on 2021-06-06
@poorguy
check my edit in post #22

---

### Post by TheFu on 2021-06-06
> **halogen2 said:**
> I use [FONT=Courier New]--overlay-tmpfs[/FONT] .  But I just tested grabbing a file out of a nameless [FONT=Courier New]firejail --private bash[/FONT] sandbox, and my usual method works there too.
Ah, manpage has this:
```
firejail {--ls | --get | --put} dir_or_filename
where 
--get=name|pid filename
              Get  a file from sandbox container, see FILE TRANSFER section
              for more details.

```
Their examples don't show using the PID. That confused me.
```
              $ firejail --get=mybrowser ~/Downloads/xpra-clipboard.png

              $ firejail   --put=mybrowser   xpra-clipboard.png   ~/Downloads/xpra-clipboard.png

```
That will be helpful next time I want to grab some broker statements.

Thanks for helping!

---

### Post by Frogs Hair on 2021-06-06
Running FF ESR for default and Nightly just to see what's upstream.

---

### Post by dddman on 2021-06-06
> **Frogs Hair said:**
> Running FF ESR for default and Nightly just to see what's upstream.

The FF snap pack solved it for me.  

Previous to the changes I made, I had firefox set up for all users and esr set up in home folder.  This works, but not with the ESR PPA which also sets up for all users.  I recently read about the PPA in another thread and wanted to install it.  So first try for everything.  By the way  the FF snaps pack works great, it's FF88 :D

---

