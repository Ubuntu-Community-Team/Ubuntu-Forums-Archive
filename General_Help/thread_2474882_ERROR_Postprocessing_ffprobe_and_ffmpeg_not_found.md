---
title: "ERROR: Postprocessing: ffprobe and ffmpeg not found"
date: 2022-05-11
forum: General Help
---

### Post by sofasurfer on 2022-05-11
I tried to download a video using yt-dlp. This is what I did...
```
 $ cd Download; yt-dlp -x --audio-format mp3 https://youtu.be/MujE5tObk50
bash: cd: Download: No such file or directory
[youtube] MujE5tObk50: Downloading webpage
[youtube] MujE5tObk50: Downloading android player API JSON
[info] MujE5tObk50: Downloading 1 format(s): 251
[download] How the Pro's sharpen a chainsaw [MujE5tObk50].webm has already been downloaded
[download] 100% of 12.82MiB
ERROR: Postprocessing: ffprobe and ffmpeg not found. Please install or provide the path using --ffmpeg-location

```
I installed and upgraded ffmpeg and this made no difference. What is happening? I bever had this problem until I recently did a system reinstall.

---

### Post by sofasurfer on 2022-05-11
I just noticed that I was trying to cd into Download instead of Downloads. I changed that but I am still getting the ffprobe/ffmpeg error.
The video downloads but I only have audio and no video.

---

### Post by sofasurfer on 2022-05-12
I found the answer. In the command line ```
 yt-dlp -x --audio-format mp3 https://youtu.be/MujE5tObk50 
``` I had to add ```
 --ffmpeg-location /usr/bin 
```. Now it works fine.
Until I did a recent OS reinstall I never had this problem. My question is, why doesn't yt-dlp know is own path to the yt-dlp binary file? Is there a config file that needs to be edited? Would a yt-dlp reinstall help? If yt-dpl is required to know the path to its binary file then I think it should be built in.

---

### Post by andrew.46 on 2022-06-12
> **sofasurfer said:**
> [...]My question is, why doesn't yt-dlp know is own path to the yt-dlp binary file? Is there a config file that needs to be edited? Would a yt-dlp reinstall help? If yt-dpl is required to know the path to its binary file then I think it should be built in.

That does seem a little odd. It would be interesting to see your $PATH statement:

```

echo $PATH

```

as well as the results of a generic search for ffmpeg:

```

sudo find / -iname ffmpeg

```

There might be some clues in there. If nothing turns up your option (--ffmpeg-location /usr/bin) can be placed in a configuration file so it does not need to be typed in every time. Details [here...]("https://github.com/yt-dlp/yt-dlp/blob/master/README.md#configuration")

FWIW I tested your YouTube mp3 extraction example and it worked flawlessly here.

---

