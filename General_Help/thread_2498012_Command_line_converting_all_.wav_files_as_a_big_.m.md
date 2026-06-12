---
title: "Command line converting all .wav files as a big .mp3 file"
date: 2024-05-26
forum: General Help
---

### Post by satimis on 2024-05-26
Hi all,

What will be the command line to convert all .wav files to .mp3 files and combine all .mp3 files as a big .mp3 file?

Thanks

Regards

---

### Post by currentshaft on 2024-05-26
> **satimis said:**
> Hi all,

What will be the command line to convert all .wav files to .mp3 files and combine all .mp3 files as a big .mp3 file?

Thanks

Regards

This is a question simple enough for LLMs to answer, and you should consider using them in future (or at the very least, search the web). I've gone ahead and done it for you this time:

To convert.wav files to.mp3 files in a Linux/Mac environment, you can use a command-line tool called ffmpeg. Here's a simple command to convert a single.wav file to.mp3:

ffmpeg -i input.wav output.mp3

Replace input.wav with the name of your.wav file and output.mp3 with the desired name for the.mp3 file.

To convert all.wav files in a directory to.mp3, you can use a for loop in bash:

for f in *.wav; do ffmpeg -i "$f" "${f%.wav}.mp3"; done

This command will convert all.wav files in the current directory to.mp3.

To combine all.mp3 files into a single.mp3 file, you can use the ffmpeg command with the -f concat option. First, create a list of.mp3 files in a text file:

ls *.mp3 > mp3files.txt

Next, create a new.mp3 file by combining the files listed in mp3files.txt:

ffmpeg -f concat -safe 0 -i mp3files.txt -c copy combined.mp3

Replace combined.mp3 with the desired name for the output file.

Please note that you need to have ffmpeg installed on your system to run these commands. If it's not installed, you can install it using the package manager for your operating system. For example, on Ubuntu, you can use the following command to install ffmpeg:

sudo apt-get install ffmpeg

---

### Post by satimis on 2024-05-26
> **currentshaft said:**
> This is a question simple enough for LLMs to answer, and you should consider using them in future (or at the very least, search the web). I've gone ahead and done it for you this time:

To convert.wav files to.mp3 files in a Linux/Mac environment, you can use a command-line tool called ffmpeg. Here's a simple command to convert a single.wav file to.mp3:

ffmpeg -i input.wav output.mp3

Replace input.wav with the name of your.wav file and output.mp3 with the desired name for the.mp3 file.

To convert all.wav files in a directory to.mp3, you can use a for loop in bash:

for f in *.wav; do ffmpeg -i "$f" "${f%.wav}.mp3"; done

This command will convert all.wav files in the current directory to.mp3.

To combine all.mp3 files into a single.mp3 file, you can use the ffmpeg command with the -f concat option. First, create a list of.mp3 files in a text file:

ls *.mp3 > mp3files.txt

Next, create a new.mp3 file by combining the files listed in mp3files.txt:

ffmpeg -f concat -safe 0 -i mp3files.txt -c copy combined.mp3

Replace combined.mp3 with the desired name for the output file.

Please note that you need to have ffmpeg installed on your system to run these commands. If it's not installed, you can install it using the package manager for your operating system. For example, on Ubuntu, you can use the following command to install ffmpeg:

sudo apt-get install ffmpeg

Thanks for your advice.

I have ffmpeg running here.

$ ffmpeg -i 1.wav -i 2.wav -i 3.wav -i 4.wav output.wav 
(all .wav files in one folder)

$ ffmpeg -i output.wav -acodec libmp3lame audio.mp3

With 2 separate commands I can get the job done.

Is there a (one) command to get the job done, not with pipe | command

Thanks and regards

---

### Post by currentshaft on 2024-05-26
They are separate commands, but you can combine them with one of the following:

**command1 && command2**: this will run command2 IF command1 SUCCEEDS
**command1 || command2**: this will run commands2 IF command1 FAILS
**command1 ; command2**: this will run command2 regardless of what happens to command1

Hope this helps.

---

### Post by satimis on 2024-05-26
Hi all,

Performed following steps;
1)  #with lame command
for i in *.wav; do lame -b 320 -h "${i}" "${i%.wav}.mp3"; done

2) # with ffmpeg
ffmpeg -i "concat:1.mp3|2.mp3|3.mp3|4.mp3|5.mp3|6.mp3|7.mp3|8.mp3|9.mp3'|10.mp3'|11.mp3" -acodec copy output.mp3

It works, converting all .wav files to one mp3 file.

Could it be done in ONE command?

---

### Post by dragonfly41 on 2024-05-27
[COLOR=#000000]> Could it be done in ONE command?
Yes .. as in post #4
Remember to tag thread as SOLVED.[/COLOR]

---

### Post by satimis on 2024-05-27
> **dragonfly41 said:**
> [COLOR=#000000]
Yes .. as in post #4
Remember to tag thread as SOLVED.[/COLOR]
Hi@dragonfly41,

Thanks

Sorry, I'm searching further;
Would there is a single command to complete 2 jobs ?

**[COLOR="#FF0000"]not a command line[/COLOR]**

Regards

---

### Post by dragonfly41 on 2024-05-27
A single command .. but not by command line?

I would use a hotkey which runs a batch of commands. Multiple ways od doing from a hot key that I have used.

Autohotkey
Actiona
Albert
etc. etc.

Desktop automation. UI emulators.


[POSTSCRIPT]
Since you appear from past theads to be building some form of media studio / library I am going to suggest that you use CherryTree as your archiving tool. It is described as a rich text hierarchical notes editor .. but it is much more.

[https://github.com/giuspen/cherrytree](https://github.com/giuspen/cherrytree)

You can create a hierarchy of notes with embedded CodeBoxes which you can run, while  taking notes.

I'm busy at moment but can expand later if you dig into it.  Your multiple commands above can be written in embedded CodeBoxes alongside archive notes.

My advice is to use *.ctd (XML) document mode for desktop indexing reasons which can be explained later (if you follow this route). Clue: Recoll desktop indexer.

---

### Post by HermanAB on 2024-05-27
I would use Sound Exchange - a program called sox.

---

### Post by dragonfly41 on 2024-05-27
I have learned to use the best of multiple tools to create your own Swiss army knife.
So combine them.

---

### Post by currentshaft on 2024-05-27
ta

---

### Post by dragonfly41 on 2024-05-27
[COLOR=#000000]> Congratulations. Please mark the thread as solved, go forth and combine to your heart's content!

Advise the OP, not me. I plough my own furrow.

[/COLOR]

---

### Post by satimis on 2024-05-27
> **HermanAB said:**
> I would use Sound Exchange - a program called sox.
Hi@HermanAB

Thanks for your advice.

sox is on REPO

```

sox *.wav output.wav

```
sox can merge all .wav files to to big .wav file.  But I still need ffmpeg to convert the big .wav file to .mp3 file

Regards

---

### Post by MAFoElffen on 2024-05-27
I'm thinking in one command using 'ffmpeg' that it might look something like this:
```

ffmpeg -i inputfile1.wav -i inputfile2.wav -i inputfile3.wav -i inputfile4.wav -i inputfile5.wav \
-filter_complex '[0:0][1:0]concat=n=5:v=0:a=1[out]' \
-acodec mp3 -ab 64k -map '[out]' test.mp3

```
...but I might be wrong. That might need to be tweaked.

---

### Post by satimis on 2024-05-27
> **MAFoElffen said:**
> I'm thinking in one command using 'ffmpeg' that it might look something like this:
```

ffmpeg -i inputfile1.wav -i inputfile2.wav -i inputfile3.wav -i inputfile4.wav -i inputfile5.wav \
-filter_complex '[0:0][1:0]concat=n=5:v=0:a=1[out]' \
-acodec mp3 -ab 64k -map '[out]' test.mp3

```
...but I might be wrong. That might need to be tweaked.
Hi@MAFoElffen,

Thanks for your advice.

Name of .wav files```

track01.wav track02.wav track03.wav track04.wav ....

```
They are copied from audio CD to a folder created for this purpose

Now I'm thinking another way.  Is there a command able to rip direct an audio CD to mp3 file?

Regards

---

### Post by MAFoElffen on 2024-05-27
> **satimis said:**
> Now I'm thinking another way.  Is there a command able to rip direct an audio CD to mp3 file?

Look at this package
```

mafoelffen@Mikes-B460M:~$ apt-cache show abcde | head -n 14
Package: abcde
Architecture: all
Version: 2.9.3-1
Priority: optional
Section: universe/sound
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Steve McIntyre <93sam@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 333
Depends: cd-discid, wget, cdparanoia | icedax, vorbis-tools (>= 1.0beta4-1) | lame | flac | speex | musepack-tools | opus-tools, libmusicbrainz-discid-perl, libwebservice-musicbrainz-perl (>= 1.0.4-1.1), sensible-utils
Recommends: vorbis-tools, libdigest-sha-perl, bsd-mailx, glyrc, imagemagick
Suggests: eject, distmp3, id3 (>= 0.12), id3v2, eyed3 (<< 0.7~), normalize-audio, vorbisgain, mkcue, mp3gain, atomicparsley
Filename: pool/universe/a/abcde/abcde_2.9.3-1_all.deb

```
Using this command:
```

abcde -d /dev/sr0 -o flac,mp3

```

---

### Post by satimis on 2024-05-28
> **MAFoElffen said:**
> Look at this package
```

mafoelffen@Mikes-B460M:~$ apt-cache show abcde | head -n 14
Package: abcde
Architecture: all
Version: 2.9.3-1
Priority: optional
Section: universe/sound
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Steve McIntyre <93sam@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 333
Depends: cd-discid, wget, cdparanoia | icedax, vorbis-tools (>= 1.0beta4-1) | lame | flac | speex | musepack-tools | opus-tools, libmusicbrainz-discid-perl, libwebservice-musicbrainz-perl (>= 1.0.4-1.1), sensible-utils
Recommends: vorbis-tools, libdigest-sha-perl, bsd-mailx, glyrc, imagemagick
Suggests: eject, distmp3, id3 (>= 0.12), id3v2, eyed3 (<< 0.7~), normalize-audio, vorbisgain, mkcue, mp3gain, atomicparsley
Filename: pool/universe/a/abcde/abcde_2.9.3-1_all.deb

```
Using this command:
```

abcde -d /dev/sr0 -o flac,mp3

```
Hi@MAFoElffen

Thanks for your advice

On Terminal ran;
$ abcde -d /dev/sr0 -o flac,mp3```

[ERROR] abcde: eyeD3 is not in your path.
[INFO] Define the full path to the executable if it exists on your system.
[INFO] Hint: sudo apt-get install 

```

Shall I install python-eyeD3 ?  If YES, please advise HOW

Thanks

---

### Post by MAFoElffen on 2024-05-28
Using the hints and breadcrumbs I gave in my last post, let me narrow that down further for you
> **MAFoElffen said:**
> 
```

mafoelffen@Mikes-B460M:~$ apt-cache show abcde | grep 'Package:'
Package: abcde

```

Using this command to install it:
```

sudo apt install -y abcde

```

---

### Post by satimis on 2024-05-28
> **MAFoElffen said:**
> Using the hinta and breadcrumbs I gave in my last post, let me narrow that down further for you

Using this command to install it:
```

sudo apt install -y abcde

```

abcde has been installed and running previously.  But I don't know WHEN

$ apt-cache show abcde | grep 'Package:'```

Package: abcde

```

Regards

---

### Post by MAFoElffen on 2024-05-28
To show if it is installed would be 
```

apt list abcde --installed

```

---

### Post by satimis on 2024-05-28
> **MAFoElffen said:**
> To show if it is installed would be 
```

apt list abcde --installed

```

$ apt list abcde --installed```

Listing... Done
abcde/jammy,jammy,now 2.9.3-1 all [installed]

```

$ apt policy abcde```

abcde:
  Installed: 2.9.3-1
  Candidate: 2.9.3-1
  Version table:
 *** 2.9.3-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status

```

Regards

---

### Post by HermanAB on 2024-05-29
For future reference with sox: There is a package called libsox-fmt-all that installs all available formats including mp3.

---

### Post by satimis on 2024-05-29
> **HermanAB said:**
> For future reference with sox: There is a package called libsox-fmt-all that installs all available formats including mp3.
Hi,

Could you please explain in more detail how to use libsox-fmt-all ripping complete audio CD as a mp4 file on PC.  Thanks

Regards

---

### Post by satimis on 2024-06-01
Hi@MAFoElffen,

Now I found out the cause of the problem encounted.

The error message was wrong.
```

[ERROR] abcde: eyeD3 is not in your path.
.....

```
It should read eyed3 NOT eyeD3

```

$ sudo apt install eyed3

$ abcde -d /dev/sr0 -o flac,mp3

```
Now it works without complaint, converting all tracks of the audio CD to mp3 files.  But it is still NOT a big mp3 file.

It took me several days to find out this error, including heavy searching on Internet.

"abcde" is similar to the GUI "Audacity" package

Regards

---

