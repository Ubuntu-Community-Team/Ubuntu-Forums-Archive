---
title: "How to fix screen resolution of Dynex LCD TV in Ubuntu 12.10"
date: 2012-12-17
forum: General Help
---

### Post by chrissy.millichamp on 2012-12-17
Hi, Im trying to fix my screens resolution on my VGA adapted *Dynex* LCD TV *Model*: *DX*-*32L*,  and there is not much options in the screen resolutions app in Ubuntu  12.10. Is there anyway I can fix my screen resolution to a smaller  resolution???

---

### Post by papibe on 2012-12-17
Hi chrissy.millichamp.

Could you post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by chrissy.millichamp on 2012-12-17
Why did it gave me these error messages in the terminal with the two commands you gave me one after the other, bash: /etc/X11/xorg.conf: No such file or directory, bash: /var/log/Xorg.0.log: Permission denied

---

### Post by chrissy.millichamp on 2012-12-17
So whats the problem?

---

### Post by dannyboy79 on 2012-12-17
those weren't commands he gave you, those were full paths to the files he wanted to see. You need to open them and copy and paste the contents to pastebin and then come back here and paste the links here.

---

### Post by chrissy.millichamp on 2012-12-17
It seems there is no such files... I cant find them

---

### Post by papibe on 2012-12-17
From post #3, it looks like /var/log/Xorg.0.log **does** exits.

Run this commands to get its content on an editor:
```
gedit /var/log/Xorg.0.log
```
Then copy and paste the content so we can see it.

Regards.

---

### Post by chrissy.millichamp on 2012-12-17
Here you go guys! 
[http://paste.ubuntu.com/1446196/](http://paste.ubuntu.com/1446196/)

---

### Post by papibe on 2012-12-17
Thanks.

This is what I can see:
[LIST]
[*]The intel driver seems to be working well for your integrated graphics.
[*]Your TV is being recognized:
```
        Identifier "DX-32L100A13"
        VendorName "BBY"
        ModelName "DX-32L100A13"

```
[*]The TV's internal timings are read well as well (EDID data).
[*]This are the resolutions available:
```
"1360x768"x60.0
"1280x768"x74.9
"1280x768"x59.9
"1024x768"x75.1
"1024x768"x70.1
"1024x768"x60.0
"1024x576"x60.0
"800x600"x72.2
"800x600"x75.0
"800x600"x60.3
"800x600"x56.2
"848x480"x60.0
"640x480"x72.8
"640x480"x75.0
"640x480"x60.0
"720x400"x70.1   

```
[/LIST]
Are you able to see those resolutions when you get into the tool 'Monitors'?

Regards.

---

### Post by chrissy.millichamp on 2012-12-17
I have the"1360x768"x60.0 option, but I want smaller actually. Thats why Ive asked for help in the first place.

---

### Post by papibe on 2012-12-17
Do you want a lower resolution, as in everything would look bigger?

...or

Are you missing the edges of the screen by any chance?

Regards.

---

### Post by dannyboy79 on 2012-12-18
> **chrissy.millichamp said:**
> I have the"1360x768"x60.0 option, but I want smaller actually. Thats why Ive asked for help in the first place.that's the highest resolution you'll get according to your Xorg.0.log

---

