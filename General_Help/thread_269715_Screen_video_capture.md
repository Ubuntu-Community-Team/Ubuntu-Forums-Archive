---
title: "Screen video capture"
date: 2006-10-02
forum: General Help
---

### Post by FuzZy2006 on 2006-10-02
Can you pls tell me a program that I may use for a screen video capture? I wanna use it to show my classmates what ubuntu+xgl+beryl can do because many of them think that linux sucks. :( pls help

---

### Post by iovar on 2006-10-02
You can use my program:
[http://recordmydesktop.sourceforge.net/](http://recordmydesktop.sourceforge.net/)

You have though to compile it.But it shouldn't be very hard and I'm
around if you have problems.

There's also istambul on the repos.

---

### Post by FuzZy2006 on 2006-10-02
solved

---

### Post by iovar on 2006-10-02
To compile you need the respective development packages. That is the ones
that end with -dev (libXdamage-dev for example). If you haven't compiled 
anything before you might need a lot of them. And you certainly need 
the build-essential package.

So if you want to compile you will need these:
libxdamage-dev
libxext-dev
libasound-dev
And for the frontend(gui) you need python-gtk2-dev and any 
automake >=1.5.

There are others too but the above should pull them in.

Edit: I'm a bit slow today...

---

### Post by FuzZy2006 on 2006-10-02
thx a lot for this suggestion -> it works gr8

---

### Post by FuzZy2006 on 2006-10-02
I'd like to request some advice on how to use it. Pls tell me which are the most recommended settings for best performance and how to use them. 
I tryed to use commands like : ```
recordmydesktop -Width 640 -Height 480 -o file.ogg
``` and it says Error parsing arguments. Is it true that lower vid quality brings more cpu usage?

---

### Post by iovar on 2006-10-02
> **FuzZy2006 said:**
> I'd like to request some advice on how to use it. Pls tell me which are the most recommended settings for best performance and how to use them. 
I tryed to use commands like : ```
recordmydesktop -Width 640 -Height 480 -o file.ogg
``` and it says Error parsing arguments. Is it true that lower vid quality brings more cpu usage?

Didn't you get the interface(gtk-recordMyDesktop)? It's on the project page and it will make your life easier. 
As for the arguments, it's all lowercase. That is -width and -height. 

Quality should always be left to max when recording. It's not something I
can change, it's just how the theora libray behaves. You can use
ffmpeg2theora to drop the quality later(it's on the repos and despite the
name it accepts theora as input, too).

To improve performance... well, you can add the --quick-subsampling option and play a little bit with the 
-shared-threshold option. The first one 
might not have a great impact. The second is a percentage and is highly
related to hardware. Default is 75, so you can try lowering it.
You can also add the --drop-frames but this is practically the same to lowering the framerate,
which you can do with the -fps option

But, again, I highly advise getting the [frontend]("http://prdownloads.sourceforge.net/recordmydesktop/gtk-recordMyDesktop-0.2.1.tar.gz?download")
It will make thing a lot easier and you can easily select the area to
capture. 
Also if you haven't seen it, there is a manpage that gets installed with the program. 
There are some explanations there, too, and you can see all the options.

---

### Post by FuzZy2006 on 2006-10-02
I've downloaded the gtk. The pb is that the framerate sucks. I want to make a fullscreen movie, i am not interested so much in the output quality or resolution. You can see my hardware specifications. Can you pls  tell me which are the best settings? I want to demonstrate the beryl's abilities through this movie. Pls help

---

### Post by iovar on 2006-10-02
What is your target framerate? I've seen your specs and I
think that the defaults(15 fps) should work on a resolution of 800x600 pretty well. 
[The videos on the project site]("http://recordmydesktop.sourceforge.net/index.php?pgenum=2") were made on my p3.2. 
Also using the interface doesn't have any performance costs.

Other than those options  I metioned on my
previous post, there isn't much to be done. Perhaps
you can disable sound with --nosound.
But this won't make a big difference. Like I said, what
can give a slight boost is trying some values with the -shared-threshold option. 
Try also the --no-cond-shared option(almost same as -shared-threshold 100) 
and --with-shared ( -shared-threshold 0) . In certain situations these can help.

Anyway, I'm afraid that if you want something higher than 15fps you should look for something else or consider using an external cam.

Also the program doesn't do scaling of the result on it's
own. You have to temporarily lower your real resolution. The -width and -height options are for cropping.

---

### Post by dada1958 on 2006-10-17
I installed recordMyDesktop and I love it, it works better here than XVidCap. It's very useful for my computer courses on my work.
Thanks!

---

### Post by gejr on 2006-11-01
geo@geo-laptop:~/Desktop/gtk-recordMyDesktop-0.2.1-r4$ gtk-recordMyDesktop --no-sound
Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/recordMyDesktop/rmdTrayIcon.py", line 146, in record_ext
    self.__execRMD__()
  File "/usr/local/lib/python2.4/site-packages/recordMyDesktop/rmdTrayIcon.py", line 212, in __execRMD__
    res=os.execvp("recordmydesktop",execargs)
  File "/usr/lib/python2.4/os.py", line 341, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.4/os.py", line 379, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 2] No such file or directory
Xlib: unexpected async reply (sequence 0x15c4)!
Xlib: unexpected async reply (sequence 0x15c5)!
Xlib: unexpected async reply (sequence 0x15c6)!
Xlib: unexpected async reply (sequence 0x15c7)!
The program 'gtk-recordMyDesktop' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 5577 error_code 5 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
geo@geo-laptop:~/Desktop/gtk-recordMyDesktop-0.2.1-r4$ man gtk-recordmydesktop

The program crashes totally when I click "Save as"-button. What can be the cause of this?

---

### Post by iovar on 2006-11-01
> **gejr said:**
> geo@geo-laptop:~/Desktop/gtk-recordMyDesktop-0.2.1-r4$ gtk-recordMyDesktop --no-sound
Traceback (most recent call last):
  

Noooo....:-D 
gtk-recordMyDesktop is just a frontend. It doesn't accept any options
when running and it doesn't have a man page. You just click on it on
your menus(or launch it without parameters from cli) and use it
graphically.
If you want commandline it's recordmydesktop(which has a manpage and
a --nosound option, which btw I plan to change to --no-sound as it's more
reasonable)

EDIT: you also need the recordMyDesktop-0.2.6.tar.gz package, as this is that does all the recording.

---

### Post by gejr on 2006-11-01
Aha...thanks for being so helpful, and sorry for me being so retarded. I'm new:)

I'll try it right away.

---

### Post by iovar on 2006-11-01
No problem  :) 
If you have any other problems I'll be around.;)

---

### Post by gejr on 2006-11-01
good to hear..cause i can't make it work. I've managed to run it with recordmydesktop and it says "capturing" with no errors.. I'm not sure how to stop it so I use ctrl+c and it says "done....written 36362 bytes" etc. then it says "shutting down" but it doesn't seem to make any progress there. A out.ogg shows up in my /home folder which I'm not really able to do anything with. I can't view it in Mplayer or xmms (it wanted to open in xmms, but it's not for videos is it?)

So i'm still kinda stuck you might say..:)

I tried running gtk-recordMyDesktop now just to see what the output were as I was not able to click the stop icon in my notification area. However, the output seems to say the "done...written"-part again, but again it's stuck on the "Shutting down..." thing, and the stop-icon doesn't change. I had to use kill -9 to stop the process.

Some minor bugs here, or am I doing something wrong? I don't get to the part where I can choose what to call the file.

Edit:

It stopped now, saying "Goodbye!" but the .ogg is still not playable in Mplayer. It says "Error opening/initializing the selected video_out(-vo) device."

Edit 2: 

Just tried opening the video in VLC. Seemed promising as the video-frame opened up to full size (1024x768), but boom!..VLC crashed :)

Edit 3:

I went to your site to try the example video there and I couldn't see that either. Maybe something's wrong with my settings for viewing video :$

---

### Post by iovar on 2006-11-01
Do you run beryl/compiz on AIGLX-edgy or something like that?

In that case there are currently "technical difficulties" that I'm trying to resolve. 
There's a faq on the project site explaining that 3d-compositing wm's and 
recordMyDesktop do not get allong well currently.

If that's your case you can still run it with
the --full-shots --with-shared switches, or enable "full shots" on the
advanced tab of the frontend, but it will give very low framerates.

Sorry, if that's not particularly helpfull, but having the whole screen
drawn much like a game is something I couldn't see coming when I started
this program.

EDIT: it's -o FILE,  for changing name.

EDIT2: can we stop the edits? I'm confused :) . Not being able to see the video might be a different problem.
the program getting stuck though, is to the best of my knowledge a compiz/beryl thing.

---

### Post by gejr on 2006-11-01
Yes, I'm running Beryl/Aiglx which was kinda why I wanted to record my desktop in the first place. I want to show my mother how fancy a desktop can be :)

I disabled Beryl (back to the metacity wm), that resolved the Shutting Down-problem as you said, but the .ogg still can't be run in either VLC or MPlayer. VLC just quits as soon as it starts playing it with no errors given. And Mplayer keeps giving that error I described above. the --with-shared and --full-shots didn't make any difference either. This was harder than I had expected :)

How have the guys over at youtube managed to record their videos of their desktops? You're obviously skilled at this business...how come it's so difficult?

Thanks for all your help:)

---

### Post by iovar on 2006-11-01
As far as playing the videos, can you post a link or something to a short one?
15-20 seconds would be enough.

If you can't play the one on project page, it's probably your
configuration (I've never heard any complaints on it and it's getting
quite some traffic since there's a link to it from the elive page).

It's not imposible or hard to record Beryl, it's just that you need more proccessing power. I don't know about which videos you're talking about though, I rarely visit youtube.

Anyway, if you can't see what you are recording there's little point 
on discussing how to do it better.
Since mplayer says about -vo, try this:

mplayer -vo x11 out.ogg

Also, apt-get install mencoder and run this:
~$ mencoder out.ogg -o out.avi -ovc lavc -oac faac

which will make an avi.

---

### Post by gejr on 2006-11-02
Hi again,

the mplayer -vo x11 worked. Funky..what does that do? and why isn't that default?:)

The video is played, but it looks pretty weird. In the attached video i'm moving the terminal window around, but as you can see it's rendered quite..buggy. I also encoded it to .avi as you said, but the out.avi looked just the same. Obviously.

[http://www.geirola.net/out.avi]("http://www.geirola.net/out.avi")

[http://www.geirola.net/out.ogg]("http://www.geirola.net/out.ogg")

---

### Post by iovar on 2006-11-02
x11 isn't the default because it's slower and more resource hungry.
The default is Xv the video extension, which directly works with the hardware. 

Two things: 

1)What you got is just the cursor rendering, which happens when 
running beryl. It doesn't matter if the effects are enabled. In order
to get proper results you must disable it from startup and relogin.
Otherwise you can run with the options --full-shots --with-shared,
which will produce a recording whether or not you run on beryl.

[B]In any case, you should run this:
xdpyinfo|grep Video

If within the results you see XVideo, you should file a bug in beryl ,
about Xv not functioning.[/B]


2)If you definately need to record beryl, and have no other way, I can
drop you a tarball of the latest CVS version(or you can go to the site
and checkout on your own the rMD-exp module). With that you will be able
to make a recording more or less of this quality:
[http://recordmydesktop.sourceforge.net/videos/edgy_kde_compiz-rMD_cvs_3.0.ogg](http://recordmydesktop.sourceforge.net/videos/edgy_kde_compiz-rMD_cvs_3.0.ogg)
(yet again, though you have to use the --full-shots --with-shared options)

As you see there is flickering yet, but otherwise the effects get shown.
Generally, right now recordMyDesktop is best suited for tutorials and
such, since  I've only started recently getting it to work on 
3d-compositing WM's. 
I've only started it 5 months ago and haven't been really productive in the summer:rolleyes: 
So it's really alpha software.

Perhaps you should try xvidcap and/or Istanbul.

---

### Post by gejr on 2006-11-02
I've tried both xvidcap and istanbul. With xvidcap i didn't manage to record full screen and with istanbul i didn't manage to record anything at all. I'm not at home right now, and I'm kinda in a hurry, but I'll try the things you suggested soon. Thanks for your assistance so far!:)

---

### Post by FuzZy2006 on 2006-11-02
well - especially for beryl - there is something on the beryl svn - i guess it is beryl-svn. more info you can find on the beryl forums. [http://forum.beryl-project.org/topic-5646-vidcap](http://forum.beryl-project.org/topic-5646-vidcap)
good luck.

---

### Post by gejr on 2006-11-03
i downloaded and compiled the svn beryl thing, but it didn't show up in my Beryl Settings Manager like it's supposed to. Anyone know how to make this work?

---

### Post by Adler on 2007-01-11
gejr,

I've got Beryl running great. And, want to capture my Desktop as a Vid.

Where were you expecting to find this Beryl add-on? Or, find it with a functional Beryl set-up?

Adler

---

### Post by Adler on 2007-01-19
Hi All,

I've got RecordMyDesktop going great, can capture my Beryl Desktop on an .ogg / orbis file, and convert it to an .avi and have posted three screen captures to YouTube.

The issue here is adding sound to the Vids. Any suggestions?

Adler

---

### Post by avatar21 on 2007-02-03
Hi IOVar,

I'm trying to make some video tutorial on Linux too, so happened to see your post here.

I tried to compile RecordMyDesktop from my bash prompt, got following errors:

When I typed in bash> ./configure <enter>

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking vorbis/vorbisfile.h usability... no
checking vorbis/vorbisfile.h presence... no
checking for vorbis/vorbisfile.h... no
checking for isnan in -lm... yes
checking for deflate in -lz... no
checking for IceOpenConnection in -lICE... yes
checking for SmcOpenConnection in -lSM... yes
checking for XOpenDisplay in -lX11... yes
checking for XShmQueryVersion in -lXext... yes
checking for XFixesQueryExtension in -lXfixes... yes
checking for XDamageQueryExtension in -lXdamage... yes
checking for vorbis_info_clear in -lvorbis... no
configure: error: Can't find libvorbis
```

Do you know what do I missing out?


Any help will be mostly appreciated. :) 


By Avatar Ng

---

### Post by avatar21 on 2007-08-27
tried "wink", but seems wink isn't working as well.

may be im using a chinese session :P
or it could be berlyn sometimes, encountered a few bugs from it, e.g.: playing video, JMF,  ...

---

### Post by Adler on 2007-08-27
avatar21,

Have you been to Synaptic and downloaded gtk-recodmydesktop, and recordmydesktop? You should also get mencoder.

That should get you going. In the meantime, I've got about 15 Linux YouTube videos posted.

Adler

---

### Post by Adler on 2007-08-27
avatar21,

Just to keep this going I hope that you have followed my suggestions. There's not enough Linux Beryl / compiz-Fusion Desktop videos out there.

With recordmydesktop you will produce an .ogg/vorbis file. To convert it to the YouTube .avi format run this is Terminal --

mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 your_movie.mov

your_movie.mov is probably /Home/something.

I just did the whole thing to send to YouTube a cool compiz-Fusion 3D within 3D Video with audio.


Adler

---

### Post by maxxum on 2007-08-30
In my case, it never saves the output. It remains stuck at 0% when saving the output. Any suggestions?

---

### Post by Adler on 2007-08-30
maxxum,

Do you have gtk-recordMyDesktop installed? 

Can you place it somewhere in your Task Bar? 

When you click it the Icon changes. That means that you are now recording. Click it again to stop recording. A Window will open, that indicates your file is being saved, probably to your /Home folder.

Adler

---

