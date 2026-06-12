---
title: "avi to VCD / SVCD aspect ratio not respected in conversion"
date: 2005-07-27
forum: General Help
---

### Post by pallaire on 2005-07-27
Hello all,

Please, help me get rid of my last attachment to windows  \\:D/ 

I have problems to convert avi to vcd / svcd. The resulting video do not have the desired aspect ratio. My sources are 16:9 or 2.35:1 ... my my destination is always deformed to 4:3 ... 

Here is my command:
```
ffmpeg -i source.avi -target svcd -hq -aspect 16:9 -b 1640 ./out.mpg
```

Is there a way to the the encoder to zoom the file while lock the aspect ratio while scaling and to add black bar if needed ? I dont mind trying other converter.

Do I make sens ? I not sure about my english, so here goes a picture :
[IMG]http://www.sypa.net/DotClear/images/Misc/vcd.png[/IMG]

---

