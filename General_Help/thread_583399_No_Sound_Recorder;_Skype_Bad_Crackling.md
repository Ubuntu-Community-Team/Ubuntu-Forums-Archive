---
title: "No Sound Recorder; Skype Bad Crackling"
date: 2007-10-20
forum: General Help
---

### Post by iggyigg on 2007-10-20
Please rescue a clueless newbie! :confused:
I'm using Ubuntu Feisty Fawn (7.04) and a modern good-quality Plantronics Skype-compatible headset.  I'm having problems making voice recordings with it (but no probs in listening to CDs, audio clips etc).
When I try to use the [COLOR="Red"]“SOUND RECORDER”[/COLOR], whatever option I choose (Capture, Microphone, MIC Master, mono, Mix, Line-in etc), I get:
[COLOR="Red"]“Your audio capture settings are invalid.  Please correct them in the Multimedia settings.” 
[/COLOR]
I made the posting below (Oct 19) and “001100” kindly sent me a reply, suggesting that I try a DIFFERENT sound recording program.  Do you other guys agree with that?  I'm perplexed (easily done as a newbie!) why that might be the case, as it seems that “Sound Recorder” seems recommended for Ubuntu.  I can't access “Add Programs” or Synaptic Package Manager at the moment (apparently due to the overload because of Gutsy etc) at the moment anyway.  But if you guys think another sound recording program is worth trying, what would you recommend to a clueless newbie?  The only program I could see that might do the same as  “Sound Recorder”, is [COLOR="Red"]“Audacity”[/COLOR] (“Record & Edit Audio Files”) 

“001100” also warned me that Ubuntu might not support the recording features on my sound card. Is there a way to check if my sound card is supported or not (and other cards in general, this would be very useful to know)?!  By the looks of things my sound card is [COLOR="Red"]ESS ES1938 [/COLOR](Solo-1), but I'm confused about this point too (see below).

I'm anxious to resolve this problem, partly so that I can work on my [COLOR="Red"]Skype problem[/COLOR]!  As said below, despite the [COLOR="Red"]crackling and sound distortions[/COLOR] on Skype, my voice can still be heard through it all (including in the Echo test).  I've tried [COLOR="Red"]Ekiga[/COLOR] too; the Echo test on that was MUCH clearer but my voice relayed back to me sounded as if I was on the moon!  But the problem is I'm going to have a tough time to persuade my contacts to download Ekiga...... 

[COLOR="Blue"]MY PREVIOUS POSTING (Oct 19) – a lot of stuff to clear up!
[/COLOR]
I'm using Ubuntu Feisty Fawn (7.04) and a modern good-quality Plantronics Skype-compatible headset.  I'm having problems making voice recordings with it (but no probs in listening to CDs, audio clips etc).
When I try to use the “SOUND RECORDER”, whatever option I choose (Capture, Microphone, MIC Master, mono, Mix, Line-in etc), I get:
[COLOR="Red"]“Your audio capture settings are invalid.  Please correct them in the Multimedia settings.” 
[/COLOR]
I have followed the Community Doc instructions for Audio Capture. So I went to gnome-volume-control; I ticked “Capture” under “Preferences”; I ensured that the microphone and speakers weren't crossed out and I moved the volume on them to maximum.

When I click on “Recording” in Volume Control, I have 3 columns with their individual recording slide bars: Line- In Capture,  Microphone Capture and Capture.  I've turned the volume to maximum on all three.  I have noticed that I can't activate the microphone clicking on the icon at the bottom of each of the 3 columns.  So for example, when I activate Microphone Capture, Line- In Capture then deactivates (ie the red cross on it appears) and vice-versa.  Is that normal?  Whichever permutation I use, the Sound Recorder still doesn't work.

In the Switches tab, there is only one entry: Hardware Volume Split .  I have ticked this too for good measure but it still hasn't made any difference.

Then when I go into [COLOR="Red"]“Sound Preferences” [/COLOR](in the System menu), and I try to test “Sound Capture”, choosing ESS Solo-1, ALSA or OSS (under the “Audio Conferencing” heading), I get the following message:
[COLOR="Red"]“gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.”[/COLOR]
If however, I choose “Test Sound” in “Sound Capture” above, then I hear very briefly the high-pitched sound (as below), followed by an equally brief deep base sound.  Does this indicate a problem?  Are the “Multimedia settings” (referred to in the dialog box) these “Sound Preferences” that I've been trying to adjust?

The Sound Playback pipeline test appears to be successful however under each of the “Sound Events”, “Music & Videos” and “Audio Conferencing” headings – I get a high-pitched continuous sound (similar to EG the BBC test page sound on TV) which only turns off when I click on “ok”.
And another question, I have never downloaded any drivers for my modern Plantronics (Audio-90) headset – can you please confirm that this isn't needed for headsets and that this model should work without problems on Ubuntu?!

I'm also having problems with Skype for Linux (the latest package 1.40.118-1).  I hear a loud crackling in the background, causing sound distortions and break-ups on both ends of the line (including when I use the robot test line). 
 
I'm also confused about sound cards.  Am I correct in thinking that ESS Technology ES1969 (Solo 1) AUDIODRIVE (as listed in my “device manager”) is my Sound card?  If that is the case, then why does ESS ES1938 (Solo-1) appear in my volume control etc?  I can't find ESS ES1938 (Solo-1) listed in my Device Manager – is that normal?

MANY THANKS FOR ANY HELP!! :KS

---

