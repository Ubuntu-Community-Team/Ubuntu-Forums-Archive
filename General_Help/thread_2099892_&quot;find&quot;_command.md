---
title: "&quot;find&quot; command"
date: 2012-12-31
forum: General Help
---

### Post by Roasted on 2012-12-31
I have surveillance cameras on my property at home. These cameras simply save via Samba 24/7. They create directories based on year/month/day/hour. Since they record 24/7, I have a bash script which runs the find command which deletes any feeds older than 3 days. This way I preserve disk space, plus within 3 days I should have noticed if a package went missing on the step that UPS dropped off, etc.

With that being said, once that script runs I'm now left with empty directories that were previously occupied by the video feeds. So I set out to find something to take care of the empty directories. I ended up whipping up this command:

find /media/storage/surveillance/rear_cam_outside/video_feeds/ -depth -mindepth 1 -empty -exec rmdir {} \;

but I'm oddly enough still a little confused by it. So we're clearly working with empty directories as indicated by the -empty flag, which sounds borderline useless since rmdir only applies to empty directories to begin with. We're also dealing with -depth, which is nice because it starts at the deepest point and works its way up. By doing this it starts at the lowest empty directory (hour) and then comes up to day, month, etc. The part that I ran into an issue with is the fact that my parent directory would get deleted as well, because by this point it's empty.

In my test environment, I was working with the command:

find /home/jason/test/ -depth -mindepth 1 -empty -exec rmdir {} \;

but when the command ran, "test" would be deleted in the process because since -depth makes the command start at the bottom and work its way up, by then everything is gone so test is an empty directory and at the mercy of the command.

Someone suggested I plug in -mindepth 1, so I did, and sure enough it worked. I'm a little confused as to... why. What is it about mindepth that allows it to leave "test" alone and go no further? I had been fighting with maxdepth for a while but that wasn't working, because I thought maxdepth just made sense since I wanted the command to only check a max... depth. Mindepth just didn't register as being a logical choice because I'm trying to limit the depth, which maxdepth sounded right.

Anyway, if you can put down in plain English why this is to help me better understand it I would greatly appreciate it!

---

### Post by dino99 on 2012-12-31
-depth The primary shall  always  evaluate  as  true;  it  shall  cause
              descent  of  the  directory  hierarchy  to  be  done so that all
              entries in a directory are acted on before the directory itself.
              If a -depth primary is not specified, all entries in a directory
              shall be acted on after the  directory  itself.  If  any  -depth
              primary  is  specified,  it shall apply to the entire expression
              even if the -depth primary would not normally be evaluated.

[http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html)

---

### Post by Roasted on 2012-12-31
I guess what I'm confused over is... -depth isn't really referring to a specific depth at all like mindepth/maxdepth would... it just starts from the bottom and works its way up. On the flip side, mindepth and maxdepth directly effect what levels the command is executed on.

I guess I'm just not making the connection in my mind on how -mindepth 1 ensures that the directory specified in the find command is not deleted even if it's empty while everything beneath it... is.

---

### Post by Vaphell on 2012-12-31
the dir itself would be *-maxdepth 0*, 1+ affects contents

---

