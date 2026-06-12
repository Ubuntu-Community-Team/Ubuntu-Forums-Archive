---
title: "&quot;Error of failed request&quot;"
date: 2007-10-13
forum: General Help
---

### Post by DevEight on 2007-10-13
Hello guys, wasn't quite sure about which category to put this thread in but I hope this will be alright.

I just started using Ubuntu and I was going to download Beryl and in the guide it wanted me to run a few commands, the response I was supposed to get was:
```

"server glx vendor string: SGI
client glx vendor string: SGI"
```

This is what I got:
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
```

Command run was **glxinfo | grep vendor**

Currently running on a ATi Radeon 9600, if you need any more hardware specs, please let me know. 

I hope you'll be able to help me out, cheers!

---

