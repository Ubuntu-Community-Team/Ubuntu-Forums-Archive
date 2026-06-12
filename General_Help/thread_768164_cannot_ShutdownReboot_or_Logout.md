---
title: "cannot Shutdown/Reboot or Logout"
date: 2008-04-26
forum: General Help
---

### Post by Cue2 on 2008-04-26
Hello everyone

I have a very odd problem where if I Logout reboot/shutdown hibernate you name it. I end up with perfectly spaced vertical strips on my screen and the system hangs. I looked around for answers but can't find much. What is usplash? I think it may be the culprit.

---

### Post by Cue2 on 2008-06-23
Months and still no reply, should I report this as a bug. Anyone with any ideas?

---

### Post by llama320 on 2008-06-23
i haven't had this problem, but i might be able to help debug it a little or at least get some more information for someone else to look at it

First off..what version are you using, gutsy? hardy?
are you on a desktop/laptop? maker/model?
what driver are you using? ATI or nVidia?

usplash is the screen that you see before you login..with the orange progress bar and logo. While I can't think of why this would cause your problem, i can tell you how to turn it off:

```
sudo gedit /boot/grub/menu.lst 
```
scroll down a ways until you hit something that looks like 

## ## End Default Options ##

After that, you should find the kernel you're currently using (probably the topmost one) and go to the "kernel" line (3rd from the top) and remove the word "splash" from the line

so BEFORE you edit the file it should look something like this:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8b0aca70-053c-482a-b2f6-00662d11ad9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

and AFTER:

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8b0aca70-053c-482a-b2f6-00662d11ad9b ro quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Then just reboot and you shouldn't see the usplash screen anymore

If that doesn't help, it may be an issue with your video drivers..
I can only really speak to nVidia..but if you're currently using nvidia-glx-new, try uninstalling it and installing nvidia-glx or nvidia-legacy

```
sudo apt-get purge nvidia-glx-new nvidia-glx+
```
^^this will uninstall glx-new and install nvidia-glx, for example

Good Luck

---

### Post by Cue2 on 2008-06-23
Thanks for the reply llama320.
sorry for not being more specific/informative

I'm using hardy (first time using ubuntu)
I'm on a desktop with a Asus P5E3 Premium wifi@n board and a 3870x2 graphics card. I think you are right it may be a graphics driver problem since my card and linux aren't friends. I have not installed any drivers at all for my card so I'm guessing it uses the default vesa drivers or something; correct? I will try the no usplash option again using your instructions and report back. Thanks for your help.

---

### Post by Cue2 on 2008-07-02
nope I disabled usplash but it still crashes. anyone have a 3870x2 running well on ubuntu or know how I can resolve this problem.

---

### Post by theshadowwithanmp5n on 2008-07-02
what card are you using?
ATI RADEON cards have notorious problems on ubuntu. it may be the drivers.

---

### Post by Cue2 on 2008-07-04
> **theshadowwithanmp5n said:**
> what card are you using?
ATI RADEON cards have notorious problems on ubuntu. it may be the drivers.

yep I'm afraid thats what I have an ATI 3870x2 but I've searched the forums and others with a 3870x2 do not seem to have a similiar problem (knew I should have stuck to nvidia :() do you think an embedded linux on the motherboard causes problems too? any ideas how I can get some info about whats failing.

---

### Post by theshadowwithanmp5n on 2008-07-05
i have never had the described problem
i'm basing my info on my friends problem.
an embedded mother board video card may not cause problems.
i know my motherboard video card works fine
but compiz will lag if it isn't a 3D accelerated card.

---

### Post by Cue2 on 2008-09-05
sorry for the very late reply (I had sort of given up on ubuntu). I don't have an embedded video card but an embedded SSD which has linux on it. "splashtop expressgate" do you think that is somehow conflicting with it?

---

### Post by Crafty Kisses on 2008-09-05
Try checking your error logs and see why it hangs.

---

### Post by Cue2 on 2008-09-06
> **Codename said:**
> Try checking your error logs and see why it hangs.

Not really sure which log to check and how.

---

