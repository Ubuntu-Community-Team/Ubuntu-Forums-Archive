---
title: "Audio Microphone Gutsy Problem"
date: 2007-11-01
forum: General Help
---

### Post by ZERO_SHIFT on 2007-11-01
My built-in Microphone used to work fine but for some reason it does not work any more.

Any ideas?

I use the HPdv2000 laptop microphone:confused:

---

### Post by ZERO_SHIFT on 2007-11-01
I also Got the following error when testing ALSA input 

```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.
```

Any ideas? I cant use skype! Sound (input and output) do not work in skype.

Thanks in Advance

---

### Post by fadereu on 2007-12-06
Dear All,

Attached is the screenshot of my $alsamixer status in Ubuntu Gutsy.
audio outputs are all working fine, but I can't seem to get my external
microphone working with anything - Chuck programming language,
Audacity, etc.

Any ideas on how to fix this? I'm on a Compaq Presarion C500. And here is
a portion of my $lspci which might be relevant here:

[I]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)[/I]

thanks in advance,:guitar:
-- fadereu
-------    -.-
1/f   )))  --.
-------    ...
[http://www.algomantra.com](http://www.algomantra.com)

---

