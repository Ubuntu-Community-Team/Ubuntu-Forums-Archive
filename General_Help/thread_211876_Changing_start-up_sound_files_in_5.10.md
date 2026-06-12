---
title: "Changing start-up sound files in 5.10"
date: 2006-07-09
forum: General Help
---

### Post by uncleed on 2006-07-09
I would like to change the start-up, and shut-down sounds to the ones used in Knoppix 4 or 5, i just like the way they sound. I have the files copied from knoppix into a folder on Ubuntu, and totem will play them. I have deleted the default sound files from Ubuntu, and all other sounds still work. How can i install the Knoppix files, and make them work in Ubuntu? Will they have to be, or can they be converted from .ogg files to .wav? Thanks.
Uncleed

---

### Post by ifokkema on 2006-07-09
Hi,

> **uncleed said:**
> I would like to change the start-up, and shut-down sounds to the ones used in Knoppix 4 or 5, i just like the way they sound. I have the files copied from knoppix into a folder on Ubuntu, and totem will play them. I have deleted the default sound files from Ubuntu, and all other sounds still work. How can i install the Knoppix files, and make them work in Ubuntu? Will they have to be, or can they be converted from .ogg files to .wav? Thanks.
Uncleed

You need to go to:
System -> Preferences -> Sound
Then select the 'Sound Events' tab, and scroll down until you see 'System Events'. There's a 'Lon in' and 'Log out' option. You may need to decode the sounds to .wav, use oggdec for that (in the package vorbis-tools).

---

