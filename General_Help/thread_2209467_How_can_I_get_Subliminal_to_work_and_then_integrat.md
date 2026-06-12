---
title: "How can I get Subliminal to work and then integrate it with a file system?"
date: 2014-03-05
forum: General Help
---

### Post by deaton25 on 2014-03-05
I have downloaded Subliminal which is a program that downloads movie subtitles.But there are several problems: (1) when I test it at the console with a 
movie that I know has an English subtitle, I get an unsatisfactory response:
alan@alan-Latitude-D530:~$ subliminal -l en la fin du jour.avi
usage: subliminal -l LANGUAGE [LANGUAGE ...] [-s] [-c CACHE_FILE]
                  [-p PROVIDER [PROVIDER ...]] [-m MIN_SCORE] [-a AGE] [-h]
                  [-f] [--addic7ed-username USERNAME]
                  [--addic7ed-password PASSWORD] [-q | -v]
                  [--log-file LOG_FILE] [--color] [--debug] [--version]
                  [--help]
                  PATH [PATH ...]
subliminal: error: too few arguments


(2) I loaded a bash script into Nautilus so that I could download subtitles by a right-click on a movie file instead of having to go to a console. But I could not get a successful download!:
 #!/bin/bash
 # NAME:         Get_subtitles
 # AUTHOR:       (c) 2014 Glutanimate
 # DEPENDENCIES: subiminal ([https://github.com/Diaoul/subliminal](https://github.com/Diaoul/subliminal))
 # LICENSE:      MIT license ([http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT))


 LANGUAGE="en"


 while [ $# -gt 0 ]; do
     MOVIE="$1"
     subliminal "$MOVIE" -l "$LANGUAGE"
     shift
 done


(3) Finally,In another attempt to download the subtitle with a right-click on the movie file, I opened Thunar File Management and loaded a command into its Custom Action:
subliminal -f -l en --%N
Alas, this did  not work either!


My objective here is:
(1) make sure that Subliminal actually is working i.e.downloads subtitles
(2) integrate Subliminal with a file system so that it operates with a right-click on a movie file without have to work at the terminal

---

### Post by j0sk on 2014-12-18
Try first with simple command like:

> subliminal -l en Name_Of_The_Movie_file.mkv

Then more complex command like:

> subliminal -m 0 -l en fi --addic7ed-username [COLOR=red]<username>[/COLOR] --addic7ed-password [COLOR=red]<password>[/COLOR] -- Name_Of_The_Movie_file.mkv

Those are working just fine for me!

---

