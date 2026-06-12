---
title: "Trouble instaling software using terminal!"
date: 2008-02-27
forum: General Help
---

### Post by Woe_is_me on 2008-02-27
I'm trying to install some drivers for my sound card. 
So I download and extracted a tar.bz2 fine. I have the successfully extracted folder in my Home folder. 

I then used the guide - "How to install ANYTHING in Ubuntu!"
[http://cutlersoftware.com/ubuntuinstall/#installing_with_terminal]("http://cutlersoftware.com/ubuntuinstall/#installing_with_terminal")

The trouble is, that once I cd into the correct folder. The guide then tells me to do
```
 ./configure
``` I do and get the following message:

> checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Fine. As suggested somewhere else I type in ```
Make
```
and then get the following:

"make all-deps
make[1]: Entering directory `/home/aka/audio/alsa'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/aka/audio/alsa'

Please, run the configure script as first..."

In the guide that I am using it says:
> If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling).

But doesn't tell you which packages to install. Or if it does, then I'm no understanding it. 

Please help, my sound is really pissing me off now! I've tried installing software manually a few times, but it is never successful :confused:

Thank you

Aisha

---

### Post by taurus on 2008-02-27
You need to install the build-essential package first before you can build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Arwen on 2008-02-27
It seems gcc isn't correctly installed,what about reinstalling it?
I think for those tar.bz2 you have to do first "./configure",then "make" and then "make install".

---

### Post by Afkpuz on 2008-02-27
You need a compiler.  Enter this into the terminal

```
sudo apt-get install build-essential
```

Then try again.  The make command only works if the configure part completes.

---

### Post by Woe_is_me on 2008-02-27
Okay thanks I'll try it now...


---few moments later---

I've successfully managed to do as you all suggested, and am now installing the software. Thank you!!

---

