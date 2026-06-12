---
title: "Audio editor to record line input from shortcut."
date: 2018-06-17
forum: General Help
---

### Post by debderivs on 2018-06-17
Hey guys,

Does anyone know an audio editor on Linux which can be launched from a shortcut to instantly start
recording? On Windows there is NGWave which does this perfectly.

Thanks.

Regards.

---

### Post by ajgreeny on 2018-06-17
Probably quickest to use a launcher (shortcut as you call it) to a shell script pointing to **arecord**, the details of which you can find in **man arecord**.

Try using command ```
arecord -f cd -V stereo outfile.wav
``` in your script.

Any GUI application will never be instant as there will always be a delay while the GUI appears and is set up as wanted, whereas arecord will, as far as I recall, always record whatever system sound is playing immediately.

---

### Post by debderivs on 2018-06-17
> **ajgreeny said:**
> Probably quickest to use a launcher (shortcut as you call it) to a shell script pointing to **arecord**, the details of which you can find in **man arecord**.

Try using command ```
arecord -f cd -V stereo outfile.wav
``` in your script.

Any GUI application will never be instant as there will always be a delay while the GUI appears and is set up as wanted, whereas arecord will, as far as I recall, always record whatever system sound is playing immediately.


Thanks! I´ll give it a try.

Well, by "instantly" I didn´t really mean it.. it´s OK if  it takes 1 second to start recording. But, I´d rather prefer
a GUI which has a VU, a volume meter, so I can see the volume going on. I hope I can find an editor which can
be launched to record like this. In the meantime arecord could do it.

---

### Post by NM5TF on 2018-06-17
> **debderivs said:**
> Hey guys,

Does anyone know an audio editor on Linux which can be launched from a shortcut to instantly start
recording? On Windows there is NGWave which does this perfectly.

Thanks.

Regards.

if you REALLY like NGWave, you could always use WINE to run it on your Linux box.......I use WINE for several
ham radio programs with good results....

WINE info here:     [https://www.winehq.org/](https://www.winehq.org/)

tommy

---

### Post by again? on 2018-06-18
Try audio-recorder... [https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)
Can start stop pause from the dock icon.
Various settings for triggered recording also.

Once installed, go to **file:///usr/share/audio-recorder/timer-syntax.html** in your web browser for help.

---

### Post by debderivs on 2018-06-18
> **NM5TF said:**
> if you REALLY like NGWave, you could always use WINE to run it on your Linux box.......I use WINE for several
ham radio programs with good results....

WINE info here:     [https://www.winehq.org/](https://www.winehq.org/)

tommy


Yes, thanks, Wine could be an option. But for such a simple task, a native light audio editor would be nicer.
I have yet to install the latest version of Wine to test some heavier Win apps.

---

### Post by debderivs on 2018-06-18
> **guber2 said:**
> Try audio-recorder... [https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)
Can start stop pause from the dock icon.
Various settings for triggered recording also.

Once installed, go to **file:///usr/share/audio-recorder/timer-syntax.html** in your web browser for help.

Thanks, I´ll have a look!

---

### Post by HermanAB on 2018-06-19
Howdy,

For me, the easiest way to handle audio from the command line is with sox (sound exchange):
$ sudo apt install sox
$ rec filename.wav
$ play filename.wav

La voila!

---

### Post by debderivs on 2018-06-19
> **HermanAB said:**
> Howdy,

For me, the easiest way to handle audio from the command line is with sox (sound exchange):
$ sudo apt install sox
$ rec filename.wav
$ play filename.wav

La voila!


Thanks for the input, but I wanted an app with GUI and VU, with volume meter so I can see the peaks
and when the sound signal stops.

---

### Post by HermanAB on 2018-06-19
Err... Sox has a VU meter and squelch control.  So you can use the VU meter manually, or configure it to automatically record only when sound is present and stop a few seconds after sound stops.

[https://linux.die.net/man/1/sox](https://linux.die.net/man/1/sox)

Sox lies below many a GUI audio app.

---

### Post by debderivs on 2018-06-19
> **HermanAB said:**
> Err... Sox has a VU meter and squelch control.  So you can use the VU meter manually, or configure it to automatically record only when sound is present and stop a few seconds after sound stops.

[https://linux.die.net/man/1/sox](https://linux.die.net/man/1/sox)

Sox lies below many a GUI audio app.

Ah, OK, sorry. Will have a look. Thanks.

---

