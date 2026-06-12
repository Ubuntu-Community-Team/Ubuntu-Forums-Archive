---
title: "Mathematica 6.0 in Hardy Render Error Workaround"
date: 2008-04-22
forum: General Help
---

### Post by jsmidt on 2008-04-22
Mathematica 6 is not rendering properly in Hardy (Ubuntu 8.4) for several people.

For me, the text won't display when I type, and I get this error:

```
X Error of failed request:  RenderBadPicture (invalid Picture parameter)
  Major opcode of failed request:  155 (RENDER)
  Minor opcode of failed request:  7 (RenderFreePicture)
  Picture id in failed request: 0x3200035
  Serial number of failed request:  12017
  Current serial number in output stream:  12252
```

For a quick workaround, start Mathematica using this command in the terminal:

```
mathematica -defaultvisual
```

See [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163") for more details in Launchpad.  The bugs title is:
"Unable to input text to mathematica 6.0.1 in Hardy (regression from Gutsy)"

Good Luck. :)

PS.  I'm not sure which forum to put this in so I will put it in the general help until it is moved to the proper place.  (Please delete this sentance after that.)

---

### Post by chellrose on 2009-07-27
From here: [http://www.linuxtent.com/?p=83](http://www.linuxtent.com/?p=83)

1) Make sure you have libqt4-core and libqt4-gui installed (use synaptics or aptitude),
2) remove (delete or backup somewhere) these files:
PathToMathematica/SystemFiles/Libraries/Linux/libQtCore.so.4
PathToMathematica/SystemFiles/Libraries/Linux/libQtGui.so.4
where PathToMathematica is typicaly /usr/local/Wolfram/Mathematica/6.0
(Substitute Linux-x86-64 for Linux if needed.)

BTW (and completely off-topic), that is an awesome avatar. :)

---

