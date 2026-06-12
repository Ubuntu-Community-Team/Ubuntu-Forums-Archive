---
title: "which 'locate' command is the correct one?"
date: 2022-05-05
forum: General Help
---

### Post by ronjjjg8885 on 2022-05-05
i've tried to use the 'locate' command but it wasn't found.
the terminal suggested installing 'plocate'.

but in [this]("https://askubuntu.com/questions/215503/how-to-install-the-locate-command") link they say to insrall 'mlocate'

it's confusing
what should be installed?

---

### Post by Doug S on 2022-05-05
mlocate is the one that used to be installed by default, but no longer is. It is the package I install on new installations.

EDIT: Although it appears that mlocate is now a dummy package and one will end up with plocate anyhow:

```
doug@serv-jj:~$ dpkg -l | grep locate
ii  mlocate                               1.1.15-1ubuntu2                         all          transitional dummy package
ii  plocate                               1.1.15-1ubuntu2                         amd64        much faster locate
```

```
doug@serv-jj:~$ ls -l /usr/bin/locate
lrwxrwxrwx 1 root root 24 May  1 15:15 /usr/bin/locate -> /etc/alternatives/locate
doug@serv-jj:~$ ls -l /etc/alternatives/locate
lrwxrwxrwx 1 root root 16 May  1 15:15 /etc/alternatives/locate -> /usr/bin/plocate

doug@serv-jj:~$ ls -l /usr/bin/updatedb
lrwxrwxrwx 1 root root 26 May  1 15:15 /usr/bin/updatedb -> /etc/alternatives/updatedb
doug@serv-jj:~$ ls -l /etc/alternatives/updatedb
lrwxrwxrwx 1 root root 26 May  1 15:15 /etc/alternatives/updatedb -> /usr/sbin/updatedb.plocate
```

I'll never remember to run plocate instead of locate, or sudo updatedb.plocate instead of sudo updatedb so I'll continue to install mlocate.

---

### Post by ronjjjg8885 on 2022-05-07
thanks

---

### Post by andrew.46 on 2022-05-08
It looks like you have found what you are after but can I say that time with the 'find' command is time very well spent. This command has has possibilities of usage way beyond applications such as locate / plocate / mlocate.

---

### Post by ajgreeny on 2022-05-08
> **andrew.46 said:**
> It looks like you have found what you are after but can I say that time with the 'find' command is time very well spent. This command has has possibilities of usage way beyond applications such as locate / plocate / mlocate.

Absolutely correct, though if I need a find answer quickly I will admit to using locate but also reducing what might be a long list of files by using grep either to find files in a particular folder or to exclude that folder with grep -v

---

### Post by Doug S on 2022-05-08
For my part of it, I use both locate and find. I also tend to use locate with grep or grep -v if the file list might otherwise be long.

---

### Post by TheFu on 2022-05-08
+1 for both **locate** and **find** here too.
And when I have specific areas of file systems that locate doesn't get, I create a daily **find** script to create a local text DB just for those files, then use **egrep** to search in that text DB file.  

For example, I have a music player tool that searches for .m3u files in the text DB and forwards matching playlists to a console music player. If more than one .m3u file is found in the search, the script presents a numbered list to select 1 playlist to be played.
```
$ m-search classical
0: /R/Music/Classical/Schroeders_Greatest_Hits/vorbis-q6/Various-Schroeders_Greatest_Hits-vorbis-q6.m3u
1: /R/Music/Classical/Shostakovich,_Dmitri/String_Quartets_nos_14_and_15_Manhattan_String_Quartet/vorbis-q6/The_Manhattan_String_Quartet-Shostakovich-vorbis-q6.m3u
2: /R/Music/Classical/Vivaldi_I_Musici/The_Four_Seasons/Vivaldi_I_Musici-The_Four_Seasons.m3u
3: /R/Music/Classical/Baroque_Music/BBC-Baroque_Music.m3u
4: /R/Music/Classical/Baroque_Music/Recorder-Baroque_Music.m3u
5: /R/Music/Classical/Cartoon_Classics/vorbis-q6/Cartoon_Classics-vorbis-q6.m3u
6: /R/Music/Classical/Heifetz,_Piatigorsky,_Friedman,_Primrose_playing_Brahms,_Bach_an/vorbis-q6/Jascha_Heifetz-Brahms,_Bach_&_Mozart-RCA_Gold_Seal_1987-vorbis-q6.m3u
7: /R/Music/Classical/Classical_all.m3u
...
Select number: 0<enter>
```
Fast, effective, simple.  Jammin' to _Schroeders Greatest Hits_ now. ;)
Creating a numbered list is 6 lines of bash.
```
CNT=0
readarray -t  M3U_ARRAY < <( /bin/egrep  -i \*${SEARCH}\* "$M3U_FILE" ) 
for item in "${M3U_ARRAY[@]}" ; do
   echo "$CNT: ${item}"
   ((CNT++))
done
```

The script also updates the text DB with this command:
```
M3U_FILE="$HOME/bin/m3u_files.dat"
MUSIC=/R/Music
   /usr/bin/find $MUSIC -type f -iname \*m3u | tee "$M3U_FILE"
```

Alas, locate pays attention to the owner, group, permissions of the found search results and only shows those objects that the current userid can read/see.

---

