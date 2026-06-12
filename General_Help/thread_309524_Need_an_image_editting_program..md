---
title: "Need an image editting program."
date: 2006-11-27
forum: General Help
---

### Post by Kittie Rose on 2006-11-27
Nobody had an answer the first time, so I'll try again.

I cannot use WINE as Winetools refuses to download the MFC libraries with are a part of basic set up. It gets stuck at 0%. When I exit that(download) window, it creates "dummy" images which make it think it's installed but it returns errors, obviously, when I use it in Terminal.

I don't know why it's not downloading. I'm on a very restricted connection, that could be it. I would appreciate if someone could tell me of a different way to get the libraries up and running as there are several tools I need to use in Windows while still using other tools in Linux.

---

### Post by ardvark71 on 2006-11-27
Hi Kittie...

Not sure if this will help but is there a way you can download them separately and then integrate them into the program? 

I've had my share of problems with WINE too, it definately requires more refinement:roll: I try to get as much linux native stuff as I can.

Best regards...

:KS

---

### Post by Kittie Rose on 2006-11-27
That's what I'd like to know... this is the third time I've posted this. I'm really disappointed as most people have tried WINE at some point and should at least have a copy of the right MFC files they can send me...

---

### Post by Kittie Rose on 2006-11-27
Come on! This is my third attempt asking about this. It's not like I need to get this working or anything :/

---

### Post by StarsAndBars14 on 2006-11-27
Well. . .

What version of Wine are you running, first?  

I have 0.9.26 and it hasn't asked me to download anything. All .dll files come packed with its tarball.  The only .dll file I had to download is msvcr71.dll and that's because I tried using America's Army with it.

If you have all the needed files, then try typing "wineprofilecreate" into the terminal.

---

### Post by Kittie Rose on 2006-11-27
Pretty sure it's 0.9.5 , as a tutorial I was linked to said to use that.

---

### Post by StarsAndBars14 on 2006-11-27
There's your problem.  Download 0.9.26 from winehq.org, it should be on the upper right corner of the page under "Latest."

---

### Post by ardvark71 on 2006-11-27
> **Kittie Rose said:**
> Come on! This is my third attempt asking about this. It's not like I need to get this working or anything :/

:roll:

---

### Post by ardvark71 on 2006-11-27
Kittie...

Is this what you are looking for?

[http://www.topshareware.com/XD---MFC-Library-download-1086.htm](http://www.topshareware.com/XD---MFC-Library-download-1086.htm)

Regards...

:KS

---

### Post by Kittie Rose on 2006-11-27
> **StarsAndBars14 said:**
> There's your problem.  Download 0.9.26 from winehq.org, it should be on the upper right corner of the page under "Latest."

Nope, new version, same problem. It's Winetools, not Wine, anyway.

---

### Post by Kittie Rose on 2006-11-27
Sorry, I should have clarified that I need help with Winetools in specific. Where can I download the Microsoft Foundation classes?

---

### Post by Kittie Rose on 2006-11-27
drael@Teletraan8:/media/Win-C/program files/jasc software inc/paint shop pro 7$ wine psp
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JCMYK.dll") failed (error c0000020).
err:module:import_dll Library MSVCIRT.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JCMYK.dll") not found
err:module:import_dll Library JCMYK.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\jbrwsutil.dll") failed (error c0000020).
err:module:import_dll Library jbrwsutil.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\jbrwsutil.dll") failed (error c0000020).
err:module:import_dll Library jbrwsutil.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\jbrws.dll") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\jbrws.dll") failed (error c0000020).
err:module:import_dll Library jbrws.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JControls.dll") failed (error c0000020).
err:module:import_dll Library JControls.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JControls.dll") failed (error c0000020).
err:module:import_dll Library JControls.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JWebTools.dll") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\jbrwsutil.dll") failed (error c0000020).
err:module:import_dll Library jbrwsutil.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JWebTools.dll") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JWebTools.dll") failed (error c0000020).
err:module:import_dll Library JWebTools.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") not found
err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") failed (error c0000020).
err:module:import_dll Library MSVCIRT.dll (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\psp.exe" failed, status c0000135
drael@Teletraan8:/media/Win-C/program files/jasc software inc/paint shop pro 7$ 


How can I fix this? Where can I get the MFC libraries online?

---

### Post by Kittie Rose on 2006-11-27
For ****'s sake there are loads of things that require the MFC libraries, I refuse to believe nobody knows where to get them.

---

### Post by ardvark71 on 2006-11-28
> **Kittie Rose said:**
> Sorry, I should have clarified that I need help with Winetools in specific. Where can I download the Microsoft Foundation classes?

Did you see my previous post with the link?

---

### Post by CatKiller on 2006-11-28
[http://appdb.winehq.org/appview.php?iVersionId=1405](http://appdb.winehq.org/appview.php?iVersionId=1405)

Perhaps you'd like to remember that people have absolutely no reason to help you.

---

### Post by Kittie Rose on 2006-11-28
That thinking is exactly why only about 3% of PCs currently run Linux.

There are plenty of reasons to help; common decency is one.

You can bash out the "You're not entitled to anything" but it doesn't change the fact that I can't do what I want with what you want to be a succesful operating system.

If nobody helps me, I will *never* get WINE running and I will probably be put off Linux altogether. I'm sure I'm not the first one if this is the common attitude in a forum that's meant to help people.

---

### Post by Kittie Rose on 2006-11-29
No, it's not what I'm looking for...

---

### Post by Cable on 2006-11-29
Is winetools really needed?  It's possible to get wine up and running just fine without it.

---

### Post by Kittie Rose on 2006-11-29
Well, since nobody seems to want to help me get PSP7 working under Wine, I'm wondering if anyone could recommend a good alternative that isn't the GIMP(a bit messy and can't figure out how to draw lines) or KRITA(Bad anti-aliasing).

I primarily use it for photomanipulation and putting action figure comics together...

---

### Post by maniacmusician on 2006-11-29
Well, for one thing, this post is in the wrong place. The cafe is a casual hangout separate from the support part of the forums. So it'd probably be best to post either in the [General Help forum]("http://ubuntuforums.org/forumdisplay.php?f=131") or in the [Art and Design forum.]("http://ubuntuforums.org/forumdisplay.php?f=16") There's also some graphics-oriented third party project forums.

---

### Post by Kernel Sanders on 2006-11-29
Gimp Shop :)

---

### Post by Kittie Rose on 2006-11-29
I need something similiar to PSP7 as I can't get it working in WINE; with layers, properly anti-aliased line tools, etc.

---

### Post by taurus on 2006-11-29
Gimp!!!

---

### Post by John.Michael.Kane on 2006-11-29
[http://www.gimp.org/](http://www.gimp.org/)
[http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)
[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html#42](http://www.linuxrsp.ru/win-lin-soft/table-eng.html#42)

---

### Post by Kittie Rose on 2006-11-29
No not Gimp or Krita... neither of them can do proper anti-aliased lines, and GIMP's interface is horribly cluttered.

---

### Post by handaxe on 2006-11-29
Hi,

Ah dear, the "I want an image editor" ... "GimP"..."Not that!".. thread again ;). It tends to get folk worked up.

And so might this suggestion:

Pixel - a cross platform commercial package. Take a look at the slightly crippled trial and see what you think. Quite Windows-like it seems and a quite extraordinary effort by one guy.

[http://www.kanzelsberger.com/](http://www.kanzelsberger.com/)

I am a happy GIMP user, btw.

HA

---

### Post by Josh1 on 2006-11-29
Pixel maybe?

---

### Post by handaxe on 2006-11-29
Snap! :)

---

### Post by graigsmith on 2006-11-29
what are you trying to do?  if you want to make anti aliased lines, perhaps try inkscape. you can make perfect line drawings with that, with full antialiasing, and then export it to a png file.

OR, use gimp's paintbrush, and adjust the brush size to get antialiasing on your lines. if you want straight lines hold down shift.

---

### Post by rioghal on 2006-11-30
I would recommend the GIMP. I have been using Linux for about two months and using the gimp even less time. I have been learning as much as I can about this wonderful image manipulation app and have created quite a few nice things. Take a look at what a newbie can do with the gimp:

[http://ubuntuforums.org/gallery/showphoto.php?photo=4153](http://ubuntuforums.org/gallery/showphoto.php?photo=4153)

Imagine what we can make if we learn more about the GIMP :)

---

### Post by Kittie Rose on 2006-12-01
[email]drael@Teletraan8:~/.wine[/email]/drive_c/Program Files/Seagrand/Pixia$ wine pixia
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  99
  Current serial number in output stream:  99


What does it mean?

---

### Post by LLRNR on 2006-12-01
"wine pixia" ???... Shouldn't that be... "wine pixia.exe" ? 

When I tried to run Flash.exe ( Macromedia Flash 8 ) with Wine, it turned out that sometimes it crashed if I didn't respect case sensitivity (and it sometimes crashed if I *did* !), also you might try to run it as "sudo"; I know it's not recommended, but sometimes it's the only way to get it working.

So I'd suggest you try all the combinations:

wine pixia.exe
wine Pixia.exe
sudo wine pixia.exe
sudo wine Pixia.exe

and see if it helps... Sorry, I don't have other ideas, this is what I learned from my experience.

LLRNR

---

### Post by Kittie Rose on 2006-12-01
No difference.

---

### Post by Kittie Rose on 2006-12-01
I thought Linux was meant to have tons of cool free software, but the best package is commerical? :/

What else does Inkscape do? I could do pretty much everything I wanted in PSP7 in one unified package... I'd like that since nobody wants to help me getting it to work in WINE.

Layers, proper anti-aliasing lines, all sorts of brushes, etc...

---

### Post by timcredible on 2006-12-01
> **Kittie Rose said:**
> I thought Linux was meant to have tons of cool free software, but the best package is commerical? :/

hmmm... very, very few people need the app you're talking about.  and it's not the best package.  the best packages list would include openoffice, firefox, thunderbird, amarok, digikam, mplayer, k3b, gaim.  that covers about 90% of what 90% of users need.

---

### Post by Kittie Rose on 2006-12-01
> very, very few people need the app you're talking about.

Then, err, why would photoshop and paint shop pro be as successful as they are?

---

### Post by aysiu on 2006-12-01
By the way, double-posting (let alone quintuple-posting) is generally frowned upon here. I've merged all your Wine/Paint Shop Pro support threads into this one thread.

You may want to consider--if Paint Shop Pro is that important to you--running it in Crossover Office, as [this thread indicates might work](http://os.vault9.net/forums/lofiversion/index.php/t10654.html).

Honestly, though, it's about assessing your needs. If you *need* Windows-only applications, you should use Windows. Many of us love the native Linux applications available to us. If I needed AutoCAD, Photoshop, iTunes, and PC games, I wouldn't be using Ubuntu. Since I don't care for any of those programs, I use Ubuntu.

---

### Post by aysiu on 2006-12-01
By the way, [DaveRowell](http://ubuntuforums.org/member.php?u=31271) indicated in [this thread](http://ubuntuforums.org/showthread.php?t=212958) that he could run Paint Shop Pro in Wine: [quote=DaveRowell]I can do this without problems if I use Paint Shop Pro under Wine rather than Gimp but it really shouldn't be necessary.[/quote] Maybe you can ask DaveRowell for some help? That was posted not too long ago.

You can also find some other non-GIMP alternatives in this thread: [Help I miss Paint Shop Pro](http://ubuntuforums.org/showthread.php?p=760257#post760257)

---

### Post by doobit on 2006-12-01
There's been plenty of good advice offered, and ignored.
Gimp can do antialiased lines or any other shape for that matter. Photoshop, et.al. are horribly complicated and cluttered as well, until you learn to use them. 
Blender can do great 3D, just look at some of the examples on their site. I've got a couple of nice Blender and Gimp creations on my desktop at work.
I work with PhotoShop practically every day and Gimp at night, and after a little while working with Gimp, I am able to do everything that I also do in Photoshop. I have to do it a different way, in some cases, and the terminology in GIMP is different, but I can accomplish the tasks I set out to do. Someone here suggested GimpShop which is Gimp with a more sticky layout, like Photoshop's. You ignored that post.
There are plenty of great tutorials out there on Gimp that will show you how to get the results you want. Here are a couple:
[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)
[http://www.ftgimp.com/](http://www.ftgimp.com/)
[http://docs.gimp.org/en/gimp-tools-paint.html](http://docs.gimp.org/en/gimp-tools-paint.html)

I Photoshop, I can get a nice looking bitmap line using the rectangle tool and drawing a flat rectangle. That works well in Inkscape and Gimp and Illustrator or what ever graphic tool you use.

[IMG]http://www.louddata.com/line.jpg[/IMG]

---

### Post by Kittie Rose on 2006-12-01
That sounds really interesting(Crossover office) - however the topic does not detail where to get it and how to install it. Also, how do I open ".package" files?

[img]http://www.louddata.com/line.jpg[/img]

Eep, that looks way to jaggy for me... PSP7 had nice smooth lines.

---

### Post by doobit on 2006-12-01
You got a problem with your monitor. I made this in PSP7. It's also only 72dpi and one pixel wide and rotated.
Why don't you post one so we can see what you are complaining about?

---

### Post by Kittie Rose on 2006-12-01
That's not what PSP7's lines look like for me at all.

[http://www.deviantart.com/deviation/14439537/?qo=26&q=by%3Awetflameg&qh=sort%3Atime+-in%3Ascraps](http://www.deviantart.com/deviation/14439537/?qo=26&q=by%3Awetflameg&qh=sort%3Atime+-in%3Ascraps)

---

### Post by cleentrax on 2006-12-01
Kittie Rose,

Why are you using an image editing program to draw lines? I would suggest using Inkscape, which has a more intuitive interface than GIMP, and is designed especially for line drawings. Think of it as more like Illustrator than Photoshop.

I do have Photoshop 7 working with WINE, and it didn't require Winetools. But these days I usually just use GIMP if I can, because Photoshop 7 doesn't run as smoothly through WINE as GIMP does natively.

---

### Post by doobit on 2006-12-01
I agree with cleentrax, however, here is an image with lines I created in Gimp just for comparison. The difference is in how I made the lines. It's not in the tool I used. That's the point I'm trying to make. The tools are all good, but you gotta learn how they work.

[IMG]http://www.louddata.com/lines.jpg[/IMG]

here's one I made with Inkscape exported as a bitmap that could be edited in Gimp.

[IMG]http://www.louddata.com/lineinkscp.png[/IMG]

---

