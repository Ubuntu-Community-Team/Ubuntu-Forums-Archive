---
title: "VLC start on boot - Ubuntu Server"
date: 2013-03-03
forum: General Help
---

### Post by AngryMallard on 2013-03-03
Hey all, I just set up the 12.04 LTS Ubuntu Server to do LAMP and some other things, but I also would like it to start playing a music playlist with VLC at boot as well. (This is a command-line ONLY machine. There is no GUI.) These are the things I've tried:

1) Adding the line "sudo -u user vlc /home/user/playlist.m3u &" to /etc/rc.local. This spits out a lot of generic errors which are fixed by:
2) Changed "vlc" in the above command to "cvlc" to use the console VLC. This seems to work, however the playback does not start until someone logs in. Also, they can't log in on tty1 because the VLC process is running there. (Adding a & at the end of the line doesn't seem to release the console back to the user for whatever reason.)
3) Then I tried to enable auto-login on tty1 to see if that would help (this only runs on my home network so security is not an issue). I did this by changing the last line of the "sudo nano /etc/init/tty1.conf" file to "exec /bin/login -f USERNAME < /dev/tty1 > /dev/tty1 2>&1". Auto-login was enabled but with VLC running nothing else can be entered in tty1, it is just sitting there running VLC, but still no sound output.
4) I noticed that if I changed to tty2 and logged in, the sound would just pick up as if it was playing all along. So it SEEMS as though VLC is actually running, but it needs a user to be logged in. So I enabled auto-login on tty2 as well. 
5) Now when the system boots, the VLC process starts in tty1 and when I ctrl+alt+F2 to tty2 the sound immediately starts. But since this is a headless, keyboardless server I can't do this every time it boots.
6) I tried adding the line "chvt 2" to /etc/rc.local to automatically switch to tty2 after it boots but it spits out an error "chvt: VT_ACTIVATE: Operation not permitted". 

I'm basically out of ideas at this point, so I came here for some suggestions. I feel like I'm doing so many workarounds at this point that I'm chasing wild geese. Has anyone tried to start VLC at boot time? Am I going about this all wrong?

---

