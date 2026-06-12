---
title: "[SOLVED] k3b and gnome baker problems with srt files"
date: 2007-02-23
forum: General Help
---

### Post by uroskriznar on 2007-02-23
I have a Philips DVD player that also plays DivX movies and can load external .srt subtitles. When I was using Nero in Windows my DVD player recognized the SRT files. But in Ubuntu I used k3b and gnome baker, but my dvd player only recognized the AVI file, but not the SRT file. Any ideas why?

---

### Post by annda on 2007-02-23
i don't know exactly how your dvd player recognizes the right srt file to play - it's probably the same filename.

so just a wild guess:

three things i can think of that make text files different on linux and on windows are character encoding (utf-8 rather than iso), case sensitivity (filenames can be affected by that), and end-of-line markers in the files themselves.

also, spaces in filenames can be an issue (but not necessarily).

check the names of the files you burned, preferably in the terminal. the problem might lie there. in fact, i hope it does, since that would be the easiest to troubleshoot.

---

### Post by uroskriznar on 2007-02-23
I am completely new to Ubuntu and Linux. What kind of commands do I use in the terminal to get to my dvd rom? DIR and CD probably work similar to DOS.

---

### Post by annda on 2007-02-23
a quick filesystem navigation giude:

dos > linux
---------------
cd is cd
cd.. is cd .. (mind the space) to get to a higher directory
dir is dir (nice to show you how spaces are handled in unix/linux console)
but ls (this ls lowercase L) is nicer
ls -a shows all files (even hidden ones)
ls -l gives long info (extra information)

when you open terminal you will land in your home/user directory. move to the highest level by 
```

cd /
```

and keep on navigating or get straight to the folder where all drives are mounted (on an installed system, on liveCD this is /mnt not /media)
```

cd /media
```

then 

```
ls
```

to find out where your dvd is mounted. try to cd down there and use the ls command to show you the files.

EDIT: here are good basics:
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

---

### Post by uroskriznar on 2007-02-23
Thanks for a quick guide of the navigation in the terminal. The ls looks cool. Are the colors random or are they different for different kinds of files?

Well I checked my DVD and the file name of the .avi and the .srt file in the terminal is the same - I pasted an example:

[email]uros6@uros6-desktop:/media/cdrom0/Stranger.Than.Fict[/email]ion[2006]DvDrip[Eng]-aXXo$ ls
Stranger.Than.Fiction[2006]DvDrip[Eng]-aXXo.avi
Stranger.Than.Fiction[2006]DvDrip[Eng]-aXXo.srt

So this is not the problem any other ideas?

---

### Post by annda on 2007-02-23
have you opened the srt file and saved in it linux? if so, character encoding or end-of-line coding may be the culprits. try downloading an srt and for the sake of testing burn it to a rewritable disc together with the avi.

other than that, i have no idea what is wrong.

---

### Post by uroskriznar on 2007-02-24
I tried not to open the .srt file in Ubuntu but this did not work as well.

But I noticed that k3b says that .srt is a PLAIN TEXT DOCUMENT under type. My DVD player only supports .srt and .sub files but not .txt files. I also converted the .srt into .sub file with subtitle editor. Still did not work.

VLC player recognizes the .srt and .sub files both in Ubuntu and in Windows but my DVD player does not. But only if i burn the CD or DVD in Ubuntu. If I burn it in Windows with Nero it works.

---

### Post by superunknown on 2007-02-25
I have the same problem...now what get´s me mad!!! is that Nerolinux seems not to be disturbed by whatever is causing k3b to fail.

Nerolinux interface sucks! I want to use k3b but this thing is driving me insane, the .srt files are right because if I burn the movie + srt file with Nerolinux my dvd player works, I´ll go on trying to guess what is different in k3b.

This is really sad, I mean is a really silly issue that I never thought would encounter on Linux, and the only link on the Internet that I found with someone having the same issue is here.

Well, if I get to found a solution I´ll let you know.

Bye.

---

### Post by rand0m on 2007-07-10
Old thread but one of the only ones I've found that addresses this problem. Anyways, I fiddled around with the settings on k3b with a RW disc and got my philips dvp642 to recognize an SRT file. Here's the settings I used:

1) Before you burn go to the File System tab
2) Under File System, click custom
3) Uncheck everything under File Systems ie; Rock Ridge, Joliet, UDF  [enabling Rock Ridge works aswell and lets you see full filenames in Ubuntu]
4) Uncheck everything under Other Settings
4) Uncheck everything under File Systems Settings
5) Iso level 2

Keep in mind I did saved the SRT files in Linux and had no problems. I also tried old SRT files from my windows partition that had the same original dvd problem so character/endline encoding didn't seem to be the problem.

Some other options also seemed to work such as allowing 31 characters. I didn't need any of these since the DVP642 is limited to 11 characters anyway. I guess you could keep adding options you might need to see if it works. I've also verified that the subtitles work with 6 different movies/srt files. Hope this helps someone else out there.

By the way, I tried nero linux 3 and couldn't get it to work. Although I prefer k3b, if anyone was successful with nero I'd like to know how they did it since I already have the program.

**[COLOR="Red"]Update:[/COLOR]** Did a little more testing and found out that the philips wouldn't recognize filenames with multiple dots/periods. If you choose Dos Compatibility as the File System it will read the file, although it shortens the filename to 8 characters. As of now I'm renaming anything with multiple periods. Not a huge problem but I could live without it...

---

### Post by webaake on 2007-09-18
I just tried the above hints by unchecking everything in K3B filesystems, but no luck. Exactly the same problem on my Philips DVP 630 (same as DVP642 but for Europe).  The srt files get an icon on the Philps with a red question mark, so it sees the srt files but don't recognize them.


Furthermore I'va have also tried editing mime types like this;

Edit 'application/x-srt' here comment it with # or delete it
in /usr/share/mime/packages/freedesktop.org.xml
And deleted application/x-srt:*srt and added text/plain:*.srt and text/plain:*.sub in
/usr/share/mime/globs

It did change the way Feisty handles the files, but not when burning in Brasero, Gnomebaker or K3b. I got those hints from this thread;

[http://ubuntuforums.org/archive/index.php/t-204426.html](http://ubuntuforums.org/archive/index.php/t-204426.html)


This is a small but terribly annoying problem! I have a newly built media mcahine with Ubuntu Feisty working sweetly, but can't burn proper backups of my divx/xvids. Of course all the standard issues have been adressed like; filenames are exactly the same except suffix. Both avi and srt files works under VLC, both in Linux and in Windows, with same burned data DVD.

So I've tan into a wall here and will look for NeroLinux and try that.....

PS Tried NeroLinux 3.0.1.3 with good results. Just standard settings (no change) and the srt files came out alright in my Philips DVP630(642). Furthermore it managed the DVD-RW perfectly, wich Gnomebaker and K3B didn't. So if Nero also manages mp3's I'll stick to it......

---

### Post by rand0m on 2007-09-18
webakke, I also have used nero 3 again since my last post and it works by default. Not sure what I did wrong the first time. Since then I just use nero 3 for burning my divx/xvid discs. I've gotten combinations to work with long filenames in K3B but I have to constantly rename files which was a hassle. Have you tried the same settings in K3B as in nero linux? Maybe I'll mess around with it again later.

---

### Post by rand0m on 2007-11-18
Thread rivival! So I put in a new kubuntu installation and it didn't have nero so I decided to see if I could fix the subtitle problem this time. Searching around led me here:

[http://eduardosextafeira.blogspot.com/2007/10/solving-philips-dvp642-subtitle-support.html](http://eduardosextafeira.blogspot.com/2007/10/solving-philips-dvp642-subtitle-support.html)

This seems to solve the problem. I haven't tested it extensively but I've burnt a handful of random srt files onto a dvd with different naming conventions I knew were problematic. So far they all work. Looks like I won't be needing nero anymore.

---

### Post by uroskriznar on 2007-11-18
Thanx for the info.

---

