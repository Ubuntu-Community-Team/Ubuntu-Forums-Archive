---
title: "Slow program start."
date: 2007-05-14
forum: General Help
---

### Post by monokom on 2007-05-14
I install feisty and vereything was OK. Until I install msttcorefonts from the repositorys and run fc-cache -fv.
Then the programs is just start opening very slowly. 10 secs are needed to open the Terminal whit AMD Athlon 64 3000+ and 1gb ram. Please, someone help :( 

> root@ubuntu:~# fc-cache -fv
/usr/share/fonts: caching, 0 fonts, 3 dirs
/usr/share/fonts: failed to write cache
/usr/share/fonts/X11: caching, 0 fonts, 6 dirs
/usr/share/fonts/X11: failed to write cache
/usr/share/fonts/X11/100dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/100dpi: failed to write cache
/usr/share/fonts/X11/75dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: failed to write cache
/usr/share/fonts/X11/Type1: caching, 8 fonts, 0 dirs
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/fonts/X11/encodings: caching, 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings: failed to write cache
/usr/share/fonts/X11/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/encodings/large: failed to write cache
/usr/share/fonts/X11/misc: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: failed to write cache
/usr/share/fonts/X11/util: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/util: failed to write cache
/usr/share/fonts/truetype: caching, 0 fonts, 22 dirs
/usr/share/fonts/truetype/arphic: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/arphic: failed to write cache
/usr/share/fonts/truetype/baekmuk: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/baekmuk: failed to write cache
/usr/share/fonts/truetype/freefont: caching, 12 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/msttcorefonts: caching, 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: failed to write cache
/usr/share/fonts/truetype/thai: caching, 27 fonts, 0 dirs
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: caching, 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-dejavu: caching, 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: failed to write cache
/usr/share/fonts/truetype/ttf-devanagari-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-devanagari-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-gujarati-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gujarati-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-kannada-fonts: caching, 8 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kannada-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-lao: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: caching, 16 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/ttf-oriya-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-oriya-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-tamil-fonts: caching, 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-telugu-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: failed to write cache
/usr/share/fonts/type1: caching, 0 fonts, 1 dirs
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: caching, 35 fonts, 0 dirs
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/share/X11/fonts: caching, 0 fonts, 6 dirs
/usr/share/X11/fonts: failed to write cache
/usr/share/X11/fonts/100dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/100dpi: failed to write cache
/usr/share/X11/fonts/75dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/75dpi: failed to write cache
/usr/share/X11/fonts/Type1: caching, 8 fonts, 0 dirs
/usr/share/X11/fonts/Type1: failed to write cache
/usr/share/X11/fonts/encodings: caching, 0 fonts, 1 dirs
/usr/share/X11/fonts/encodings: failed to write cache
/usr/share/X11/fonts/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/encodings/large: failed to write cache
/usr/share/X11/fonts/misc: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/misc: failed to write cache
/usr/share/X11/fonts/util: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/util: failed to write cache
/usr/local/share/fonts: caching, 0 fonts, 0 dirs
/usr/local/share/fonts: failed to write cache
/root/.fonts: skipping, no such directory
/var/lib/defoma/fontconfig.d: caching, 0 fonts, 26 dirs
/var/lib/defoma/fontconfig.d/A: caching, 14 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/B: caching, 11 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/B: failed to write cache
/var/lib/defoma/fontconfig.d/C: caching, 12 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/D: caching, 24 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/D: failed to write cache
/var/lib/defoma/fontconfig.d/E: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/E: failed to write cache
/var/lib/defoma/fontconfig.d/F: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/F: failed to write cache
/var/lib/defoma/fontconfig.d/G: caching, 16 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/H: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/H: failed to write cache
/var/lib/defoma/fontconfig.d/I: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/J: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/J: failed to write cache
/var/lib/defoma/fontconfig.d/K: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/K: failed to write cache
/var/lib/defoma/fontconfig.d/L: caching, 10 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/M: caching, 19 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/M: failed to write cache
/var/lib/defoma/fontconfig.d/N: caching, 25 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/O: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/O: failed to write cache
/var/lib/defoma/fontconfig.d/P: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/P: failed to write cache
/var/lib/defoma/fontconfig.d/R: caching, 3 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/R: failed to write cache
/var/lib/defoma/fontconfig.d/S: caching, 7 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/S: failed to write cache
/var/lib/defoma/fontconfig.d/T: caching, 30 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/U: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/V: caching, 5 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/W: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/a: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/a: failed to write cache
/var/lib/defoma/fontconfig.d/j: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/j: failed to write cache
/var/lib/defoma/fontconfig.d/m: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: failed to write cache
/var/cache/fontconfig: cleaning cache directory
/root/.fontconfig: cleaning cache directory
fc-cache: failed


---

### Post by j0sh0 on 2007-05-25
Hi,
I have the same problem and was going to post a similar question, although I don't think I can trace it back to msttcorefonts. I thought the problem may have been screenlets, but slow program starts persist even after killing the screenlets and daemon. Say, for example, I click on the firefox quicklaunch button, "Starting firefox" appears in the window list for about five to seven seconds, with the "busy" mouse icon flashing, and then the program appears. Programs seem to run fine once they're loaded, but it's getting them loaded which takes forever. I've got fiesty 64 on Intel E6400 1Gig ram. It used to run like lightning, but I can't put my finger on what caused the slowdown. Any help would be greatly appreciated!

---

### Post by j0sh0 on 2007-05-25
t to let you know, I solved the problem byt editing /etc/hostname and appending 127.0.0.1 localhost preceeding the host name that was already in the file. worked for me. refer to this [http://ubuntuforums.org/showthread.php?t=329463&highlight=slow+program+start](http://ubuntuforums.org/showthread.php?t=329463&highlight=slow+program+start) thread for details.

cheers

---

