---
title: "Help setting  up some things..."
date: 2006-11-26
forum: General Help
---

### Post by Kittie Rose on 2006-11-26
First off, I want to change the colours of windows and stuff from brown to various shades of green. 

Secondly, I need to set up my Sound Blaster Live! and anything else I need for playing mp3s. I have no idea how to install this "advanced linux sound architecture". Can someone talk me through this?

Thirdly, I need help setting up Wine...

Thanks.

---

### Post by Kittie Rose on 2006-11-26
Hello? :/ I really need to install Mp3 support and themes... please help...

Also, it won't let me install any .deb packages... urgh...

---

### Post by PriceChild on 2006-11-26
System>Preferences>Themes will let you change your theme. Find more at gnome-look.org

I have no experience with sound cards not working sorry.

Excellent wine tutorial here: [http://ubuntuforums.org/showthread.php?t=149585&highlight=wine+howto](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine+howto)

Pricey

---

### Post by Kittie Rose on 2006-11-26
Thanks. Unfortunately, I do not know what to download these themes to, and my lack of permissions(Ubuntu has some weird security thing with root access you have to sort out I think?) might interfere.

---

### Post by qpieus on 2006-11-26
Ubuntu disables the root account by default. The password you need to install debs is your own password that was created during installation. This is an interesting read on this subject: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
Look here [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") for info on mp3 support.
Unfortunately I know nothing of soundblaster setup, so I can't help you with that.

---

### Post by Kittie Rose on 2006-11-26
WINE doesn't work for me.

drael@Teletraan8:~/wine/wine-0.9.26$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by PriceChild on 2006-11-26
Why are you trying to compile wine? The link I gave doesn't tell you to?

You don't need to use the root account to install themes. Just download the tar to your home, then open up the themes menu entry and "install new theme". Alternatively you could extract icons to ~./icons and themes to ~/.themes :)

---

### Post by Kittie Rose on 2006-11-26
Okay, unfortunately I can't get Wine to run anything now... it's supposed to work with PSP7 but when I click on it nothing happens. It doesn't rely on the registry. I don't understand why it doesn't work.

I'm trying to Terminal in there but I don't know how to switch to other mounted drives.

---

### Post by PriceChild on 2006-11-26
> **Kittie Rose said:**
> Okay, unfortunately I can't get Wine to run anything now... it's supposed to work with PSP7 but when I click on it nothing happens. It doesn't rely on the registry. I don't understand why it doesn't work.

I'm trying to Terminal in there but I don't know how to switch to other mounted drives.Your best bet is to install in wine, not try and run from an existing install.

---

### Post by Kittie Rose on 2006-11-26
I think I've found the problem, the MFC libraries are not installed.

When I was installing them, it was stuck at 0% constantly. However after I exited out of it it said they were installed so I thought it might just be a progress indicator error. Apparently not.

So what do I do?

:/

> err:module:import_dll Loading library MFC42.DLL (which is needed by L"E:\\Program Files\\Jasc Software Inc\\Paint Shop Pro 7\\JCMYK.dll") failed (error c0000020).
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


Trying to download again, still stuck on 0%...

---

### Post by Kittie Rose on 2006-11-26
For some reason Myspace videos aren't playing... I get audio but no video. What should I do?

---

### Post by PriceChild on 2006-11-26
> **Kittie Rose said:**
> For some reason Myspace videos aren't playing... I get audio but no video. What should I do?Install flash 9

---

### Post by reclusivemonkey on 2006-11-26
> **Kittie Rose said:**
> For some reason Myspace videos aren't playing... I get audio but no video. What should I do?

Does that mean you got your Sound Blaster Live working?

---

### Post by Kittie Rose on 2006-11-26
Yes, that works. I just switched outputs on my soundcard... have to do it every time I reboot into windows, a little frustrating.

What's really bugging me is the MFC libraries being stuck at 0%.

---

### Post by reclusivemonkey on 2006-11-26
> **Kittie Rose said:**
> Yes, that works. I just switched outputs on my soundcard... have to do it every time I reboot into windows, a little frustrating.

You should be able to get the output going that same as in windows... which outputs are you using for Linux/Windows?

---

### Post by Kittie Rose on 2006-11-26
It's some weird drivers I'm using... kAudio.

But for now I REALLY need to get WINE working - why isn't it downloading the MFC libraries? Is there another way to get them?

---

### Post by reclusivemonkey on 2006-11-26
> **Kittie Rose said:**
> It's some weird drivers I'm using... kAudio.

But for now I REALLY need to get WINE working - why isn't it downloading the MFC libraries? Is there another way to get them?

Installing Wine is as simple as

```

sudo apt-get install wine

```

I would remove your wine config files, do a "sudo make uninstall" if you've installed your own compiled version and try the ubuntu version first.

Are you that desperate for PSP7? There are several application native to Linux you can try.

---

### Post by Kittie Rose on 2006-11-26
That's not my problem with WINE though.

When I try to use WINETools, one of the basic components of Windows listed is the MFC Libraries. They do not download for me. I do not know why, and I am wondering if there is another way of getting them.

---

### Post by graham_100 on 2006-12-05
I have a major problem with Wine!! ](*,)  :confused: 
It worked fine when i first installed 6.06lts (dapper) then I upgraded to 6.10 (Edgy), removed the old wine program and then installed the corresponding 6.10 version!
Upon doing so I get the same line every time I try to run it:
libGL warning: 3D driver claims to not support visual 0x4a

Please can someone give me a fix or a command promt to fix this?? It's being driving me mad for a week now!!

I converted over from windows completely and as a new user I am still learning things (only been using this for about a month now)!!

please please please help! lol

---

### Post by strabes on 2006-12-05
to get sound you're going to need an oss wrapper... ```
sudo apt-get install alsa-oss[code]

then when you run applications that use sound, put "aoss" in front of them like [code]aoss firefox
```

for mp3 and other multimedia codecs, go [here](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

---

