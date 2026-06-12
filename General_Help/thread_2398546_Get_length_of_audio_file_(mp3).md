---
title: "Get length of audio file (mp3)"
date: 2018-08-14
forum: General Help
---

### Post by raleigh3 on 2018-08-14
I am trying to get the length of a mp3 file.

```
soxi -D Alarm-sound-buzzer.mp3
soxi FAIL formats: no handler for file extension `mp3'
```

---

### Post by oygle on 2018-08-14
This bash script works fine for me.

```

#!/bin/bash
find /root/dir -name "*.mp3" -o -name "*.mp4" | while read file;
do
 duration=$(ffprobe "$file" 2>&1 | awk '/Duration/ { print $2 }')
 echo -e $file"\t"$duration
done | sort -n
```

Just change "/root/dir" to the path required. There is a TAB before duration , as I had hundreds of files, so just imported the output from the bash script into a spreadsheet.

---

### Post by ajgreeny on 2018-08-14
You could also install mediainfo if you don't have it and run command ```
mediainfo path/to/filename.mp3 | grep Duration
```

---

### Post by mc4man on 2018-08-14
As far as sox - for mp3,
```
sudo apt install libsox-fmt-mp3
```
or for all
```
sudo apt install libsox-fmt-all
```

---

### Post by raleigh3 on 2018-08-14
Thanks to all.

I went with mediainfo.

---

### Post by Yellow Pasque on 2018-08-15
> **mc4man said:**
> As far as sox - for mp3,
```
sudo apt install libsox-fmt-mp3
```

With mp3 patents expiring, this really shouldn't be a separate package anymore, should it?
I don't see a Debian bug report requesting this. I wonder if I should file one.

---

