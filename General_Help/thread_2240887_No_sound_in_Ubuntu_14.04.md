---
title: "No sound in Ubuntu 14.04"
date: 2014-08-22
forum: General Help
---

### Post by linkdan8 on 2014-08-22
lJust upgraded to Ubuntu 14.04 I have a Vaio VGN-A690 laptop I go to setting, sound,  drivers are there but no sound comes out. Please help

---

### Post by gdesilva on 2014-08-23
Run 'alsamixer' in a terminal and make sure your settings are not muted. If a channel is muted there will be 'm' on that channel. Pressing 'm' on your keyboard will unmute it. If this does not work it would be helpful if you can post the output from alsamixer.

---

### Post by bizhat on 2014-08-23
Must be alsamixer, every time i install ubuntu, i have this problem, playing with alsamixer solve the issue.  If you can't fix, post a screenshot of alsamixer screen.

---

### Post by linkdan8 on 2014-08-23
[ATTACH=CONFIG]255756[/ATTACH]Not sure but is this what you needed?

---

### Post by bizhat on 2014-08-23
See some with MM ? They muted, use arrow key to select these and press M to un-mute.  Also there are more settings, if you use right arrow key you will see more of them, make sure all of these are un-muted.

See these pictures.

This is when my screen is small, only show few of the settings

[[IMG]http://i.imgur.com/5HAUWpel.png[/IMG]](http://imgur.com/5HAUWpe)

When i maximize (or move right with arrow key) you can see more of the settings

[[IMG]http://i.imgur.com/RtgGkVml.png[/IMG]](http://imgur.com/RtgGkVm)

try un muting these while playing some music. One of them will work.

---

### Post by linkdan8 on 2014-08-23
[ATTACH=CONFIG]255771[/ATTACH]I put all up and still nothing

---

### Post by bizhat on 2014-08-23
Can you post result of

```

cat /proc/asound/cards
aplay -l

```

---

### Post by linkdan8 on 2014-08-23
[ATTACH=CONFIG]255778[/ATTACH]

---

### Post by gdesilva on 2014-08-26
I would check to see that you have plugged the speakers into the line-out port.

Also, go to Sound Settings -> Playback tab and then play audio. If you have got the software settings right you would see audio playback indicator working. In that case the problem is that you have not plugged into the correct port.

---

