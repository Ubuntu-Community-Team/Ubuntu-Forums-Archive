---
title: "Sound Recorder not recording"
date: 2006-10-29
forum: General Help
---

### Post by morgue on 2006-10-29
Hey, I don't know what's wrong, on Skype I use the microphone (Logitech Webcam's Mic) and it works like a charm, but when I try to record something all I get it's silence.

Any suggestions?

---

### Post by morgue on 2006-10-29
bump

---

### Post by morgue on 2006-10-30
bump

---

### Post by morgue on 2006-10-30
anyone please?

---

### Post by iamhugeinjapan on 2006-10-30
Have you changed the capture source to use the Microphone?

---

### Post by jordilin on 2006-10-30
type in the command line
> alsamixer
and set the mic channel in capture mode
You can as well open the audio controls and set the Microphone channel in capture mode.

---

### Post by morgue on 2006-10-30
I can't get it to work, I double click on the speaker icon and I change the device to Camera but when I 'record' something nothing is recorded when I playback...

---

### Post by morgue on 2006-10-30
:(

Am I not choosing the device correctly?

---

### Post by iamhugeinjapan on 2006-10-30
I'm not sure how well Sound Recorder really works. On my laptop with built in speaker the only way I can make it hear anything is if I tap the speaker :P

When you're trying to record something, are there any other programs open that play sounds?

You can select the capture source in the Sound Recorder main window. But going to File - Open Volume Control, will give you more advanced selection and unmuting abilities. Checked all is ok in there?

---

### Post by morgue on 2006-10-30
Yeah when I go to Volume Control I go to File -> Change Device and I select:
1: Camera (Alsa mixer)

But I try to record and nothing :(

On Skype the camera works so I dunno...

---

### Post by iamhugeinjapan on 2006-10-30
What happens if you select Microphone instead of Camera? or is that not an option?

---

### Post by morgue on 2006-10-31
> **iamhugeinjapan said:**
> What happens if you select Microphone instead of Camera? or is that not an option?

Well the device list on Volume Control says:
0: HDA Intel (Alsa mixer)
1: Camera (Alsa mixer)
2: Generic 14f1 ID 5047 (OSS Mixer)

On Skype's audio in devices I get:
HDA Intel and Camera, when I choose HDA Intel it doesn't work but the camera does.

](*,)

---

### Post by morgue on 2006-10-31
](*,) ](*,)

---

### Post by morgue on 2006-10-31
nothing :@

---

### Post by iamhugeinjapan on 2006-10-31
Only thing I can suggest is if you have another mic that you can plug into a mic sound port?

---

### Post by morgue on 2006-10-31
> **iamhugeinjapan said:**
> Only thing I can suggest is if you have another mic that you can plug into a mic sound port?

The camera has a mic, and it works 'cause on Skype I can use it, it's sound recorder that's not working

---

### Post by morgue on 2006-10-31
](*,)

---

### Post by morgue on 2006-10-31
can anyone help me out with this?

---

### Post by morgue on 2006-11-01
](*,)

---

### Post by morgue on 2006-11-02
grr

---

### Post by Syock on 2006-11-06
Please don`t bump too often. I know you want attention and quickfix but you can`t have everything solved in a day.

Someone else had a similar problem too. Check out this link and see if my solution can works for you:
[http://ubuntuforums.org/showthread.php?t=275103](http://ubuntuforums.org/showthread.php?t=275103)

---

