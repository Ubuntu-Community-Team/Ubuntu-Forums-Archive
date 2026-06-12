---
title: "Tuxguitar No Sound"
date: 2006-09-10
forum: General Help
---

### Post by Kleist on 2006-09-10
Hi,

I just installed tuxguitar, so I could open my gp3, gp4, files, 

Now, when I tried to play them, I got this error mesage:
[B]
Unnavailable soundbank error[/B]

Does anyone can help me with this? Does anyone has tuxguitar working? Do I need to install something else?

thanks.

---

### Post by DeadEyes on 2006-09-12
What I did was downloaded the sounbank deluxe from [http://java.sun.com/products/java-media/sound/soundbanks.html](http://java.sun.com/products/java-media/sound/soundbanks.html)
. Set tux guitar to use a custom soundbank and pointed it at the deluxe file.
I then added alsa-oss from the repos.
[b]
$sudo modprobe snd_seq
$aoss ./tuxguitar
[/b]

Edit your /etc/modules and add snd_seq if you want it loaded every time.

---

### Post by Kleist on 2006-09-13
Thanks, I'll try that.

---

### Post by Kleist on 2006-09-13
Well, now it's working. Thank you so much. Now, I don't need to boot again to windows.

---

### Post by DeadEyes on 2006-09-14
Your welcome, glad to have been able to help.

---

### Post by Gargamella on 2006-12-17
> **Kleist said:**
> Well, now it's working. Thank you so much. Now, I don't need to boot again to windows.

me too! awesome!

thank you for helping me ;D :mrgreen:

---

### Post by Recker on 2007-05-31
> **DeadEyes said:**
> What I did was downloaded the sounbank deluxe from [http://java.sun.com/products/java-media/sound/soundbanks.html](http://java.sun.com/products/java-media/sound/soundbanks.html)
. Set tux guitar to use a custom soundbank and pointed it at the deluxe file.
I then added alsa-oss from the repos.
[b]
$sudo modprobe snd_seq
$aoss ./tuxguitar
[/b]

Edit your /etc/modules and add snd_seq if you want it loaded every time.

I did that. When i type $aoss ./tuxguitar in the terminal, it says...

bash: ./tuxguitar: No such file or directory

I do not understand why it says this. I looked and the directory is there. I did the other steps and still no sound, so this must be very important. Sorry, I am completely new to Linux and Ubuntu... it's probably very easy to fix.

---

### Post by DeadEyes on 2007-06-01
I think things have changed a bit. Did you install tuxguitar using the ubuntu .deb file from their website?
If you did then you can launch it from the menu Applications->Sound & video->tuxguitar.
In the terminal you can type whereis tuxguitar to see where it is stored, mine is in /usr/bin/tuxguitar
Because it is in the /usr/bin directory you can launch it by just typing tuxguitar.

Now for the sound, if you also downloaded the ALSA plugin disable it.

Hopefully that should get you going.

---

### Post by Recker on 2007-06-02
> **DeadEyes said:**
> I think things have changed a bit. Did you install tuxguitar using the ubuntu .deb file from their website?
If you did then you can launch it from the menu Applications->Sound & video->tuxguitar.
In the terminal you can type whereis tuxguitar to see where it is stored, mine is in /usr/bin/tuxguitar
Because it is in the /usr/bin directory you can launch it by just typing tuxguitar.

Now for the sound, if you also downloaded the ALSA plugin disable it.

Hopefully that should get you going.

Yeah, I did install using the .deb file. I found the directory. The sound works when I use the $aoss /usr/bin/tuxguitar to launch it. I'm not sure about the ALSA plugin... I have a bunch of alsa things installed, but apparently it's not enabled because the sound works! Thanks, your help is much appreciated. 

Now i have another question. Everytime I try to run amarok and tuxguitar at the same time, one works and the other does not. Is it possible to run amarok, the music program, and tuxguitar at the same time and get sound from each? I like to listen to music frequently and it'd be nice if I am tabbing something if I could listen to it then.

---

### Post by DeadEyes on 2007-06-02
Yeah I have noticed that some programs seem to hog the audio, and you can only run one or the other. but its never bothered me enough to look for a solution.

---

### Post by ArtInvent on 2007-08-13
Timidity is a pretty nice program. It's music features are almost comparable to GuitarPro or Tabledit (my favorite Windows program for guitar). The printing features are not very flexible yet, but it's definitely coming along as one of the better Linux guitar tab programs.

Unfortunately it has some issues working with midi in Linux.

Using Timidity as the midi port in TuxGuitar, I am able to play using the Java 6 stock soundbank. This a different method from the one using the aoss command as outlined above. It sounds very good, and I'm able to play other music at the same time with no conflicts. Unfortunately I had to struggle with no sound for a while before I figured this out. There are some posts in the TuxGuitar forums but the Documentation page for Ubuntu is pretty inadequate. HOWTO:

In Feisty:

1. Make sure you have Timidity installed.
2. Make sure you have Sun Java JRE 6 installed. This seems to have a midi sound bank package included already (at least I'm pretty sure I haven't downloaded anything additional for it.)
3. Download and install the main TuxGuitar Ubuntu binary deb packages from the project site.
4. Also download and install the TuxGuitar Alsa-Plugin binary.
5. Start timidity with the command: 
  $ timidity -iA -Os
6. Start TuxGuitar. In Settings | Configure Tuxguitar | Sound you will be using the default soundbank, which should be set already.
7. Go to Plugins | Tuxguitar-alsa Plugin and look in the dropdown box. Select the 'Timidity port 0' and make sure 'Active Plugin' is checked.
8. That should be it. You can hit the play button and hear something, assuming your sound is hooked up and functioning. It will probably sound like a piano. To change the instrument to the guitar of your choice, go to Track | Properties  and you will see a dropdown box with all the available midi sound instruments. 

It probably doesn't matter if you don't download and install things in the same order. But you will have to run the timidity command as above every time you start the program, or write a shell script or a special launch menu command.

Worked for me anyway.

---

### Post by LuckyDevil on 2007-09-06
Thanks a lot for the tip!  Helped a bunch.

---

### Post by TWO on 2007-12-29
Thanks very much! Your suggestion has solved my problem too!

---

### Post by isaacj87 on 2007-12-29
Wow old thread! But extremely helpful...

I love using GuitarPro and with the Java soundbank and TuxGuitar, it's as good as the real thing!

Thanks for the tips...It works great :) 

:guitar:

P.S. I didn't have to add snd_req to my /etc/modules file...not sure why? I'm guessing it doesn't need to load on each boot up

---

