---
title: "Disable Speakers in Laptop"
date: 2008-03-27
forum: General Help
---

### Post by Tews on 2008-03-27
I have been having a problem with my Sony Vaio AR630e.  When I have my external speakers/headphones plugged in, I still get sound out of the laptop speakers!  Has anyone been able to solve this problem?  Ive done a search of the forums, but no luck so far ...

Thanks

---

### Post by Ub1476 on 2008-03-27
Just a guess, but maybe you can disable something from

```
alsamixer
```

---

### Post by amd is the best on 2008-03-29
I am getting the same issue with my HP laptop.  All sound works properly but when I plug in headphones and/or external speakers my laptop's speakers will continue to put out sound.

Nick

---

### Post by danwood76 on 2008-03-29
In the gnome volume control click the switches section and make sure that 'headphones' is ticked.
If its not ticked it wont shut of the sound when you plug headphones in.

---

### Post by amd is the best on 2008-03-29
> **danwood76 said:**
> In the gnome volume control click the switches section and make sure that 'headphones' is ticked.
If its not ticked it wont shut of the sound when you plug headphones in.

I right click on the sound icon near the clock and go to open volume control but I don't see a mention of headphones anywhere in there.

Please advise and thank you,
Nick

---

### Post by danwood76 on 2008-03-29
This is what I have for the headphone switching, admitidly this is on my desktop but I have the same option on my laptop too.

If you dont have that option click edit -> prefrences and look for a headphone option (highlighted in my second image) and make sure its selected.

---

### Post by Tews on 2008-03-29
Thanks for the suggestions, but my mixer is OSS and doesnt have the headphone option.

---

### Post by amd is the best on 2008-03-29
Wow, I actually have none of those options in my list.

---

### Post by danwood76 on 2008-03-29
It could be that the alsa driver is not quite finished for your sound card.
Im assuming you have a HDA-Intel sound card?
These drivers arent quite complete for most laptops, though you can choose different options which might hlp you.

---

### Post by amd is the best on 2008-03-29
I have HDA-NVidia sound on my laptop.

---

