---
title: "Using SSH to login"
date: 2007-01-26
forum: General Help
---

### Post by Voodooengine on 2007-01-26
I have Xubuntu installed and i have Apache / Azureus installed. Now i would like to disconect my monitor, keyboard, and mouse and be able to login through a terminal. Is this possible, and if so how would i do so?

Thanks for your help.

---

### Post by Ramses de Norre on 2007-01-26
```
sudo aptitude install ssh
```
Then from the other machine do **ssh user@host** or **ssh -l user host**, to make it a bit more safe you can tweak the config files for the ssh client and server and install denyhosts.

---

### Post by lamego on 2007-01-26
If you want a graphical login, you will need to install a X client (for windows you can use XMing), or you can install a vnc server on your linux box and use a vnc client.

---

### Post by pod25 on 2007-01-26
Your best choice would be to install Webmin.
It runs from a browser either on the same machine or a remote machine.

Using Webmin, you can pretty much do everything required to admin your comp.

---

### Post by bernied on 2007-01-26
My tuppence - It's a very good idea to have a recovery system set up on such a machine. Once you've disconnected the monitor and keyboard and put it in the cupboard/attic/under the stairs, *when* something goes wrong it's a real pain to either find a monitor and keyboard to attach, or to pull the thing out and put it somewhere you can use a monitor and keyboard. My main problems were caused when the thing didn't get shut down cleanly either because it got unplugged by an innocent, or there was a power failure.

So some viable solutions I've found:
1 - get a live-cd that is easy to modify and add sshd to it that it runs on startup, so if things go bad you can put the cd in, turn on the machine, get a coffee (live-cds take longer to boot), then log in and do your fixing up that's needed. I found this fairly easy to achieve using slax - I think I just had to add the link to the init script in the /rootcopy/etc/init.d/ folder. 
2. Create an emergency linux install on a separate partition on the hard-disk (1GB is plenty). Again I used slax for this as a quick and dirty install. I had two grub menu.lst files - one was for recovery and booted the slax install. The other booted my full-time system. So on startup I had a script that did cp menu.lst.recovery menu.lst and on shutdown I did cp menu.lst.normal menu.lst. So if the machine shutdown properly then the normal boot was started, but if there was a power failure the recovery install was started. This recovery install did a fsck with the forcing options, and a few other bits and pieces, then copied the normal menu.lst file back, then restarted. Worked a charm. (This was actually my final and best solution - when the machine was reset, it would be back online within 5 minutes)
3. The other thing you can do is put a terminal on the serial port. You can then use a null-modem cable (basically a crossover serial cable) with another machine (laptops are handy at this point) to log in directly to your machine. You have to compile your own kernel to enable this and there are boot options in the kernel line you have to add, and also a line in menu.lst. (This was my second solution and is the only way to watch what goes on at boot without having a monitor connected). You can even attach an external modem, phone the machine and watch it boot if you want.

---

