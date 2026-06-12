---
title: "Help with wget"
date: 2007-10-30
forum: General Help
---

### Post by saryu on 2007-10-30
Hi,
I am trying to use wget to download music from [http://sangeetradio.com/music/default.asp]("http://sangeetradio.com/music/default.asp") .
I want every song that is under the Indian\Movies folder and all subfolders. I used the following wget command but it didn't work:
> wget -c -o sangeetlog.txt -r -H -l 10 -Dsangeetradio.com -A wma,mp3,asp,htm,html -I/music,/music/Indian/Movies,/Indian,/Movies -X"/music/Indian/Artists,/music/Indian/Ghazals,/music/Indian/Oldies,/music/Indian/Remixes,/music/Pakistani,/music/Religious,/music/UrduAbab,/music/new comers" -np "http://www.sangeetradio.com/music/Default.asp"
It did two things:
[LIST]
[*]It downloaded the song "Tau Phir Aoo" from the music\Indian folder, but nothing below that, and
[*]It downloaded a whole lot of files from the music\New Comers folder.

[/LIST]
Can somebody please help me? Thanks very much!

Saryu

---

### Post by scrooge_74 on 2007-10-30
man wget

---

### Post by saryu on 2007-10-30
> **scrooge_74 said:**
> man wget

Hi,

Thanks, I read and reread the documentation from [www.gnu.org/software/wget/manual/wget.html](www.gnu.org/software/wget/manual/wget.html) but it has only gotten me so far. I don't usually ask for help with things like this because I enjoy the challenge of figuring things out for myself, but this one has me stumped! If anyone could help me with this specific example (it is a bit confusing to me because of the way the website is structured) then I will be really grateful. Thanks!

Saryu

---

### Post by scrooge_74 on 2007-10-30
What about using the:  *--include-directories=LIST  list of allowed directories.* command?

I really only use wget from time to time

---

### Post by FXEF on 2007-10-30
> **saryu said:**
> Hi,
I am trying to use wget to download music from [http://sangeetradio.com/music/default.asp]("http://sangeetradio.com/music/default.asp") .
I want every song that is under the Indian\Movies folder and all subfolders. I used the following wget command but it didn't work:

It did two things:
[LIST]
[*]It downloaded the song "Tau Phir Aoo" from the music\Indian folder, but nothing below that, and
[*]It downloaded a whole lot of files from the music\New Comers folder.

[/LIST]
Can somebody please help me? Thanks very much!

Saryu



Try this and let us know if it works.

  wget -r -l1 --no-parent -A.mp3 [http://sangeetradio.com/music/](http://sangeetradio.com/music/)

---

