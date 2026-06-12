---
title: "Sound only available as root. I combed the forums without finding any solution."
date: 2016-07-22
forum: General Help
---

### Post by YQ002lc2 on 2016-07-22
My version:

4.4.0-31-generic
Username@Hostname:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial



The problem:

espeak "test" does not work
sudo espeak "test" works
Audio with firefox youtube doesn't work, but it works with sudo firefox youtube.

Troubleshooting:
Nothing is muted on AlsaMixer
I've tried adding my usernames to the various audio groups such as: sudo adduser MyUsername audio... to no avail. 
I've also tried various chown commands on my home directory....


Any ideas? 

Other notes:

I originally installed Ubuntu server and then ran a massive bash script file to install all my software from my previous install. My username had sound before the bash script ran, but only as root afterwards. 

I'm booting into the terminal and then launching lightdm using systemctl, as needed.
I have had to use chown for .Xauthority to be able to login a time or two. 

This same problem exists on two of my machines.

---

### Post by TheFu on 2016-07-23
Create a new userid and see if sound works with it.  If it does, then there is a configuration issue with the old userid, possibly due to file permissions (being owned by root).

---

### Post by YQ002lc2 on 2016-07-23
Thank you for your reply, TheFu! 
It's very important that I have sound. 

I'm not very familiar with creating new users. 

I did the following:

sudo adduser testuser
sudo adduser testuser audio.....pulse...pulse-access....sudo
Logged out and logged in with the new user
alsamixer was fine. 
espeak "test" yielded no sound.
sudo espeak "test" gave "testuser is not in the sudoers file. This incident will be reported.

---

### Post by TheFu on 2016-07-23
I don't have a clue. Sorry.  There is a sound troubleshooter that I've used.  Had an issue and posted the results to the multimedia forum and someone there provided one chmod command that fixed everything.  I'm fairly experienced in multi-user environments with thousands of users and the command didn't make any sense to me. Just know that it worked. This was a few releases ago, so that cmd isn't likely to be helpful in your situations.

I've never played with epeak.  Tried it here and it worked.

Sorry I can't help more.

---

### Post by YQ002lc2 on 2016-07-23
No worries! Thank you for taking of your time to try and help!

---

### Post by YQ002lc2 on 2016-07-23
No worries! Thank you for taking of your time to try and help!

---

### Post by YQ002lc2 on 2016-07-24
Per a suggestion on some other posts -- I can't remember which ones -- I purged pulseaudio.

Partial SOLUTION: ---------------> sudo apt-get purge pulseaudio    (Worked only on machine 1)

The following packages will be REMOVED:
  acfax* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio*
  pulseaudio* pulseaudio-module-bluetooth* pulseaudio-module-x11*
  unity-control-center* unity-control-center-signon*
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.

After doing this and restarting, audio was restored to my username. 


espeak "test" yeilded sound and the following:

ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:867:(find_matching_chmap) Found no matching channel map
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock


On the second machine, I copied this proceedure. 
When I ran espeak, I got the usual output along with wave_open_sound > Pa_OpenStream : err=-9996 (Invalid device) and no sound. 

 
Any ideas? I will update this when I can resolve the issue on the second machine.

---

### Post by YQ002lc2 on 2016-07-27
So, I've been away a few days. 

I tried again tonight and was able to finally get sound working on my second machine, as well! :)

Basically, I followed the same procedure, but this time it worked. 


sudo apt-get purge pulseaudio
sudo adduser username audio
sudo reboot -h now

Incidentally, I also added myself to root, but that may not be necessary. 

I start my Ubuntu server in text mode. I only selectively launch my prefered display manager when I need it. 
I've noticed that sometimes using root permissions to launch a graphical environment or connect over ssh can change the permissions in my home directory... screwing up things like .Xauthority (creating login loops)...

I say that to say: if you haven't already, try 

sudo chown username /home/ -R

You may find that, if you home directory is encrypted and it's permissions have changed, your applications are unable to access necessary configuration files to function as they should.

 
I hope this helps someone else save hours of headaches!  
Have a blessed day!

---

### Post by TheFu on 2016-07-27
Don't ever use:
```
sudo chown username /home/ -R
```
It is very dangerous!!!  
If you are on a multi-user system (and all Linux systems ARE multi-user), you've just screwed every other user account completely.

Probably what you want is
```
sudo chown -R username.username $HOME 
```
or
```
sudo chown -R username.username ~/ 
```
These mean the same thing, but only touch the currently in-use userid HOME. Much safer.  If that userid doesn't have sudo capabilities, then it probably won't have the permissions issues.

Using sudo with GUI programs is a bad idea. Use the shell for that stuff. For editing files use **sudoedit** - all 1 word. We can control which editor gets used (GUI editors are fine this way) through the EDITOR environment variable. The manpage has more details.

---

