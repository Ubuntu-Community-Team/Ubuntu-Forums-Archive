---
title: "Sound Does Not Work. Intel High Definition Audio 5.1 Used."
date: 2008-03-25
forum: General Help
---

### Post by Psyon on 2008-03-25
Well, I have had Ubuntu for about two days now, and I need help with my sound. I already have all of the ALSA Programs installed. I use a 503 GR Gateway for Ubuntu with Gutsy Gibbon.I use a Intel Highdefintion Audio 5.1 Sound Card for my sound properties. The speakers that came with the computer do not work due to a broken adapter.

---

### Post by LaRoza on 2008-03-25
> **Psyon said:**
> Well, I have had Ubuntu for about two days now, and I need help with my sound. I already have all of the ALSA Programs installed. I use a 503 GR Gateway for Ubuntu with Gutsy Gibbon.I use a Intel Highdefintion Audio 5.1 Sound Card for my sound properties. The speakers that came with the computer do not work due to a broken adapter.

Wait. You don't have working speakers? How do you expect to get sound?

Are you using another device?

---

### Post by Psyon on 2008-03-26
Yes, I am using headphones.

---

### Post by LaRoza on 2008-03-26
> **Psyon said:**
> Yes, I am using headphones.

Are they connected with USB or the sound jack?

Try installing:
```

sudo aptitude install asoundconf-gtk

```

Then run it with:

```

asoundconf-gtk

```

Select the headphones/adapter

---

### Post by Psyon on 2008-03-26
They are connected to the sound jack. By run, do you mean just type it in the terminal and do I have to restart?

---

### Post by Psyon on 2008-03-26
It's installed. By run do you mean type it in terminal? Because I did and it gave me two sound cards: intel and pulseaudio.

---

### Post by superprash2003 on 2008-03-27
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

