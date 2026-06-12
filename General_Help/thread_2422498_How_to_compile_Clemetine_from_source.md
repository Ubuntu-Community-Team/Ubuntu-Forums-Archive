---
title: "How to compile Clemetine from source"
date: 2019-07-08
forum: General Help
---

### Post by Ralph L on 2019-07-08
I have been trying to use Clementine player to rip CDs, since it is the only GUI app, that I know of, that will rip to acc mp4 format.  However, Clementine does not include metadata in the ripped files, because of this bug:  [https://github.com/clementine-player/Clementine/issues/6045](https://github.com/clementine-player/Clementine/issues/6045) .  Supposedly the bug was fixed, but never distributed, so I thought I would try to compile it from source thinking that maybe the fix was in the latest source.  I tried to follow the instructions for compiling from source in [https://github.com/clementine-player/Clementine](https://github.com/clementine-player/Clementine) .  These were the instructions:```
git clone https://github.com/clementine-player/Clementine.git && cd Clementine 
cd bin
cmake ..
make -j8
sudo make install

``` I made it to the cmake .. command, where it failed with ```
Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: CMAKE_CXX_COMPILER-NOTFOUND 
Build flags: 
Id flags:  

The output was:
No such file or directory
```

I tried all sorts of suggestions that I found with google, but none of them worked.

Anybody got any suggestions????

---

### Post by SeijiSensei on 2019-07-08
Did you install the build-essential package first?

If so, maybe you're missing g++?

---

### Post by Ralph L on 2019-07-08
SeijiSensei:  Thanks for responding.  I really appreciate it.
Yes, when I look up "build-essential" and "g++", they are both there.  In fact I installed them during the time I was trying to get cmake to work.  Would it make a difference that those were installed after the "git" was done???

---

### Post by Yellow Pasque on 2019-07-09
I'd suggest a different tact: Use abcde
It's not a full-fledged GUI, but using it is pretty easy since the hard work is done for you and the .conf file to do what you want is a matter of copy and paste: [http://www.andrews-corner.org/linux/abcde/abcde_aac.html#ffmpeg](http://www.andrews-corner.org/linux/abcde/abcde_aac.html#ffmpeg)

---

### Post by SeijiSensei on 2019-07-09
> **Ralph L said:**
> Would it make a difference that those were installed after the "git" was done???
No. It only matters that they are installed before you compile.

Next, you can try using "sudo apt-get build-dep clementine" which will download all the various source files that clementine requires. (These are the packages with -dev in their names.)  You'll first need to edit /etc/apt/sources.list and remove the hash marks ("#") at the beginning of the lines that begin with "deb-src".  When I tested this now on my 19.04 machine, there were nearly two hundred packages that were required.

---

### Post by Ralph L on 2019-07-09
Thanks again for the responses.
I got Clementine compiled and so far it seems to run fine including metadata, when ripping from a CD, solving my original problem.  Transcoding from flac to acc mp4 also seems to work, although it doesn't transcode the album cover.  However, I was able to, using Cover Manager>Fetch Missing Covers then right-clicking the album cover, clicking Save cover to disk, and saving the cover (as .jpg) to the folder containing the music files.  This seemed to associate the cover with the album.  However, it was only necessary with transcoded files.  Maybe if I can find more documentation on Clementine I can get things to work better.  So far the only documentation I have found is in [https://github.com/clementine-player/Clementine/wiki](https://github.com/clementine-player/Clementine/wiki).

Anyway I finally reread the instructions in [https://github.com/clementine-player/Clementine](https://github.com/clementine-player/Clementine) and found reference to [https://github.com/clementine-player/Clementine/wiki/Compiling-from-Source](https://github.com/clementine-player/Clementine/wiki/Compiling-from-Source) .  This showed the dependencies needed for compilation.  So the instructions for compilation are:```
sudo apt-get install liblastfm-dev libtag1-dev gettext libboost-dev \
    libboost-serialization-dev libqt4-dev qt4-dev-tools libqt4-opengl-dev \
    cmake g++ libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev \
    libglew1.5-dev libqjson-dev libgpod-dev libplist-dev \
    libusbmuxd-dev libmtp-dev libcdio-dev \
    protobuf-compiler libprotobuf-dev libcrypto++-dev \
    libfftw3-dev libsparsehash-dev libsqlite3-dev libpulse-dev \
    libqtwebkit-dev libchromaprint-dev libqca2-devcd bin
git clone https://github.com/clementine-player/Clementine.git && cd Clementine 
cd bin
cmake ../
make
sudo make install
```  This installs Clementine Version 1.3.1-610-ga0e478534

Also see [https://ubuntuforums.org/showthread.php?t=2422068](https://ubuntuforums.org/showthread.php?t=2422068) for my experience using Clementine vs K3b for ripping.
SeijiSensei:  Thank you for showing me how to find dependencies "sudo apt-get build-dep clementine".  I did not know about that and it will be useful if I try to compile anything else from source.

---

### Post by SeijiSensei on 2019-07-10
As someone who would occasionally compile things on RedHat-flavored platforms, "build-dep" is a dream come true. No more time spent tracking down each dependency individually.

---

