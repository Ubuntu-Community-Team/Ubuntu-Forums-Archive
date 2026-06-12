---
title: "Oh what the **** happened now?"
date: 2008-04-06
forum: General Help
---

### Post by AquaStreak on 2008-04-06
Ok, first off, disclaimer: I am very pissed. Ubuntu is nothing but problem after problem after problem after problem. You fix one and cause another. I have to say this is the worst operating system I have ever used.

With that being said...

I lost my sound. AGAIN.

Now, last time when I fixed my sound, it was because I screwed up my graphics drivers. I'm not doing all that again, so I'm asking you guys for help.

The problem essentially lies in the fact that, I have my sound drivers set to ALSA. If my sound drivers are set to anything but ALSA, nothing gives me sound, unless I'm using that STAxxx one in which only Movie Player gives me any sound (o.O).

Now, God blessed me last time when ALSA decided to work. But now, I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing." This happens with ALL drivers except the STAxxx one but again, that doesn't work for programs.

I am really getting frustrated. Changing settings on Ubuntu is a maze and I have no idea how to fix this problem. I tried going to terminal and typing "sudo apt-get install alsa", but it says I have the latest version and that nothing was changed.

I don't know how I got ALSA to magically work that one time, but it did, and I can't get it to work again. I need my sound. WHY is this so complicated? Why can't they make Ubuntu easy to use....?

---

### Post by Jussi Kukkonen on 2008-04-06
Please use descriptive titles, even if you're frustrated. Someone who knows sound issues might read this post if it had a a good title -- and I (and others who know nothing about sound on linux) would not have wasted time here...

---

### Post by HermanAB on 2008-04-06
It sounds like you would do better with a distribution that has decent wizards, so you can point and click your way to nirvana.  Mandriva Spring is coming on 10 April.

---

### Post by AquaStreak on 2008-04-06
*It sounds like you would do better with a distribution that has decent wizards*

...Are you trying to call me stupid? :(

---

### Post by overdrank on 2008-04-06
> **AquaStreak said:**
> Ok, first off, disclaimer: I am very pissed. Ubuntu is nothing but problem after problem after problem after problem. You fix one and cause another. I have to say this is the worst operating system I have ever used.

With that being said...

I lost my sound. AGAIN.

Now, last time when I fixed my sound, it was because I screwed up my graphics drivers. I'm not doing all that again, so I'm asking you guys for help.

The problem essentially lies in the fact that, I have my sound drivers set to ALSA. If my sound drivers are set to anything but ALSA, nothing gives me sound, unless I'm using that STAxxx one in which only Movie Player gives me any sound (o.O).

Now, God blessed me last time when ALSA decided to work. But now, I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing." This happens with ALL drivers except the STAxxx one but again, that doesn't work for programs.

I am really getting frustrated. Changing settings on Ubuntu is a maze and I have no idea how to fix this problem. I tried going to terminal and typing "sudo apt-get install alsa", but it says I have the latest version and that nothing was changed.

I don't know how I got ALSA to magically work that one time, but it did, and I can't get it to work again. I need my sound. WHY is this so complicated? Why can't they make Ubuntu easy to use....?

Hi and I am glad to see you have a GUI again
[http://ubuntuforums.org/showthread.php?p=4663532#post4663532](http://ubuntuforums.org/showthread.php?p=4663532#post4663532)
I am not much with the sound but have you looked at this link
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
It may provide some help.
Edit and I do not believe name calling is necessary. Sometimes Ubuntu takes a little tweaking and it is a great idea to use the live cd to search for issue then use the forums to find solutions, :)

---

### Post by AquaStreak on 2008-04-06
Yeah, I got the GUI back. What you said did the trick. I got back into "Low Graphics" mode, and I reinstalled the ATI drivers.

I'll give that sound problems guide a whip.

---

### Post by AquaStreak on 2008-04-06
Back on ole reliable Windows.

Because for some reason, Ubuntu ****ed up. AGAIN.

Now if I boot up, I get a terminal! I never get a GUI! YAY!

</sarcasm>.

Can someone point me in the right direction for uninstalling Linux? Preferably without using Linux at the time?

---

### Post by overdrank on 2008-04-06
> **AquaStreak said:**
> Back on ole reliable Windows.

Because for some reason, Ubuntu ****ed up. AGAIN.

Now if I boot up, I get a terminal! I never get a GUI! YAY!

</sarcasm>.

Can someone point me in the right direction for uninstalling Linux? Preferably without using Linux at the time?

Hope this will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by tubasoldier on 2008-04-06
> **AquaStreak said:**
> Back on ole reliable Windows.

Because for some reason, Ubuntu ****ed up. AGAIN.

Now if I boot up, I get a terminal! I never get a GUI! YAY!

</sarcasm>.

Can someone point me in the right direction for uninstalling Linux? Preferably without using Linux at the time?

Sounds like Windows is for you. You can use any partition editor to delete the Ubuntu partition and resize your windows partition to it's full size. GParted (a live cd Linux distro can do that) or Partition Magic.

You will also have to restore the Windows MBR. This is done by putting in the Windows install media. I believe the command is restorembr? Not really sure since I haven't used it in a while. Good luck.

---

