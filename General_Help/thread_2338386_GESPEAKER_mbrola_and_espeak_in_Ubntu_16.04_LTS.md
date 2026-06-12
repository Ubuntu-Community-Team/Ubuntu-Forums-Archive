---
title: "GESPEAKER mbrola and espeak in Ubntu 16.04 LTS"
date: 2016-09-27
forum: General Help
---

### Post by Vidorin on 2016-09-27
Well my issue is simple, I would love to upgrade to Ubuntu 16.04 from Ubuntu 14.04 however there seems to be an issue.  It is a bug on launchpad known that gespeaker, espeak or mbrola (I suppose they're all one in the same or used that way) simply do not work in Ubuntu 16.04 I use the X64 distro if that helps.  This text to speech program is actually quite important to me because it is used for my hobby which is table top role playing.  Since I play a droid I use the computer to speak, so you can see the necessity of this program to function.  I am still using Ubuntu 14.04 for this purpose.  If anyone knows how to get it working in Ubuntu 16.04 that would be a great help to me.  Also does Skype work in Ubuntu 16.04?  I simply tried the TTS program and went back to 14.04 afterwards.  Thank you in advance.

---

### Post by Vidorin on 2016-09-29
*thread bump*

---

### Post by CantankRus on 2016-09-29
I don't use text to speech but testing here both festival and espeak appear to work.
```
echo "This is a test to see how it sounds." | festival --tts
echo "This is a test to see how it sounds." | espeak
```

Also, booted to a Live Xenial ISO, installed festival and espeak.....both above commands worked.

Not up with this stuff... maybe it's just an issue if you want to use different voices.

---

### Post by Vidorin on 2016-10-02
I was unaware you could install programs while running it live without installing the OS.

---

### Post by deadflowr on 2016-10-02
> **Vidorin said:**
> I was unaware you could install programs while running it live without installing the OS.

As long as the package doesn't require a reboot, you can install anything in a live session.
It'll just disappear when you shutdown/reboot.

---

### Post by CantankRus on 2016-10-02
...and you may have to enable the universe and multiverse sources depending on what you want to install.
PS: You can also log out and back in from a live ISO....type "ubuntu" for username and leave the password field blank.

---

### Post by john250 on 2016-10-27
after installing gespeaker, try to install the python-dbus package. It seems that there is a dependency missing as I describe in the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/gespeaker/+bug/1637075](https://bugs.launchpad.net/ubuntu/+source/gespeaker/+bug/1637075)

---

### Post by Vidorin on 2016-10-30
The commands worked which is great but I do however require the ability to use the other voices. The gespeaker front end allowed me to do that with ease changing the pitch, speed, delay, gender and even vocal inflections such as Russian or English accents.  I actually do need these capabilities I found a link to install Gespeaker in Ubuntu 16.04 but it does not appear to function properly the GUI front end also made it much easier to work with.

[https://www.howtoinstall.co/en/ubuntu/xenial/gespeaker](https://www.howtoinstall.co/en/ubuntu/xenial/gespeaker)

And to install the Mbrola package for the additional voices: [https://www.howtoinstall.co/en/ubuntu/xenial/mbrola-de4](https://www.howtoinstall.co/en/ubuntu/xenial/mbrola-de4)

I am going to install Ubuntu 16.04 side by side with 14.04 and do a little experimenting to see if this will work even though I tried it before perhaps it has been added to the Ubuntu software center.  Thank you in advance.

---

### Post by CantankRus on 2016-10-30
Use synaptic to search for and install mbrola voices.

---

### Post by Vidorin on 2016-10-30
All right when I had posted my last reply I hadn't seen the other ones.  Probably a glitch but oh well.  Anyway here is what I had done following the help from all of you here after installing a fresh install of Ubuntu 16.04.

First Step:  Checked Software and Updates and enabled (universe) updates.

Second Step:

sudo apt-get update
sudo apt-get install python-dbus

Third Step:

sudo apt-get update
sudo apt-get install synaptic

Fourth Step:

Then used the synaptic package manager as directed to install additional mbrola packages.

Fifth Step:

Installed Gespeaker from the Ubuntu Software Center.

It seems to be working however it takes a second to start up, a crash report comes up but the program seems to work perfectly. EDIT: The crash has seemed to correct itself, thank you again for all of your assistance. I would've done this sooner however the CPU fan died right after I posted this initially and I had to wait for the new one to arrive. I will mark this as solved.

---

