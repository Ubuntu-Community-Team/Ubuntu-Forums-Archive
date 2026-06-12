---
title: "Voice-to-Text not working in Google Docs"
date: 2019-10-13
forum: General Help
---

### Post by acrosome2 on 2019-10-13
Hi, all.

My daughter has a learning disability and one of her accommodations is to be allowed to use voice-to-text and text-to-speech for schoolwork, and right now I'm working on the former.  Do I understand correctly that the only truly practical way to do voice-to-text in Ubuntu right now is through Google Docs? (Where they call it "voice typing" for some reason.) Of course it is also helpful that her school uses Google Docs, so really it's the best option for her.  But I can't get it to work.

First, I'm running Ubuntu 18.04- which I keep up to date- and yes I'm using Chromium.  The hardware is a System76 desktop, pretty high-end, so it should be reliable.  I have installed a Blue Yeti mic through the Sounds menu and it works with everything else on the computer... but not Google Docs.  I have tried Incognito Mode and it still didn't work.  I press the mic activation button in Docs and it turns red as it should but the voice-to-text simply doesn't work.  No typing appears on screen.  Google's help forum has been useless.

If I check the tab in the Sounds menu that displays all applications that are currently recording audio then when I press the mic button on Docs a line labeled "Chrome input" does appear, but it has the TV icon with the slashed circle next to it and it all keeps flashing, alternating with a prompt that there are no applications recording audio.  So I'm guessing this is an Ubuntu issue, or maybe Chromium, but probably not Docs?  Nothing in Chromium Settings seems to apply.

Any ideas?

---

### Post by milesweb on 2019-10-14
Yes this has been reported  [https://bugs.chromium.org/p/chromium...?id=902217#c29]("https://bugs.chromium.org/p/chromium/issues/detail?id=902217#c29")

Try to installing Slimjet and the VoiceNote II extension.

OR 

refer the following :
[https://www.debugpoint.com/2018/07/speech-recognition-to-text-in-linux-ubuntu-using-google-docs/](https://www.debugpoint.com/2018/07/speech-recognition-to-text-in-linux-ubuntu-using-google-docs/)

---

### Post by acrosome2 on 2019-10-14
Well, yes, that debug.com article is what I used to set it all up.

Slimjet appears to be a web browser.  How does installing that help?  Does Google Docs's voice typing somehow work with it?

VoiceNote II is a separate speech-to-text extension for Chrome, right?  I installed it but it's not working.  It looks like the mic button doesn't work or something.  Since the last release is from 2014 maybe it's incompatible with newer versions of Chrome?

---

### Post by acrosome2 on 2019-10-14
Well, wow.  The answer is, yes, Google Docs's voice typing **does** magically work with Slimjet.

Thank you!

---

### Post by milesweb on 2019-10-15
That's great.. Glad to see that it solved your problem.

---

