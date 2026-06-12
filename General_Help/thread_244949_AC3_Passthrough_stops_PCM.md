---
title: "AC3 Passthrough stops PCM"
date: 2006-08-27
forum: General Help
---

### Post by the_tiger on 2006-08-27
I use an optical out connection to my external amp. Since upgrading to Dapper I have been able to listen to music output as PCM over SPDIF. However this recently stopped working and I have found it is caused by enabling AC3 Passthrough in Totem. I have found an ugly method of getting sound to work again by tweaking a post by Shu - 

```
chmod -x /etc/init.d/alsa-utils
```

*Restart*

```
alsactl store
```

```
chmod +x /etc/init.d/alsa-utils
```

However as soon as I output a movie this needs to be done again. I also can no longer mute the IEC-958 slider anymore. It simply appears as unmuted when I open the sound settings again. Please help!

---

