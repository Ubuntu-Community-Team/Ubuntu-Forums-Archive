---
title: "X Server won't start after updates"
date: 2007-06-27
forum: General Help
---

### Post by Shack_ on 2007-06-27
I recently download rougly half of the updates for Ubuntu (I have dial-up, so it takes *forever*). After quitting, I shut down the computer. The next time I booted up, I got an error message saying the X Server wouldn't load because it couldn't find any "screens".

I tried running

```
sudo dpkg-reconfigure xserver-xorg
```

but I don't know any of the information it asks for.

I'd really appreciate some help, and if I need to give more information please just let me know.

---

### Post by MikeEvans on 2007-06-27
What type of video adapter do you have?  ati, nvidia, integrated?

---

### Post by Shack_ on 2007-06-27
It's an NVIDIA.

---

### Post by MikeEvans on 2007-06-27
Okay.  I only have experience with ATI cards but I should be able to help.  If the following doesn't work let me know the model of your card. Different groups of cards use different drivers.

If you have an older card try this:
For X server driver choose 'nv'
The identifier is just a description.  Put whatever you want.
From here you should be able to accept the defaults for things you don't understand, such as PCI bus address.

If you have a newer card AND the above doesn't work you will need to pick a different driver. Since the video was working you should already have the correct driver in the list.  Look for something like Nvidia or nvidia-glx-legacy and try it out.

If you are able to get X running I recommend you install and run Envy to straighten out any remaining video issues.

---

### Post by jimbob on 2007-06-27
If you run *[COLOR="Blue"]dpkg-reconfigure -phigh xserver-xorg[/COLOR]* the only two things you will have to select are the resolution you want and the driver.  If you weren't using the nvidia-glx package select "nv" as above.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Shack_ on 2007-06-27
Thanks for the suggestions. I was able to fix the problem.

---

