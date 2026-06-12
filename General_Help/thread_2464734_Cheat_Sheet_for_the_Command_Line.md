---
title: "Cheat Sheet for the Command Line"
date: 2021-07-10
forum: General Help
---

### Post by dddman on 2021-07-10
I'm building a cheat sheet and could use suggestions.  I want to fill it with common commands.  I just started this list with update/upgrade/clean/shutdown...  I know I need to add find/locate.  What else?


All added commands
```

SoundMixer   "Alsamixer"
Sound        "Pavucontrol"
Aptitude     "PackageManager"
Log          "dmesg"
Memory       "Ram"
Editor       "Tilde"
SysMonitor   "Htop"
Zcolor       "Zenity Color Picker"
INXI         "System Resources"
DF           "Disk Files"
Update       "Update & Full Upgrade"
Clean        "autoRemove & autoClean"
FixBroken    "-f install"
Cache        "Archives"
Edit         "Edit this script"
Reboot       "Reboot the System"
Shutdown     "Shutdown the System"
Shell        "Exit to Shell"
CLIlist      "Commands apropos"

```

---

### Post by dddman on 2021-07-10
*Note
I created the attachment to my post, but not the screenshot.  When I tried to edit it displays two post.

edit
[COLOR=#ff0000]Again it happen and I cannot edit out the first pic.[/COLOR][COLOR=#ff0000][/COLOR]

---

### Post by TheFu on 2021-07-10
There are hundreds of existing cheat sheets on line.  Google this: "linux cheat sheet -type:pdf"

Or look in these directories on your system:
[LIST]
[*] /usr/bin
[*] /bin
[*] /sbin
[/LIST]

If you want a summary, use **apropos**.  **apropos ' '** will create a list, 1 line per command.  I'm seeing 7700 commands on a desktop
```
$ apropos ' '|wc -l
7741
```
On a minimal server, there are
```
$ apropos ' '|wc -l
5345

```
commands.  Scan 500 every day and mark the ones that seem interesting for full manpage reading later.  Commands like sort, cat, tac, head, sed can go a long way.

One page just doesn't cover enough.  I use vimwiki to group commands by purpose and keep them organized.  Here's my inxi notes:
```
* inxi -Fxz     - Full overview w/ sensitive filtered
* inxi -Gx      - GPU+driver
* inxi -Ax      - Audio+driver
* inxi -Dx      - disks
* inxi -pl      - disk partitions/labels
* inxi -dupl    - disks labels + UUIDs + mounts
* inxi -Rx      - RAID
* inxi -Nnxz    - networking w/ extra information and sensitive data filtered 
* inxi -iz      - network IPs w/ link information and sensitive data filtered 
* inxi -I       - uptime, process, ram, shell overview
* sudo inxi -m  - detailed RAM modules
* inxi -rx      - Repos
* inxi -t cm    - Top CPU/RAM for top 5 processes
```
Sometimes I just want the answer without slurping into a detailed manpage.

There are 2 stages - remembering the command and getting to my summary.  apropos (man -k) is very useful.

---

### Post by scorp123 on 2021-07-10
> **dddman said:**
> I'm building a cheat sheet... 

The only cheat sheet you will ever need: [cheat.sh]("https://cheat.sh/")

You can either use it in a web browser by visiting the URL above or you use **"curl"** from the terminal. Examples:
```
curl cheat.sh
curl cheat.sh/zfs
curl cheat.sh/mdadm
curl cheat.sh/vim

```

If the thing you wanted to ask doesn't match anything it will try to guess what you might have meant and make suggestions, e.g.

```

> curl cheat.sh/ext4
Unknown topic.
Do you mean one of these topics maybe?

    * exit 75
    * next 75
    * mkfs.ext4 62

```

---

### Post by dddman on 2021-07-10
I'm not going to try to post any more today, something is still glitching in the forum.  I did add some suggestions in post #1.

---

### Post by TheFu on 2021-07-10
cheat.sh/exfat didn't work. ;(
The returned html isn't valid, BTW.  Interesting idea.  OTOH, google for "man exfat" did return this: [https://manpages.debian.org/jessie/exfat-fuse/mount.exfat.8.en.html](https://manpages.debian.org/jessie/exfat-fuse/mount.exfat.8.en.html) ... which is the normal manpage for the exFAT mount command from 2010.  

But 
```
$ apropos exfat 
dumpexfat (8)        - dump exFAT file system
exfatfsck (8)        - check an exFAT file system
exfatlabel (8)       - get or set an exFAT file system label
fsck.exfat (8)       - check an exFAT file system
mkexfatfs (8)        - create an exFAT file system
mkfs.exfat (8)       - create an exFAT file system
```
has some useful information for the commands on the current system.

---

### Post by dddman on 2021-07-11
Thanks you two

I added some more command launchers to post #1 and still looking for more.

I need a script for "find and locate" so I can add it to my menu.

Keeping scripts in my Home directory I guess is ok.  Is there a official place to keep scripts?

---

### Post by coffeecat on 2021-07-11
> **dddman said:**
> *Note
I created the attachment to my post, but not the screenshot.  When I tried to edit it displays two post.

edit
[COLOR=#ff0000]Again it happen and I cannot edit out the first pic.[/COLOR][COLOR=#ff0000][/COLOR]

@dddman, another member of forum staff removed the [noparse][IMG] and [/IMG][/noparse] BBCode tags to reduce the large image to a URL. You then put the IMG tags back again multiple times over multiple edits, thus restoring the large image. I think that is what you mean by a "screenshot". That's not a screenshot, simply a full-sized image that you get when you use [noparse][IMG] and [/IMG][/noparse] BBCode tags. I'm guessing you were using the "insert image" icon in the message editor toolbar. You don't need that - the thumbnails you created with the attachment utility suffice.

I'm removed the large image in its entirety now. I've also substituted BBCode code tags for quote tags for your list. Please observe how code tags have restored the proper spacing of the columns. There is a link in my sig for using code tags if you need it.

---

### Post by TheFu on 2021-07-11
> **dddman said:**
> Thanks you two

I added some more command launchers to post #1 and still looking for more.

I need a script for "find and locate" so I can add it to my menu.

Keeping scripts in my Home directory I guess is ok.  Is there a official place to keep scripts?

I'm not a fan of re-inventing things. 
It is customary to put scripts into ~/bin/ and has been for 40+ yrs.  Then add ~/bin/ to your PATH. Be certain to only add it if it isn't already there or you could end up with a PATH that is longer than allowed, slow, and causes problems.

I don't understand *find and locate* script.  Just use find or locate or recoll or one of the 50 other file index tools.  Or you can create your own index and use grep.  I do all of these things.  

For example, I have a CLI front end to audio files. It looks through an index of playlists and matches based on a pattern. If more than 1 line is returned, it shows a menu of answers to be selected from. If only 1 item is returned, that gets played either in order or randomly.  There are options. 
```
$ m-search Cartoon
0: /R/Music/Classical/Cartoon_Classics/Classical-Cartoon_Classics.m3u
INFO: Playing: /R/Music/Classical/Cartoon_Classics/Classical-Cartoon_Classics.m3u 
```

The playlist index can be updated using the same tool.
```
$ m-search -u
INFO: Done updating $HOME/bin/m3u_files.dat
```

```
$ m-search Spice
0: /R/Music/Pop/s/Spice_Girls/Spice_Girls_all.m3u
INFO: Playing: /R/Music/Pop/s/Spice_Girls/Spice_Girls_all.m3u 

```
**I'm not embarrassed at all. ;)**

The $HOME/bin/m3u_files.dat file is just the output from a **find** command.
```
# #############################
# want to update m3u lists
if [ "$SEARCH" == "-u" ] ; then  
   /usr/bin/find $MUSIC -type f -iname \*m3u | tee "$M3U_FILE"
   echo "INFO: Done updating "$M3U_FILE" "
   exit 0;
fi
```

Simple little stuff, but extremely powerful when grouped together as a script.  Most of the script is just 2-5 lines at a time doing little stuff. I could have used **locate** instead, but the system with the 5.1 speakers isn't the same as where the files are stored. The *locate* command doesn't really like crossing onto NFS (or CIFS) storage.

For media stuff, **recoll** can slurp the metadata from the files, so that information can be searched. Recoll is basically your own google or your files, local. I have it reindex daily.  That's a different "media" search.
```
$ media-search.sh -u  # will update the index.
```
See my pattern?

I keep a list of already seen movies, TV shows, and ratings, so I never need to see a bad movie twice. That's a huge time-saver. Nobody needs to see *The Princess of Nebraska* twice.

---

### Post by dddman on 2021-07-11
> **coffeecat said:**
> @dddman, another member of forum staff removed the [noparse][IMG] and [/IMG][/noparse] BBCode tags to reduce the large image to a URL. You then put the IMG tags back again multiple times over multiple edits, thus restoring the large image. I think that is what you mean by a "screenshot". That's not a screenshot, simply a full-sized image that you get when you use [noparse][IMG] and [/IMG][/noparse] BBCode tags. I'm guessing you were using the "insert image" icon in the message editor toolbar. You don't need that - the thumbnails you created with the attachment utility suffice.

I'm removed the large image in its entirety now. I've also substituted BBCode code tags for quote tags for your list. Please observe how code tags have restored the proper spacing of the columns. There is a link in my sig for using code tags if you need it.
Ok, thank you.  But just so you know the last two edits to post #1 were text only edits and the image would simply appear.  I only used [QUOTE] tags in the edit and the full screen (yes, screenshot) image reappeared.  I think something is broke.

Edit
Just tried an edit to #1, it worked ok this time.  I don't understand

---

### Post by CharlesA on 2021-07-11
Closed at the request of OP.

---

