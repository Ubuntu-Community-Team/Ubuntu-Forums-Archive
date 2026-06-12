---
title: "I need to check a list of files against a playlist"
date: 2007-10-24
forum: General Help
---

### Post by macele on 2007-10-24
I had a sort of hard disk catastrophe last night, and I was luckily able to recover most of my data, the directories most effected where my music directories. Now I have somewhere on the order of 10K mp3s but I don't know which ones where lost and not. It seems some directories have lost one song and others have lost everything. I have a complete playlist from before the incident and would like to check the playlist against the directory. The playlist is an .m3u type playlist that looks like this:

#EXTM3U
#EXTINF:0,311-11-Don't Stay Home.mp3
\\192.168.1.31\storage\250a\Music\311\311\311-11-Don't Stay Home.mp3

#EXTINF:0,311-15-Love Song.mp3
\\192.168.1.31\storage\250a\Music\311\Greatest Hits '93-'03\311-15-Love Song.mp3

#EXTINF:0,The Academy is-05-Everything We Had.mp3
\\192.168.1.31\storage\250a\Music\The Academy Is\Santi\The Academy is-05-Everything We Had.mp3

I can load the playlist and change it into another format if need be.

Now I am no Linux guru, but I know there must be a way to make a script that can parse this file and check the mp3s to see if they exist. Now I realize that simply verifying the existence of the file means little. Without a hash check there is no way to be sure that the files are not damaged, but I need some place to start.

The file server runs Ubuntu Linux and I can run the script there, so if there is some way to skip the \\192.168.1.31\ part of the file it would be handy.

I really need your help here guys,
Thanks.

---

### Post by nick_h on 2007-10-24
Try something like:
```
#!/bin/bash
awk '/^\\/ {filename = substr($0,15); \
gsub("\\\\","/",filename); \
missing = system("test -e \"" filename "\""); \
if (missing == "1") print filename " is missing" \
}' test.m3u
```
put it in a file and make it executable.

The script looks for lines starting with a \
then it strips the beginning off and changes \ to /
then it uses the test command to check if the file exists.

Edit the .m3u to your file.

This may provide a start - you could use the file command to try to find the file type instead.

---

