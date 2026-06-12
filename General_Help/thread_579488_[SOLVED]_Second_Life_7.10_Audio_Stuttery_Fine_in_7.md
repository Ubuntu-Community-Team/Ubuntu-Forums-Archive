---
title: "[SOLVED] Second Life 7.10 Audio Stuttery Fine in 7.04"
date: 2007-10-18
forum: General Help
---

### Post by Kristopher on 2007-10-18
I have just updated to 7.10 and everything is fine apart from, the audio in second life is very stuttery. This was perfect in 7.04, can someone help?

---

### Post by Kristopher on 2007-10-18
A remove and install didn't fix this issue. I don't know what to try now. :confused:

---

### Post by Kristopher on 2007-10-19
I have been told a clean install would fix this, is this correct?

---

### Post by Nunu on 2007-10-19
If you upgraded it's possible. I don't know of any newer driver for the audigy either. This is rather interesting  i also have the audigy ZS on feisty at the moment and that also works fine. I had a bit of a battle to get the 7.1 to work but after figuring out that the volumes on the side and rear channels where muted it was perfect. I still need to upgrade to Gutsy so don't know if i am going to have the same issue.:-k

---

### Post by Kristopher on 2007-10-19
Clean install, same issue. :(

---

### Post by fjleal on 2007-10-19
Same problem here. Couldn't find any solution yet...

---

### Post by Kristopher on 2007-10-19
I have also posted this issue here - 

[http://forums.secondlife.com/showthread.php?t=217645&page=1&pp=15](http://forums.secondlife.com/showthread.php?t=217645&page=1&pp=15)

Hopefully we will find a solution.

---

### Post by hartungu on 2007-10-20
I had the same problem and found a solution:

Go to System > Preferences > Multimedia-System. Choose ESD as output plugin and test it to make sure it works. When it works, go to the SL-folder, open the secondlife file and comment out the following lines:

## - Avoids using the OSS audio driver.
export LL_BAD_OSS=x

## - Avoids using the ALSA audio driver.
export LL_BAD_ALSA=x

so that the top of the file looks like this:
## - Avoids using the ESD audio driver.
# export LL_BAD_ESD=x
## - Avoids using the OSS audio driver.
export LL_BAD_OSS=x
## - Avoids using the ALSA audio driver.
export LL_BAD_ALSA=x

Than save and start SL. Worked fine for me.

---

### Post by Goroii on 2007-10-20
I had same issue. 

you can try to install pulseaudio and pulseaudio-esound-compat from synaptic. and relogin

after this, its become fine in my enviroment.

---

### Post by Kristopher on 2007-10-21
will this only effect my SL game or the whole OS?

---

### Post by Kristopher on 2007-10-21
I tried what was suggested on the SL forums to install esound and uncomment the ESD line, this didnt work so i uninstalled esound and recommented the ESD and it worked fine...closed SL and reopened and its back to the way it was before.

Pulse audio looks like a server thing? i am not doing my own streams its the Ambient sound and UI sound and when i press the music play button that is very stuttery.

---

### Post by sonicj73 on 2007-10-21
> **Goroii said:**
> I had same issue. 

you can try to install pulseaudio and pulseaudio-esound-compat from synaptic. and relogin

after this, its become fine in my enviroment.

Thanks, this fixed the problem!!!

---

### Post by Kristopher on 2007-10-21
Did you need to make any setting changes or just install them?

---

### Post by Kristopher on 2007-10-22
Installed pulseaudio and pulseaudio-esound-compat forced SL to use ESD and all sounds a lot better. 

There is a little delay every now and then but its definitely a lot better than it was. The music stream is perfect, the delay is on the UI sounds and the TP sound....it might happen 1 to 2 seconds later.

installing these extra packages and editing the conf file should not be needed, especially since it was fine in Ubuntu 7.04.

---

### Post by Kristopher on 2007-10-22
Though this is a temp fix till SL fix this issue, i have just noticed that it effects Amarok. If you press pause it freezes it for 1min. Removing Pulse and doing a restart fixes Amarok but then the SL audio goes back to the way it was.

---

### Post by fjleal on 2007-10-24
Greeting!

This issue seems to be solved for me simply by installing esound. Everything sounds great now! :)

---

### Post by Kristopher on 2007-10-24
yeah i had tried that but it didnt work...so i tried again yesterday

1. install esound
2. restart laptop
3. started up SL

All 100% Fine WOOOHOOO. I think the restart was the key here so the process would start up, probably just a CTRL+ALT+BACKSPACE would have done the trick....ah well it works woohoo..

---

### Post by asmiller-ke6seh on 2007-11-19
[SIZE="4"]I want to confirm what worked for me:[/SIZE]

In [COLOR="Navy"]SYNAPTIC PACKAGE MANAGER[/COLOR], search for "esound" and install it.

In the [COLOR="Navy"]secondlife[/COLOR] shell script, uncomment the OSS and ALSA lines; this tells Second Life to use the new ESound (ESD) driver - like this:

> ## - Avoids using the ESD audio driver.
#export LL_BAD_ESD=x

## - Avoids using the OSS audio driver.
export LL_BAD_OSS=x

## - Avoids using the ALSA audio driver.
export LL_BAD_ALSA=x

It worked like a charm.

[SIZE="3"][FONT="Impact"]
I'm using a System76 Serval Performance (serp2) laptop and Ubuntu 7.10 (Gutsy Gibbon)[/FONT][/SIZE]

---

### Post by kattman on 2008-05-20
Can someone help a Newbie ?   Please !!!

---

