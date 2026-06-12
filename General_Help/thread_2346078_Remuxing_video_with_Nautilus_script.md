---
title: "Remuxing video with Nautilus script"
date: 2016-12-11
forum: General Help
---

### Post by Roasted on 2016-12-11
Hi friends. I have a scenario where I'd like to be able to right click a file, such as an mkv, go to scripts, click the script, and it remuxes for me. Originally I had hoped to have ffmpeg remux the file (mkv to mkv**) and overwrite the input file. As I dug deeper, I found some discussion suggesting this doesn't really work, as ffmpeg doesn't load the video into a buffer. Because of this, it remuxes the very file it's working on, thus corrupting it. If anybody has any ideas on how I can work around that (basically, remux a video so the output file *is* the same name as what the input file was), that'd be great.

** = Reason I'm remuxing mkv to mkv is to update the mkv headers. In this scenario, the videos often don't know how long they are, so I cannot seek during playback. Remuxing them is a very fast way to re-enable the ability to seek as it seemingly updates the mkv headers to make the video player (totem, vlc, etc) know how long the video actually is. The positive side effect of this is it allows seek to function.

The command I'm working with now is:
for i in *.mkv; do ffmpeg -i "$i" -codec copy "v2-$i"; done

This functions, however I'd like to make it a little bit better. As it stands now, the command does every single mkv in the directory. This is... fine. I don't exactly keep a ton of mkvs in my downloads folder, but I'd just like to see if I could figure out a way to make it pinpointed. That way I can right click an mkv, hit this script in the right click menu, and ONLY the video I right clicked on gets remuxed. Is there a way I can have the script detect which file I clicked on and use that as $i?

Thanks for any suggestions!

---

### Post by TheFu on 2016-12-11
Rename the original file BEFORE starting. Then output to the original filename directly. This is a normal thing.

Can't help with nautilus. Don't use it.  Rather than using *mkv (no need for the '.', since this isn't Windows), why not process $1?

---

### Post by Roasted on 2016-12-11
Thanks for your insight, TheFu. It dawned on me after posting I could probably rename the original, and then name the output back to match the original input name. I haven't tried it yet, but perhaps I'll look into that.

Something interesting has some up since posting this that sparked some curiosity. The story goes like this. I use Bluecherry for video surveillance. I do full time recording. Bluecherry records to mkv files, split into 15 minute segments. If I'm 10 minutes in to a 15 minute recording and I download the video for review, the video players (Totem, VLC) don't know how long the video is. As a result, the slider skips to the end, yet the video keeps playing. The length will say 0:00, yet it'll count up while playing, 0:01, 0:02, 0:03, etc, and in this example would go up to 10 minutes. But... I cannot move the slider, so I have no seek capability. That's where the root of this question came in with adding a Nautilus script to easily remux the video. Reason being, remuxing the mkv seems to update the mkv headers, thus telling video players like Totem and VLC how long it is. With this, I can move the slider, seek through the video, etc.

...but then I downloaded MPV, which works just fine without having to remux the video. I have no idea what sort of black magic MPV is using to know how long the video is despite Totem and VLC choking on this and requiring a remux to figure it out. Very strange, but certainly has me curious on how in the world MPV is making this work.

As a result, using MPV for this task kind of negates what I was after as far as the Nautilus script. Good to know I was on the right track and pretty close to a more refined script, but now I might shift my focus a bit to see what on earth MPV is doing to make this work.

Thanks again!

---

