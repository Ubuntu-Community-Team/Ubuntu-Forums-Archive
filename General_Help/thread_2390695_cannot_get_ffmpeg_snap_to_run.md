---
title: "cannot get ffmpeg snap to run"
date: 2018-05-01
forum: General Help
---

### Post by bugsquisher on 2018-05-01
Apologies if this has been posted before, I could not find it via the search so I thought I would ask.

I have installed the [FONT=courier new]ffmpeg[/FONT] snap with the following command:

```

bugsquisher@workhorse:~$ snap install ffmpeg

```

However, when executing [FONT=courier new]ffmpeg[/FONT] it returns the following:

```

bugsquisher@workhorse:~$ ffmpeg/snap/ffmpeg/3/usr/local/bin/ffmpeg: error while loading shared libraries: libpulsecommon-8.0.so: cannot open shared object file: No such file or directory

```

The snap is very definitely up-to-date:

```

bugsquisher@workhorse:~$ snap refreshAll snaps up to date.

```


The snap reports the following information:

```

bugsquisher@workhorse:~$ snap info ffmpeg
name:      ffmpeg
summary:   Record, convert, and stream audio and video
publisher: snapcrafters
contact:   https://github.com/snapcrafters/ffmpeg/issues
license:   unknown
description: |
  FFmpeg is a collection of libraries and tools to process multimedia content
  such as audio, video, subtitles and related metadata.
commands:
  - ffmpeg
snap-id:   Ee7LGphwQR669pcfCCdl0oJQouta69to
tracking:  stable
refreshed: 2017-08-23T14:44:41+01:00
installed:   N-76538-gb83c849 (3) 150MB classic
channels:                         
  stable:    N-76538-gb83c849 (3) 150MB classic
  candidate: &#8593;                          
  beta:      &#8593;                          
  edge:      N-76538-gb83c849 (8) 150MB classic

```
[FONT=Verdana]
I notice from the github url in the snap information that this bug looks to have been reported:
[/FONT][https://github.com/snapcrafters/ffmpeg/issues/2](https://github.com/snapcrafters/ffmpeg/issues/2)[FONT=Verdana][URL="https://github.com/snapcrafters/ffmpeg/issues/2"]
[/URL]and subsequently fixed with this commit on 17th November 2017:
[/FONT][https://github.com/snapcrafters/ffmpeg/commit/c52eea8cbf05c27cbe2dec3ebb9e8d234406610c](https://github.com/snapcrafters/ffmpeg/commit/c52eea8cbf05c27cbe2dec3ebb9e8d234406610c)[FONT=Verdana]

So my question is, how do I get this snap updated? The snap available in 18.04 is dated August 2017 and the fixed version from November 2017. [FONT=courier new]ubuntu-bug[/FONT] warns that it is for reporting against the [FONT=courier new]apt[/FONT] version of [FONT=courier new]ffmpeg[/FONT], so creating a launchpad issue doesn't seem correct, and the github url in the snap shows very definitely that the team were aware of this problem and have fixed it.

Who do I contact to get the snap repackaged and updated?
[/FONT]

---

### Post by TheFu on 2018-05-01
I've seen a number of issues around snap packages.  Is there away to NOT use snap for ffmpeg?  Does that work better?

---

### Post by bugsquisher on 2018-05-02
> **TheFu said:**
> I've seen a number of issues around snap packages.  Is there away to NOT use snap for ffmpeg?  Does that work better?

Thanks for your reply.

Removing the ffmpeg snap, rebooting to clear the squashfs and then installing ffmpeg through apt does indeed work.

This is a fresh install of a work computer used for rendering, and the direction given for all new installs is to use snaps where possible. Sadly, it looks like this isn't possible in this case.

There is a suggestion from the snap team that this snap is broken and needs removing from the snap repository:
[https://forum.snapcraft.io/t/ffmpeg-snap-on-ubuntu-18-04-installs-but-is-missing-shared-library-libpulsecommon-8-0-so/5227](https://forum.snapcraft.io/t/ffmpeg-snap-on-ubuntu-18-04-installs-but-is-missing-shared-library-libpulsecommon-8-0-so/5227)

I'm going to close this thread, as I consider it resolved as far as these forums are concerned.

---

