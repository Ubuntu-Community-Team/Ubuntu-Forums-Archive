---
title: "[ubuntu] Logged in but no prompt"
date: 2013-12-01
forum: General Help
---

### Post by kylepeyton on 2013-12-01
I'm pretty new to using unix with vmware player but after logging in with the correct credentials I'm not getting a prompt.  I can type but the text just shows up and hitting "enter" just goes to next line instead of submitting command.  Any ideas how to fix this?

[IMG]http://i.imgur.com/7wqJluC.png[/IMG]

---

### Post by jeanjd63 on 2013-12-01
Hello
You can try  a : ctrl+c 
Bye

---

### Post by kylepeyton on 2013-12-01
ctrl+c just seems to log me out and put me back at the login prompt

---

### Post by Impavidus on 2013-12-01
Maybe there's some command in your .bashrc (or whatever you use) that never returns. In that case you never get the prompt.

---

### Post by steeldriver on 2013-12-01
Agreed - maybe try getting into a default bash subshell

```
bash -norc -noprofile
```

or a dash shell

```
sh
```

---

### Post by kylepeyton on 2013-12-01
Where do I type this in?  soon as the machine is powered on I get the login prompt and if I login in to it, I only get this weird screen where I can type but it doesn't respond to anything but ctrl-c:

[IMG]http://i.imgur.com/w0LGNpC.png[/IMG]

---

### Post by steeldriver on 2013-12-01
OK so I was hoping that typing it exactly like you've done would drop you to a (working) subshell - apparently not. Sorry.

You could boot into recovery mode and examine your /home/*username*/.profile and/or /home/*username*/.bashrc (or temporarily rename them)

Hmmm... before you do that how about

```
**exec** bash -noprofile -norc
```

This may be able to **replace** the hung shell

---

### Post by kylepeyton on 2013-12-01
Still just no response when I type that command in.  How do I boot up in recovery mode?  Actually I figured that out, but now I'm in a "grub" shell and I'm not sure how to get to the dir so I can rename the login files

---

### Post by steeldriver on 2013-12-01
No you don't want to be in the grub **shell**, you want to get to the grub **menu** and then select "whatever x.x.x kernel (recovery mode)" - then you should get a menu where you can select "Drop to **root** shell". Usually you need to hold the 'Shift' key right after the BIOS screen to get the grub menu.

If you want to make changes to files you will need to remount the filesystem with rw permissions once you're in the root shell

```
mount -o remount,rw /
```

---

### Post by kylepeyton on 2013-12-01
You're being very helpful and I appreciate it.  Now I just have the problem of not being able to log in to root through your instructions.  It's asking for the root password and I don't know it.

---

### Post by steeldriver on 2013-12-01
Hmm well the root account is disabled by default so it normally drops straight to the '#' root prompt - if someone has enabled the root account by setting a password then afaik there's no way around that short of doing a live boot with a CD/DVD/USB and fixing stuff from there - I don't know what the equivalent of that would be for a VM

---

### Post by drmrgd on 2013-12-01
> **steeldriver said:**
> Hmm well the root account is disabled by default so it normally drops straight to the '#' root prompt - if someone has enabled the root account by setting a password then afaik there's no way around that short of doing a live boot with a CD/DVD/USB and fixing stuff from there - I don't know what the equivalent of that would be for a VM

The equivalent in this case would be to choose the Ubuntu .ISO image in the virtual machine settings of VMware Player, and then powering on the virtual machine.  This is quite a strange problem indeed!

---

### Post by kylepeyton on 2013-12-01
As an update I fixed this problem but not because I figured how to login to root without knowing the password, but because I remembered the password.  Thanks for all of the help.

---

### Post by steeldriver on 2013-12-01
Just out of curiosity, were you able to determine what was causing the hang up - or did you just replace the file(s)?

---

### Post by kylepeyton on 2013-12-01
Yes, I figured it out.  The problem was an infinite loop where init scripts were including each other in a cyclical fashion.

---

