---
title: "help for a simple bash script"
date: 2016-06-15
forum: General Help
---

### Post by YaPaY on 2016-06-15
I have a script: check.sh

```
#!/bin/bash
ffmpeg -i http://127.0.0.1:8000/live/user/pass/82.ts 2>&1 | grep aac
```


this script gives me information if the stream (82.ts) has got AAC codec. If everything ok I am getting this line:

[HTML]Stream #0:1[0x101]: Audio: aac (LC) ([15][0][0][0] / 0x000F), 48000 Hz, stereo, fltp, 108 kb/s[/HTML]

I need to use this line for Monit but in this form it is useless for me. I need to check the line and if any stream (in this example 82.ts) hasn't got aac I need to set the file name (or better only filename without extension) to any variable.

example: 82.ts hasn't got aac and when I execute check.sh I can not see any output but I need to see ERRORTS=82 as message.

Is that possible?

---

### Post by &amp;KyT$0P# on 2016-06-15
Does this do what you're looking for?
```
#!/bin/bash
HAS_AAC_OUT=`ffmpeg -i http://127.0.0.1:8000/live/user/pass/82.ts 2>&1 | grep aac`
if [ -z "$HAS_AAC_OUT" ];then
  echo 'ERRORTS=82'
else
  echo "$HAS_AAC_OUT"
fi
```

---

### Post by YaPaY on 2016-06-16
many thanks halogen2 it works. Last thing Is there any possibility to make small modification on the . Can ERRORTS variable get the value from automatically from filename without extension? If this would be hard this is awesome, too.

Thanks again.

---

### Post by btindie on 2016-06-16
```
#!/bin/bash
URL='http://127.0.0.1:8000/live/user/pass/82.ts'
HAS_AAC_OUT=$(ffmpeg -i $URL 2>&1 | grep aac)
if [ -z "$HAS_AAC_OUT" ];then
  FILE=${URL##*/}
  echo "ERRORTS=${FILE%.*}"
else
  echo "$HAS_AAC_OUT"
fi

```

or change URL to take the first parameter passed to the script

```
#!/bin/bash
URL="http://127.0.0.1:8000/live/user/pass/$1"
HAS_AAC_OUT=$(ffmpeg -i $URL 2>&1 | grep aac)
if [ -z "$HAS_AAC_OUT" ];then
  FILE=${URL##*/}
  echo "ERRORTS=${FILE%.*}"
else
  echo "$HAS_AAC_OUT"
fi

```
```
$ ./check.sh 82.ts
```

---

### Post by YaPaY on 2016-06-16
thanks @btindie. It works great

---

### Post by FakeOutdoorsman on 2016-06-17
Use ffprobe instead which eliminates the need for the redirect and grep:
```

$ ffprobe -loglevel error -select_streams a:0 -show_entries stream=codec_name -of default=nw=1:nk=1 input.foo
aac
```

---

### Post by YaPaY on 2016-06-18
it was very useful to gather information. Sometimes encode goes corrupt and single solution the restart the transcode. Is there any possibility the detect any corrupt stream with ffprobe?

---

### Post by FakeOutdoorsman on 2016-06-18
How can I reproduce the issue?

---

### Post by YaPaY on 2016-06-19
if you have interested I can send the link from my corrupted streams but for this we will wait. Sometimes any stream works without corrupt 5-6 days, sometimes only in a few hours goes corrupt.

---

