---
title: "AMD Driver installation"
date: 2014-07-28
forum: General Help
---

### Post by Dustin_Whisenhunt on 2014-07-28
I just recently installed Ubuntu and when I attempt to play anything on steam I get an OpenGL error. I believe it is because of my drivers but I can't find a way to install them. I am using a R7 250 Radeon card. I also have the A10-7850K APU and can't get the computer to boot up without the 250 installed. Does anyone know how to fix this?

---

### Post by QIII on 2014-07-29
By "boot up" do you mean Ubuntu won't start, or the machine does not POST?

Is this a laptop or a desktop?

Did you install the ATI proprietary driver?

---

### Post by Dustin_Whisenhunt on 2014-07-29
When I'm only using the APU I just get a black screen.

This is a desktop.

and I chose the propietary drivers under the additional drivers section in the settings.

---

### Post by QIII on 2014-07-29
OK.  Did you do that when you had the dedicated graphics adapter installed?

---

### Post by Dustin_Whisenhunt on 2014-07-29
Yes I did. I was only able to see anything with the dedicated gpu installed. I tried with all three different drivers that were available under additional drivers. Each time steam would give me an Open GL error. It would also say that I need to update my opengl or that my graphics card is not supported.

---

### Post by QIII on 2014-07-29
OK.  Does the machine get past the POST without the dedicated card installed?

Do you know if you BIOS/EFI allows for the use of a dedicated adapter and an integrated one at the same time?  Many desktop motherboards don't, and will choose the dedicated one if present at first startup.  If that is the case, you may only have initialized the dedicated card and Ubuntu knows nothing of the other.

---

### Post by Dustin_Whisenhunt on 2014-07-29
Without the dedicated card the system turns on but I get no display. And I don't know if my BIOS allows that. How could I tell?

---

### Post by Dustin_Whisenhunt on 2014-07-29
My motherboard has two hmdi ports on the back and I have tried both of them without the dedicated card but I still get no display.

---

### Post by QIII on 2014-07-29
You will need to get into your BIOS/EFI setup and take a look at the settings.  Do you have a user manual for the motherboard -- or for the machine if you bought it assembled?

Unfortunately, it is time for me to wander off to bed.  But there are plenty of other folks who should be able to help you out.  :)

Cheers!

---

### Post by Dustin_Whisenhunt on 2014-07-29
Same for me. Thanks for the help. When I get the chance I will look into and reply with what I find out

---

### Post by GreenRaccoon on 2014-07-29
I have this same APU, and I had this same problem. Now if only I could remember how to fix it haha. :oops:

You're using 64 bit, right? If you have Ubuntu 32 bit, don't do these steps.

I never had a problem with blank screens, but I'm guessing it's a driver thing. *Theoretically*, to fix that, you'd go into Terminal and type in "sudo aticonfig --adapter=all --initial", *but* it's kinda hard to do that when you can't see anything. :?

I would try [COLOR=#0000ff]installing AMD's beta driver[/COLOR] while your Radeon GPU is plugged in. That solved a bunch of problems for me. It's a beta driver, but it's the most stable one for me (computers are confusing ](*,)). I even wrote a tutorial on it. :cool: To install the driver, you would follow **step 1** and then **steps 8-13** here: [http://ubuntuforums.org/showthread.php?t=2235189](http://ubuntuforums.org/showthread.php?t=2235189).

For the OpenGL error, I believe all I had to do was [COLOR=#0000ff]make a link[/COLOR]. Steam is trying to find a file that isn't there. Apparently, that file is located in a different place with the current version of the "fglrx" and "fglrx-updates" proprietary drivers (which is what you're using). It's a bug on AMD's end. So to fix it, you'd look at the file path that Steam is using, find out where the file actually is instead, and then make a link to it so that Steam can find it.

Could you post the exact OpenGL error? That might refresh my memory.

I remember [COLOR=#0000ff]installing some packages[/COLOR], but I can't remember if this is what fixed it or if it was something I did *before* I found the right fix. Either way, doing this wouldn't hurt, so I say you should try it. Open up Ubuntu Software Center and search for "mesa". Then click "Show * technical items" at the bottom. Install these packages:
```
libgl1-mesa:i386
libgl1-mesa-glx:i386
libglapi-mesa:i386
libglu1-mesa:i386
libegl1-mesa:i386
```
Btw, this man QIII knows what he's talking about. He's been a lifesaver for me in the past.

---

### Post by Dustin_Whisenhunt on 2014-07-30
Alright. Finally a day off to work on this. I do use 64 bit. You said for the opengl error you had to do what? All it says is "make a link"
I tried installing amds driver straight from the site and when it finishes I get an error saying to enable POSIX shared memory.

---

### Post by Dustin_Whisenhunt on 2014-07-30
Well I installed those mesa packages and steam will now play games!

I just need to make sure I have to correct drivers for for my card and apu.

---

### Post by GreenRaccoon on 2014-08-05
> **Dustin_Whisenhunt said:**
> Well I installed those mesa packages and steam will now play games!I just need to make sure I have to correct drivers for for my card and apu.Cool! Maybe it was those mesa packages that fixed it for me too.

---

