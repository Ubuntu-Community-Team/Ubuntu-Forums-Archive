---
title: "Play and Enqueue with XMMS or BEEP"
date: 2005-05-26
forum: General Help
---

### Post by Behel on 2005-05-26
Is there a possiblity to enqueue by default songs in XMMS or BEEP when I select mutilple MP3 from a folder. So far, it either play the first file or open a different instances of XMMS or BEEP (depending on the option that allows or not multiple instances...).

What I would like is by default: select the songs I want, press enter and that's it. The first file is played, the others are enqueued... like with Winamp.

Maybe the solution is very simple then I apology in advance... O:) 

This thread almost solved my problem... [http://ubuntuforums.org/showthread.php?t=26970&highlight=enqueue+xmms](http://ubuntuforums.org/showthread.php?t=26970&highlight=enqueue+xmms)

I am using Gnome.

Thanks.

---

### Post by bored2k on 2005-05-26
[QUOTE=Behel]Is there a possiblity to enqueue by default songs in XMMS or BEEP when I select mutilple MP3 from a folder. So far, it either play the first file or open a different instances of XMMS or BEEP (depending on the option that allows or not multiple instances...).

What I would like is by default: select the songs I want, press enter and that's it. The first file is played, the others are enqueued... like with Winamp.

Maybe the solution is very simple then I apology in advance... O:) 

This thread almost solved my problem... [http://ubuntuforums.org/showthread.php?t=26970&highlight=enqueue+xmms](http://ubuntuforums.org/showthread.php?t=26970&highlight=enqueue+xmms)

I am using Gnome.

Thanks.[/QUOTE]
 Play Files > Select your files > Play.
That it ?

---

### Post by Behel on 2005-05-27
Yeah yeah... I suppose I could do that but this require to open xmms first then go to option, play file, naviguate to the music directory, select the files and press enter...

I would rather prefer to open the music directory, select files in nautilus and press enter. Then xmms is open, the first played, the others enqueued... This might sound lazy but it is so much convenient...
Is this impossible?

---

### Post by Mr. Electric Wizard on 2005-07-19
Has anyone figured this out yet?
This is the only thing that has been a dissppointment for me in regards to playing music in Linux...

There has got to be a script or something...

---

### Post by akshoslaa on 2005-07-19
right-click the folder
open with other application
use a custom command
xmms -e

(I assume -e works with beep too)
xmms (or bms(?) --help

---

### Post by Desolation on 2005-07-27
Well, that forum hit it dead on.
Kind of.
I edited the file association to xmms, but Under "Use a custom command" added -e after xmms. It works fine

---

### Post by charlieg on 2005-07-27
Probably got a better solution.

Create an executable script in ~/.gnome2/nautlius-scripts called "Enqueue in XMMS":
```
$ cd ~/.gnome2/nautilus-scripts
$ touch Enqueue\ in\ XMMS
$ chmod +x Enqueue\ in\ XMMS
```
Then edit it to contain something like this (**WARNING: untested**):
```
#!/bin/sh
# Enqueue a song in XMMS
xmms -e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```
This probably won't work as-is (I don't have XMMS installed and don't plan on installing it either) because $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS is a new-line delimited list and I don't know whether that'll be a valid argument to pass to XMMS.  If it isn't, the solution is to use a while loop to add the songs one by one (i.e. splitting $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS by new-line) but I'm an adept scripter so cannot provide a likely sample of how that would work.

Anyway, the advantage with doing it the above way is that it'll be available for any type of file (not just .mp3 - .ogg, .wav etc) and you can duplicate it if you have more than one media player.  Also double-clicking on a song will still play it immediately because you've not had to tinker with the file assosciation to use a custom command.

---

### Post by Sam on 2005-07-27
Better script:
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done
```

---

### Post by charlieg on 2005-07-27
Cheers Sam!

I had just found a script that uses perl but I think yours is better (very concise!) so I'll not bother copying it here.

Look for more scripts here:
[http://sourceforge.net/mailarchive/forum.php?forum=g-scripts-devel](http://sourceforge.net/mailarchive/forum.php?forum=g-scripts-devel)

---

### Post by charlieg on 2005-07-27
Here's a more complex script.  This one will parse directories so you can enqueue directories as well!  (Great if you have your music organised into lots of directories like I do!)

Link:
[http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Audio/queue_to_xmms](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Audio/queue_to_xmms)

Script:
```
#!/usr/bin/python
#
# simple script to recurse a subtree, find all the mp3 and queue them to
# XMMS.
#
# Please modify this script!  My python is rusty at best.
#
# Travis Hume -- travis@usermail.com
# Thu Oct 24 11:06:54 2002

import sys, glob, os, os.path

FALSE,TRUE = 0,1

def isAudioFile( f ):
    # to support additional file types just add their appropriate
    # extentions to this list (lower case).
    file_types = ['.mp3','.ogg','.wav']

    p,ext = os.path.splitext(f)
    try:
        file_types.index(ext.lower())
    except:
        return FALSE

    return TRUE


# change this to something other than None to make the script
# follow symlinks
follow_links = None

def find_mp3s( dirs=None ):
    """ finds all mp3 files rooted at dirs and returns them as a list """
    if not dirs:
        return []

    mp3s = []
    while dirs:
        if os.path.isfile(dirs[0]) and isAudioFile(dirs[0]):
            mp3s.append(dirs[0])
        else:
            found_dirs = []
            for f in glob.glob( dirs[0] + "/*" ):
                if os.path.isfile(f) and isAudioFile(f):
                    mp3s.append( f )

                if os.path.islink( f ):
                    if follow_links:
                        found_dirs.append( f )
                elif os.path.isdir( f ) and not f.endswith( "/proc" ):
                    found_dirs.append( f )

            dirs = found_dirs + dirs[1:]

    return mp3s

dirs = sys.argv[1:]
dirs.reverse()
mp3s = find_mp3s( dirs )
os.execvp("xmms", ['xmms','-p']+mp3s )
```

---

### Post by Behel on 2005-08-02
[QUOTE=Sam]Better script:
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done
```[/QUOTE]

Thanks everyone!
This script works fine for me and I can easily  enqueue my music files now! \\:D/ 

But...
First, XMMS doesn't play automatically the files after enqueuing them... How to do it?
*Edit: ok I added 'xmms --play' after the 'for' loop and it plays*

Second, how to automatically erase the previous playlist when enqueuing new songs when XMMS is not running and  how to just enqueue without erasing the playlist if XMMS is already up and running?

Finally is there a possibility that the script is ran by default instead of having to 
right-click and select the desired script?

I am finicky I know...

Thanks again all!

---

### Post by charlieg on 2005-08-03
Try changing the -enqueue to a -Q, as implied by the below:
```
  -e, --enqueue                 Don't clear the playlist
  -Q, --queue                   Add file(s) to playlist and queue
```
I guess you may need to get the contents of $NAUTILUS_SCRIPT_SELECTED_URIS into a format that does not need to be iterated over.

---

### Post by Behel on 2005-10-05
Hi,
thanks for your advice but puting -Q didn't work. For me the files are not enqueued... Just one file is played.
What is weird is that if I simply click on 1 file then the playlist is cleared. If I select several files and use the following script, the playlist is not cleared by default...
#!/bin/sh
# Enqueue a song in XMMS
#xmms --clear
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done
xmms --play

As you can see I tried to force a clear but it didn't work out...
Any idea?

---

### Post by dkirk on 2006-01-02
I was searching for a way to enqueue files in XMMS when I came across your post.  I ended up figuring it out for myself, but I'm posting it here in case others find it useful.

Right click on your audio file again and select "Propterties".  Go to the "Open With" tab.  Click on add and put in the custom command of "xmms -e".

Now start double clicking on audio files and watch them queue up in XMMS.

-- 
Later

David Kirk

---

### Post by Behel on 2006-01-17
Thanks Dkirk!
This is probably the easiest and practical solution so far... It is still required to press the play button but just once... but then I can enqueue other musics while listening...

Hem... Who knows how to stream the music to an airport express? (see my thread [http://www.ubuntuforums.org/search.php?searchid=3420820](http://www.ubuntuforums.org/search.php?searchid=3420820))

BL

---

### Post by Alex-boy on 2006-07-01
[QUOTE=Sam]Better script:
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done
```[/QUOTE]

The script from Sam did it for me, thanks a lot! ;D

In my case y sudo in Midnight Commander and past it in the root directory
in order to have it for all users.

Also, You need to restart Nautilus. In a Terminal window:
```
nautilus -q
```
So you could see it under your context menu.

Greetings.:D

---

### Post by SpanishFranks on 2006-12-02
G'day all,

Ive been using Sam's script
```

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done

```
for ages and it worked great...until now. Queued  songs show up in BMP with %20 symbols instead of spaces. Any ideas how to fix this?
Thanks

---

### Post by louisgag on 2007-04-14
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done

Unfortunately that does not work for urls in firefox

---

