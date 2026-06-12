---
title: "ffmpeg Problem"
date: 2014-05-24
forum: General Help
---

### Post by Quarkrad on 2014-05-24
I'm running 14.04 and wanted to install ffmpeg so I followed this guide - [http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).  Everything appeared to go ok until I got to the Conclusion section and tried to launch ffmpeg.  I entered the suggested terminal command and got the following:

[B]dad@dadubuntu:~$ cd ~/bin && ./ffmpeg -i ~/input.mp4 ~/videos/output.mkv
ffmpeg version 2.2.git Copyright (c) 2000-2014 the FFmpeg developers
  built on May 24 2014 12:36:38 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --prefix=/home/dad/ffmpeg_build --extra-cflags=-I/home/dad/ffmpeg_build/include --extra-ldflags=-L/home/dad/ffmpeg_build/lib --bindir=/home/dad/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 86.100 / 52. 86.100
  libavcodec     55. 63.100 / 55. 63.100
  libavformat    55. 40.100 / 55. 40.100
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  5.100 /  4.  5.100
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
/home/dad/input.mp4: No such file or directory
dad@dadubuntu:~/bin$[/B] 


I have tried just entering ffmpeg but I get:

[B]dad@dadubuntu:~$ ffmpeg
ffmpeg: command not found[/B]

I am looking to convert a dvd to mp4 and a lot of advice from ubuntu users is to use ffmpeg - I've tried mencoder and arista but 14.04 does not appear to like them.  Having gone through [http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) I would like to try ffmpeg but I'm at yet another block.  Thanks.

---

### Post by coldcritter64 on 2014-05-24
Try the command
```
which ffmpeg
```to see where the ffmpeg binary is located. 
Check that the location given for ffmpeg is in your user path
```
echo $PATH
``` this should give an idea to what is happening.

Edit: just noted in the link instructions the binary should be in your home "bin" folder.
> ```
--bindir="$HOME/bin"
``` config option used.

If the guide created the home bin folder because of that configuration option, bash would not have known where the binary was until after the next log out / in, to set the ~/home/bin folder in your path. This would explain the error of ffmpeg not being found.

---

### Post by steeldriver on 2014-05-24
It's locating and executing the ffmpeg program (in your ~/bin directory) just fine - what it's **not** finding is the specified ~/input.mp4 file - do you have such a file in your home directory?

---

### Post by coldcritter64 on 2014-05-24
> **steeldriver said:**
> It's locating and executing the ffmpeg program (in your ~/bin directory) just fine - what it's **not** finding is the specified ~/input.mp4 file - do you have such a file in your home directory?

Note when he runs the ffmpeg command and gets a not found error
> [B]dad@dadubuntu:~$ ffmpeg
ffmpeg: command not found[/B]
You are right about the file as well of course. But note the start of the command where the OP is cd'ing into ~/bin. So the ffmpeg binary will be found on the first command given, the OP is in the home directory when trying to run ffmpeg the second time, **edit:** following the guide will need a logout to set the bin folder in the path if it is being created by following the guide.
> ** cd ~/bin...**

---

### Post by steeldriver on 2014-05-24
The OP will get 'ffmpeg: command not found' when running it without an explicit path, unless/until $HOME/bin is added to their path

By default, $HOME/bin is added to PATH on login by the .profile file if it exists - i.e. if the OP only just created a ~/bin 9as part of the ffmpeg install process) it won't appear in their path until *next* login

---

### Post by Quarkrad on 2014-05-24
Thank you for your replies.  I'm still not sure whether ffmpeg is installed or not - I think it is.  I tried to install a gui called **sinthgunt** via the software centre and it says **Dependency is not satisfiable: ffmpeg**.  The output of the various commands is:

[B]dad@dadubuntu:~$ which ffmpeg
/home/dad/bin/ffmpeg
dad@dadubuntu:~$ echo $PATH
/home/dad/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
dad@dadubuntu:~$ --bindir="$HOME/bin"
bash: --bindir=/home/dad/bin: No such file or directory
dad@dadubuntu:~$ ffmpeg
ffmpeg version 2.2.git Copyright (c) 2000-2014 the FFmpeg developers
  built on May 24 2014 12:36:38 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --prefix=/home/dad/ffmpeg_build --extra-cflags=-I/home/dad/ffmpeg_build/include --extra-ldflags=-L/home/dad/ffmpeg_build/lib --bindir=/home/dad/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 86.100 / 52. 86.100
  libavcodec     55. 63.100 / 55. 63.100
  libavformat    55. 40.100 / 55. 40.100
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  5.100 /  4.  5.100
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'[/B]

note: I do not have that file in /home.  Can I just create it as an empty text file - I assumed it would have been created as part of all those install instructions.

---

### Post by coldcritter64 on 2014-05-24
edit: Yes you have ffmpeg installed in your home bin folder, it is now in your path as it works from the home folder from those results

>  note: I do not have that file in /home.  Can I just create it as an  empty text file - I assumed it would have been created as part of all  those install instructions.                 That "file" as such is an example format; you replace the path and filename to an actual video file of yours you want converted, same with output mkv file ... where you are saving it to, an example of usage for you to alter as needed.

---

### Post by FakeOutdoorsman on 2014-05-25
**Why ~/bin?**
The guide installs ffmpeg to ~/bin because:

[list]
[*]it avoids conflicts with repository packages
[*]it is non-destructive and avoids messing with the system (useful for users with no sudo privileges, like some server users)
[*]it avoids the complexity of the package management system
[*][removal is simple](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#RevertingChangesMadebyThisGuide)
[/list]

**Adding ~/bin to your PATH**
The [Persistent Environment Variables](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#PersistentEnvironmentVariables) section of the guide has the following instructions:
```
echo "MANPATH_MAP $HOME/bin $HOME/ffmpeg_build/share/man" >> ~/.manpath
. ~/.profile
```
The first line allows you to use "man ffmpeg" to get the associated man pages for your new ffmpeg. The second line sources ~/.profile which should immediately add ~/bin to your PATH, meaning that when you run "ffmpeg" in the terminal it will use ~/bin/ffmpeg (instead of the old, fake, crappy repository version for Ubuntu releases older than 14.04). However, now that I wrote that I now notice that in post #6 that ~/bin is now in your PATH, so it looks like you already did this.

Sinthgunt, even if it did recognize it, may not work with your new ffmpeg. FFmpeg development is very active, and these GUIs tend to age quickly. You can try using ffmpeg directly. If you have any questions you can ask them here.

---

### Post by gordintoronto on 2014-05-25
I'm puzzled why you didn't just install ffmpeg from the repositories, using software manager, Synaptic or apt-get install.

---

### Post by monkeybrain20122 on 2014-05-25
> **gordintoronto said:**
> I'm puzzled why you didn't just install ffmpeg from the repositories, using software manager, Synaptic or apt-get install.

Because 1) the version in the repository is not real ffmpeg. It is a fork called avconv. If you install from the repository and type ffmpeg in the terminal it will say something like 'ffmpeg is deprecated.. " 2) There is no more ffmpeg package in the repository in 14.04 (that being the case may be the concern about conflicting with system 'ffmpeg' no longer applies?)

---

### Post by FakeOutdoorsman on 2014-05-25
> **monkeybrain20122 said:**
> ...that being the case may be the concern about conflicting with system 'ffmpeg' no longer applies?
Unfortunately the fork decided to use the same names for the libraries too, and these are still provided by the libav-tools package dependencies.

---

