---
title: "Where can I find logs of all media files played/accessed by a user?"
date: 2022-09-29
forum: General Help
---

### Post by painted-rhubarb on 2022-09-29
[COLOR=#1A1A1A][FONT=&amp]Hi All. I have a bit of a conundrum.

[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]Yesterday I was organizing some home video archives, and I accidentally moved a file into the wrong folder of about 3000 other clips, before copying said folder onto a new disk and wiping the original.

[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]They're records of battery testing, so thumbnails all visually very similar - which means finding this clip again will mean going through each clip, one at a time. Sadly they all have the same creation/modification timestamps now too, so can't even get a hint there.

[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]The only hope is - I watched the file before moving it yesterday. So I'm hoping that SOMEWHERE on that ubuntu machine, there's a log file that says I accessed [filename].mp4, which I can then search for in the new archive.

[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]So - for the forensics experts out there - are there any logs in the system that track what media files are played/opened. I was using the MPV deb at the time.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]Thanks![/FONT][/COLOR]

---

### Post by TheFu on 2022-09-29
If you didn't disable the access time mount option, then the atime is part of each file.  Use the 'stat' command to see it for each file. For example:

```
$ stat /usr/bin/zs*
  File: /usr/bin/zsync
  Size: 92312           Blocks: 184        IO Block: 4096   regular file
Device: fd00h/64768d    Inode: 957048      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2021-01-30 13:18:50.000000000 -0500
Modify: 2018-02-18 23:42:55.000000000 -0500
Change: 2021-01-30 13:23:19.298472186 -0500
 Birth: -
  File: /usr/bin/zsyncmake
  Size: 92408           Blocks: 184        IO Block: 4096   regular file
Device: fd00h/64768d    Inode: 957050      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2021-01-30 13:18:50.000000000 -0500
Modify: 2018-02-18 23:42:55.000000000 -0500
Change: 2021-01-30 13:23:19.298472186 -0500
 Birth: -
```

Add a little grep to filter and Bob's your uncle.

---

### Post by painted-rhubarb on 2022-09-29
> **TheFu said:**
> If you didn't disable the access time mount option, then the atime is part of each file.  Use the 'stat' command to see it for each file. For example:

```
$ stat /usr/bin/zs*
  File: /usr/bin/zsync
  Size: 92312           Blocks: 184        IO Block: 4096   regular file
Device: fd00h/64768d    Inode: 957048      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2021-01-30 13:18:50.000000000 -0500
Modify: 2018-02-18 23:42:55.000000000 -0500
Change: 2021-01-30 13:23:19.298472186 -0500
 Birth: -
  File: /usr/bin/zsyncmake
  Size: 92408           Blocks: 184        IO Block: 4096   regular file
Device: fd00h/64768d    Inode: 957050      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2021-01-30 13:18:50.000000000 -0500
Modify: 2018-02-18 23:42:55.000000000 -0500
Change: 2021-01-30 13:23:19.298472186 -0500
 Birth: -
```

Add a little grep to filter and Bob's your uncle.

Thanks for the reply, but I must confess I don't really follow what youre saying here, terminology is rather above my level . Any chance you could explain it at an entry-level for a new user?

---

### Post by Holger_Gehrke on 2022-09-29
If you used mpv from the command line, then the whole command including the file name should be in the command line history in the file ~/.bash_history. If you started mpv through smplayer (GUI for mplayer and/or mpv) then that might have generated an entry in ~/.local/share/recently_used.xbel (not sure if smplayer does this, I usually use mpv from the command line).

Holger

---

### Post by TheFu on 2022-09-29
> **painted-rhubarb said:**
> Thanks for the reply, but I must confess I don't really follow what youre saying here, terminology is rather above my level . Any chance you could explain it at an entry-level for a new user?

Perhaps someone else can.  That isn't in my skill set.   

All my prior attempts at doing simple explanations have frustrated me and pissed off the other person. Sorry.

---

### Post by &amp;KyT$0P# on 2022-09-29
> **TheFu said:**
> Perhaps someone else can.

Ok, I'll try to explain it without advanced terminology.

Here's how I would implement TheFu's suggestion.  Open a Terminal in the folder that has the 3000+ files, and run
```
/usr/bin/stat -c '%X %n' * | sort -n
```
Which lists the access timestamp followed by the filename, then sorts the output.

If TheFu's suggestion applies in your case, the file you're looking for should be one of the files named near the bottom of that command's output.

Refer to [FONT=Courier New]man stat[/FONT] for more info about that command.

---

### Post by #&amp;thj^% on 2022-09-29
> **TheFu said:**
> Perhaps someone else can.  That isn't in my skill set.   

**_All my prior attempts at doing simple explanations have frustrated me and pissed off the other person. Sorry._**
Nicely said, I as well find it harder and harder to explain how, now I just do with no how to. (Not the best in forums)

> **halogen2 said:**
> Ok, I'll try to explain it without advanced terminology.

Here's how I would implement TheFu's suggestion.  Open a Terminal in the folder that has the 3000+ files, and run
```
/usr/bin/stat -c '%X %n' * | sort -n
```
Which lists the access timestamp followed by the filename, then sorts the output.

If TheFu's suggestion applies in your case, the file you're looking for should be one of the files named near the bottom of that command's output.

Refer to [FONT=Courier New]man stat[/FONT] for more info about that command.

+1 That should be a great start

---

### Post by dragonfly41 on 2022-09-29
An idea, but i do not have previous experience of scanning mp4 folders (only others).

If you can remember some _internal_ term / keyword _inside_ your *.mp4 you might try this .. change directory in terminal to  the directory containing 3000 files.

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

---

### Post by Holger_Gehrke on 2022-09-29
The idea of using the access timestamp is clever, but it probably doesn't work. painted-rhubarb said he copied the files then wiped the original. Copies are new files and have their timestamps set to the time they are created. At least that's what happens when using 'cp' or 'Thunar', it might be different when using other tools, for example 'rsync' with the right set of options ('-tUN' would preserve all three timestamps on the copies).

Holger

---

### Post by dragonfly41 on 2022-09-29
If he "wiped" the file could testdisk recover it?

---

### Post by TheFu on 2022-09-29
This might have nothing related to this thread, but a little background may be helpful.

The internals of mv and cp are very different.  

25 yrs ago, we weren't allowed to mv any file system objects between different file systems. It would error out.  That's because a 'mv' just changes the parent for the inode and is effectively instantaneous.   Shortly after that time, the mv command was changed to implement moving across file systems ... as a cp + rm.  Initially, that was very dangerous, because copying could fail and the rm would still happen.

What's this have to do with anything?  Perhaps nothing.  But if the mv was used and is is on the same file system, then the ctime/atime/mtime would be unchanged.  Going across file system boundaries and I'd suspect it was a cp use, so those timestamps would all reflect the specific time of the cp.

If a GUI is used, all bets are off.  GUI programmer seldom thing about performance and typically use an existing library that has a command for the file process desired. Who knows what the internals actually do?  Not me.

All of this also explains why every file system has a .Trash/ directory at the top level.  When a GUI that supports trash is used to delete a file, it 'mv's the deleted files in to that .Trash/ directory, usually placing the deleted files below based on the username under the .Trash/  This is nearly instantaneous. If the trash is prevented from working (there are a few techniques to prevent it), then the files will not be copied to the ~/Trash/ because that takes too much time and would quickly fill the HOME directory with deleted files ... and those would end up in backup sets, assuming every $HOME is backed up.

If the system has good backups, you could look through those backup sets for atime data. That would really depend on the backup tool used.  A good tool (in this specific situation), would retain the timestamps.  Timestamps within 1 day of the true value are usually sufficient in my experience. 

BTW, the 'find' command could be used to search for specific mtime, atime, ctime values too, if the files are in many different directories.

If all the files were copied. I have no good answer, besides looking in the command history.  This is one of those problems where knowing some details about the files and how the system is managed that only you can know would help.

---

### Post by painted-rhubarb on 2022-09-29
Thankyou all for the replies.

> **TheFu said:**
> Perhaps someone else can. That isn't in my skill set.

All my prior attempts at doing simple explanations have frustrated me and pissed off the other person. Sorry.

Apologies but am I in the wrong place to be asking this question as a beginner? If so, it wasn't clear this was a space for advanced users only....




> **Holger_Gehrke said:**
> If you used mpv from the command line, then the whole command including the file name should be in the command line history in the file ~/.bash_history. If you started mpv through smplayer (GUI for mplayer and/or mpv) then that might have generated an entry in ~/.local/share/recently_used.xbel (not sure if smplayer does this, I usually use mpv from the command line).

Holger

Thankyou but I don't use the command line for anything - plain language instructions on its use are far too hard to find, and I feel the risk of doing damage too great. I only dabble there with very clear guidance and explicit direction. This was all just the normal Ubuntu 'point and click' desktop interface.

I have checked that file but it seems to be empty




On second reading, I noticed that the method  here*seems * to be describing the metadata you can find by right clicking and selecting properties

> **TheFu said:**
> 
```
Access: 2021-01-30 13:18:50.000000000 -0500
Modify: 2018-02-18 23:42:55.000000000 -0500
Change: 2021-01-30 13:23:19.298472186 -0500
```


Any methods looking for this won't help. As Holger Gehrke rightly points out

> **Holger_Gehrke said:**
> The idea of using the access timestamp is clever, but it probably doesn't work. **painted-rhubarb said he copied the files then wiped the original. **Copies are new files and have their timestamps set to the time they are created. At least that's what happens when using 'cp' or 'Thunar', it might be different when using other tools, for example 'rsync' with the right set of options ('-tUN' would preserve all three timestamps on the copies).

Holger


All the files in their new drive have the exact same timestamps for all fields, as I said in my original explanation.

Hence, I'm looking at this from a lo file perspective.

I have had "/var/log" suggested where I have asked this elsewhere, and I've had a look there and there seem to be a lot of files, some openable and seem to have timestamped lists of events,

Would any of these files, or any other files, have entries showing which files were accessed, and when?

Thankyou all again

---

### Post by TheFu on 2022-09-29
> **painted-rhubarb said:**
> Thankyou all for the replies.

Apologies but am I in the wrong place to be asking this question as a beginner? If so, it wasn't clear this was a space for advanced users only....


The question didn't seem like a beginner question, so I didn't assume you were a beginner. I also didn't think you were an expert ... rather early intermediate user was my guess.

And as is clear now, the stat method won't work after a copy to a different file system and deleting the originals.  Only your special knowledge of the files will be any aid, I fear, especially for a beginner.

BTW, we've all done something similar.  I've done something like this in the last 2 months, just on a smaller scale.  Did about 5 minutes of processing for each of 20 video files, then promptly deleted everything.  I didn't intend to, but an extra space in a 'rm' command with an '*' in it took care of everything. ;( 
I have backup religion and would have gotten a backup of the files overnight, but this was all new files, processed that day, so no backups.  The disk that the files arrived on, was already wiped and formatted, when I saw the copy off that disk had worked.

Happens to everyone, even if we have systems in place that would have made it a minor inconvenience if the files were untouched for about 16 hours.  Sigh.

Now, if you used a file manager and the delete key to remove the files, they might be in your Trash/ ... either on the source disk or the target disk.  Just depends if you have trash enabled and how much deleted stuff it is set to allow.  I don't use trash and wipe it nightly as a pest.  I'm not a fan, especially for large files.  Anyway, you might check that option.

> **painted-rhubarb said:**
> Thankyou but I don't use the command line for anything 

The command line is faster and easier to convey that writing 50 lines and 5 pictures of what needs to happen. This is more useful and concise in a forum.

I can't think of any reason that /var/log/ would have any logs related to normal file moves or copies. If you want everything logged, that's a different OS - the military probably has one.

The Unix philosophy isn't about protecting users from themselves/us.  It is about allowing users to perform whatever they think they need, efficiently.  In Unix, we are allowed to shot ourselves in the foot, leg, head, if that's what we ask.  The system cannot tell of it is a stupid request or pure genius (or both).  That's great and terrible, depending on your point of view.

If you do want all file activities logged, you could create a wrapper that does just that, but it isn't a beginner task.  I suspect any wrapper will break some things too.  You can look at the 'sudo' command and how it logs every command made using it to /var/log/auth.log  This doesn't help with the current issue.

---

### Post by Impavidus on 2022-09-30
The creation date may be stored in the file itself. That is, the creation date of the video, not of the file in which it's stored. If you have installed the package ffmpeg, there should be a command line utility named ffprobe that can extract metadata from the video file, which may include the creation date. I've never done this myself, so you'll have to look up the manual for ffprobe.

---

