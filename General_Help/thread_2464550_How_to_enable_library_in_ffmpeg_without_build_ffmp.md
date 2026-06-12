---
title: "How to enable library in ffmpeg without build ffmpeg from source?"
date: 2021-07-05
forum: General Help
---

### Post by hiepvs on 2021-07-05
Hi, I installed ffmpeg from ubuntu repository and built libaom. So, how to enable libaom in ffmpeg without reinstall ffmpeg from source ([https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#FFmpeg](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#FFmpeg))?
the ffmpeg cmpilation guide screenshot
[ATTACH=CONFIG]288768[/ATTACH]
Thanks.

---

### Post by HermanAB on 2021-07-05
I think you are out of luck and need to compile it.  That is time consuming but not impossible: [https://www.aeronetworks.ca/2015/11/compile-latest-ffplay-from-source.html?m=1](https://www.aeronetworks.ca/2015/11/compile-latest-ffplay-from-source.html?m=1)

---

### Post by SeijiSensei on 2021-07-05
I agree with Herman. Just having the library isn't enough. You have to compile ffmpeg to use it.

You should give compilation a try. Run the command
```
sudo apt-get build-dep ffmpeg
```
to install the libraries and helper code that was used in the official build. Then try running
```
./configure --with-aom
```
in the directory where you expanded the source code tarball. I don't guarantee this will work, but you should give it a try.

---

