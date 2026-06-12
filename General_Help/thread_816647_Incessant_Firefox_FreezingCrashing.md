---
title: "Incessant Firefox Freezing/Crashing"
date: 2008-06-02
forum: General Help
---

### Post by Locutus_of_Borg on 2008-06-02
Ubuntu 7.10
Firefox 3 beta 5 (occurs with all versions at equal rate)
Every minute or so, sometimes four times a minute, Firefox will turn gray and cease responding to anything.  It will sometimes last for a few seconds, other times it will stay frozen until I have to kill the process, only then to find it will not restart.  Sometimes it happens while opening about:blank, sometimes while using Google, or browsing any various forums.

This is on my wife's computer, on my own I experienced no such problem.  When she was using 7.04 there didn't seem to be this issue.  There is no output from terminal, there are no strange configurations that I am aware of.

Any ideas at all what might be causing this?

It makes her computer barely usable really, and I don't want to tell her to stop using Firefox. Nor do I want her to return to Windows simply because of this very aggravating annoyance.

Thanks for any assistance.

---

### Post by marcelo danico on 2008-06-02
I fixed my crash issue thanks to defcon (ubuntu-unleashed), maybe this will help you too ---> [http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

> This is a quick fix that will require the terminal: Applications->Accessories->Terminal

> wget http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb

> sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb

> sudo apt-get remove --purge flashplugin-nonfree

> sudo apt-get install flashplugin-nonfree


My problem was on youtube, digg, but sometimes random like you mentioned.
Hope this helps.

---

### Post by Locutus_of_Borg on 2008-06-02
thanks for the reply

isn't nspluginwrapper for 64 bit though?

also i got a dependency problem when trying it anyway, needs newer version of libcairo2 but apt is saying i have the latest version...

---

### Post by marcelo danico on 2008-06-02
Here's the background to this fix find Conn's comments 38-39

https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888

Worked on my system Pentium 4 (w/c I think is 32 bit).

---

### Post by Locutus_of_Borg on 2008-06-02
i will give it a try then

any way of upgrading libcairo2 and libpango short of manually downloading them and all of the dependencies from the packages.ubuntu.com?

like, can i add some hardy repositories to my gutsy sources.list and just install those two things?

because i am getting ```
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on libcairo2 (>= 1.6.0); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 nspluginwrapper depends on libpango1.0-0 (>= 1.20.1); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.

```when installing nspluginwrapper

thanks

---

### Post by marcelo danico on 2008-06-03
That previous launchpad thread points to a better solution, manually installing Flash 10 + plugin etc.

Here's the how-to

[http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html](http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html)

---

### Post by Locutus_of_Borg on 2008-06-03
oh, thanks

ill give it a try if i can get a hold of her computer again tonight

:)

---

### Post by marcelo danico on 2008-06-03
This is a very nice, and very recent fix.  Here are some references for people sharing the same problem

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/)

and specifically,

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/218](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/218)

> From Conn
Currently, our only "sane" options are:

1. Flash 9 + libflashsupport + nspluginwrapper. This is suboptimal as it does not prevent flash from crashing, it merely provides a layer of protection to prevent Firefox from crashing with flash.

2. Flash 10 + bug #198453 configuration - libflashsupport. This configuration allows flash sound to get routed through pulseaudio without any crashes.

I wrote a guide on the forums to set up this second option, and nobody has complained about Flash since. I have been using Flash 10 non-stop and Firefox has not crashed a single time, even after extended browsing on flash-enabled sites.

And again the how-to for getting the flash 10 and plugin

[http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html](http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html)

Thanks to everyone that actually worked to get these fixes out to the rest of us.

---

### Post by psyke83 on 2008-06-03
Hi, it's Conn. 

It's no longer necessary to use the nspluginwrapper package that I built, as Flash v10 beta works with PulseAudio (with some configuration changes). Please see my guide here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I trust that these issues will be fixed officially in Hardy, but this guide gives you "early access" by using some Intrepid packages.

---

### Post by mixtri on 2008-06-03
Hi guys.
I'm getting the same problems too.
It is the most aggravating thing one can experience. 
Firefox crashing all the time. i am unable to use my favourite chatsites because the java applets load and freeze.
Whats more I have this strange problem with ubuntu logging me out of a session to the log in screen even when i have not logged off. this usually happens when i click on anything on the screen it could be to minimise a window or some other obscure action. 
What is wrong with ubuntu.
i have just returned to using 7.10 from 8.04 as i find it very unstable and of course the issue wit firefox is 10 times worse under 8.04. 7.10 appears to be more stable for the last week since reinstalling it. but now it too has started to crash and exhibit unstable behaviour.
I love ubunut and cannot even contemplate returning to windows. So does anyone know why this is happening?

---

### Post by mixtri on 2008-06-03
Psyche.

I just tried your instructions re: installing flash 10 plugin.

In the instructions you say 
" Download the new Flash 10 beta player from here to your home directory and unzip it.
Remove 'flashplugin-nonfree' and 'libflashsupport' using Synaptic"

Well i got two files in the folder i downloaded namely  
1. flashplayer-installer with a padlock attached to the icon
2. and libflashplayer.so

neither of which are what you mentioned above.
Are these the right files? I'm assuming the .tar file is the correct one to download?

---

### Post by marcelo danico on 2008-06-03
> **psyke83 said:**
> Hi, it's Conn. 

It's no longer necessary to use the nspluginwrapper package that I built, as Flash v10 beta works with PulseAudio (with some configuration changes). Please see my guide here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I trust that these issues will be fixed officially in Hardy, but this guide gives you "early access" by using some Intrepid packages.

I jumped on the bandwagon for the nsdispluginwrapper fix about a week ago and it has worked like a charm. I'll keep it a while longer, thanks a lot.

---

### Post by Locutus_of_Borg on 2008-06-03
After implementing the suggested solution, the problem still persists.

Firefox freezes, turns gray, and crashes about 20 times every hour.

There is seemingly no pattern to this behavior.  There doesn't appear to be any relation to flash. And I do not see how pulse audio is involved, as it had not been installed prior to following the instructions here: [http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html](http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html)

This was not an issue in 7.04

Can anyone think of anything else that might be causing it?

I don't really want to downgrade that computer, as it's a pain to set up the wireless card in that one.  

Thanks.

---

### Post by RobOrr on 2008-06-04
I had the same problem. Removing every flash player and then installing macromedia flash player only solved all my firefox crash problems. I could also tell that firefox was going to crash when my Motherboard temperature started rocketing towards 80+ degrees (its  normally around 42)

---

### Post by psyke83 on 2008-06-04
> **Locutus_of_Borg said:**
> 
Can anyone think of anything else that might be causing it?

The problem is due to a combination of PulseAudio (installed by default in Hardy) being mis-configured and a bug in Flash v9. You can find all the information and fixes in my guide (including linked bug reports) [here]("http://ubuntuforums.org/showthread.php?p=4928900").

---

### Post by psyke83 on 2008-06-04
> **mixtri said:**
> Psyche.

I just tried your instructions re: installing flash 10 plugin.

In the instructions you say 
" Download the new Flash 10 beta player from here to your home directory and unzip it.
Remove 'flashplugin-nonfree' and 'libflashsupport' using Synaptic"

Well i got two files in the folder i downloaded namely  
1. flashplayer-installer with a padlock attached to the icon
2. and libflashplayer.so

neither of which are what you mentioned above.
Are these the right files? I'm assuming the .tar file is the correct one to download?

Are you talking to me? You're looking at the wrong instructions. See my previous posts for the correct link.

---

### Post by mixtri on 2008-06-10
hmm. Not the remedies suggested seem to work.
I though i would get some respite from the instability of 8.04 by reinstalling 7.10 (gutsy)
Boy!! Was I wrong. I am now getting strange behaviour which i cannot seem to fathom
Ubuntu crashes for no apparent reason.
there seems to be a new and different occurence by the day.
yesterday it was to do with firefox crashing on me even though flash pluggins had been expunged from the system
Java applets freeze and then crah.
today My system just shuts down for no apparent reason, no pattern to this weird behaviour,  honestly cannot pin to anything that I am doing. As this strange behaviour could happen while listening to music using rythmbox or exaile. or by just innocently surfing the web,.
i have taken to just listening to music using exaile rather than stream musicoff the web which is what i would prefer to do.
I hate the fact that Ubuntu is slowly begining to control how I use it rather than the other way round.
HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!I really am F**KED OFF WITH THIS BEHAVIOUR. CRASHES and shutdowns every 20 mins is intolerable.
Please forgive the expletives but I think i'm going to chuck my efing PC out the window into oncoming traffic on the road below if it effing shuts down on me again.
HELP!!!!!!!!!!!!!!!!!!!!!!!!
iS THERE ANY ALTERNATIVE os ONE CAN USE THAT IS A LITTLE BIT MORE STABLE!!

---

