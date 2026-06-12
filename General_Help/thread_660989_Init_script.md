---
title: "Init script"
date: 2008-01-07
forum: General Help
---

### Post by GLMnet on 2008-01-07
Hi everybody:

I just wrote my first script:

#! /bin/sh

sudo nvclock --memclk 8
sudo nvclock --nvclk 2

thats it. the script works running in the command line.

I want it to run when sys goes runlevel 2 so I did copy the script to /etc/init.d chmoed it to +x

then I ran update-rc.d nvclockset defaults 99

it ran and setted up a link on several rcN.d folders.

did not work: I check the clock frequencies with the tools but they are the default.
How can I troubleshoot this?

p.s. Im on a blind server here remotely access. I can go and attach a screen on this but i still don't know if it is necessary.

Thanks in advance

---

### Post by Vixis on 2008-01-07
remove sudo from your script

---

### Post by GLMnet on 2008-01-07
no. I doesnt work either.

---

