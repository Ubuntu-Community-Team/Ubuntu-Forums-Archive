---
title: "I'm having trouble running a skydome..."
date: 2008-06-05
forum: General Help
---

### Post by Jshaw on 2008-06-05
Hello everyone,

I've been having trouble enabling the skydome feature in hardy heron. Take a look at the screenshot I have attached below...

[IMG]http://i13.photobucket.com/albums/a277/bowser60/Screenshot-1.png[/IMG]

As you can see, where the skydome should be, there is just a cream colored background.
This is the skydome I had attached...
[IMG]http://i13.photobucket.com/albums/a277/bowser60/glassearth3skydome.png[/IMG]

If someone could give me a few pointers it would be much appreciated.

---

### Post by Gourgi on 2008-06-06
don't use it, is not cool :-P
[[IMG]http://img380.imageshack.us/img380/1048/200806061347271680x1050vg5.th.png[/IMG]](http://img380.imageshack.us/my.php?image=200806061347271680x1050vg5.png)

ok now let's see 
in ccsm enable png plugin and tell me if it works

---

### Post by Jshaw on 2008-06-06
> **Gourgi said:**
> don't use it, is not cool :-P
[[IMG]http://img380.imageshack.us/img380/1048/200806061347271680x1050vg5.th.png[/IMG]](http://img380.imageshack.us/my.php?image=200806061347271680x1050vg5.png)

ok now let's see 
in ccsm enable png plugin and tell me if it works

Oh, the skydome was way bigger, somehow the attached image was just  scaled down.

---

### Post by Forlong on 2008-06-06
Maybe it's just a problem of geometry.
Give us a link to the original image, so we can test it.


P.S. please do not post such huge screenshots in the forum.

---

### Post by Gourgi on 2008-06-06
it works here (see photo above)
i use latest-git

---

### Post by Forlong on 2008-06-06
> **Gourgi said:**
> it works here (see photo above)
You managed to use a scaled down version of the original.

But that is not what Jshaw wanted to achieve. Nobody in their right mind would want to use a skydome that tiny ;)

---

### Post by Jshaw on 2008-06-06
> **Forlong said:**
> You managed to use a scaled down version of the original.

But that is not what Jshaw wanted to achieve. Nobody in their right mind would want to use a skydome that tiny ;)

The jpeg, png, svg, and text things were enabled in ccsm, I'm not sure what's happening.

here's the link to the full skydome...
[[IMG]http://img166.imageshack.us/img166/7266/glassearth3skydomeio3.th.jpg[/IMG]](http://img166.imageshack.us/my.php?image=glassearth3skydomeio3.jpg)

---

### Post by Jshaw on 2008-06-06
and here's a picture of my ccsm settings for skydome. 
[[IMG]http://img379.imageshack.us/img379/5310/screenshot1rk4.th.png[/IMG]](http://img379.imageshack.us/my.php?image=screenshot1rk4.png)

---

### Post by Gourgi on 2008-06-06
direct link 
[http://img166.imageshack.us/img166/7266/glassearth3skydomeio3.jpg](http://img166.imageshack.us/img166/7266/glassearth3skydomeio3.jpg)

i'm still able to see the skydome correctly

---

### Post by Forlong on 2008-06-06
I can confirm the image doesn't work on an Ubuntu default install.
I'm getting a plain white screen (other images work, though).

Will do some further testing later.

---

### Post by Forlong on 2008-06-06
OK... here's the thing:

The problem is the maximum 3D texture size your graphics card is capable of.
You can find out what yours is by running this command:
```
glxinfo -l | grep MAX_TEXTURE_SIZE | awk '{print $3}'
```

Mine is 2048, thus I am able to use only images that are lower in resolution than 2048x2048


The solution:
1) Crop the image until it's small enough
2) Scale it down
3) both (trial and error what looks best in the end)

---

### Post by caro on 2008-06-06
Forlong is right... I had the same problem and only figured out when I realized some pics would work as skydomes and others wouldn't.  I used gimp and resized the ones that wouldn't work and problem solved.

---

### Post by Jshaw on 2008-06-06
> **Forlong said:**
> OK... here's the thing:

The problem is the maximum 3D texture size your graphics card is capable of.
You can find out what yours is by running this command:
```
glxinfo -l | grep MAX_TEXTURE_SIZE | awk '{print $3}'
```

Mine is 2048, thus I am able to use only images that are lower in resolution than 2048x2048


The solution:
1) Crop the image until it's small enough
2) Scale it down
3) both (trial and error what looks best in the end)
Thank you forlong! Turns out mine was the same as yours.

---

