---
title: "Keyboard bursts in 7.04 (Feisty), 7.10 (Gutsy), 8.04 (Hardy)"
date: 2008-04-28
forum: General Help
---

### Post by spamgoat on 2008-04-28
---- NOTE TO MODERATORS ----
This is a repost of the [thread on the old forum layout]("http://ubuntuforums.org/showthread.php?t=599978"). I'm hoping to centre all the attention of this bug into a single thread, to keep it cleaner and easier for users to track, whilst also moving the problem onto the new forum layout.

If the forum moderators do feel they should remove this copy, please remove this one and not the old one containing all the replies.
---- /NOTE TO MODERATORS ----

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

### Post by Paul S on 2008-04-28
Thanks for fixing the title.

One of the suggestions in the bug 124406 report suggested entering "atkbd.softrepeat=1" in your grub boot kernel parameters line.  But, I tried that and it did no good.

This is an intermittent bug here, I haven't had it for a few hours now, but earlier today it was so disruptive I had to reboot.

Has anyone found a way to stop it when it's happening, as sometimes occurs on it's own?  I see a command line program kbdrate that can be used to set the repeat rate, but don't know if it's useful.

regards,

---

### Post by sistoviejo on 2008-04-28
Some things you can try:
Change your Window manager from compiz to metacity. An easy way to do this is to install the fusion icon (a little icon that appears in the task bar and allows fast window manager switching and tweaking).

Also you can try disable services which use up the CPU. trackerd uses lots of CPU and is not an essential service. You can also try to run top on console and see which processes are taking most CPU or memory resources and kill them.

Also if you updated, you could try reinstalling if this is possible for you. 

Lastly you could also try a different keyboard/mouse.

I don't think anyone has identified an exact cause for this problem. Everyone has had different causes and solutions for it so far. So you should try everything and see if it gets sorted out for you.

Good luck

---

### Post by foresto on 2008-05-16
I just posted some more info in launchpad [bug 124406](https://bugs.launchpad.net/ubuntu/+bug/124406).  To summarize, my USB mouse seems to be triggering the stuck key problem.  Each time it happens, I get a syslog message like this:

```
usb 2-1: reset low speed USB device using uhci_hcd and address 3
```

I have never seen this happen when I plug in my mouse using its usb to ps2 adapter.  It happens only when I plug directly into one of my computer's usb ports.

Thanks to carlosbrolotobar for [calling my attention](http://ubuntuforums.org/showthread.php?p=4610774) to the syslog entries.

---

### Post by ElDave on 2008-06-15
I am absolutely having the same problem. It's especially frustrating when I'm trying to read a PDF and it automatically repeats PgDn until it hits the bottom of the document.

---

### Post by RodDavison on 2008-06-17
Ubuntu Hardy Sticky Keyboard problem:

I installed Ubuntu (Hardy) on my laptop about a month ago and I have been very, very happy with it.  I won't ever go back to Windows!  However, there seems to bbbbbbbbbbbbbbbbbbbe an ongoing problem with key presses and releases being missed.  

In searching the forums it appears that this problem has existed since Feisty (Bug #124406, first reported on 2007-07-06), maybe even since Dapper ([http://ubuntuforums.org/showthread.php?t=172696](http://ubuntuforums.org/showthread.php?t=172696)) and has not been fixed yet.  This one issue and the lack of a fix for it, for about a year now, makes Ubuntu seem very amateurish.  This one problem has me on the verge of dumping Ubuntu and trying to find a more "professional" disssssssssssssssssssssstribution.   Since I am relatively new to Ubuntu, I don't know how one goes about getting a bug escalated to the level where it will get fixed, especially a hard to reproduce one, however, this bug needs to be escalated.  I can see that this is a tricky problem to solve since it clearly only happens on some machines (I believe that most but not all are laptops, and I suspect the laptop trackpad as being complicit in the problem).

I experienced this problem with an out-of-the-box installation in Firefox, within the first 10 minutes of using Ubuntu.  So, there it has nothing to do with 3rd party applications.  

Please, please fix this problem soon, before I am forced to move on from Ubuntu!!!!!  I'm sure I speak for many sticky-keyboard users!

NB.  So far during the typing of this report (in gedit) I lost 5 characters which I went back and inserted (so that I wouldn't look like someone who can't type), but I did leave in the missed key-up events that occurred.

Here are some details in the hope that someone can try to track this one.  PS.  If you need someone to test ixes (fixes) please contact me, I would be happy to help!
 
My hardware is a stock Toshhhhhhhhhhhhhhhhhhhhhhhiba Portege M300 Laptop.  The other bug reports here list the symptoms adequately; but to summarize: the response to keys presses seems very sluggish and bursty and in conjunction with the sluggishness, key events are frequennnnnnnnnnnnnnnnnnnnnnnnntly lost (they may be up or down events).  They can be ascii keys or control or shift keys.

Many thanks,

Rod Davison.

---

### Post by ruetheday on 2008-06-17
> **RodDavison said:**
> Ubuntu Hardy Sticky Keyboard problem:

I installed Ubuntu (Hardy) on my laptop about a month ago and I have been very, very happy with it.  I won't ever go back to Windows!  However, there seems to bbbbbbbbbbbbbbbbbbbe an ongoing problem with key presses and releases being missed.  

In searching the forums it appears that this problem has existed since Feisty (Bug #124406, first reported on 2007-07-06), maybe even since Dapper ([http://ubuntuforums.org/showthread.php?t=172696](http://ubuntuforums.org/showthread.php?t=172696)) and has not been fixed yet.  This one issue and the lack of a fix for it, for about a year now, makes Ubuntu seem very amateurish.  This one problem has me on the verge of dumping Ubuntu and trying to find a more "profession" disssssssssssssssssssssstribution.   Since I am relatively new to Ubuntu, I don't know how one goes about getting a bug escalated to the level where it will get fixed, especially a hard to reproduce one, however, this bug needs to be escalated.  I can see that this is a tricky problem to solve since it clearly only happens on some machines (I believe that most but not all are laptops, and I suspect the laptop trackpad as being complicit in the problem).

I experienced this problem with an out-of-the-box installation in Firefox, within the first 10 minutes of using Ubuntu.  So, there it has nothing to do with 3rd party applications.  

Please, please fix this problem soon, before I am forced to move on from Ubuntu!!!!!  I'm sure I speak for many sticky-keyboard users!

NB.  So far during the typing of this report (in gedit) I lost 5 characters which I went back and inserted (so that I wouldn't look like someone who can't type), but I did leave in the missed key-up events that occurred.

Here are some details in the hope that someone can try to track this one.  PS.  If you need someone to test ixes (fixes) please contact me, I would be happy to help!
 
My hardware is a stock Toshhhhhhhhhhhhhhhhhhhhhhhiba Portege M300 Laptop.  The other bug reports here list the symptoms adequately; but to summarize: the response to keys presses seems very sluggish and bursty and in conjunction with the sluggishness, key events are frequennnnnnnnnnnnnnnnnnnnnnnnntly lost (they may be up or down events).  They can be ascii keys or control or shift keys.

Many thanks,

Rod Davison.

HAHAHAH Exxxxxxxactly --this has happened within the last two major updates.

  it is also occurring in ubuntu and xbuntu.  oh well.. microsoft xp was doing this near the first reeeeeeeleaces.  i am going to try turning off button repeat, and shut up aboutttttt it until one month from now.

---

### Post by a.janke on 2008-06-22
Hi, 

I too have this problem (although on a Quad core Intel desktop system with a Microsoft Ergo Keyboard). In my case this problem occurs randomly (I am yet to find the exact series of presses that causes it) when bashing about in vi with Ctrl-F and Ctrl-B. 

In my case it appears that Ctrl gets "stuck" down because the mouse then behaves as if this is so (clicking in an xterm brings up the old "Main options" menu etc.

I have suspicions that it is an X problem because when it happens I can dump to a virtual terminal (Ctrl-Alt-F1) and all works fine. There appears to be nothing amiss from ps and the likes and dmesg/syslog. I then have to resort of pressing Ctrl-Alt-Backspace and login again at which stage all is fine. 

Perhaps this is a different bug as I only have a problem with Ctrl sticking.  In any case I point my finger at the GNOME "Show position of pointer when control key is pressed" in "Mouse Preferences". If I disable this the problem becomes less frequent.  I also have turned off all the accessibility things I can find but it still happens from time to time.


a

---

### Post by lvm on 2008-07-17
I suffered from this problem in gutsy, but a week ago I upgraded to 8.04 and it's gone. In 7.04 it was intermittent, but there was a definite pattern: immediately before a burst of repeated characters there  always was a slight delay in reaction to a keystroke. The delay is still there (and I'd prefer it not to be) but the burst is gone, hope for good. nforce 430 chipset, ps/2  keyboard and mouse.

---

### Post by fswayze on 2008-08-24
Hi everyone,

Ubuntu newbie here, although I've been using ubuntu since Dapper came out, if that means anything. Just upgraded to Hardy and everything seemed to be going fine for a day. I've started experiencing the sticking keys and also my Shift key(both left and right) no longer work. I'm using a KVM with a USB keyboard/mouse which I thought could be the problem, however I plugged both keyboard/mouse into a USB port with same result. Funny thing though, I then went back to a PS2 keyboard/mouse and things have worked fine(only been 1 day though). Since I'm new to Ubuntu this info doesn't help me much in determining a fix but perhaps it will someone else. Also ran 'xev' from prompt and found the shift keys are not registering at all. Hope this info helps somebody.

fswayze, newbie.

---

### Post by Scunge on 2008-09-05
I get keyboard bursts as well, but slightly differently from what has been said in this and the other thread pointed to above.

Firstly, I've seen it happen when I first log in to Dapper, before starting Firefox (and I don't have compiz), simply by opening a terminal window and typing stuff in there (update: can't repeat this), or running some other application.

Secondly, it didn't used to do it, but recently started. Given that my laptop keyboard is a bit old (it has lost 3 keys already) I figured it was just some connection problem, and so unfortunately do not recall *when* it started. But given that it seems to be a bug, then a relatively recent update or installation must have introduced it ("recent" being in the last couple of months).

The thought did occur, though, as to whether this could be a virus. Perhaps from a website rather than an installed program?

Finally, the reason I found this thread in the first place, why I was even looking, is that I have Dapper running on three other machines here at home, and none of them are exhibiting the problem. So of course I thought it was my laptop hardware. But I am just starting to move over to Hardy, and so I installed a dual-boot with Dapper, and it's not doing it with Hardy!

I experimented this morning: I rebooted out of Hardy, working, and into Dapper. Within a minute it was going off. Rebooted back into Hardy and it hasn't done it today since.

As time goes on, I will be gradually installing the same programs that I use under Dapper in Hardy instead. So as soon as I see the keyboard problems again, if I do, I can try and narrow down what could have introduced it.

Edit: Oh yeah, sorry. Laptop is an Amilo D 8820, 32-bit.

And, here's what I did to try and alleviate the problem whilst in Dapper. I started a terminal window and moved it off to the right, so that a few columns are visible. Make it always on top, and always on visible workspace. Any time the repeating thing starts, jsut whizz the mouse over to the right (and if you are set up to not automatically select a window your mouse moves over, you'll need to click as well) and let the terminal window grab all the keypresses. Then hit ESC loads of times until it stops, and move back to what you were doing.

---

### Post by Dubbayoo on 2008-09-05
This has been happening to me for a few weeks now. In my case it is the spacebar either failing to register a stroke or continuing to enter strokes nonstop. I just thought it was my bad typing. the last 3 days it has made the computer nearly unusable. Disabling repeat lets me get by but I could sure usea  real fix.

---

### Post by sevesteen on 2008-11-01
I had a similar problem in Hardy.  I primarily use my laptop at my desk, with an external keyboard and mouse through a PS2/USB adapter.  No problems there.  When I started using the built-in keyboard and trackpad, the bug triggered--I'd get a burst of characters.  Once it triggered, I'd also get random dropped keys.  Also once the bug triggered, the bug would remain with the external keyboard until a reboot or logoff. 

I eventually found a fix after trying many different things.  Unfortunately,  I cannot remember what the fix was.   I just upgraded to Intrepid, and the bug is back--this time it triggered while using my external keyboard.

---

### Post by apoth on 2008-11-05
I just installed a new laptop keyboard - I broke the last one because of this problem. Unfortunately the issue is still here in Innnnnnnnnnnntrepid. This bug has cost me about 50 USD!

---

### Post by apoth on 2008-11-05
Slowing down the repeat key duration and delay in system/preferences/keyboard seems to have eased it - no repeats yet for the last three hours, woo hoo!

---

### Post by apoth on 2008-11-06
It's borked again. Took me an over half an hour to get past the encrypted disk passphrase - eventually I just plugged in a USB keyboard. I really don't want to have to go back to lugging that around with the laptop.

---

### Post by xerman on 2008-11-07
Hello there,

This maybe be the same i am experiencing. I firstly thought the issue was due to the presence of a KVM Device to share keyboard between server and desktop machines. But today i just plugged directly to pc ports, no KVM, and still the same issues.

The issues relate to both: Mouse and Keyboard.

State: Now i am using:
- Microsoft wireless comfort keyboar 1.0A 
- Microsoft wireless optical mouse 2.0

but the issue happened before with other microsoft pair:
- Microsoft wireless natural multimedia keyboard
- Microsoft wireles optical mouse

Issues are the following:
1- Mouse related:
1.1. Mouse randomly does not respond to clicks. 
Mouse can move cursor when move mouse on table, but when trying to click on a menu, nothing will happen for a while. After some "rest time" will decide to do the click. 
This applies to Right Click, and to Left Click, Single click or double.
This results on sometimes not able to select, open, even mess work on inkscape, gimp, qcad...

2- Keyboard related:
2.1. The already noted about keys repeating like crazy.
2.2. Modifying keys some times get "locked" in one position and takes a while to get back to normal.
E.G.: typing a text, then need to type caps so press Shift, though shift key is depressed after, keyboard still acts as if it was pressed so keeps typing caps, if moving cursor and being lucky to get a click will come out a complete selection of things.
This produces awkward behavior as depending on the key locked (****, ctrl, alt, ...) the mouse movements will produce desktop to go crazy (compiz installed).
This lock does not appear as lock in Lock Keys Applet.

This happens in the u804 desktop and the u704 server, so seems that has been here for some time.

On another machine i have a Logitech Wave keyboard combo, and there have no issues at all. This seems a problem mostly related to use of MS hardware, as with Logitech keyboard-mouse combos never noticed this issue. I do not use that computer that much, as it is a home computer, so maybe this also helps to have no issues yet.

Still have not found a way to solve it.

Regards
Xermán

---

### Post by Tiler on 2009-02-05
EeePC 1000, 2GB, Hardy checking in.  I have been using the (Bounce)sticky keys option in accessibility to prevent duplicate key presses.  

The problem I'm having is that every other reboot or power up, I have to reset it.  I have the session active for startup but it doesn't retain it for some reason.

---

### Post by Mikael P. on 2009-07-01
So, how can I go about helping out to raise the importance of a fix for this?
Right now it makes Ubuntu almost unusable.

---

### Post by RodDavison on 2009-09-21
I posted a request for help to this thread, over a year ago now.  The bug is still here.  However, I now have this narrowed down quite a bit more.  Hopefully, someone can use this info to finally track down this bug.

1) if I disable the "Internal Pointer Device" in the bios of my laptop, the bug goes away completely.
2) by doing "cat /proc/interrupts  | grep i8042" I can watch the interrupt count on int 12 climbing.  Even a very light touch on the trackpad (too light to even cause the cursor to move), will cause about 600 interrupts.  These 600 interrupts take about 2 to 3 seconds to process.  Any cursor movement using the trackpad prevents any typing for  at least 3 seconds.
3) I can reproduce the problem 100% by touching the trackpad while typing.
4) The trackpad and the keyboard both share the i8042, so it seems pretty clear that problem is around here somewhere.


Please, could someone look at this.  Feel free to give me a shout if you a fix tested.  Or need more info on this.

Thanks,

Rod Davison.

PS.  My laptop is a Toshiba Portege M300.  I'm running jaunty, but I've had the problem in feist and hardy too.

---

