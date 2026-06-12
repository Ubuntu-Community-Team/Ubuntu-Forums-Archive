---
title: "lost evolution new mail sound"
date: 2008-04-24
forum: General Help
---

### Post by rplantz on 2008-04-24
I just upgraded from 7.10 to 8.04. Now I cannot set Evolution's new mail arrival sound. I do get a beep, but I used to be able to set a sound.

Help for Evolution claims:
> 
New Mail Notifications:
Evolution can alert you to the arrival of new mail with a beep or by playing a sound file. Choose your alert noise, or select none, as you prefer. You can choose not to notify on new mail arrival.

but I don't see it.

Does anyone else have this same problem?

---

### Post by canadianwriterman on 2008-04-25
You're right, it's gone from the preferences menu. However, it works if you go to Edit > Plugins > Mail Notification, open the Configuration tab and select a notification sound at the bottom. I had to restart to get it activated.

---

### Post by rplantz on 2008-04-25
> **canadianwriterman said:**
> ...go to Edit > Plugins > Mail Notification, open the Configuration tab and select a notification sound at the bottom. I had to restart to get it activated.

Thank you! It actually makes some sense. Now someone needs to fix the help documentation.

---

### Post by sgtkazz on 2008-09-17
I've changed my Mail Notification in the Plugin for Evolution and it will not play the sound. It will play the 'beep' but will not play 'any' WAV files. This is still a bug IMO.

---

### Post by christianvaldes on 2008-10-09
> **sgtkazz said:**
> I've changed my Mail Notification in the Plugin for Evolution and it will not play the sound. It will play the 'beep' but will not play 'any' WAV files. This is still a bug IMO.

Hey I really liked this feature. 
The exact same thing happen to me.
Is there any fix?

---

### Post by ricky08 on 2008-11-05
Also got the same problem. Evolution will play the default system beep (from the pc speaker), but this is very quiet and easily missed. 

I have tried setting a new .wav file sound in 

[COLOR="Red"]Edit > Plugins > Mail Notification > Configuration[/COLOR]

But the sound will not play from the test icon, or when new mail is received. I've also re-started evolution to no avail.

Is this a bug in Evolution, or am I using an incompatible sound file format (i.e. .wav). Do I need an ogg or something similar?.

Cheers, 

Ricky

ps, now 3-weeks into UBUNTU from XP, and NO GOING BACK - EVER !!!

---

### Post by mykrob on 2008-11-25
got the same problem here. It worked fine in the beta, but after a clean install of the finished product, no sound on incoming email.

---

### Post by clever on 2009-03-24
My sound won't play for a new email either.  I configure a sound file in the Mail Notification plugin, but the "Play" button to test the sound doesn't do anything.

Have any of you guys found a solution?

---

### Post by dcstar on 2009-03-25
> **clever said:**
> My sound won't play for a new email either.  I configure a sound file in the Mail Notification plugin, but the "Play" button to test the sound doesn't do anything.

Have any of you guys found a solution?

Works perfectly on my 8.04 system.

---

### Post by prostar on 2009-03-31
Neither beep, nor sound file works for me (tried .wav and .mp3). Also, does anyone know how to:

- Get sound for calendar events?
- Make calendar reminders repeat by default?

EDIT: Using 8.10 with backports enabled.

Thanks

---

### Post by spacesamurai on 2009-04-30
Add me to the list of having the same problem. Tried midi as well to no avail.

---

### Post by pepperedeggs on 2009-06-19
Yeah same here, I have tried ogg, mp3 and wav files and it makes no difference. Idea's would be much appreciated.

---

### Post by Frobozky on 2009-06-19
I believe evolution depends on esd (esound) so you need the pulseaudio esound plugin.  If you have pulseaudio disabled, I am not sure how to get evolution mail notification sound working.

---

### Post by pepperedeggs on 2009-06-22
Yes, thanks I had seen this already however I do have pulse audio enabled and working but evolution has a bug in the latest version 2.22 with jaunty main. However as already stated this is a low level issue so I guess we will have to wait :(

---

### Post by nortexoid on 2009-10-31
Same problem as everyone else. Look how old this thread is and it's still not fixed. Crazy.

---

### Post by Cyoor on 2010-03-07
Same problem still..

Anyone gotten it solved yet?

---

### Post by Rodney9 on 2010-05-20
> **Cyoor said:**
> Same problem still..

Anyone gotten it solved yet?

On Ubuntu 10.4 64bit with Evolution 2.8.3 it worked for me with a wav sound,* Hurray* !

---

### Post by Redsunz on 2010-06-18
> **Rodney9 said:**
> On Ubuntu 10.4 64bit with Evolution 2.8.3 it worked for me with a wav sound,* Hurray* !

Hmm I have Ubuntu 10.04 64bit Evolution 2.28.3 and it's not working.  Is there a size requirement for the wav the one I want is 133k

---

### Post by philinux on 2010-06-18
I'm using one that's 980kb. Only stops working after a suspend.
[https://bugs.launchpad.net/evolution/+bug/292585/comments/19](https://bugs.launchpad.net/evolution/+bug/292585/comments/19)

I forgot after I'd posted that that it's easier to goto Edit>plugins in evo.

---

### Post by oubiwann on 2010-06-30
In 10.04, I havne't been able to use .ogg files for this. After testing other file types, I found that .wav previewed consistently. I then used Audacity to convert the desired .ogg notification file to a .wav.

To complicate matters, after I selected the new wave file, when I hit preview, the old one played. I then selected an .ogg that didn't play, hit preview, and then selected the desired .wav. Preview *still* didn't work. I closed the plugins dialog, re-opened it, and didn't get any result from the play button until it was hit multiple times. 

Needless to say, a terrible user experience story...

That being said, the notification just went off as I was typing this message, so in the end there was success.

---

### Post by Andrew_P on 2012-04-05
> **oubiwann said:**
> That being said, the notification just went off as I was typing this message, so in the end there was success.

That wasn't success.  That was a fluke.:(  I'm finding Evolution 2.28.3 on Lucid Lynx to be so buggy and inconsistent in its behavior as to make it useless.  For example, the calendar notification works with sound and pop-up message on rare occasions; usually just the message pops up; sometimes neither appears.  The GUI settings seem to be completely out of sync with what Configuration Editor (gconf-editor) shows, and some features in the Evolution GUI seem to have no corresponding parameters in gconf-editor, i.e., they're probably non-functional, just put there to make one tear one's hair out.

---

