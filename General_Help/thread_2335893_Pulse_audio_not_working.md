---
title: "Pulse audio not working"
date: 2016-09-02
forum: General Help
---

### Post by zuto2 on 2016-09-02
Hello,

Pulse audio is not working or maybe it is working, but not much is detecting it. I used to be able to pick pulse audio in wine configure and pavucontrol.

```
E: [pulseaudio] pid.c: Daemon already running.

E: [pulseaudio] main.c: pa_pid_file_create() failed.



```

I tried reinstalling it and I get the same error output.  My main issue is that I cannot record any internal sound.
[http://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04](http://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04)

I tried killing it and starting it again, but nothing.
```
[COLOR=#111111][FONT=Ubuntu]First run [/FONT][/COLOR]pulseaudio --kill[COLOR=#111111][FONT=Ubuntu] then [/FONT][/COLOR]pulseaudio --start
```
[FONT=Ubuntu][COLOR=#111111][http://askubuntu.com/questions/186822/audio-stopped-working-suddenly-in-12-04](http://askubuntu.com/questions/186822/audio-stopped-working-suddenly-in-12-04)

I tried deleting .pulse and rebooting.

Can anyone help?

[/COLOR][/FONT]

---

### Post by zuto2 on 2016-09-03
I solved it, but it was super strange! Must be a glitch.

pavucontrol > configuration > analog stereo input

Then go to recording section. Make sure that you are currently recording with Recordmydesktop or nothing will be there.

Make sure it is on built-in audio analog stereo.

Go back to configurations and pick analog stereo duplex. Make sure it is on built-in audio analog stereo.

After that my audio began to record. I changed none of my settings and just picked them again. That made my audio work when recording internally.

[B]Edit:
[/B]Sometimes the audio needs to be already playing before recording begins for it to work, but I just tried again and I did not need to. Must be some tweak delay. Fiddling with it will fix it with minor tests.

---

### Post by 894532185610544562 on 2016-09-03
[delete me]

---

