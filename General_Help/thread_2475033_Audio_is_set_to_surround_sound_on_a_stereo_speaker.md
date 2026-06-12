---
title: "Audio is set to surround sound on a stereo speaker setup"
date: 2022-05-14
forum: General Help
---

### Post by egursin on 2022-05-14
Hello, total linux newb here. i have an audio setup with an external soundcard, scarlett 18i8. I notice when i play games I sometimes hear sounds very faintly and sometimes way too loud, as if speakers in the setup is missing. 
I checked sound settings and as you can see on this screenshot:

[IMG]https://i.imgur.com/OGRGHpe.png[/IMG]
it seems like the settings are set to a surround sound speaker setup. 
There is no alternative in the settings to switch it to stereo as far as i can tell. How do i fix this?

---

### Post by Yellow Pasque on 2022-05-15
Check the card's settings in pavucontrol and alsamixer:
```
pavucontrol
alsamixer
```

---

