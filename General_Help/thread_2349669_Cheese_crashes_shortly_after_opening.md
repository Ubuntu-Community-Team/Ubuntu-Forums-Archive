---
title: "Cheese crashes shortly after opening"
date: 2017-01-17
forum: General Help
---

### Post by rdh61 on 2017-01-17
Hi,

On my Lubuntu 16.04 system, cheese always Crashes soon after opening. I've tried uninstalling and reinstalling, but no joy. It worked fine before I upgraded from 14.04.

Any ideas?

Or, can anybody recommend an alternative to Cheese?

Thanks.

---

### Post by ajgreeny on 2017-01-17
Try guvcview.

I have never ever managed to get cheese working properly and have always replaced it with guvcview which has worked very well.

---

### Post by rdh61 on 2017-01-18
Hi, Thanks for your reply. Unfortunately guvcview always crashes on opening, too!

---

### Post by ajgreeny on 2017-01-18
What errors, if any, show if you open the two applications in terminal? It may give us some clues.

---

### Post by rdh61 on 2017-01-19
Here is the output of the terminal:

```

robert@robert-desktop:~$ cheese


(cheese:19520): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Segmentation fault (core dumped)
robert@robert-desktop:~$ guvcview
GUVCVIEW: version 2.0.2
GUVCVIEW: couldn't open /home/robert/.config/guvcview2/video0 for read: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
V4L2_CORE: V4L2_CAP_TIMEPERFRAME supported
control[0]:(unknown - 0x6) 0x980001 'User Controls'
V4L2_CORE: V4L2_CAP_TIMEPERFRAME supported
Segmentation fault (core dumped)
robert@robert-desktop:~$ 

```

---

