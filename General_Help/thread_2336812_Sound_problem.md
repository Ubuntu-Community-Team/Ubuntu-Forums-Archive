---
title: "Sound problem"
date: 2016-09-11
forum: General Help
---

### Post by wjbradley on 2016-09-11
Not long after the install of ubuntu 14.04 on my HP mini I had sound from thee speakers and earphones. When I test it on youtube there is no sound and I have followed their instructions in case there was a "mute" at work but that did not solve the problems. Any thoughts would be appreciated.

---

### Post by RobGoss on 2016-09-11
Hello and welcome. What version of Ubuntu do you have installed? providing details about your system will help others give you the best possible help

This may sound like a silly question but did you click on the X by the speaker on the YouTube video sometimes people over look this small detail

---

### Post by &amp;KyT$0P# on 2016-09-11
What browser?
Does sound work for you on something other than your browser?

---

### Post by wjbradley on 2016-09-11
> **RobGoss said:**
> Hello and welcome. What version of Ubuntu do you have installed? providing details about your system will help others give you the best possible help

This may sound like a silly question but did you click on the X by the speaker on the YouTube video sometimes people over look this small detail

If you look at my message again you will see that I listed the Ubuntu 14.04 and the computer HP mini. I looked at youtube again but could not see an X beside the speaker.

Is there a way to mute the speakers from within Ubuntu 14.04.

Thank your for your help

---

### Post by &amp;KyT$0P# on 2016-09-11
> **wjbradley said:**
> If you look at my message again you will see that I listed the Ubuntu 14.04 and the computer HP mini. 
I think RobGoss is asking about which flavor of Ubuntu you're on / which desktop environment you're running.  Are you on Unity, or Kubuntu/KDE, or Lubuntu/LXDE, or Xubuntu/XFCE, or...?

> Is there a way to mute the speakers from within Ubuntu 14.04.
I'm confused.  First you seem to be asking how to get sound, now you want to mute it? :confused:

Please clarify and provide the rest of the details requested above by RobGoss and myself, so that people can help you get this problem sorted.
Thanks.

---

### Post by Bucky Ball on 2016-09-11
Start the Youtube clip, forget that you can't hear it yet, just let it go. Open Pulseaudio Volume control. Check in the 'Output' tab. See the 'Youtube' audio stream? Check the device the audio stream from Youtube is streaming to (Port). Change it to the correct one (external speakers, headphones, HDMI, whatever). Check the 'Playback' tab. See the stream?

Experiment with PAVControl and see if you come up with anything. If you don't have PAVControl installed, it is in the repositories. Install from Software whatever and launch.

---

### Post by &amp;KyT$0P# on 2016-09-12
> **Bucky Ball said:**
> If you don't have PAVControl installed, it is in the repositories. Install 
... by entering this command in a Terminal -
```
sudo apt-get install pavucontrol
```

---

### Post by giridhar.07 on 2016-09-12
halogen2, thank you for the above command. 

I was having trouble with sound not working on youtube. The command you posted solved the issue.

---

### Post by Remson_Felipa on 2016-09-12
Try to reinstall the driver and then restart the computer, it should work

---

### Post by RobGoss on 2016-09-12
If you were able to fix your problem would you marking this thread as solved. You can do this by using the Thread tool tab at the top of this post. Thanks so much

---

### Post by Bucky Ball on 2016-09-12
> **RobGoss said:**
> If you were able to fix your problem would you marking this thread as solved. You can do this by using the Thread tool tab at the top of this post. Thanks so much

wjbradley is the OP. Posts #8 and #9 have nothing to do with this as Installing Pulse Audio Volume Control will fix nothing without actually using it for something and that post adds nothing to solve the OP's actual issue. Post #9? Re-install what drivers? Stab in the dark I'd think as we have no idea what the issue is as the OP hasn't said much.
 
wjbradley, the OP, has not mentioned anything about having solved their issue.

---

### Post by RobGoss on 2016-09-12
Thanks Bucky I didn't see the original poster name. I thought he stated he solved this problem

---

### Post by RobGoss on 2016-09-12
> **wjbradley said:**
> If you look at my message again you will see that I listed the Ubuntu 14.04 and the computer HP mini. I looked at youtube again but could not see an X beside the speaker.

Is there a way to mute the speakers from within Ubuntu 14.04.

Thank your for your help

When viewing YouTube videos sometimes the speaker will be disabled and you will see a little red X next to the speaker icon right under each video. You sometime have to click the X to re-enable the sound. If your sound is working on your system and you have no sound when watching YouTube videos that tells me its YouTube and may need adjusting to hear the videos

---

### Post by wjbradley on 2016-09-12
Reading down the replies I am using Ubuntu 14.04 on HP notepad. Don't know what else to say. When it installs I use the control panel that comes with the install..

Next I see that there is a solution for someone with the same problem.

Next I wanted to know if the sound card was being muted internally by the ound cards' own software. Then  I went to System Setting and opened the sound card it did indeed say that it was muted. I unmuted the card, rebooted and the sound was fine. So there  are two solutions on this thread.

What happened to me came about after I had updated Ubuntu 14.04 and it has happened in Ubuntu 13.10 also. Looking back now I had sound before the update and none after updating.

Thank you for all the help and suggestions.

---

### Post by RobGoss on 2016-09-12
I'm glad you was able to fix this issue it was a bit confusing because you state you had sound from three speakers but no sound when watching YouTube videos, that lead me to believe it was something  to do with the functions with YouTube but it wasn't so it's  always good know what the cause was

---

### Post by wjbradley on 2016-09-12
> **RobGoss said:**
> I'm glad you was able to fix this issue it was a bit confusing because you state you had sound from three speakers but no sound when watching YouTube videos, that lead me to believe it was something  to do with the functions with YouTube but it wasn't so it's  always good know what the cause was

Thank you, things seem to  have become a little muddled but in the end the problem was solved.

Just an aside, I see you are running: "Ubuntu Gnome 16.04 Xenial Xerus" The first bit I understand but the "Xenial Xerus" what are they?

---

### Post by RobGoss on 2016-09-12
> **wjbradley said:**
> Thank you, things seem to  have become a little muddled but in the end the problem was solved.

Just an aside, I see you are running: "Ubuntu Gnome 16.04 Xenial Xerus" The first bit I understand but the "Xenial Xerus" what are they?

As far as I know I could only find this meaning,** Xenial Xerus, meaning friendly ( African ) Squirrel )**

---

### Post by Bucky Ball on 2016-09-12
> **wjbradley said:**
> Just an aside, I see you are running: "Ubuntu Gnome 16.04 Xenial Xerus" The first bit I understand but the "Xenial Xerus" what are they?

Then let your [fingers do the walking]("https://duckduckgo.com/?q=Xerus&t=h_&iax=1&ia=images").

[Xenial]("https://en.wiktionary.org/wiki/xenial") Xerus is the release name for 16.04 LTS. All releases have one. :)

Thanks for marking the thread as solved and glad you figured it out.

---

