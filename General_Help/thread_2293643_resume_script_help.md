---
title: "resume script help"
date: 2015-09-06
forum: General Help
---

### Post by waitingroomsnap on 2015-09-06
My computer's audio does not work after suspend/resume.  The solution in this thread: [http://ubuntuforums.org/showthread.php?t=2206335]("http://ubuntuforums.org/showthread.php?t=2206335&highlight=resume+script+audio") works, but I was curious if I could put this into a resume script such that it occurs automatically when resuming.  I've done a bit of searching to try to make this script but it's not working, and I don't know enough about resume scripts to figure out why it doesn't work. I added the autospawn=no to the pulse client.conf file.  I then created a 50alsa file in my /etc/pm/sleep.d/ directory and made it executable.  Is this possible, or do I just need to manually run the script after resuming?

```

#!/bin/bash

resume_audio() {
    pulseaudio --kill
    /sbin/alsa force-reload
    pulseaudio --start
}


case "$1$" in
    hibernate|suspend)
        # stopping is not required
        ;;
    thaw|resume)
        resume_audio
        ;;
    *) exit $NA
        ;;
esac

```

Thanks in advance!

---

### Post by waitingroomsnap on 2015-09-06
Well I've made a little progress.  After a lot of googling I discovered that because I'm using 15.04, need to put the file into /lib/systemd/system-sleep/

I also tried to add in some debugging, but its not really giving me anything useful, except that I know the script is at least running, but I don't know what kind of errors may be arising from those commands, and the script isn't isn't fixing the problem.

```
#!/bin/bash

set -x
exec 5> /home/brian/50alsa_debug.txt
BASH_XTRACEFD="5"

case $1/$2 in
    pre/*)
        exit 0
    ;;
    post/*)
        sudo -u brian pulseaudio --kill
        /sbin/alsa force-reload
        sudo -u brian pulseaudio --start
    ;;
esac

```

the debug is just 

```

$ cat 50alsa_debug.txt
+ case $1/$2 in
+ sudo -u brian pulseaudio --kill
+ /sbin/alsa force-reload
+ sudo -u brian pulseaudio --start

```
Just to restate, the following is what I do to fix the audio problem after a suspend/resume.  I just would like to get this into a resume script so that it's done automatically after resume.  I've been working on it for a while now, but can't figure this out.

```

$ pulseaudio --kill
$ sudo alsa force-reload
$ pulseaudio --start

```

---

