---
title: "no sound (not a noob)"
date: 2012-11-20
forum: General Help
---

### Post by android272 on 2012-11-20
I just installed Ubuntu 12.04 and I am unable to get my sound to work. my first thought was to go into the sound options in system settings but when I click on it nothing happens. sometimes it even freezes when I click on it, making it so that I can not even close that window. I even tried opening it through the dash but nothing works. should I install another program and delete the one that comes with Ubuntu?

---

### Post by syerges on 2012-11-20
I had a similar problem after installing certain programs... What I did to fix it was reinstalled the restricted extra's.

---

### Post by NikTh on 2012-11-20
Hi , 
**1st attempt**

Open a terminal and write 
```
alsamixer
``` 
see there if something is muted [MM] , if yes then unmute with M key on your keyboard. You can navigate with arrow keys (left-right) , you can increase - decrease volume with arrow keys (up-down). [ESC] to exit. 

**2nd attempt** 
Open a terminal and do 
```
killall pulseaudio 
rm -r .pulse/
sudo apt-get install --reinstall  pavucontrol linux-sound-base alsa-base alsa-utils ubuntu-desktop  linux-image-`uname -r` libasound2
sudo alsa force-reload
``` 
Open pavucontrol and try to select your speakers from there.

**3rd attempt - debugging**
If none of above works , then open a terminal and do
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
```
at the question > Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] answer y(es) and give here the link.

Thanks

---

### Post by efflandt on 2012-11-20
While I have never had any problem with analog stereo sound in Ubuntu (other than default sometimes muted on fresh install) digital or HDMI audio may require additional configuration depending upon what hardware you have.  In a terminal, besides trying **alsamixer**, see what, if any, output you get from **aplay -l** (small L) and **aplay -L** (capital L). The former should list the default audio device and latter all available audio devices.  You might also post what **sudo lspci -v** shows about your audio device.

Note that to make things easier to follow that have indents or columns, wrap that output in code tags by highlighting it and clicking **#** in the message window.

I did have a problem with no sound in Lubuntu on a tablet PC.  In that case **alsamixer** did not show any PCM device.  The only way I could get it to work was to install **pulseaudio** and **pavucontrol** (but the latter is not installed in Ubuntu 12.04 and it looks like it uses **indicator-sound** instead).  After installing pulseaudio, alsamixer showed a PCM device and sound worked.

Although, I have regular Debian sound working fine in a virtualbox using just alsa related audio.

---

### Post by android272 on 2012-11-20
I tryed the first two of NikTh's post.

first the one of the mixer settings was muted, but the problem still not fixed.

the second thing. for some reason this made some windows that I had tried to open earlier but was unable to open pop up which is weird. I am now able to open sound under the system settings but nothing works. I closed the window and now it wont pop up again.

the volume menu button also will not drop down.

---

### Post by android272 on 2012-11-22
bump

---

### Post by android272 on 2012-11-27
NikTh

dmesg                                                                    &#9474;
&#9474;   lspci                                                                    &#9474;
&#9474;   lsmod                                                                    &#9474;
&#9474;   aplay                                                                    &#9474;
&#9474;   amixer                                                                   &#9474;
&#9474;   alsactl                                                                  &#9474;
&#9474;   /proc/asound/                                                            &#9474;
&#9474;   /sys/class/sound/                                                        &#9474;
&#9474;   ~/.asoundrc (etc.) 

See './alsa-info.sh --help' for command line options.

---

### Post by android272 on 2012-12-08
Bump

---

