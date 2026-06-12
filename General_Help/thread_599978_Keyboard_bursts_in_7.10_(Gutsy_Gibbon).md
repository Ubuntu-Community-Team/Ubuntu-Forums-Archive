---
title: "Keyboard bursts in 7.10 (Gutsy Gibbon)"
date: 2007-11-01
forum: General Help
---

### Post by spamgoat on 2007-11-01
This thread was reposted. Please follow [the new thread]("http://ubuntuforums.org/showthread.php?p=4824777") instead.

.
.
.
.
.
.
.
.
.
.
.
.
.
-EDIT, PLEASE READ-

There is no fix for this problem as of yet, but the bug has officially been confirmed for Feisty, Gutsy and Hardy now. One way to make this behaviour stop is to disable key repeating altogether in the keyboard settings, but this would obviously have to be a short-term solution. Increasing the repeat delay seems to improve the situation somewhat for most users.

This bug is confirmed for many system setups, including both AMD and Intel, ATI and Nvidia, open- and closed-source video drivers, compiz enabled and disabled.

The official bug report on Launchpad for this bug can be found [on number 124406]("https://bugs.launchpad.net/ubuntu/+bug/124406")

As a final note, there seemed to have been numerous similar bug reports going around at the same time -- with different causes. Please see if [this Launchpad issue (#194214)]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194214") is yours, rather than the one discussed here, as a fix has been released for it.

Finally, I would like to recommend everyone still stuck with this bug to keep an eye on [the launchpad page]("https://bugs.launchpad.net/ubuntu/+bug/124406") as that seems to be the centre of discussion at this time. I shall keep everyone updated through this thread as well (with replies and edits), so feel free to bookmark this thread as well.

I hope to have informed you enough for now,

original post follows:
-----
Hey,

Lately, and more specifically from the day i've upgraded Ubuntu from Feisty to Gutsy, my keyboard (laptop keyboard, Dell Inspiron 9300, US International with Dead Keys) has been unpredictably crazy in Ubuntu. I find it somewhat hard to explain what exactly is going on, but i'll do my best. My keyboard, at random as far as I can tell, sometimes starts bursting out keys. This means that when I press the F3 key on my keyboard it doesn't just process a single F3 press, but between 20 and 80 of them. I first noticed this while running Firefox. My shortcut key for opening a new tab is F1, and at times when I press F1 not one but about 60 tabs open (nearly crashing Firefox in the process). At first I assumed this was a firefox extension bug, so I disabled all my extensions. However, it still did the same when using CTRL+T. I then figured it'd be firefox-related, but when the same thing happened when I pressed ALT+<TAB> to switch windows (it froze in the alt+tab window in compiz-fusion, switching between windows like crazy for a good 6 or so seconds) I figured it'd have to be ubuntu (driver?) related.

Now, this does not happen all the time. I'd say about once every 15 minutes (how often does one open a new tab though?). Also, it seems to happen only with F-keys and ALT/CTRL+<letter>, as i've yet to have it go crazy while chatting (on Pidgin).

This seems a rather serious bug, but so far I have the feeling i'm the only one in the world experiencing this. I cannot find any bug reports on this specific issue (there's numerous reports on keyboards being unresponsive, but those are probably the exact opposite of what i'm having). Therefore, if you have or had the same problem i'm having, please do reply even if it's just to say "me too".

I hope I have provided enough information on what's going on, and explained it well enough for others to understand. If any more information is required from my end, please do just let me know by replying.

Thanks for reading,
spamgoat

--------

More information...

(Possible) duplicate reports on ubuntuforums: [432057]("http://ubuntuforums.org/showthread.php?t=432057"), [663309]("http://ubuntuforums.org/showthread.php?t=663309"), [95466]("http://ubuntuforums.org/showthread.php?t=95466"), [609047]("http://ubuntuforums.org/showthread.php?t=609047"), [366888]("http://ubuntuforums.org/showthread.php?t=366888"), [231645]("http://ubuntuforums.org/showthread.php?t=231645"), [602876]("http://ubuntuforums.org/showthread.php?t=602876"), [601375]("http://ubuntuforums.org/showthread.php?t=601375"), [566216]("http://ubuntuforums.org/showthread.php?t=566216"), [467012]("http://ubuntuforums.org/showthread.php?t=467012"), [315872]("http://ubuntuforums.org/showthread.php?t=315872"), [170518]("http://ubuntuforums.org/showthread.php?t=170518"), [54171]("http://ubuntuforums.org/showthread.php?t=54171"), [689140]("http://ubuntuforums.org/showthread.php?t=689140").
(Possible) reports of bug on launchpad: [39315]("https://bugs.launchpad.net/ubuntu/+bug/39315"), [124406]("https://bugs.launchpad.net/ubuntu/+bug/124406"), [65249]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/65249"), [63024]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024"), [153024]("https://bugs.launchpad.net/ubuntu/+bug/153024").

Anything missing?

---

### Post by spamgoat on 2007-11-01
It just happened to me in gedit as well (on the backspace key, long live ctrl+z/undo or i'd have lost parts of my website). And, more interestingly, I think my mouse just did it as well but i'm not 100% sure on that.

---

### Post by linguini on 2007-11-02
The same here. It happens quite often in Firefox (ctrl-t), while switching desktops (alt-ctrl-left/right arrow), and while pressing PageDown in Kile and Adobe Reader. I think it also happened with the delete key in Thunderbird, and on a few other occasions with other keys, but this is much less common.

---

### Post by spamgoat on 2007-11-02
I thought I'd add it just for the first time happened to me on Pidgin as well, I was trying to type Bible and "biiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii" is how it started. So it doesn't seem to be special-characters exclusive, just a lot more common.

Also, i'm both glad and sad to hear i'm not the only one suffering from this horribly annoying bug, linguini.

---

### Post by Yv12345vY on 2007-11-02
I've seen this issue on my Alienware Sentia starting back with Ubuntu 6.06.  I know my laptop has some weird hardware, that's probably why.

---

### Post by deformation on 2007-11-02
Happens here too, plus as an extra, sometimes the keyboard refuses to type any letter in FF,gedit,pidgin..etc


bug?

---

### Post by spamgoat on 2007-11-06
Because i'm about to switch OS because of this, i'd rudely like to *bump*

---

### Post by therealbrewer on 2007-11-08
Same problem here.

---

### Post by spamgoat on 2007-11-10
The bug seems to have been reported numerous times outside this thread now, most notably [here]("http://ubuntuforums.org/showthread.php?t=601375"), [here]("http://ubuntuforums.org/showthread.php?t=602876"), [here]("http://ubuntuforums.org/showthread.php?t=602876"), [here]("http://ubuntuforums.org/showthread.php?t=231645"), and [here]("http://ubuntuforums.org/showthread.php?p=3743021").

---

### Post by Kralizec on 2007-11-11
I have to say I'm experiencing the same problem, and have been for a while (since fiesty). I do have to say that my problem seems to be confined to when Firefox is the active window. Specifically annoying are when I open many tabs at once, which is commonly reported, and even more serious when i close many tabs (usually every single one I have open) and then I must resort to going into History->Recently Closed Tabs-> and clicking every single tab individually, which is really troublesome when I have on average 5 or so tabs open. Also, I have trouble with application switching in general, not just alt+tab, but the extra CompizFusion switchers too.

All these problems occur only in Firefox/when Firefox is the active window.

---

### Post by Kralizec on 2007-11-14
I've had key-repeating turned off for a while now (its disorienting not being able to scroll with the arrow keys, or to delete a whole line by holding backspace down) and I've noticed something:

Unmentioned before was the fact that before spazzing out and simulating a held key, there would be a slight pause before the task began (i.e. with the application switcher, it would freeze briefly at the first application, and then start moving rapidly through all my open applications). I've noticed that this pause still occurs even with the repeating keys off, although the repeating keys phenomenon doesn't actually occur.

In summary, I think the problem is a combination of repeating keys + some other unknown factor.

---

### Post by spamgoat on 2007-11-14
I decided to dig a bit deeper into the problem, and found some more references to the problem on launchpad and ubuntuforums:

[Here]("http://ubuntuforums.org/showthread.php?t=432057") is a thread describing the same problem, dating back to May 3rd of 2007. 

Further, it can be found in some form or another on launchpad:

[Here]("https://bugs.launchpad.net/ubuntu/+bug/39315") it is reported and set to "fix released", a long long time ago.
[Here]("https://bugs.launchpad.net/ubuntu/+bug/124406") it is reported and set to "Confirmed", but with no action as of yet.
[Here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/65249") is another bug report, status "Incomplete", refering to the first bug report correctly stating the bug was not fixed.
[Here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024") is a very old report of seemingly the same bug, on Ubuntu 6.06LTS Dapper Drake, and a very old kernel. Yet to be fixed.

---

### Post by Kralizec on 2007-11-17
I may have discovered something.

How many (if any) Firefox tabs does everyone have open when this happens to them? I've just noticed that the more tabs I have open (currently six) the more likely it is to happen to me. This makes me think its a processing issue, since I know Firefox uses a lot of processor space and the amount it uses increases with the number of tabs open.

---

### Post by darthbith on 2007-11-22
I'm having the same problem, and it does seem mostly to do with Firefox. The number of tabs open doesn't seem to make a difference (it just happened to me with 3 tabs open). Other keys I've had this problem with:
CTRL+W to close tabs
'j' and 'k' when reading feeds in Google reader
Arrow keys when scrolling on pages
I'd been using Gutsy for a few weeks (since it came out) before this started happening - or at least, i started noticing it only today.

For anyone who has the problem of too many tabs closing, CTRL+SHIFT+T opens recently closed tabs (and if this bug starts happening, it might reopen all your tabs again :-D)

---

### Post by Kralizec on 2007-11-22
Thanks for the CTRL+SHIFT+T thing, I'd been wasting my time going into History->Recently Closed Tabs.

---

### Post by euchrid on 2007-11-23
Don't know if this is useful just to get people thinking, but I'm pretty convinced that Firefox and Java do something weird together; sometimes I get 100% CPU usage as soon as I'm on a page that over-uses Java, and many months ago, I had a lot of problems with X or Gnome suddenly dying. 

Thankfully, that's been resolved, but sometimes windows seem to stick, or the system goes slow - and ONLY when Firefox is running (which it usually is). I still have an unfounded suspicion that Java does something weird to the system, but I'm sure a smarter person than me can advise a way to explore that... 

This key repeating thing seems a kind of similar behaviour- as if something is interfering with Ubuntu's normal behaviour rather than there being anything wrong with Ubuntu itself... Sorry if this wasn't useful, just thought it was worth looking into!

---

### Post by flukierdonut on 2007-11-27
I've been having these problems as well.. the multiple tabs in FF seems to be the worst.. sometimes my compiz cube spins around really fast, kinda gets dizzying. I'm using Gutsy on a HP dv8000 series laptop. Feisty didn't do this to me back when I had it.

---

### Post by Kralizec on 2007-11-27
I, too, have the problem with the dizzily spinning Compiz cube, although it doesn't happen often. Am I the only one who experienced this problem in Feisty?

---

### Post by sistoviejo on 2007-11-27
I am experiencing it in gutsy in my laptop. I also experienced it in Feisty.
It happens only on my laptop but not on my desktop computer.
It's an HP Pavilion TX1000 series (TX1215nr).

---

### Post by Kralizec on 2007-11-27
I suppose I should add something that everyone else has contributed...dunno why I didn't before.
My laptop is a **Gateway MX6446**.
And in case it matters, which I suppose it could, I'm running an **AMD Athlon 64 processor** with an **ATI Radeon Xpress 1100 video card**.

---

### Post by sistoviejo on 2007-11-27
> **Kralizec said:**
> I suppose I should add something that everyone else has contributed...dunno why I didn't before.
My laptop is a **Gateway MX6446**.
And in case it matters, which I suppose it could, I'm running an **AMD Athlon 64 processor** with an **ATI Radeon Xpress 1100 video card**.

I am also running on an AMD processor (turion 64 dual core).
My VGA is an nvidia geforce go 6150.
My other desktop (intel celeron) doesn't have this problem.

---

### Post by Kralizec on 2007-11-27
So now our best clue is that it has to do with Firefox (maybe) on an AMD 64 processor...
Don't really know much about OS integration with the processor, but in case its important, although I have a 64-bit processor I'm still running a 32-bit version of Ubuntu.
I'm planning on getting a new computer soon so I may be able to test it to see if this problem crops up; it, too, will have an AMD 64 processor.

---

### Post by stylishpants on 2007-11-27
I can provide a counterexample.

I see this problem frequently on my work computer, running a 2.4 GHz Celeron.  My home machine, which is an AMD64, doesn't have the problem.  Both machine are running up-to-date 32 bit Gutsy.

I can also confirm that the problem was not fixed by today's firefox update.

---

### Post by Kralizec on 2007-11-27
It seems as if the number of those suffering from this malady is growing; perhaps if enough people begin reporting it something will actually be done.

Something else that might be influencing: how many of you guys upgraded from Feisty to Gutsy and how many did a fresh install of Gutsy? I upgraded; I'm thinking maybe something happened during the upgrade...?

---

### Post by blu3ness on 2007-11-27
confirmed problem for feisty, still looking for a fix.

---

### Post by sistoviejo on 2007-11-28
I did a fresh install, of the 64 bit version of gutsy.

---

### Post by Kralizec on 2007-11-28
So what do we know...and please correct me if I'm wrong or have missed something.

It occurs mostly with Firefox, although sometimes with Compiz.
It occurs mostly (totally?) on 64-bit processors.

Right?

---

### Post by stylishpants on 2007-11-28
It does not occur only on 64 bit processors.  Mine occurs on a 32-bit Celeron.  
Firefox seems to be the culprit.  No Compiz involved though, for me.  
My system has been upgraded through several Ubuntu releases, not clean installed.

Here's another theory: What about firefox extensions?  I have the following firefox extensions installed:

Better Gmail
Chromatabs
Download Statusbar
Password Exporter
Ubufox

In particular I wonder if the Better Gmail extension is at fault.  I have two computers running gutsy, both fully up-to-date with patches, and I only see this problem on the system with Better Gmail.  Furthermore, the Better Gmail extension provides some special keyboard shortcut functionality which I have fully enabled.  (Tools->Better Gmail->General/Macros Keyboard Shortcuts)

Anybody else using Better Gmail?

---

### Post by Kralizec on 2007-11-28
Not I :-| Actually, the only extension I see that we have in common is Ubufox.

Here's my extension list:
[LIST]
[*]AdBlock Plus
[*]Download Helper (problem was occurring before installing this)
[*]FireTray
[*]Image Zoom
[*]mplayerplug-in
[*]Splash
[*]StumbleUpon
[*]Stylish
[*]WeatherBug
[*]Yahoo! Mail Notifier
[/LIST]

Another thing; here's my plugin list:

[LIST]
[*]Adobe Reader 8
[*]mplayerplug-in (all extensions)
[*]Shockwave Flash
[*]Java 6
[/LIST]

---

### Post by sistoviejo on 2007-11-28
> **Kralizec said:**
> So what do we know...and please correct me if I'm wrong or have missed something.

It occurs mostly with Firefox, although sometimes with Compiz.
It occurs mostly (totally?) on 64-bit processors.

Right?

I think it would be more accurate to say that it happens when you have a high cpu load.
It happened to me sometimes on X using a terminal window without having firefox open.

---

### Post by Kralizec on 2007-11-28
Okay, I'll concede to that. So any ideas on what to do next?

---

### Post by spamgoat on 2007-11-28
My current theory is that it has something to do with CPU scaling. Ubuntu downscales the CPU whenever there's little to no activity (on my laptop at least), and upscales again once it notices activity. It could perhaps be that during these down-/upscales (especially the upscales) things get registered multiple times because speed is suddenly set to 3 times what it was half a second ago. I'm of course merely guessing, so someone with more technical know-how can hopefully either confirm or shoot down this theory. 

Also, based on the thread replies so far it does happen mostly in Gutsy (but also in Feisty), mostly on laptops (but also on desktops), on both 64 and 32 bit (intel AND amd), mostly on Firefox (but definitely also on other applications) and it happens to both fresh installs and upgrades. So no clues there, sadly.

Is there anyone who does not have the CPU scale feature enabled but still has this problem?

---

### Post by sistoviejo on 2007-11-29
Now that you bring the subject into the table... I've been having problems with cpu scaling. It doesn't work when I disconnect the ac adapter. The speed stays fixed at 88% no matter what governor I use. I can't confirm whether I had the keyboard bursts problem or not while using battery power.

When I use the AC adapter cpu scaling works fine but I tend to set it to the performance governor which leaves the CPU at full speed. I can confirm that I have had keyboard bursts even on the performance governor.

I posted a message on an existing bug report in launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/65249") a while back.
I'm not sure what we should do next. Maybe we should look for other bug reports?
Surely this is a high priority issue for us people having the problem and we should try to attract the developers attention.

---

### Post by emwine on 2007-11-29
I was going nuts with keyboard problems, living in hell because of it for months.

Keys would sometimes stick, the worst offenders being SHIFT, CTRL, or ALT.  Invariably, when I had keyboard issues, I'd be randomly hitting those keys to "unstick" whichever of them was causing grief.  Additionally, I had unknown keypress or keycode issues spamming the logs (dmesg | tail, you either have the problem or you don't)

In my case it was a hardware problem, or more specifically, some kind of PS/2 gook generated by my wireless MS keyboard that Ubuntu didn't handle right.  I went back to an old MS Natural keyboard, the HEAVY original one from way back, and my keyboard troubles are over.  This is probably worth a bug report somewhere that the keycodes for "Microsoft Wireless Photo Keyboard" (and probably lots of others as evidenced by the rest of this thread and others) are not handled completely by something-- not sure if it's Ubuntu, the kernel, or what that should be doing this.  I think the package was something like Photo Keyboard 4000, if that matters.

I was also on a KVM switch and still had some minor keyboard issues after replacing the keyboard, so I removed that as well.  But the wireless keyboard was the main culprit.  Anyway, it's been great ever since I reverted keyboards, though I miss having handy multimedia keys.

---

### Post by Kralizec on 2007-11-29
spamgoat and sistoviejo, tell me more about this CPU scaling (how do I configure/check configuration of it?) I'm not familiar with the term and am interested in contributing my data to this newest theory.
In addition to this, a while ago sistoviejo posted that it occurs when there is a high CPU load...I have to say that ironically nearly as soon as I read that post, I experienced the problem with approximately 20% CPU load, so that theory may be out, at least for me.

Also, in response to what emwine posted about the keyboard problem, I have to say that I rarely, if ever, use external keyboards/mice; typically I only use the built-in ones on my laptop.

---

### Post by sistoviejo on 2007-11-29
Here's the man page for cpufreq-selector which allows you to change cpu frequency or governor:
[http://www.linuxcertif.com/man/1/cpufreq-selector/](http://www.linuxcertif.com/man/1/cpufreq-selector/)
Here's my thread asking for help about my cpu scaling issue:
[http://ubuntuforums.org/showthread.php?t=600188](http://ubuntuforums.org/showthread.php?t=600188)
I haven't had the time to try the last suggestion that was made. It might help solve my issues. I will try it when I have time.
Please ask anything else you want to know.

> ...I experienced the problem with approximately 20% CPU load, so that theory may be out, at least for me.

Correct me if I'm wrong... I think 20% cpu load might be a little bit high in linux. 

> In my case it was a hardware problem, or more specifically, some kind of PS/2 gook generated by my wireless MS keyboard that Ubuntu didn't handle right.
> ...I have to say that I rarely, if ever, use external keyboards/mice; typically I only use the built-in ones on my laptop.


Maybe it has something to do with non standard keyboards? (usb and/or multimedia keyboards)
I don't know what kind of keyboards are built into laptops.

---

### Post by doorknob60 on 2007-12-06
That sometimes happens to me, but only repeats it like 3-6 times not 80 :P I'd like to know why it happens though.

---

### Post by iris-n on 2007-12-06
Well, could be a naïve shot, but in my latpop I corrected it just by going in (yes, GUI) System->Preferences->Keyboard and changing the speed or unmarking repetition keys =)

---

### Post by sistoviejo on 2007-12-06
@iris-n
That is an option. We could learn to live without key repetitions.
I think a better idea would be to solve the problem instead of getting rid of the feature.
We should keep trying until we fix it.

---

### Post by iris-n on 2007-12-06
Of course it should. But in the meanwhile it's useful to have a nice keyboard.
And, in my laptop just slowing down actually solved it, I have key repetition enabled.

---

### Post by sistoviejo on 2007-12-08
I already tried that and can't get used to it so it's not a solution for me.
I use fast repeating keys for scrolling through text a lot. I am using windows a lot more often because of this and another problem (I can't configure cpufreq-selector correctly while using battery). 

Still this problem doesn't happen on my desktop computer for some reason.
It's an Intel Celeron 2.4Ghz with 512 MB of memory.

Another problem that I have when typing sometimes is that the keys have a little lag to appear on screen. This problem is also also very annoying. It's even more annoying when playing games because key presses will take some time to register on the game also.
:(

---

### Post by torstenaf on 2008-01-01
I'm experiencing the multiple key presses on my laptop, a Sony VGN-S505P/B (Intel Pentium M 1.86GHz).

The primary application I see it in is Firefox. I've installed the "Undo Closed Tabs Button" add-on which allows me to re-open tabs, since using ctrl-w will spontaneously close many tabs.

I use the laptop primarily connected to AC power. There is a slight pause or sluggishness when it appears the frequency selector is bumping up the speed, and this corresponds with the unwanted multiple keypresses events.

My CPU scaler reports it is always running at the full 1.86GHz. I suspect it is not reporting correctly. Based on previous experience [http://www.ubuntu-forums.net/showthread.php?t=539365&highlight=sony+laptop+hot&page=3](http://www.ubuntu-forums.net/showthread.php?t=539365&highlight=sony+laptop+hot&page=3)
I would expect my laptop to be burning hot all the time, but it is not. It is running cool. However, it could be correct.

I'm at a loss as to how to proceed.

torstenaf

---

### Post by tbook on 2008-01-07
For what it's worth, I am having the same problem.  It doesn't seem restricted to firefox, but it is also on a laptop (AMD Sempron), and is associated with strange mouse behavior - the mouse cursor sometimes flies around the screen as though the acceleration were all off.  For me, this all began when I upgraded to gutsy.  A reinstall didn't solve the problem, either, although it appears a bit better.

---

### Post by spamgoat on 2008-01-13
According to semi-recent posts [here]("https://bugs.launchpad.net/ubuntu/+bug/39315") the solution to the problem would be upgrading the kernel to 2.6.23.

I, for one, am running kernel 2.6.22-14-generic (retrieved with 'uname -r'). Is there anyone currently experiencing this problem on the most recent kernel (2.6.23)? Also, what kernel versions are the rest of you running?

Also, who feels like finding out whether the new kernel fixes things? :)

---

### Post by Mad_Max_1412 on 2008-01-14
Guys,

I'm using a KVM switch on my Ubuntu and Windows boxes. The keyboard and mouse is a wireless Logitech version.

I am having no problems with the keyboard in Windows, but in Ubuntu 7.10, I find that on many occasions when I press a key I either get 2 entries or sometimes it continues to register the keystroke until I press another key such as backspace.

Last night it caused a problem which was a pain in the proverbial. I was renaming a folder full of digital files and occasionally I think it was when I pressed enter after entering the new name that Ubuntu kept registering the "Enter" key thus causing it to open multiple (and I mean a heck of a lot) of image viewing windows of the photo. The windows kept trying to open until it got to the point where the computer stopped responding (or was too busy still opening windows that didn't show on the taskbar) so I was forced to re-boot.

I know the keys on the keyboard are not sticking, plus I've never had this problem on the Windows box.

I also find it happens after I first start up and I get told there are updates.  I go to enter my admin password but after 2 keypress's I notice that there are 3 or more 'asterisks'.  Entering the password is usually the first keyboard entry I'm doing after bootup.

Any ideas? I thought there might be some setting for the refresh rate or something for the keyboard.

Thanks

Max

---

### Post by clong83 on 2008-01-14
I'd been having the same problem and it was driving me mad.  I read all the threads on it and tried everything suggested and nothing stopped this type of problem.  I was eventually drawn to format and reinstall to see what that did.  

It worked properly upon a clean installation.  That is, before I installed any superfluous programs that weren't necessary.  Usually it would crap out within five minutes, especially if firefox was running.  But my scrollbar worked for a long time (usually crapped out after the first mouse/keyboard going crazy instance), and no crazy unscripted mouse movements or clicking or typing was going on.  Then I decided to start installing programs, one by one, to see what effect they had.  

Low and behold as soon as I installed bcm43xx-fwcutter, and it installed the firmware for my wireless card, the mouse went crazy and the scrollbar stopped working.  Typing became problematic.  I uninstalled it, disabled the firmware, and rebooted.  It's three days later and I haven't had a single problem yet, and I've installed every other program I previously had.  This type of problem NEVER went more than one hour without raising its head before...

Not sure if this is the root cause, as I'm sure many people here don't have broadcom wireless cards, but those of you who do might want to try getting rid of the restricted drivers for it and see what happens.

---

### Post by spamgoat on 2008-01-15
You're not the first to report bcm43xx-fwcutter messing with your keyboard, as this thread points out ([http://ubuntuforums.org/showthread.php?t=624131](http://ubuntuforums.org/showthread.php?t=624131)) so that's a very interesting find, clong83. :)

Can anyone confirm getting rid of the restricted drivers solves the problem for them?

---

### Post by clong83 on 2008-01-15
Thanks spamgoat.  I am glad I did the fresh install, or I never would have thought that bcmxx-fwcutter was the culprit.  I mean really... wireless drivers causing all these problems?  I have no idea why it does what it does, but I've repeated the problem quite consistently if I reinstall the package.

---

### Post by sistoviejo on 2008-01-15
> **clong83 said:**
> I'd been having the same problem and it was driving me mad.  I read all the threads on it and tried everything suggested and nothing stopped this type of problem.  I was eventually drawn to format and reinstall to see what that did.  

It worked properly upon a clean installation.  That is, before I installed any superfluous programs that weren't necessary.  Usually it would crap out within five minutes, especially if firefox was running.  But my scrollbar worked for a long time (usually crapped out after the first mouse/keyboard going crazy instance), and no crazy unscripted mouse movements or clicking or typing was going on.  Then I decided to start installing programs, one by one, to see what effect they had.  

Low and behold as soon as I installed bcm43xx-fwcutter, and it installed the firmware for my wireless card, the mouse went crazy and the scrollbar stopped working.  Typing became problematic.  I uninstalled it, disabled the firmware, and rebooted.  It's three days later and I haven't had a single problem yet, and I've installed every other program I previously had.  This type of problem NEVER went more than one hour without raising its head before...

Not sure if this is the root cause, as I'm sure many people here don't have broadcom wireless cards, but those of you who do might want to try getting rid of the restricted drivers for it and see what happens.

I did have Broadcom wireless but I was using the Windows driver through Ndiswan because the restricted driver would not work.
I never tried removing the drivers to see if that solved the problem and will not be able to do it now because I removed Ubuntu from the laptop.
I promised myself to try again when Hardy Heron comes out though!

---

### Post by spamgoat on 2008-01-15
Updated first post to include more information. Were there any threads, urls or suggested fixes I missed?

---

### Post by Mad_Max_1412 on 2008-01-16
For what it's worth, I don't have wireless drivers installed and am having the problem.  Yesterday when I booted up and found there were updates, I went to put in my password and I typed the first 2 characters rather quickly but did seem to notice that it was the first keystroke which repeated (so i ended up with 3 stars in the box).  Just as I was about to hit the backspace, a whole heap of stars started to appear even though i hadn't touched the keyboard.  Pressing backspace stopped the characters appearing and I was able to clear the password box and enter my password cleanly in one go.

---

### Post by clong83 on 2008-01-16
I'm at a loss for this bug.  Have you tried turning off some startup programs to see if one of those is doing it at the startup?  What about your ~/.xsession-errors file?  Does it show anything weird at about the time of the first error?

---

### Post by Mad_Max_1412 on 2008-01-17
Where do I find this file (sorry I'm not that experienced)?  I tried using the "Tracker Search Tool" and searched for "error" but it found nothing.

---

### Post by clong83 on 2008-01-17
No problem.  It's a hidden file, so it probably won't show up on searches (don't know, I've never used the search tool much...), but if you open a terminal, you should be able to type 

```

ls -A ~/

```

and you'll see it in your home directory.  You can then do

```

gedit ~/.xsession-errors

```

and it will open the file so you can browse the contents.  Be sure and note that there is a '.' at the beginning of the file name.  Most of the contents will have a time stamp on it somewhere, so you can see if there's any xsession errors right around when your keyboard starts screwing up.  Hope that helps, and don't forget to post the results.

---

### Post by sistoviejo on 2008-01-17
~ is your home directory.
So if you were mario ~ would equal to /home/mario
If you were root ~ would equal to /root

---

### Post by Mad_Max_1412 on 2008-01-18
Well guys,

I booted up and installed some updates, then checked my mail (Evolution).  I had 1 notification about your reply to this thread and 4 junk emails.  I clicked on the first  junk email and pressed shift whilst I clicked on the last junk email so I could delete them and the highlight quickly scrolled continuously throughout those 4 emails.

I had to press backspace for it to stop.  I then deleted the 4 junk emails.  This was at about 10:20am local time. I then clicked on the link in the thread email and read your reply about the .xsession-errors file.

I opened a terminal window and the command I used was:

max@ubuntu:~$ gedit /home/max/.xsession-errors

I don't think my file is showing any errors relating to multiple keystrokes.  Anyway, it's listed below.

(Oh, by the way, I replaced the batteries in my wireless Logitech keyboard before booting up to eliminate that as the cause.)

(process:5336): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5402): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5333

** (x-session-manager:5333): WARNING **: Host name lookup failure on localhost.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0140 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
** Message: Starting remote desktop server
Initializing gnome-mount extension
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gnome-panel:5478): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
** (evolution:6266): DEBUG: mailto URL command: evolution %s
** (evolution:6266): DEBUG: mailto URL program: evolution

(evolution:6266): camel-CRITICAL **: camel_store_get_folder: assertion `folder_name != NULL' failed

(evolution:6266): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:6266): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed

(evolution:6266): camel-CRITICAL **: camel_store_get_folder: assertion `folder_name != NULL' failed

(evolution:6266): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:6266): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception

---

### Post by sistoviejo on 2008-01-18
has anybody had the problem with a standard ps2 (non usb) keyboard?

---

### Post by Mad_Max_1412 on 2008-01-19
My keyboard is a wireless one that plugs into the PS2 socket and I'm having problems (see entries above)

---

### Post by Nerdriot on 2008-01-31
I was having a similar issue, and posted how I solved mine here: [http://ubuntuforums.org/showthread.php?t=658446&highlight=logitech+wireless+keyboard]("http://ubuntuforums.org/showthread.php?t=658446&highlight=logitech+wireless+keyboard")

I hope this can help someone. :)

---

### Post by zgoda on 2008-02-06
> **sistoviejo said:**
> I already tried that and can't get used to it so it's not a solution for me.
I use fast repeating keys for scrolling through text a lot. I am using windows a lot more often because of this and another problem (I can't configure cpufreq-selector correctly while using battery). 

Still this problem doesn't happen on my desktop computer for some reason.
It's an Intel Celeron 2.4Ghz with 512 MB of memory.

Another problem that I have when typing sometimes is that the keys have a little lag to appear on screen. This problem is also also very annoying. It's even more annoying when playing games because key presses will take some time to register on the game also.
:(

I confirm the behaviour on my shiny new HP Compaq 6510b (7.10 32-bit, kernel 2.6.22-14-generic). Keys have lags, though I have delay set to practically minimal acceptable. Each few minutes random keystroke produces 2-3 characters.

---

### Post by spamgoat on 2008-02-23
I'd like to bump to bring attention to this bug yet again.

I just updated the original post to include more previous forum posts and launchpad entries. Anything i'm missing, or anything that does not belong?

I would like to point out that [the most recently active launchpad entry]("https://bugs.launchpad.net/ubuntu/+bug/124406") has the bug written down as Confirmed, but still (after 6 months of being open) has not had an importance status added (I would reckon this bug would be big enough to ratify at least 'High', but I might be biased). I would like to ask everyone who has not responded to this launchpad entry to read up and add as much as information as possible. The best way of getting this bug looked at is to make clear this is not just some rarity on obscure hardware, but this is actually hitting many of the users.

Furthermore, as has been reported numerous times, the proper fix for this problem might actually be a kernel update. Is there anyone running Hardy alpha that can confirm this problem is now fixed for them?

Thanks

---

### Post by stylishpants on 2008-03-03
I have another data point.

My system (Intel Celeron 2.4 GHz) has been experiencing the problem in Gutsy.  

In January, my hard drive failed, and I had to reinstall Gutsy from scratch.  My home dir is nfs mounted from a fileserver, so it was unaffected, only my OS was changed.  I have not had the problem since I reinstalled.  

It's the same machine (even replaced with an identical model hard drive), the same user config, and the same OS version (Gutsy in both), but now the problem is gone.

My system was originally installed with Ubuntu 6.04, and has been upgraded through every release since then.

---

### Post by sistoviejo on 2008-03-04
Has anybody tried Hardy Alpha?
[https://wiki.ubuntu.com/HardyHeron](https://wiki.ubuntu.com/HardyHeron)

---

### Post by WasteOfSpace on 2008-03-31
I have the same problem as many others but slightly different.

cname -a gives me:  Linux ubuntu1 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

The problem that I have is that in the bash shell or when required to fill in a password or when I sometimes open Firefox; the area for typing starts to fill up with asterisks.

In order to stop this undesirable activity, I have had to set the keyboard delay to 1000ms and the repeat rate to 20cps. This fixes the problem but can be annoying when waiting for 1000ms for the repeat to kick in.

As are others, I am running a KVMS and also have a wireless ethernet card in the box. The keyboard is also wireless.

---

### Post by sistoviejo on 2008-04-01
I was able to solve the problem on my laptop by installing Hardy Heron 8.04 beta. :)

---

### Post by arbeck on 2008-04-18
I'm running hardy beta and I still have this problem.  It's quite annoying.  Has anyone come up with a solution?

---

### Post by Paul S on 2008-04-28
> **arbeck said:**
> I'm running hardy beta and I still have this problem.  It's quite annoying.  Has anyone come up with a solution?

I'm running a fresh install of hardy kubuntu and have it still.  See launchpad 124406.

Apparently it's a kernel problem.

I think it's a security issue because think of the problem occuring during an on-line banking session.

Also, when I do aptitude full-upgrade, the carriage return repeats and causes the Y/N prompt to be answered with the default y!

regards,

---

### Post by Paul S on 2008-04-28
By the way, since this bug is still present in hardy, can the originator edit the title to reflect it's not just a gutsy bug anymore?

regards,

---

### Post by spamgoat on 2008-04-28
> **Paul S said:**
> By the way, since this bug is still present in hardy, can the originator edit the title to reflect it's not just a gutsy bug anymore?

regards,

[I]Good call, edited as requested. I also included some more information into the first post, I recommend everyone still having this bug to read the first part.

If there are any more mistakes or suggestions for this thread, please do let me know by replying.[/I]

--- edit: I've decided to repost the thread onto the new forum layout, so it shows up for new users who might be experiencing this issue as well. I would like to ask and recommend users to reply and keep track to the new thread rather than this one. Thanks.

[The reposted thread can be found here.]("http://ubuntuforums.org/showthread.php?t=772773")

---

