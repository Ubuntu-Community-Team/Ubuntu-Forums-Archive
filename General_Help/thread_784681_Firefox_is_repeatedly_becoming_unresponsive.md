---
title: "Firefox is repeatedly becoming unresponsive"
date: 2008-05-06
forum: General Help
---

### Post by rainwalker on 2008-05-06
It just started today; Almost any time I open a new window, close a tab, have a pop-up, etc, Firefox becomes unresponsive and the window dims to gray. Viewing and downloading stuff on Gnome-look has caused it (with screenshots in pop-up windows and the download window appearing), as well as simple navigating between pages. Clearing a download from the Download Statusbar caused it too. 
Basically, any time the window changes (I guess that's the best way I can describe what's happening) it freezes. After a few seconds it will come back, but it's still annoying, especially cause it keeps happening.
I've tried running ```
firefox
``` and ```
firefox jsconsole
``` but neither has told me what's causing this.

Any ideas? Again, this just started today and I haven't installed anything new.

PS - It froze very briefly after submitting this thread...

---

### Post by Pc_Madness on 2008-05-06
Gah! Its happening to me as well.  8.04 / FireFox 3.5 on a MacBook C2D.

Sometimes its a short freeze other times it actually fades to grey due to it being unresponsive.

:(

---

### Post by rainwalker on 2008-05-06
I'm running Hardy 8.04 with FF3b5 on an Inspiron 8600, Pentium M.

Did it just start happening to you today?

---

### Post by Vitaminc23456 on 2008-05-06
me too! i have no idea what to do, i tried to uninstall/reinstall and nothing.

---

### Post by edm1 on 2008-05-06
This has been happening to me since the hardy release but it didnt happen using the beta.

---

### Post by Pc_Madness on 2008-05-06
> **rainwalker said:**
> 
Did it just start happening to you today?

It happened to me acouple of times yesterday, but I had like 10 times while trying to get to this thread to make my original post. :p

Alright atm though.... very strange.

---

### Post by dchoi6 on 2008-05-06
Same thing happening to me. Just started today.
new Ubuntu user, 8.04 is the first I have tried.
Toshiba Satellite, dual boot with Vista.

---

### Post by sicofante on 2008-05-06
I just came here looking for a solution and found this thread. It freezes every few seconds for a few seconds here (I'm not using Compiz, so I don't get the grey window).

I've checked and keyboard input is working during the freezes. I can blindly click on the address bar and type a new URL and when it comes back, it'll write all the characters and go to the URL.

---

### Post by gearshifter on 2008-05-06
same problem here.  It gets unresponsive with even just one tab open.  I thought it was because of Flash but I am also have the problem on this site as well.

---

### Post by Parlay on 2008-05-06
I've got the same issue too.  I'm on Hardy with the firefox 3 beta 5.  It froze just while trying to view this thread.  Very annoying.  Any ideas?  I'm a bit too much of a noob to figure it out on my own.

---

### Post by Bigtime_Scrub on 2008-05-06
Same thing is happening to me. Sometime Firefox freezes and turn grey or black/white. I saw in another thread people talking about it happening to them. Someone said to uninstall Firefox and put Firefox 2 on it, they said it cleared it up for them.

---

### Post by Christopherius on 2008-05-06
I'm using Firefox 3 beta 5 and have the same problem with the gray screen and Firefox being unresponsive. I haven't been able to see a pattern at all.

---

### Post by esteckis on 2008-05-06
Here also, slows down and firefox window turns grey and my hard drive LED is lit up for a long tome, Now at times I start to lose the minimiz/maximize, close boxes on the right top.  This just started happening today.

Hardy Heron Firefox 3 Beta

---

### Post by underwater on 2008-05-06
Yeah the hard drive is thrashing I think because of some new bug with the sqlite part of firefox.  It is leaking or something and then writing and reading from disk a lot.

Hopefully there will be a fix soon.

---

### Post by rainwalker on 2008-05-07
Ok so it's good to know this is happening to lots of other people...but for some reason, it's fine for me now. Of course, as soon as I post this is will probably start happening again, but for now it *seems* to have cleared up...

---

### Post by barista on 2008-05-07
You should check what plugins you have, try running it in safe mode for a while.

I have lots of freezes on windows FF3b5, but haven't had one issue with FF3b5 on U804 and I really smack the heck out of it with multiple windows across desktops and 30 tabs in each.

I have about 10 addons. (the usual suspects). So it might be one particular addon.

---

### Post by pch0mey on 2008-05-07
A lot of HD activity here too for ff3b5 in Hardy Heron. I've had YouTube or other streaming videos go to grey and sometimes never recovery (and yes my sound does work fine).

---

### Post by Pc_Madness on 2008-05-07
Yeah, its cleared up for me. I had Pidgen freeze for a few seconds.  Had anyone else just turned on? I'd probably had my machine on for about an hour or so... so perhaps it will happen again tomorrow morning.

---

### Post by GregHunts on 2008-05-07
I had the same issues.  Repeated graying out of Firefox and non-response to mouse or keyboard activity.  The hanging was happening every 10 seconds or so regardless of whether I was trying to follow a link or just looking at a loaded page.

I run gkrellm and noticed a lot of disk activity while firefox was unresponsive.  What seems to have resolved the hanging for the last hour now was to close all firefox sessions and run firefox --profilemanager.  I renamed the default profile and created a new default profile.

I lost my bookmarks and saved passwords and the like but I didn't have enough of those for it to be an issue.  I performed an upgrade from 7.10 to 8.04 so I can only guess that there is some incompatibility between the old Firefox profile and the beta 5 Firefox.

Hope this helps.

---

### Post by pickboy87 on 2008-05-07
^^^^I'll have to give that a shot and see if it works. I've been having similar issues with Firefox 3 Beta 5. I didn't have a problem in the beginning, but recently it's been greying out and causing it to freeze for short periods of time (I've noticed it tries to load the whole image or sometimes page before it will show it).

---

### Post by asrai on 2008-05-07
There's a bug report here: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728") that might help.

It looks like there is a fix that has come through hardy-proposed otherwise this workaround worked for me:

go to firefox preferences/security and untick the options 'tell me if this site is a suspected forgery' and 'tell me if this site is suspected attack site'
shut firefox
rename or delete the urlclassifier files from your /home/.mozilla/firefox directory
restart firefox

Hope that is useful

---

### Post by GregHunts on 2008-05-07
That explains why creating a new profile resolved the issue for me and suggests that it will be a temporary fix.  After I've used Firefox long enough, (a couple of days maybe?), the urlclassifier.sqlite file will probably cause Firefox to start freezing again.  At least I'll know why it's happening.

I kind of hate to turn off those security settings as I have received warnings from them periodically when I check out links on emails in my Postini quarantine.  Hopefully it will be fixed in the next Beta.

---

### Post by asrai on 2008-05-07
With those 2 settings disabled in firefox my and deleted those files, the new urlclassifier file hasn't grown at all (and I changed it ages ago).  It looks like there is a fix in testing now though so shouldn't be too long to wait :)

---

### Post by NE Key on 2008-05-07
Similar problem.
Upgraded to Hardy yesterday. Today Firefox is "stalling" when switching between tabs and the hard drive is thrashing. Takes about 5 seconds to change tabs.

I have deleted the urlclassifier files and changed the settings for "this site is suspected forgery".

Result - immediate improvement. Changing tabs is instantaneous.

---

### Post by enoughsaid05 on 2008-05-07
Probably it is called beta for a reason?

Gee...I didn't know that firefox has bugs that slows the system down. I still think that no matter whether it is firefox 2 or 3, it is still quite resource hungry (though not as much as er hem...IE...)

So is thunderbird....

Or is it just my processor too slow. :P

---

### Post by sports fan Matt on 2008-05-07
Why is the urlclassifier file recreated everytime the browser starts?

---

### Post by rainwalker on 2008-05-07
The issue is totally gone for me now, and I didn't do anything...strange...

And yes, it is beta software, but it was still strange for it to randomly start freezing.

---

### Post by esteckis on 2008-05-08
Just a note, I do not think it is Firefox. Yesterday I totally removed Forefox 3 and installed Firefox 2.  Worked fine yesterdat, but just now I had 2 tabs open and the Firefox2 window greyed out and I had to force quit.  One thing that was strange is that when I clicked on my panel to close firefox, the close option was no where nere the firefox tab.

---

### Post by rainwalker on 2008-05-08
Alright, I lied, it's freezing again.
Whether it's that file causing it or not, that doesn't explain why this would randomly start happening...does it?

---

### Post by esteckis on 2008-05-09
What I find strange is, that all morning I have the computer on and no problem. In the evening is when the greying out of Firefox happens. See if your fine during the day but in the evening is when the trouble happens.  I wonder if the system has something scheduled at a preset time to do?

---

### Post by theBuggane on 2008-05-09
There is a deb available for Opera, so you can use that until final release of Firefox 3...

[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by esteckis on 2008-05-09
Opera is listed in the synaptics package manager if anyone wants it.

---

### Post by sicofante on 2008-05-09
It comes and goes here too. I was very happy for a few hours where it was working fine, then it went back to ill.

:confused:

---

### Post by owen_cook on 2008-05-11
Bit old now, but when I watch the cpu usage, it cycles from very low to 99% and that's the 'freeze' time.

No idea why, I suspect it is to do with java code, but will wait and see

---

### Post by Shazaam on 2008-05-11
Is everyone running desktop effects?
To make it stop turning grey=
ccsm>General Options>Ping delay
Make it longer and see what happens. It will not resolve the freezing problem though.

[http://ubuntuforums.org/showthread.php?t=722155](http://ubuntuforums.org/showthread.php?t=722155)
I have the opposite problem. FF2 greys out, FF3 doesn't.

---

### Post by jmagsho on 2008-05-11
I suppose you could always uninstall FF 3 B5 and then install FF 2.x.  I have seen the phenomenon described in this post myself and the cpu spikes, but I am running a higher end P4 machine with 4 GB of ram so while it is annoying it doesn't kill my system.

I just installed Opera 9.50b.  Will see how that goes.

---

### Post by Blinkiz on 2008-05-12
Oh, seems like am having the same problem. But my complete ubuntu freezes for a couple of seconds. The clock stops in Gnome!

Everyone that has this problem, please visit [http://www.armada.nu](http://www.armada.nu) and say if your browser freezes when you click on the links. I can ALWAYS reproduce my error by going to this site. Firefox 3.0 b5 ALWAYS freezes and taking my ubuntu with it.

---

### Post by Coplen on 2008-05-12
> **Blinkiz said:**
> 

Everyone that has this problem, please visit [http://www.armada.nu](http://www.armada.nu) and say if your browser freezes when you click on the links. I can ALWAYS reproduce my error by going to this site. Firefox 3.0 b5 ALWAYS freezes and taking my ubuntu with it.

Nothing here.

---

### Post by quanumphaze on 2008-05-14
Using both Swiftweasel 3b4.5 and Firefox 3b5, both have this same problem.

The freezing comes and goes and it happens frequently when the CPU is at 100% use by the browser. (I'm using Htop, background CPU is red which is at 100% and the browser is between 20 and 99% of that (green))

This also has effect on Amarok when Firefox is at 100% CPU. Amarok stops responding and won't load up the next track, however it will continue playing the remainder of the current track.

Other observations are when I am using a Flash video page and it goes 100% CPU the video just *pauses*, the buttons still work on the Flash applet and it can skip to different parts of the video and then plays for 2 sec before pausing again, the browser is still responding and using 100% CPU at this time. It seems like Firefox is screwing over Flash for once ;).

---

### Post by engstrom on 2008-05-26
I did a clean install of Hardy complete with FF3.5b. I've had trouble with the greying out and freezing so I uninstalled 3.5b and installed FF2. I still have the freezing and greying. I also have intermittent freezing while booting (some have taken 30 mins) so I'm not sure it even directly FF-related for me, it might just be a symptom of something else...

---

### Post by drfrog on 2008-09-19
setting the ping in compiz to 30000ms seems to do the trick , i was experiencing grey outs in ff as well as pidgin, 


does anyone know how to disable the ping rate?

---

### Post by efittery on 2008-09-28
> **Parlay said:**
> I've got the same issue too.  I'm on Hardy with the firefox 3 beta 5.  It froze just while trying to view this thread.  Very annoying.  Any ideas?  I'm a bit too much of a noob to figure it out on my own.

I finally got fed up with this problem and installed the web browser "Opera".  Opera has its own set of problems.  As an example, I can't view YouTube movies.

Anyhow, I have been using "Opera" for about 2 days and the problems of a greying screen have gone away.  I am using Opera right now to write this.

I frankly feel that "firefox 3 beta 5" is the problem.  I used Firefox for years and this is the first time it has been buggy.  Has anybody migrated backwards to earlier releases of firefox to determine when the problem started occurring?

Actually I was using the web browser Mozilla back in 1995.

---

### Post by saunders on 2008-09-29
Same issue here...I have the latest FF3 from the repositories on Hardy, and it's constantly greying out. It even greys out temporarily when I open the Ubuntuforums site. It's been this way for the last 3 weeks or so.

This shouldn't be happening. I've got 1.5Gb RAM, there's only FF3 running with a single tab. I even only have 1 add-on in FF, so it's not due to those.

Opera works fine for me, as does Epiphany. I'm off Firefox until this gets fixed, or until the problem gets identified.

---

### Post by Excalibre on 2008-09-29
> **efittery said:**
> Actually I was using the web browser Mozilla back in 1995.
That's pretty amazing, given how it didn't exist back then.

---

### Post by jf812 on 2008-09-29
Try right clicking on desktop, change desktop background, go to visual effects tab and select None. It worked for me.

---

### Post by clarknova on 2008-10-05
```
sudo apt-get install flashplugin-nonfree
```
I carried my firefox profile over onto a new install and started getting these freezes. Starting FF from the terminal revealed that it was searching for and not finding npviewer.bin and nspluginwrapper. That's when I remembered that I hadn't yet installed flash on the new machine, but somehow my profile was expecting to find the flash binaries and thus causing the freezes. I just installed flash player and the freezing is gone.

Hope this helps some.

db

---

### Post by Bèrke on 2009-12-15
Even though this thread is relatively old, I'm experiencing the same problem in U9.10 (firefox 3.5.5) since a couple of days. Ubuntu runs fine untill firefox is loaded and then the entire system (especially firefox) gets unresponsive (will work from time to time).
However, the previous workaround apparantly still works (for me at least). Remove or rename the urlclassifier file (\home\user\.mozilla\firefox\v62wmdri.default) and restart firefox.

---

### Post by duanedesign on 2009-12-16
moving, renaming or deleting ~/.mozilla/firefox/v62wmdri.default (or whatever your profile is called) folder will certainly remove any corrupted Firefox profiles and thus solve many common issues. However you should consider that the ~/.mozilla folder is also the place where Mozilla Settings like bookmarks and history, and applications like Sunbird keep there settings. So removing this folder will also remove their settings.

There is another way to fix a corrupted profile. The Firefox Profile Manager. Open a Terminal (Applications > Accesories > Terminal) and issue the following command.

```
firefox -P
```

Then bookmarks and history can be brought into the new profile (Bookmarks > Organize bookmarks > Import and Backup > Restore) Be careful copying stuff over from the old profile. Most Firefox problems are caused by a single profile file and you dont want that in your new profile. You can slowly start adding your Plugins and History one at a time, use the computer for awhile, and see if the problem comes back. If it does you have narrowed it down to the last thing you added to the New Profile.

---

