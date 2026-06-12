---
title: "Use Kubuntu CD to add Amarok in Ubuntu"
date: 2008-07-04
forum: General Help
---

### Post by iampriteshdesai on 2008-07-04
I have dial up and I would like to use amarok. I have Kubuntu 8.04 CD. Can I use it to install Amarok in Ubuntu 8.04?

---

### Post by txcrackers on 2008-07-04
Yes - open up the Adept package manager from the system menu, select "Adept/Manage repositories." In the dialog, select "Third-Party Software" and click the button "Add CD-ROM"

---

### Post by Elfy on 2008-07-04
You won't find adept on ubuntu - use software sources to add the cdrom - it'sin system > admin menu

---

### Post by iampriteshdesai on 2008-07-04
Guys what next?
I did the add cd-rom part sucsessfully. Now what to do?
I tried adding amarok via synaptic but it tries to download

---

### Post by Elfy on 2008-07-04
Never done it myself as I've never been without net - first thought did you reload?

If you did try to disable the other repos and leave the cd as the only one which will work, then reload agaian and have another go at installing.

Edit - yea that works, disble all except for cdrom - reload and it will work.

---

### Post by iampriteshdesai on 2008-07-04
I unchecked all but the CD and reloaded. Now synaptic shows some dud softwares. No AmaroK. :(:([http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by Elfy on 2008-07-04
I just checked that it worked with the first thing I saw - I didn't actually look for amarok on the disc - you're right of course and thinking further I don't get it from ubuntu repos at all - it comes from medibuntu.

---

### Post by txcrackers on 2008-07-04
Amarok is on the Kubuntu CD - and you have to use Adept to add it. Do not try to use Synaptic.

---

### Post by Elfy on 2008-07-05
Well the op will have to install adept because it isn't default on ubuntu and I couldn't see it in there, either looking through the cd or when the cd was added as a repo. 

If the package is on there why would it show up in adept and not in synaptic?

---

### Post by txcrackers on 2008-07-05
Ah! I see where my confusion lies - I was reading the question slightly wrong as I thought the computer installation was *also* Kubuntu.

Anyway, I note that synaptic also has an "Add CD-ROM" option, so I wasn't too far off...

I could have sworn that would work. I don't have a CD or DVD to try this myself, but I've done it before with both .deb and RPM packages/distros.

---

### Post by Elfy on 2008-07-05
Yes - I only noticed on second read myself. I thought it should be on the cd myslef - but I assume it's not because amarok pulls in, at the least, the libxine1-ffmpeg package and thus gives mp3 support, which goes gainst the ubuntu copyright thing.

I only have kubuntu as a vm, I know it installs as default but I can't find it on the cd to even point as a dpkg :(

I think the op will be best of using the dial up which isn't the ideal option, unless you can find it on the disc for him. Of course he could end up with a bit of dependency hell if he tries the dpkg route.

In the meantime another player might be best - I've turned amarok off for the moment anyway - pulseaudio problems I think :)

---

