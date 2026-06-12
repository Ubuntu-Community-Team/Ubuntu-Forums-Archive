---
title: "help with skype (doesnt say i have pulse)"
date: 2013-09-30
forum: General Help
---

### Post by ben34 on 2013-09-30
skype says problem with audio playback and it wont let me call anyone. I am a bit of a noob at linux. So if you could please help me that would be awesome and also i know my mic works because i can hear it in sound recoreder. Also i have seen in other posts saying set skype to "pulse" audio device but skype doesnt list a pulse option for me.

---

### Post by Francisco Cardoso on 2013-09-30
can you check the settings and then try to make a test call?

---

### Post by ben34 on 2013-09-30
settings say deafualt on everything, but i have tried doing a test sound and none of the options work.

---

### Post by ben34 on 2013-09-30
also it doesnt let me do a test call gives me same error

---

### Post by Adam_GUI on 2013-09-30
What is your Ubuntu edition?
Do you have PulseAudio installed?
Open a terminal.  Any terminal emulator will do.  gnome-terminal, xfce4-terminal, etc.
Please, Run "pulseaudio --version" with no quotes and see if you get a version number.

---

### Post by ben34 on 2013-09-30
i have ubuntu 12.04 and also i have pulse audio 1.1

---

### Post by Adam_GUI on 2013-09-30
> **ben34 said:**
> i have ubuntu 12.04 and also i have pulse audio 1.1

Huh, weird.
Alrighty.  First, I'd quit skype.  
=> Click the tray icon, quit.  Easy stuff, but I'm trying to hit everything.

Same terminal, run "sudo dpkg-reconfigure skype".
Launch skype again.  See if it sees pulseaudio.  4.2.0.1.1. is the latest version of skype in the repos.

If that doesn't work, I'd try grabbing a deb from Microsoft's website.
[http://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=ubuntu64]("http://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=ubuntu64")
Current version there is also 4.2.  

You shouldn't have a bad package from the repos.  But, sometimes weird stuff happens.  
Can't hurt to install the version direct from the vendor.

---

### Post by ben34 on 2013-09-30
would this work, if i put it into a terminal.
[COLOR=#000000]killall pulseaudio[/COLOR]
[COLOR=#000000]sudo apt-get remove pulseaudio[/COLOR]
[COLOR=#000000]sudo apt-get install esound[/COLOR]
[COLOR=#000000]sudo rm /etc/X11/Xsession.d/70pulseaudio


someone said this may fix it but could this mess with other audio such as if this doesnt fix skype could it make me not be able to hear any audio at all.


[/COLOR]

---

### Post by Adam_GUI on 2013-09-30
> **ben34 said:**
> would this work, if i put it into a terminal.
[COLOR=#000000]killall pulseaudio[/COLOR]
[COLOR=#000000]sudo apt-get remove pulseaudio[/COLOR]
[COLOR=#000000]sudo apt-get install esound[/COLOR]
[COLOR=#000000]sudo rm /etc/X11/Xsession.d/70pulseaudio


someone said this may fix it but could this mess with other audio such as if this doesnt fix skype could it make me not be able to hear any audio at all.


[/COLOR]

Yikes!  No, no, no, no, no, no, no.
This looks somewhat like instructions I followed replacing pulse with pure ALSA back when pulse was first introduced.

Those instructions will totally uninstall pulseaudio.  Not the route you really want to take just yet.
You can go ahead and try to kill pulseaudio with "pulseaudio -K".
Pulseaudio will restart automatically.  
This will stop all currently playing audio.  
You'd have to restart anything playing music or video to hear anything.

Removing pulseaudio certainly won't help skype use pulseaudio.

---

### Post by ben34 on 2013-09-30
doesnt seem to want to work for me ):. why does skype have to be such a pain. i killed pulseaudio and made sure skype audio was set to default device but it still  says problem with audio playback

---

### Post by Adam_GUI on 2013-09-30
> **ben34 said:**
> doesnt seem to want to work for me ):. why does skype have to be such a pain. i killed pulseaudio and made sure skype audio was set to default device but it still  says problem with audio playback

Let's back up a bit then.
Your Audio Settings Option Screen should look like this:
[ATTACH=CONFIG]246641[/ATTACH]

Can I get you to grab a screenshot of the same option screen?

Also, if you launch skype from terminal, does it give you any text output after launch?

---

### Post by ben34 on 2013-09-30
on another thread it people say to change audio playback device to pulse, is that in the skype options because i dont see it. I went to sound settings and it isnt there. there isnt anything called audio playback device at least

---

### Post by ben34 on 2013-09-30
[http://gyazo.com/1edb813e29a718bd39490aa81a1dc91c](http://gyazo.com/1edb813e29a718bd39490aa81a1dc91c) here is mine

---

### Post by ben34 on 2013-09-30
i launch skype through dash home

---

### Post by ben34 on 2013-09-30
i uninstalled skype, how would i download it through terminal (i know im a noob, i got linux yesterday)

---

### Post by ben34 on 2013-09-30
hey i didnt see what you said earlier about re configuring skype. IT WORKS. thanks so much and very awesome community linux has here.

---

### Post by MrAutumn on 2013-11-04
Hello, Im also having problems with Skype. Im running Skype 4.2 on Ubuntu 13.10. Every time I try to make a call, the "Problem with Audio Playback" error pops up. 

I installed the .deb package manually from the Windows web page and then I run: 

$ sudo apt-get update

After the first failed call I end up in this thread and I try:

$ sudo dpkg-reconfigure skype
$ skype

the skype windows opens but the following lines appear repeatedly in my terminal

ALSA lib pcm_dmix.c:1022 (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:618 (snd_pcm_dsnoop_open) unable to open slave

Anyone know what this error message mean or what I should do to fix it?

---

### Post by Adam_GUI on 2013-11-04
> **MrAutumn said:**
> Hello, Im also having problems with Skype. Im running Skype 4.2 on Ubuntu 13.10. Every time I try to make a call, the "Problem with Audio Playback" error pops up. 

I installed the .deb package manually from the Windows web page and then I run: 

$ sudo apt-get update

After the first failed call I end up in this thread and I try:

$ sudo dpkg-reconfigure skype
$ skype

the skype windows opens and but the following lines appear repeatedly in my terminal

ALSA lib pcm_dmix.c:1022 (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:618 (snd_pcm_dsnoop_open) unable to open slave

Anyone know what this error message mean or what I should do to fix it?

Under your users and groups settings, are you a member of the "audio" and "video" groups?
If not, add your account to those groups and do a system reboot to try again.

---

### Post by MrAutumn on 2013-11-06
> **Adam_GUI said:**
> Under your users and groups settings, are you a member of the "audio" and "video" groups?
If not, add your account to those groups and do a system reboot to try again.

Eh... I cant find those settings..

---

### Post by Adam_GUI on 2013-11-06
> **MrAutumn said:**
> Eh... I cant find those settings..

You're running Unity, yes?

Ugh.  I see now.  The user account manager doesn't allow you to manage groups.
That's strange and frustrating.

```
sudo apt-get install gnome-system-tools
```

Then, run ```
users-admin
```.

From there, you should see "Manage Groups".  Click it.

From there, you'll see a list of groups.
Double click "Audio".  
Click the checkbox to add your account to the group.
Authenticate with your password.

Repeat those steps again with the "Video" group.

Reboot.

Attempt to launch skype again.

---

### Post by MrAutumn on 2013-11-06
Still doesn't work and these messages keeps popping up in the terminal

```
 
ALSA lib pcm_dmix.c:1022 (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:618 (snd_pcm_dsnoop_open) unable to open slave

```

---

### Post by Adam_GUI on 2013-11-06
> **MrAutumn said:**
> Still doesn't work and these messages keeps popping up in the terminal

```
 
ALSA lib pcm_dmix.c:1022 (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:618 (snd_pcm_dsnoop_open) unable to open slave

```

Weird.  
My wager is that it cannot open those devices to write.
You may be missing some ALSA libraries.

Do you have?:
libsndfile1
libsoxr0

Are you able to record audio using something like Audacity?

---

### Post by MrAutumn on 2013-11-06
> **Adam_GUI said:**
> Weird.  
My wager is that it cannot open those devices to write.
You may be missing some ALSA libraries.

Do you have?:
libsndfile1
libsoxr0

Are you able to record audio using something like Audacity?

For some reason I had libsndfile1 installed but not libsoxr0. Is that weird? 

Anyway, just installed both. Nothing changed. Still getting "Problem with Audio Playback" from Skype and weird errors on Terminal.

---

### Post by Adam_GUI on 2013-11-06
> **MrAutumn said:**
> For some reason I had libsndfile1 installed but not libsoxr0. Is that weird? 

Anyway, just installed both. Nothing changed. Still getting "Problem with Audio Playback" from Skype and weird errors on Terminal.

Still the "unable to connect to slave device" messages?

Say, are you using 64-bit Ubuntu?
I found an older post with a similar problem.
[http://askubuntu.com/questions/370062/skype-no-sound-on-kubuntu-13-10]("http://askubuntu.com/questions/370062/skype-no-sound-on-kubuntu-13-10")

Try: > sudo apt-get install libasound2-plugins:i386


---

### Post by MrAutumn on 2013-11-07
> **Adam_GUI said:**
> Still the "unable to connect to slave device" messages?

Say, are you using 64-bit Ubuntu?
I found an older post with a similar problem.
[http://askubuntu.com/questions/370062/skype-no-sound-on-kubuntu-13-10](http://askubuntu.com/questions/370062/skype-no-sound-on-kubuntu-13-10)

Try:


YES! Finally, well not really. Skype is working but it still behaves weird. 

Audio is generally quite shoddy (its not a connection issue, I have another computer and the it work fine)  and every now and then a loud screech will come out when I end a call and it wont stop until I kill the process. 

The mic is also a bit off. The sensitivity is so low I have to practically scream just so it will record my voice. (could be hardware issue, but it worked fine back when I was running Ubuntu 12.04) .I would change its sensitivity but the system's sound setting don’t seem to affect Skype and I cant change any of the audio settings in said program (they are all set to "pulse"). 

At least I’m not getting those error messages on the terminal any more... What where those suppose to mean anyway?

Anyway, thanks for all your help, Adam!!

---

### Post by Adam_GUI on 2013-11-07
> **MrAutumn said:**
> YES! Finally, well not really. Skype is working but it still behaves weird. 

Audio is generally quite shoddy (its not a connection issue, I have another computer and the it work fine)  and every now and then a loud screech will come out when I end a call and it wont stop until I kill the process. 

The mic is also a bit off. The sensitivity is so low I have to practically scream just so it will record my voice. (could be hardware issue, but it worked fine back when I was running Ubuntu 12.04) .I would change its sensitivity but the system's sound setting don&#8217;t seem to affect Skype and I cant change any of the audio settings in said program (they are all set to "pulse"). 

At least I&#8217;m not getting those error messages on the terminal any more... What where those suppose to mean anyway?

Anyway, thanks for all your help, Adam!!

I think the bug you're describing is the same bug found here:
[http://community.skype.com/t5/Linux/No-sound-or-crappy-sound-on-Kubuntu-13-10/td-p/1839659]("http://community.skype.com/t5/Linux/No-sound-or-crappy-sound-on-Kubuntu-13-10/td-p/1839659")

The work around I've seen reported has to do with modifying the Skype launcher.
```
sudo sed -i 's/^Exec=.*/Exec=env PULSE_LATENCY_MSEC=30 skype %U/' /usr/share/applications/skype.desktop
```
That should modify your desktop launcher.  You know, that icon that shows up in your programs list.
I'm not sure how the search fields and sidebar are referred to in Unity.

That just modifies that launcher and doesn't act as a wrapper to allow you to simply launch "Skype" from terminal or an old ALT+F2 method.

If you want to test that, try ```
Exec=/usr/bin/env PULSE_LATENCY_MSEC=30 /usr/bin/skype
``` in a terminal and make a test call to check your quality.

With luck, that should fix your sound quality issue.

I can't test that 1st hand.  I'm on an i386 platform and I stick to LTS releases for just these package-quirk reasons.

Oh!  And un-check the "Allow Skype to Automatically adjust my mixer Levels" box.
That caused all sorts of wackiness for me.  It's easier to adjust the microphone and output settings from the pulseaudio bar in the top panel.  (Package pavucontrol, just in case that's missing for some strange reason.  It shouldn't be.)

---

