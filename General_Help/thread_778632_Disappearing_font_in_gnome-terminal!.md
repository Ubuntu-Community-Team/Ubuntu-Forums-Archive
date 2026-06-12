---
title: "Disappearing font in gnome-terminal!"
date: 2008-05-02
forum: General Help
---

### Post by oc3an on 2008-05-02
Hi, not sure exactly where to post this..

I've run into an issue with gnome-terminal when using the "Proggy" font, the best way to explain this is through screen shots I think..

The first screen shot (antialias.png) is taken with the following ~/.fonts.conf

```

<fontconfig>
  <match target="font">
    <test name="family">
      <string>ProggyCleanTTSZ</string>
    </test>
    <edit name="pixelsize">
       <double>16</double>
    </edit>
    <edit name="hinting">
       <bool>false</bool>
    </edit>
  </match>
</fontconfig>

```

The second screen shot (no-antialias.png) is taken with antialias forced to false, as required for this font!

```

<fontconfig>
  <match target="font">
    <test name="family">
      <string>ProggyCleanTTSZ</string>
    </test>
    <edit name="pixelsize">
       <double>16</double>
    </edit>
    <edit name="antialias">
       <bool>false</bool>
    </edit>
    <edit name="hinting">
       <bool>false</bool>
    </edit>
  </match>
</fontconfig>

```

As you can see, text is missing from the output of the 'sudo' command, and from the next line.  After that it's fine.

I've only seen this after running 'sudo'!?!?

Anyone have any clue as to why this is happening? It's driving me mad!

Thankyou,

-Patrick

Edit: forgot to mention, running 8.04.

---

### Post by oc3an on 2008-05-04
I've read through everything I can find on font rendering and I have no idea what could be causing this :(

Should I be posting this as a bug somewhere?

---

### Post by oc3an on 2008-05-05
Looks like this issue isn't limited to gnome-terminal.  I've seen it in gvim now too.

---

