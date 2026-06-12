---
title: "LinDVD and Audigy"
date: 2008-03-02
forum: General Help
---

### Post by n3rxs on 2008-03-02
Ok I have LinDVD installed and working and I am using an Audigy sound card. Everything works fine except for some reason under my volume controls I have an item under swtiches called IEC958 and for some reason everytime I play a DVD that switch gets checked and kills my audio.

Now granted I can go in and uncheck it and audio is fine again but I can't seem to figure out what makes it auto check on it's own and how to stop it.

Any ideas?

---

### Post by gobbles414 on 2008-03-03
n3rxs,

I believe that the IEC958 switch enables/disables [SPDIF]("http://en.wikipedia.org/wiki/S/PDIF") audio output. It sounds like LinDVD is defaulting to your SPDIF output instead of your analog output. Look in LinDVD's audio prefereneces and change any instances of  SPDIF or AC3 to 2.0 stereo.

One question... Why are you using LinDVD? It's rather easy to configure Ubuntu's built-in Movie Player for DVD playback. Here's what I do on my Ubuntu machines:

1. Enable the Medibuntu repository using the directions found [here]("https://help.ubuntu.com/community/Medibuntu").
2. Don't forget to install the *libdvdcss2* package.
3. If you want access to your DVD menus, follow the directions found [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").
4. The link in step 3 also contains information of setting your DVD player's region code.

Does that help?

---

