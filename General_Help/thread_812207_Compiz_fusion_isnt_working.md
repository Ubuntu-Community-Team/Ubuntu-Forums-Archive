---
title: "Compiz fusion isnt working"
date: 2008-05-29
forum: General Help
---

### Post by Spoken on 2008-05-29
alright, so when i upgraded from 7.10 to 8.04 i have had trouble getting compiz to work.

i go to apperance > visual effects and try to turn them on. but it just prompts me saying "could not be enabled"

when i go to preferences > ccsm , all of the plugins are faded and i cant select nor deselect anything.

my graphics card was blacklisted for 7.10 but according to 8.04 it isnt anymore, but i have no idea if this statement is true or false.  my card is a intel media accelorator 3100x.

ive tried running skip_check through terminal just incase and it hasnt changed anything. thats why im so unsure about my g-card being blacklisted or whatnot.

i can kinda get compiz to work if i use compiz-icon but that just gives me a basic cube etc, i still cant modify ccsm or anything. so....

ive tried uninstalling and reinstalling compiz through add/remove and nothing has changed.

when i run  "compiz --replace" through terminal it removes my metacity titlebars and moves all open windows to the top of the screen, making them uncloseable, unmoveable, and unusable. which is weird cause in ccsm i have windows decorations enabled.  this forces me to reboot so as of now this code isnt an option lol.

here is the output in terminal i get when i run that code:

```

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

ive tried many suggestions and guides, and still no prevail. ive used compiz check and it gave me an "ok" on all checks, so my current system / setup is capable of running compiz.

anyone got any ideas? :confused:

EDIT: oh and last thing, im missing about 1/3 of the plugins that came with the original install i got with 7.10, just noticed.

---

### Post by Spoken on 2008-05-29
alright, so when i upgraded from 7.10 to 8.04 i have had trouble getting compiz to work.

i go to apperance > visual effects and try to turn them on. but it just prompts me saying "could not be enabled"

when i go to preferences > ccsm , all of the plugins are faded and i cant select nor deselect anything.

my graphics card was blacklisted for 7.10 but according to 8.04 it isnt anymore, but i have no idea if this statement is true or false. my card is a intel media accelorator 3100x.

ive tried running skip_check through terminal just incase and it hasnt changed anything. thats why im so unsure about my g-card being blacklisted or whatnot.

i can kinda get compiz to work if i use compiz-icon but that just gives me a basic cube etc, i still cant modify ccsm or anything. so....

ive tried uninstalling and reinstalling compiz through add/remove and nothing has changed.

when i run "compiz --replace" through terminal it removes my metacity titlebars and moves all open windows to the top of the screen, making them uncloseable, unmoveable, and unusable.

ive tried many suggestions and guides, and still no prevail. ive used compiz check and it gave me an "ok" on all checks, so my current system / setup is capable of running compiz.

anyone got any ideas? :confused:

EDIT: oh and last thing, im missing about 1/3 of the plugins that came with the original install i got with 7.10, just noticed.
__________________

---

### Post by ercferret18 on 2008-05-29
try going to administration, hardware devices, and install the proprietary (or however you spell that) driver

---

### Post by Spoken on 2008-05-29
the closest thing i have to that under administration is "hardware drivers", and when i open it, there isnt anything listed, nor is there any option for installing / enabling any.

---

### Post by ercferret18 on 2008-05-29
yeah thats the right one... thats what worked for me...

---

### Post by ercferret18 on 2008-05-29
i think your graphics card isnt compatible with it... o and to fix ur title bars right click the compiz icon and go to window decerator and select emerald

---

### Post by Spoken on 2008-05-29
there is a statement at the top of the hardware drivers dialog box that pops up, "no proprietary drivers are in use on this system"

so....:confused:

---

### Post by ercferret18 on 2008-05-29
what kind of graphics card do you have... try getting the linux version of the driver from the manufacturer

---

### Post by Spoken on 2008-05-29
my g-card is definitely compatable, ive already ran the checks for it.  every step that test took "ok'd" everything.  so i doubt its that.  idk if its a driver that i need or what, but i really dont know.

---

### Post by Spoken on 2008-05-29
i have a intel media accelorator 3100X , and as i stated before, it was blacklisted for 7.10, but 8.04 states that its not anymore.  so idk.  how would i go about getting the appropriate drivers?

---

### Post by criskat777 on 2008-05-29
Have you installed and run EnvyNG? if you have not go to synaptic and install it. then install your ATI Drivers with it.

---

### Post by ercferret18 on 2008-05-29
you might have a driver, but it might not provide full functionality (thats what happened to me) by the way, when you enable desktop effects from the icon, are they slow?

---

### Post by issih on 2008-05-29
I suspect you should ignore everything said about drivers thus far. If you had an ati or an nvidia card the graphics driver would indeed be the first port of call, but you don't, you have an intel one, and in my experience (from putting ubuntu on a macbook which has x3100 graphics) you do not need any proprietary drivers at all. The open source ones used by default will work just fine.

I suspect that you have managed to end up in the same state as I did after upgrading to hardy.

Open ccsm, then in the list on the left hand side click Preferences.

On the Plugin List tab ensure that "Automatic plugin sorting" is enabled. Now go back to the main ccsm page, and hopefully your plugins are no longer greyed out, and you will be able to enable them.

Hope thats the problem, otherwise I'm stuck :s

---

### Post by 00arthuryu on 2008-05-29
make sure you enable window decorations in ccsm before you do compiz --replace

---

### Post by Spoken on 2008-05-29
EDIT: nvm, ur right issih, no reason to use envy, for i have a intel card., let me try what you said.

---

### Post by Spoken on 2008-05-29
alright, so i turned the plugins to "automatic", idk how that got changed. but my plugins are now selectable. yet still, when i try to turn on visual effects it says its unable to do so.

what is the next step i should undertake :P

---

### Post by Spoken on 2008-05-29
EDIT: nvm, im lame :P.

anyone else have any ideas?

---

### Post by issih on 2008-05-29
Curious, check you have direct rendering enabled....

Something like "glxinfo | grep direct" ought to show you.

If you now ensure the Window decoration plugin is enabled in ccsm can you do compiz --replace and still have titlebars etc

If not, what does compiz --replace spit out in the terminal as error messages?

In the end doing a complete removal of all compiz packages in synaptic might be a good idea, then bring them back, although you may well have been round that merry go round once already

let us know what you can/can't do now

---

### Post by issih on 2008-05-29
One more random thought, the box I had issues with had at one point been running compiz/beryl via XGL, XGL is not used any more, so if you've had that installed at some point maybe its related. If so just remove the offending xgl server via synaptic.

---

### Post by starcannon on 2008-05-29
Just gonna throw this link up here for you to look into:

[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

It looks like the Intel 965 drivers will get you going, its the same gpu, the x3100 is a stand alone gpu where the 965 has other stuff built into it as well from what I'm reading.

GL

---

### Post by Spoken on 2008-05-29
here is the output i get (along with everything messing up) when i do "compiz --replace"

```

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

and yes, i do have rendering enabled.

EDIT: yea i have already tried completely removing everything then reinstalling. nothing...

---

### Post by Spoken on 2008-05-29
AND ALSO, as it shows in synaptic, xglserver is uninstalled, so its not that either :L.

---

### Post by Spoken on 2008-05-29
i just noticed that that error message i got from "compiz --replace" has a glx error in it, but glx isnt even installed when i look in synaptic. :confused:

---

### Post by Spoken on 2008-05-29
it is enabled, :l, but yet it still messes up when i run that command.

---

### Post by issih on 2008-05-29
Couple of possible fixes, no idea if these might help really, but worth checking:

[http://ubuntuforums.org/showthread.php?t=532289](http://ubuntuforums.org/showthread.php?t=532289)

[http://ubuntuforums.org/showthread.php?t=663848](http://ubuntuforums.org/showthread.php?t=663848)

A lot of threads on this are related to needing XGL, but I'm fairly certin that is not the case now at all..XGL has been killed summarily :)

---

### Post by Spoken on 2008-05-29
in that first link they say that a lot of people have been having problems if their settings werent set before the 19th, so i guess this is forcing me to wait a week or 2 for the fixes to be released or whatever. gah, dissapointment :(

---

### Post by issih on 2008-05-29
Um...I doubt that bit is relevant...look at the dates on those posts a bit more carefully :)

---

### Post by Spoken on 2008-05-29
oh, ur fault, gave me outdated links :P jk jk...but seriously

i have no clue what to do now :p

---

### Post by techstop on 2008-05-29
You really shouldn't [crosspost]("http://ubuntuforums.org/showthread.php?t=812207").

---

### Post by issih on 2008-05-29
Have you tried the fixes mentioned in those two threads I posted?

---

### Post by Spoken on 2008-05-29
are u suggesting i install and run xgl?  eventhough its outdated? i have no problem with that if its a quick fix until i find another solution.

---

### Post by Tamjay on 2008-05-29
just for kicks try this in a terminal with visual effects ticked "none":


```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace --sm-disable ccp &
```


just out of curriosity, before the upgrade were you using compiz from git or ubuntu supplied?

---

### Post by Tamjay on 2008-05-29
just for kicks try this in a terminal:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace --sm-disable ccp &
```

---

### Post by Forlong on 2008-05-30
Run [this]("http://ubuntuforums.org/showthread.php?t=799070") and post the output here.

---

