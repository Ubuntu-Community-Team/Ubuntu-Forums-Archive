---
title: "trouble installing veejay"
date: 2007-06-03
forum: General Help
---

### Post by vj air on 2007-06-03
im trying to install veejay and im having a complete nightmare. is there any way to install it other than the way listed on the site.... i just seem to get errors all the time :(

at the monent, im getting this when i run the ./configure command for veejay :

**checking for MJPEGTOOLS... configure: error: Cannot find mjpegtools. Did you set PKG_CONFIG_PATH variable?**

 i installed the mjpegtools via the synaptic package manager, so i assume its in the right place, the veejay installation instructions also tell me this :

[B]You need to set the PKG_CONFIG_PATH environment variable to the directories that contain the .pc files.

$ echo $PKG_CONFIG_PATH
$ export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig[/B]

but it doesnt seem to resolve it :(

[http://www.veejayhq.net/?p=79](http://www.veejayhq.net/?p=79)   contains the installation instructions,can i somehow get it to install via the "add/remove applications" or the "synaptic package manager" ?

or does some kind soul fancy trying to help me through it?

thanks.

---

### Post by amonsul on 2007-06-05
Same problem here. I`ve installed the ile manually in the right directory but then u get following error:

configure: error: jpeglib.h not found - please install the libjpeg headers



Its incredible, it seems impossible to install veejay on Ubuntu. We need a .deb package!!

---

### Post by qx! on 2007-06-09
You need also dev package ;)
I did'nt manage to compile veejay too. Bad things with JACK. In dyne:bolic distro it is ready to go. And there is a lot of literature in about veejay - Ubuntu howto too! Maybe it'll work in your situation. (I can e-mail it to you - just write: autodafe at tlen.pl)
Truthfully - after veejay Ubuntu-kick-in-face I've started to look around for some other distro.

---

### Post by planctus on 2007-09-06
You have to compile mjpegtools by yourself and the same for the other packages needed by veejay (unicap, ffmpeg, cairo....)
It's a boring work but it will solve your problem
Davide (planctus)

---

### Post by silverbyte on 2007-09-06
I tried / i really tried / installed all the dev packages followed a tutorial on how to install via following link

( link in french -  use google to translate - warning the commands may add a (.)period when google translates page so copy paste commands in french page open seperate page to read the instructions)


[http://ubuntufromscratch.wordpress.com/2007/09/02/compiler-veejay/](http://ubuntufromscratch.wordpress.com/2007/09/02/compiler-veejay/)

anyways... im not at home but i had an error somewhere saying my QT >= 3.1... 

so no luck getting veejay to work.. If anyone has a success attempt please post the howto.. i see alot of people asking for this and i haven't seen a simple easy way to do it..

---

### Post by silverbyte on 2007-09-06
I found a second tutorial to install on edgy here: 

[http://veejay.dyne.org/trac.cgi/wiki/CompilingOnUbuntu](http://veejay.dyne.org/trac.cgi/wiki/CompilingOnUbuntu)

I'll try this tonight.... i hope it works cuz veejay looks like it kicks ***.

---

