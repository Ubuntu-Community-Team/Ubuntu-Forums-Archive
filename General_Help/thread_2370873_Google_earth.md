---
title: "Google earth"
date: 2017-09-08
forum: General Help
---

### Post by 4l3x2 on 2017-09-08
Good morning.
I installed XUbuntu 16.04 on the laptop of a colleague/friend of mine, it is an Intel Quad Core with 4Gb of Ram and Ati mobility Radeon HD 4650.

After downloading from google's site the x64 .deb for google earth I couldn't install it with Software or Synaptic, so I installed with:
sudo dpkg -i goo*.deb

After starting again Synaptic I got a window saying I had a damaged package, I did Modify-Repair damaged packets and it installed all the dipendencies.
Now I have the icon under Internet Apps, but launching it the splash screen doesn't disappear and I see the sky only in the upper left part of the window.

Is it a known bug or do you know any workaround to make it work well?

Thank you very much in advance :)

---

### Post by BenginM on 2017-09-08
Top of the morning to you.

remove the google earth package you've installed using synaptic , then install google-earth-pro [this way using the official repo for it]("http://ubuntuhandbook.org/index.php/2017/04/install-google-earth-in-ubuntu-17-04/"), 

if it still behave the same , then run it in terminal like so:
sary@tru-uli63:~$ google-earth-pro %f

and see what the logs has to say..

---

### Post by echotech2 on 2017-09-09
Ubuntu 16.04.03, GeForce 650TI video using Noveau driver.
 
  I have the same problem after following BenginM instructions.  I get nothing except a blinking cursor in the terminal and the logo in the middle of the screen and a small window in the top left corner.

---

### Post by BenginM on 2017-09-09
[ATTACH=CONFIG]276657[/ATTACH]

---

