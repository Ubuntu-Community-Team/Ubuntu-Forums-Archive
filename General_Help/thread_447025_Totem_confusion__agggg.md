---
title: "Totem confusion  agggg"
date: 2007-05-17
forum: General Help
---

### Post by the lemming on 2007-05-17
Anybody know why I can watch a DVD when I pop it into the DVD drive but I can't when I try and open the DVD from within Totem?

I get the following error

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.

Please install the necessary plugins and restart Totem to be able to play this media.

Anybody know how I solve this problem?

Cheers

---

### Post by spamking2000 on 2007-05-17
when you pop the DVD in, does it launch totem to view it?

---

### Post by strabes on 2007-05-17
Totem sucks. Use VLC, mplayer, anything.

---

### Post by the lemming on 2007-05-18
> **spamking2000 said:**
> when you pop the DVD in, does it launch totem to view it?

That's right.

But when I try to run the disc from the drop-down menu I get the error message

---

### Post by gm0t0 on 2007-05-18
i'm having probs.w/Totem also. 1. i can pop in a dvd, totem opens doesn't play. 2.i can pop in ripped dvd it plays fine? 3.i added demuxer (that totem needed to play ex.1 dvd) and now neither of them play. yet ex.2 worked @ first and the plugin needed to play the first dvd hosed both dvd's now? I admit it is a fresh install of "Studio", like its not even 24hrs. old on the lappy.

---

### Post by vikramsharma on 2007-05-18
> **the lemming said:**
> Anybody know why I can watch a DVD when I pop it into the DVD drive but I can't when I try and open the DVD from within Totem?

I get the following error

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.

Please install the necessary plugins and restart Totem to be able to play this media.

Anybody know how I solve this problem?

Cheers


Installing totem-xine should so the trick also install libxine1, libxine1-ffmpeg, libxine though synaptic. Hope this helps. 

PS Installing totem-xine would remove totem-gstreamer

---

### Post by the lemming on 2007-05-18
> **vikramsharma said:**
> Installing totem-xine should so the trick also install libxine1, libxine1-ffmpeg, libxine though synaptic. Hope this helps. 

PS Installing totem-xine would remove totem-gstreamer

Seing as I am very new to all this Linux stuff, could you please tell me where I can find these recomendations?

Cheers

---

### Post by vikramsharma on 2007-05-18
> **the lemming said:**
> Seing as I am very new to all this Linux stuff, could you please tell me where I can find these recomendations?

Cheers

In the "System" menu go to "Administration" in the "Administration" section go to "Synaptic Package Manager".  In "Synaptic Package Manager" you would be able to find what I am saying.

---

### Post by the lemming on 2007-05-18
> **vikramsharma said:**
> In the "System" menu go to "Administration" in the "Administration" section go to "Synaptic Package Manager".

I'll give it a go after work this evening.

Cheers

---

### Post by the lemming on 2007-05-18
> **vikramsharma said:**
> In the "System" menu go to "Administration" in the "Administration" section go to "Synaptic Package Manager".  In "Synaptic Package Manager" you would be able to find what I am saying.



Agggggggggggggggggg.

I just followed these instructions and I can no longer use the Totem appliction.

Is it possible to undo what I just did?

---

### Post by Cappy on 2007-05-18
```
sudo apt-get install totem-gstreamer
```

---

### Post by the lemming on 2007-05-18
> **Cappy said:**
> ```
sudo apt-get install totem-gstreamer
```

As I said earlier, I am exceptionally new to Linux.

Could you please advise what I should do next?

PLease excuse my ignorence but I really have no idea what to do.

---

### Post by Cappy on 2007-05-18
Copy this:
```
sudo apt-get install totem-gstreamer
```

Open a terminal with the Applications menu: (Applications-->Accessories-->Terminal)
Right click IN the window, click paste. Hit enter if needed.

Edit:
You'll have to enter your password.
Type "y" and press enter when it asks to install it.

---

### Post by the lemming on 2007-05-18
> **Cappy said:**
> Copy this:
```
sudo apt-get install totem-gstreamer
```

Open a terminal with the Applications menu: (Applications-->Accessories-->Terminal)
.


Thanks for that as I had never done it before.

Well, I'm back to square one.  I can watch a DVD when I insert it but not when I click on the DVD icon in the Computer section.

I've tried to install VLP and MPlayer but neither application worked.

I must point out that I am using a copied DVD which I made myself after using DVD Decrypter and DVD Shrink in Windows XP.

I'd appreciate any suggestions.

Cheers


BTW 

May I ask what I just did in the Terminal?

---

### Post by Cappy on 2007-05-18
I did a quick search and this may work:
```
sudo apt-get install totem-xine xine-ui
```
If it still doesn't work, you can always reinstall totem-gstreamer until someone has a better idea =P

The line tell ubuntu package manager to download the packages "totem-xine" and "xine-ui" and install them

---

