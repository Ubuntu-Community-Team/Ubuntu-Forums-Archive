---
title: "Soundcard"
date: 2008-05-27
forum: General Help
---

### Post by London_Red on 2008-05-27
Hi all. Formatted my computer as i said in my other thread. Totally forgotten what sound card i had. I was wondering if there are any programs on the net which can detect it for me because i have formatted everything so drivers have disappeared and it was built by a mate and i dont think he gave me any documents with it.

Cheers in advance.

---

### Post by Grognot on 2008-05-28
If your sound is currently working in ubuntu you can check for the audio controller in the Device Manager (System -> Preferences -> Hardware Information). Alternatively you can look through your boot messages
```
dmesg | less
```
or
```
cat /proc/asound/cards
```

---

### Post by kpkeerthi on 2008-05-28
Or
```
lspci | grep -i audio
```

---

