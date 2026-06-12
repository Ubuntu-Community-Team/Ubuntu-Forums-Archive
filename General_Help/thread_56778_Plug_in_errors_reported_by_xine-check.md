---
title: "Plug in errors reported by xine-check"
date: 2005-08-14
forum: General Help
---

### Post by ssck on 2005-08-14
Hi ALL,

Some errors reported by xine-check on plug ins.How do I install them ?

[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

Thanks. :-|

---

### Post by nad on 2005-08-14
I haven't completely figured out how totem/gstreamer handles plugins, but it seems to be irrespective of how xine (maybe just xine-check) expects.

Try playing a movie or song. It should work anyway.

---

### Post by ssck on 2005-08-14
[QUOTE=nad]I haven't completely figured out how totem/gstreamer handles plugins, but it seems to be irrespective of how xine (maybe just xine-check) expects.

Try playing a movie or song. It should work anyway.[/QUOTE]

i have a problem when playing dvds ... totem xine will say that there are no plug ins available to handle

---

### Post by nad on 2005-08-14
Ahhh... To play dvds you need to install libdvdcss (thank you Jon). This is the library that decodes the encrypted commercial dvds.

Be aware that using this library may be illegal in your country. Just one more problem plaguing our _modern_ world.

I will not give you a link, but, just search the web. You will find a .deb package in many places.

Once downloaded, run: dpkg -i libdvdcss_full_name_here  as root.

You will be up and watching movies in no time.

---

### Post by ssck on 2005-08-14
[QUOTE=nad]Ahhh... To play dvds you need to install libdvdcss (thank you Jon). This is the library that decodes the encrypted commercial dvds.

Be aware that using this library may be illegal in your country. Just one more problem plaguing our _modern_ world.

I will not give you a link, but, just search the web. You will find a .deb package in many places.

Once downloaded, run: dpkg -i libdvdcss_full_name_here  as root.

You will be up and watching movies in no time.[/QUOTE]

what is the difference between libdvdcss and libdvdcss2 ? 

sorry for the noob question ....

---

### Post by nad on 2005-08-15
The number 2? Beats me.

Seriously, with thousands of library files on a typical system I am mostly concerned with stability. I don't care what version of a file is installed, as long as it satifies dependencies. That is the beauty of a quality package manager.

If you want to learn more about libdvdcss, the information is out there for _anyone_ to look over.

---

### Post by ssck on 2005-08-15
[QUOTE=nad]The number 2? Beats me.

Seriously, with thousands of library files on a typical system I am mostly concerned with stability. I don't care what version of a file is installed, as long as it satifies dependencies. That is the beauty of a quality package manager.

If you want to learn more about libdvdcss, the information is out there for _anyone_ to look over.[/QUOTE]

fact is i can view dvds using gxine, vlc, xine, ogle.the only problem is it freezes after about 10 mins or so.till now i still can't solve it.no problems in windows xp though. ](*,)   :|

---

### Post by nad on 2005-08-15
Generally, the latest stable version is the correct one to use.

So you've been at this for 12 hours and got the software to freeze. Buffer overflow, memory leak? When it freezes, switch to a console and check your memory usage. You can also kill your program from here and continue troubleshooting.

I've seen this happen before. It usually can be fixed with some application tweaking (buffers and timing) provided your hardware is up to the task.

---

### Post by ssck on 2005-08-15
[QUOTE=nad]Generally, the latest stable version is the correct one to use.

So you've been at this for 12 hours and got the software to freeze. Buffer overflow, memory leak? When it freezes, switch to a console and check your memory usage. You can also kill your program from here and continue troubleshooting.

I've seen this happen before. It usually can be fixed with some application tweaking (buffers and timing) provided your hardware is up to the task.[/QUOTE]


how do i check for buffer overflow and memory leak ? how do i check for memory usage ? sorry for the noob question ..... appreciate your help.

---

### Post by nad on 2005-08-15
Use the top utility in a terminal window to see what is going on.

---

### Post by ssck on 2005-08-16
[QUOTE=nad]Use the top utility in a terminal window to see what is going on.[/QUOTE]

this is the screenshot of the top  utility when the display of the DVD has frozen.i am not sure what it means.how do i i check if there is a memory leak ?

thanks very much for your help.

---

