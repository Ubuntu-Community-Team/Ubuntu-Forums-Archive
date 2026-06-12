---
title: "Totem media thumbnails consuming CPU cycles?"
date: 2007-08-04
forum: General Help
---

### Post by Mblackwell on 2007-08-04
I wasn't sure exactly where to mention this, so it's not a filed bug since I wasn't even exactly sure of the source. But amazingly I discovered a strange source of my system being slowed down. (note: for reference I am using Ubuntu Feisty 7.04)

I happened to be navigated to a "movies" folder and was downloading a trailer. My computer was going very slowly and I couldn't figure out why and I started closing applications and strangely after I closed the file manager everything sped up. I noticed that it continued to go fast until I navigated back into that folder.

The thing that struck me was that all of the movies have a thumbnail associated with them, except the one I'm downloading (since of course it's not a whole file yet).

I did two checks, the first with glxgears to make sure it wasn't just some hitches and was actually a significant drop. My results where:

```

17803 frames in 5.0 seconds = 3560.567 FPS
17828 frames in 5.0 seconds = 3565.539 FPS
16769 frames in 5.0 seconds = 3353.666 FPS
3804 frames in 5.0 seconds = 759.763 FPS
2358 frames in 5.0 seconds = 471.583 FPS
3122 frames in 5.0 seconds = 621.416 FPS

```

During this test I navigated to the folder, and as you can see there is a significant performance drop (around 80%+).

Then I used top to check the system load and got these numbers:

Before going in to the folder:
```

Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  1.7%sy,  0.0%ni, 93.1%id,  0.0%wa,  0.0%hi,  0.9%si,  0.0%st
Mem:   1035732k total,  1017632k used,    18100k free,    55896k buffers
Swap:  3028212k total,    23312k used,  3004900k free,   545976k cached

```

After:
```

Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.6%us, 10.3%sy, 65.5%ni,  0.0%id,  0.0%wa,  0.0%hi,  2.6%si,  0.0%st
Mem:   1035732k total,  1015940k used,    19792k free,    59840k buffers
Swap:  3028212k total,    23312k used,  3004900k free,   539036k cached

```

So there you go, we suddenly jump from barely any CPU being used by applications to all of it.

I wasn't sure if it was beagle or what at first, but it turns out the only actually new application being launched at this time is "totem-video-thumbnailer". So all I can determine is that the program is attempting to create a thumbnail from a non-accessible video file over and over and getting stuck (eating resources in the process) until you navigate out.

I'm hoping someone else reads this and can confirm it so it gets reported.

---

### Post by Mblackwell on 2007-08-05
bump

---

### Post by dn* on 2007-12-28
I can confirm this. I run Xubuntu 7.10 on an Advent 7027 laptop and when i leave a folder with a video file open, my CPU usage is 100% (the usage being totem's thumbnail generator).

edit: i've done some fiddling about and it seems turning off compositing in xubuntu has resolved the issue. i'm guessing it's something related to the graphics card (a radeon 9000) in the laptop being a bit poor. the laptop is actually running good as new now, it's excellent!

---

### Post by crjackson on 2007-12-28
> **Mblackwell said:**
> I wasn't sure exactly where to mention this, so it's not a filed bug since I wasn't even exactly sure of the source. But amazingly I discovered a strange source of my system being slowed down. (note: for reference I am using Ubuntu Feisty 7.04)

I happened to be navigated to a "movies" folder and was downloading a trailer. My computer was going very slowly and I couldn't figure out why and I started closing applications and strangely after I closed the file manager everything sped up. I noticed that it continued to go fast until I navigated back into that folder.

The thing that struck me was that all of the movies have a thumbnail associated with them, except the one I'm downloading (since of course it's not a whole file yet).

I did two checks, the first with glxgears to make sure it wasn't just some hitches and was actually a significant drop. My results where:

```

17803 frames in 5.0 seconds = 3560.567 FPS
17828 frames in 5.0 seconds = 3565.539 FPS
16769 frames in 5.0 seconds = 3353.666 FPS
3804 frames in 5.0 seconds = 759.763 FPS
2358 frames in 5.0 seconds = 471.583 FPS
3122 frames in 5.0 seconds = 621.416 FPS

```

During this test I navigated to the folder, and as you can see there is a significant performance drop (around 80%+).

Then I used top to check the system load and got these numbers:

Before going in to the folder:
```

Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  1.7%sy,  0.0%ni, 93.1%id,  0.0%wa,  0.0%hi,  0.9%si,  0.0%st
Mem:   1035732k total,  1017632k used,    18100k free,    55896k buffers
Swap:  3028212k total,    23312k used,  3004900k free,   545976k cached

```

After:
```

Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.6%us, 10.3%sy, 65.5%ni,  0.0%id,  0.0%wa,  0.0%hi,  2.6%si,  0.0%st
Mem:   1035732k total,  1015940k used,    19792k free,    59840k buffers
Swap:  3028212k total,    23312k used,  3004900k free,   539036k cached

```

So there you go, we suddenly jump from barely any CPU being used by applications to all of it.

I wasn't sure if it was beagle or what at first, but it turns out the only actually new application being launched at this time is "totem-video-thumbnailer". So all I can determine is that the program is attempting to create a thumbnail from a non-accessible video file over and over and getting stuck (eating resources in the process) until you navigate out.

I'm hoping someone else reads this and can confirm it so it gets reported.

You need to report the bug on launchpad.  Don't count on anyone else doing it.  That's the only way to get it resolved.

---

