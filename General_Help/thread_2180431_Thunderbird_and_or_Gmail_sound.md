---
title: "Thunderbird and or Gmail sound"
date: 2013-10-12
forum: General Help
---

### Post by Big_tone on 2013-10-12
Hello, all..

I am using Ubuntu 13.04 and for a while now, haven't been able to get sounds working in Mozilla Thunderbird. I know that Gmail (which is my email provider) doesn't allow you to play sound notifications (when logged into their site).

Is there a good method for getting either Thunderbird or Gmail "proper" to play sounds when a new mail arrives?  I've searched the internet for answers but only come across others having the same problem or outdated replies.

Any help would be greatly appreciated.

---

### Post by jz77f on 2014-01-26
This is how I solved the problem:
1. Install pulseaudio ("PulseAudio sound server" from Ubuntu Software Center)
2. Install PulseAudio Manager (from Ubuntu Software Center)
3. In Ubuntu Dash search for "PulseAudio Volume Control"
4. Run it. When it opens, click on Playback tab
5. Under System sounds, you should see a horizontal slider for volume. Mine was near Silence. It that is also your case, drag it to 100%.
6. Close PulseAudio Volume Control. Now your Thunderbird notification sound should be heard.

jz77f

---

### Post by deadflowr on 2014-01-26
post #2 seems like a lot more work than actually needed.

All I did was opened thunderbird.
Then go to edit.
The scroll down to preferences.
click on the tab for genral.
You set the sound settings there.
It'll even let you playback the sound.

I works fine for me.

---

