---
title: "fb: unsupported in X"
date: 2006-11-27
forum: General Help
---

### Post by amacieli on 2006-11-27
Hi there,

Relatively new Ubuntu Edgy user.  Trying to install AdvanceMENU, compiles OK as far as I can see, but getting fb: unsupported in X error when trying to run.  Have tried this:
- installing all dependencies that i could find using synaptic
- installing all SDL libraries, including dev versions (one at a time - recompiling advmenu each time)
- using --enable-sdl when doing ./configure
- googling the planet (one hit - no resolution)
- installed and successfully ran xmame (rtype lives!!!) using synaptic

Any ideas? :confused:

---

### Post by Horbert on 2006-12-13
I know this is a little late but I was getting ready to install Advancemenu here on Edgy and was searching the forums to see if anyone had any issue before I started.

I found the following information concerning the error you were getting and wanted to share. 

I take no credit for this and will post back if I have the same error and end up having to follow these steps:

"Running and compiling AdvanceMAME, as well as AdvanceMENU without framebuffer support.
Code:
./configure --disable-fb

Make sure that you have set the correct environment variables, to execute the command sdl-config. Or else you will get a error message like that:
Code:
configure: error: no video library found. If you have the SDL library installed somewhere try using the --with-sdl-prefix option.

Fix it in following order:
Code:
locate sdl-config

Then check if in /etc/profile the correct environment variables are set and if the directories listed in /etc/profile contain the command sdl-config. Probably not. Do...
Code:
export PATH="$PATH:/usr/local/bin"

e.g. if /usr/local/bin is the directory where sdl-config is located (it's strange, because it should be in there by default, and not only /usr/bin or something similar)

Then go again through the configure and compile procedure
Code:

./configure --disable-fb
make
sudo make install

advmenu (First time to create a advmenu.rc profile)
advmenu (Second time to start the emulator)

If you hear "let's rock", then it works. Press F1 inside of AdvanceMenu for the HelpScreen."

---

