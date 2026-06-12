---
title: "Problem after installing K3b"
date: 2007-10-19
forum: General Help
---

### Post by DrScum on 2007-10-19
I installed k3b from the repository. When I start the program I am getting the following message

Mp3 Audio Decoder plugin not found.
K3b could not load or find the Mp3 decoder plugin. This means that you will not be able to create Audio CDs from Mp3 files. Many Linux distributions do not include Mp3 support for legal reasons.
Solution: To enable Mp3 support, please install the MAD Mp3 decoding library as well as the K3b MAD Mp3 decoder plugin (the latter may already be installed but not functional due to the missing libmad). Some distributions allow installation of Mp3 support via an online update tool (i.e. SuSE's YOU).

how do I go about this. The suggestions in the message don't help, there is neither a mad mp3 decoding library nor a libmad in the Ubuntu repository.

---

### Post by davidjmayo on 2007-10-19
If you are trying to create audio CDs from MP3 I don't know but if not:

If you want to burn anything else just ignore (close) the message and k3b will work fine
I get this message every time I use k3b but haven't looked into how to stop it as it is a minor annoyance

---

### Post by por100pre1 on 2007-10-19
```
sudo aptitude install libk3b2-mp3
```

---

### Post by DrScum on 2007-10-19
Thx that helped!

---

