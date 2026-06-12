---
title: "915Resolution - Greenish Display when Manual"
date: 2008-03-11
forum: General Help
---

### Post by hudsonhauck on 2008-03-11
Greetings!

I have a notebook attached to a LCD screen, 1440x900. However, it only automatically sets it to 1280x1024 and it looks weird and stretched.

I tried editing /etc/default/915resolution to manually set the resolution. When I restarted it looks like the resolution was different, but there was a greenish-bluish tint.

Any ideas?

---

### Post by dokdoom on 2008-03-11
I'm guessing you have an intel card as do I. If you start X with the monitor plugged in it will mess up the resolution (ie.. incorrect resolution). However, if you restart X your resolution will still be correct. I have a similar setup at work (I think) and in order for my laptop to work with dual screens I don't plug my monitor in until I'm at the login window.

---

### Post by hudsonhauck on 2008-03-11
Sorry, I should have added that the built in notebook display does not work anymore, hence the LCD screen. The notebook lid is still physically attached, but I have disconnected the notebook display's connection to the motherboard.

So all I have is the LCD monitor. My notebook is now a desktop. =)

---

### Post by hudsonhauck on 2008-03-14
Any ideas?

---

### Post by hudsonhauck on 2008-03-14
Okay, I did some more tests:

I first ran this command:

```
sudo /usr/sbin/915resolution 4b 1440 900 16
```

Then i unplugged my monitor and restarted X (ctrl+shift+backspace). When I heard the Ubuntu sound, I plugged the monitor back into find my greenish-bluish screen.

So I logged in and tried to change it back when I discovered something new. I tried to set it back using the following two commands two distinct times) and each one of them set it back to the previous resolution, but *still had the bluish/greenish screen!*

```
sudo /usr/sbin/915resolution 49 1280 1024 16
sudo /usr/sbin/915resolution 38 1280 1024 8
```

So, it appears that the problem is not with the resolution per say but with the tool itself or with the way I am doing it. 

Any thoughts?

---

