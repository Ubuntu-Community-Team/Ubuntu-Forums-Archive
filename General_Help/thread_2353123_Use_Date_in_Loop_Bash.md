---
title: "Use Date in Loop Bash"
date: 2017-02-19
forum: General Help
---

### Post by lp.descamps on 2017-02-19
Hi,

i'm capturing a stream to a file using ffmpeg. I want the file to have the timestamp. a new file is created every 15 min. the issue is it's using the 1st timestamp when it's creating the second file and wants to overwrite the 1st file.

any idea?
thanks

```

#!/bin/bash

IPCAM=rtsp://user:password@10.11.12.13:554//Streaming/Channels/1
DURATION=900
DEST=/home/user/stream/$(date '+%Y-%m-%d_%H%M%S').mp4
APP=/usr/bin/ffmpeg

for (( ; ; ))
do
   $APP -i $IPCAM -vcodec copy -an -t $DURATION $DEST

done

```

---

### Post by steeldriver on 2017-02-19
It should just be a matter of moving the DEST assignment inside the loop

```

#!/bin/bash

IPCAM=rtsp://user:password@10.11.12.13:554//Streaming/Channels/1
DURATION=900
APP=/usr/bin/ffmpeg

for (( ; ; ))
do
   [COLOR=#0000ff]DEST=/home/user/stream/$(date '+%Y-%m-%d_%H%M%S').mp4[/COLOR]
   "$APP" -i "$IPCAM" -vcodec copy -an -t "$DURATION" "$DEST"

done

```

BTW get into the habit of quoting shell variables - also it's a good idea to avoid all-caps names for your private variables (to prevent unintentionally overwriting important environment variables)

---

### Post by lp.descamps on 2017-02-19
perfect thanks! below the final script following your advice

```

#!/bin/bash

ipcam=rtsp://user:password@10.11.12.13:554//Streaming/Channels/1
duration=900
app=/usr/bin/ffmpeg
dest=/home/user/stream/

for (( ; ; ))
do
   destdate=$dest$(date '+%Y-%m-%d_%H%M%S').mp4
   "$app" -i "$ipcam" -vcodec copy -an -t "$duration" "$destdate"

done

```

---

### Post by kingneutron on 2017-02-21
--Please don't forget to mark this thead as SOLVED, thanks...

---

