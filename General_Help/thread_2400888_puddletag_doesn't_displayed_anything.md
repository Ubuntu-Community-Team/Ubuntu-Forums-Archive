---
title: "puddletag doesn't displayed anything"
date: 2018-09-11
forum: General Help
---

### Post by czgirb on 2018-09-11
currently, i'm using xubuntu 18.04 and puddletag 1.2.0 in my compaq cq40 328TU lappie
today i found my unable to displed any information.
when i run puddletag via console, it show me the following information:

```

czgirb@czgirb-laptop:~$ puddletag
puddletag Version: 1.2.0
Locale: en_US
Object::disconnect: Unexpected null parameter
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/05 Drone.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/09 Never Fade.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/03 Red Giant.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/02 Rainier Fog.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/01 The One You Know.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/04 Fly.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/08 So Far Under.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/07 Maybe.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/06 Deaf Ears Blind Eyes.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
An error occured.
/home/czgirb/Downloads/AiC-2018 = Rainier.Fog === iTunes&#8471;2018.AIC.Entertainment,.LLC = BMG.Rights.Management.(US).LLC/10 All I Am.m4a
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/puddlestuff/puddleobjects.py", line 675, in gettag
    return audioinfo.Tag(f)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 298, in ReplacementTag
    return extensions[ext][1](filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/tagmodel.py", line 151, in __init__
    super(ModelTag, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 190, in __init__
    util.MockTag.__init__(self, filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/util.py", line 663, in __init__
    self.link(filename)
  File "/usr/lib/python2.7/dist-packages/puddlestuff/audioinfo/mp4.py", line 366, in link
    isinstance(v, unicode) else v for v in audio[key]]
TypeError: coercing to Unicode: need string or buffer, int found
czgirb@czgirb-laptop:~$ 

```

please guide me what should i do to fix it
thank you

---

