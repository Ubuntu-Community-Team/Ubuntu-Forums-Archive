---
title: "New Chrubuntu (Ubuntu) update 13.10 messed up my Acer C7"
date: 2013-10-19
forum: General Help
---

### Post by Jewel_Strother on 2013-10-19
Ok so yesterday , i got alarmed to update my ubuntu on my chromebook to 13.10.
I went out somewhere while the update was installing cause it was taking a minute.
Came back my laptop was restarted, so I assumed it finished.
it was on the screen where it said "Chrome OS Verfication Off" and where i have to hit "Ctrl + D" to proceed on to ubuntu.
After I hit Ctrl + D. It just goes into a plain black screen. And does nothing. just sits there.

I'm in the need of major help because I have files and stuff that i really need from my Chrubuntu.

If there is anyway I could like restore my laptop back to its originality. Back to 13.04.
Or anyway to back where I could just use my Acer C7 without having to remove any type of files from the hardrive. That'd be great.

Thank You

---

### Post by Subharo on 2013-10-20
Hello Jewel,

I think you're in rather deep doo doo.  Like you, I have a Samsung Chromebbok with Chrubuntu (still 13.04).  And I'll wait a good long while before I attempt an upgrade to 13.10.  I purposely disabled the aggressive, wildly-over-optimistic release-upgrading tool, from my "Software & Updates" (see "Updates" tab -> "Notify me of a new Ubuntu version:" -> Never).   I was bitten by exactly this sort of problem back when upgrading to Ubuntu 11.10, and I'm still wary of it happening again.

Unfortunatelty, Chrubuntu is not an officially supported Version of Ubuntu.  So you might find little help on these forums.  You can bet that the upgrade from 13.04 -> 13.10 was hardly "Quality Assured" whatsoever, *if at all*.  You'll notice there's not even a website in existence specifically about chrubuntu, if you do a Google search.  It would seem the situation is so pathetic that nobody even has about $10 to register the domain name chrubuntu.org.

The one ray of hope seems to be that there are cross-distro efforts (for all linux distros, not just Ubuntu) for the Samsung ARM Chromebook here:
[https://launchpad.net/chromebook-arm](https://launchpad.net/chromebook-arm)

I mention this because you could potentially "Report a Bug" there.  But it sounds like you have only a vague description of what's happening to you so far.  You have no specific error messages to offer, as seen in various log files from within Chrubuntu.  And it'll be damned hard to access those log files from where you're at now.  But at least perhaps you can help get the ball rolling.  The so-called "Samsung Chromebook (ARM) hackers," who monitor those Bug Reports, might then be able to suggest tricks to help you obtain these error messages.

In summary, using any linux distro on the Samsung ARM Chromebook is still very much a "wild west", that only hardcore linux ARM geeks would do well to venture into.  From what I'm observing, the future of Chrubuntu is a dim one.  The development momentum seems to be really slow.  

Most Linux geeks would probably rather choose an AMD64-based chromebook, as the software support is MUCH more mature for that architecture (than ARM).

---

### Post by Subharo on 2013-10-20
I previously said, above:

[INDENT]The one ray of hope seems to be that there are cross-distro efforts (for all linux distros, not just Ubuntu) for the Samsung ARM Chromebook here:
[https://launchpad.net/chromebook-arm](https://launchpad.net/chromebook-arm)

I mention this because you could potentially "Report a Bug" there.  But it sounds like you have only a vague description of what's happening to you so far.  You have no specific error messages to offer, as seen in various log files from within Chrubuntu.  And it'll be damned hard to access those log files from where you're at now.  But at least perhaps you can help get the ball rolling.  The so-called "Samsung Chromebook (ARM) hackers," who monitor those Bug Reports, might then be able to suggest tricks to help you obtain these error messages.
[/INDENT]
 
Oops, you probably shouldn't create a bug there, because you don't have an ARM CPU in your Acer C7 Chromebook.  

But everything else I said is still valid, pertaining to how Chrubuntu is currently very, very "unofficial," and support options generally don't look good at present.

---

### Post by Jewel_Strother on 2013-10-20
Thanks for the information! 
But this is how I solved it:
I Hit Ctrl + Alt + F1 to get one of the tty's, you'll see a disk mount failed error. Apparently Ubuntu 13.10 has a problem with Chromebooks right now and can't be installed, or at least with the Acer C7.
To go on with the installation, you first have to mount the drive using:

sudo mount -o remount /dev/sda7 (or whatever the Ubuntu partition is named in your case)

Then run:

dpkg --configure -a

And then the installation resumed. Sadly Ubuntu 13.10 is not really working properly on it. but right now it is running in low graphics mode because apparently it fails to recognize the Intel Sandybridge  graphic card.&#65279;

But that's fine cause I'm glad I was able to regain back my important
files. Any idea when the update will be fixed and working for the Acer c7?&#65279;

---

### Post by rectec794613 on 2013-10-25
Thanks for sacrificing your install for us, Jewel_Strother : )
Guess I'll hold off on updating to 13.10 for a while. Don't need that extra hassle.

---

### Post by randel on 2013-10-26
Just adding - the exact same thing happened on my Acer C7 with ChrUbuntu, the 13.04 to 13.10 upgrade crashed.  I did the very same steps of manually mounting and running "dpkg --configure -a" and I'm up and running.  Only left with 13.10's apparent dislike of IDLE 2.7.

Love my $200, full-featured, laptop.  Been my primary workstation for a year now!

---

### Post by Entreated on 2013-11-14
The same has happened to me, upon pressing ctrl + d to dismiss verification is off screen, I am presented with a blank black screen.
Following the instructions stated above entering the tty by pressing ctrl + alt + f2 brings me to a screen which states:

Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems.
Any further errors will be ignored.
Give root password for maintenance (or type Control-D to continue):


After entering the default root password (of which I have never changed) still being 'user', it prompts me with 'Login incorrect'.
I need the files from the Chrubuntu partition and would very much like everything to return back to normal.

If anyone has any advice it would be highly appreciated.

---

### Post by tsalmond on 2013-11-19
Same here with one difference: instead of the black screen of death, Chrome OS boots up. Will try the suggested fix later as my situation is less pressing than others. Like anyone else, any suggestions greatly appreciated.

---

### Post by rectec794613 on 2013-12-05
Well I gave upgrading to 13.10 a go. I just used the do-release-upgrade command. Afterwords, when I rebooted, I had no problems booting up. The only issue I had was Cinnamon not starting properly. Regardless, I see people here have had mixed results. I would recommend just going for a fresh install. The [ChrUbuntu script]("http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html") can install 13.10. I'm doing it right now, as a matter of fact.

---

### Post by hans12345 on 2013-12-18
So, how did the upgrade to 13.10 go?

---

### Post by Subharo on 2013-12-19
> **rectec794613 said:**
> Well I gave upgrading to 13.10 a go. I just used the do-release-upgrade command. Afterwords, when I rebooted, I had no problems booting up. The only issue I had was Cinnamon not starting properly. Regardless, I see people here have had mixed results. I would recommend just going for a fresh install. The [ChrUbuntu script]("http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html") can install 13.10. I'm doing it right now, as a matter of fact.

Can you verify it went OK?  Does video hardware accelleration work for you now in X11?

I currently have Chrubuntu 13.04 installed on my Samsung ARM Chromebook, and I'd also like to follow this route myself (a fresh install of Chrubuntu 13.10).  Can you verify that:

[LIST=1]
[*]the Chrubuntu script you linked to is intelligent enough to handle how my internal 16GB flash drive is already partitioned for Chrubuntu 13.04 (and it'll just install 13.10 over top of the existing 13.04, perhaps after reformatting those partitions)?  I ask because my assumption is that the script you've linked to is meant for Chromebooks with ONLY the factory install of ChromeOS (and no Chrubuntu yet). 
[*]The script you linked to is meant to be run from back within ChromeOS (not from within my Chrubuntu 13.04). 
[*]If I'm not mistaken a Ctrl+D or Ctrl+L might boot back to ChromeOS. 
[/LIST]

Any replies are most appreciated!

---

### Post by Joseph_Markham on 2014-01-13
Upgraded to 13.10 from 13.04...

Major issue... unity test crashes and so X is running the graphics hardware in software mode... not using graphics acceleration of the chipset... so everything works sloooooooooowwwwwwwlllllllllllyyyyyyyy.!

---

