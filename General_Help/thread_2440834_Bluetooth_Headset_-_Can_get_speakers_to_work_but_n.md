---
title: "Bluetooth Headset - Can get speakers to work but not microphone"
date: 2020-04-15
forum: General Help
---

### Post by Agnishom_Chattopadhyay on 2020-04-15
I am using a bluetooth adapter on my computer to connect to a bluetooth headset which also has a mic. I am using Ubuntu 18.04 LTS and I try going to the settings and setting it as an A2DP Sink or HSP/HFP. When I set it to A2DP sink, the speaker works, the mic does not. When I set it to the other mode, nothing works.

[IMG]https://i.imgur.com/aGT9S89.png[/IMG]

---

### Post by CelticWarrior on 2020-04-15
> When I set it to A2DP sink, the speaker works, the mic does not. 
Which is exactly how it should work. A2DP = Stereo headphones only.

> When I set it to the other mode, nothing works.
HFP = Mono output ("hands-free headset or earset mode) + microphone input. This mode is usable for voice chat apps only.
Exactly how have you came to the conclusion "nothing works"?

---

### Post by Agnishom_Chattopadhyay on 2020-04-15
Thanks for the quick response

I do not know what voice chat apps are. It does not seem to be mirroring audio that is coming from my browser.

When I pair my bluetooth device to my phone, I am able to use it both as a speaker as well as a mic. How can I get the same feature on my Ubuntu machine?

---

### Post by CelticWarrior on 2020-04-15
Voice chat software is Skype and similar. Again, HFP is only for those.
Yes, in Android you can use that way but NOT at the same time. Android toggles modes quite easily but in desktop Linux you have to do it manually. This is unfortunately the part you don't understand: When you're let's say watching Youtube or listening to music in Android you're using A2DP but as soon as you pick up a call it changes to HFP, it doesn't matter if the call is a traditional cellular network call or from a VoIP app (Whatsapp, Skype, Telegram, etc.).

---

### Post by Agnishom_Chattopadhyay on 2020-04-15
So what I understand is that my device is behaving correctly, for a definition of correct which is not very useful.

Okay, so I downloaded Skype from skype.com and tried the echo/call testing service. It does not seem to work over the HSP/HFP mode.

---

