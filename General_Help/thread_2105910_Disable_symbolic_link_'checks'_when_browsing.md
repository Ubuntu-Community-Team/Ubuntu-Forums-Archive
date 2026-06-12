---
title: "Disable symbolic link 'checks' when browsing"
date: 2013-01-17
forum: General Help
---

### Post by lol on 2013-01-17
Hello

The problem is simple: by default, when you list the files in a directory (either using Nautilus or doing an ls) 'something' performs a check on all the symbolic links so see if they are dangling or not.
This is why we can see the dangling links in red in a terminal, or with a cross on the icon in Nautilus.

- Now my first question is: what is this 'something' doing the checks? Is it the tool used for browsing (Nautilus, ls) or is it a feature implemented by the 'system' (and by this I mean anything that works in the background and is not an end user application or command, such as the kernel)?

- And then, is there a way to completely disable this behavior?


Here is more background info:

Admittedly this is a nice feature to have, but I can live without it and it is really annoying when used with autofs.

The whole point of using autofs is that the resource will be mounted only if you need to access it. In my case I am using it to mount remote shares and I would like the remote server to stay idle unless I really want to access one of the share.
But if somewhere I have a link pointing to the mount point, just browsing to this somewhere causes the resource to be mounted. For example:

- /mnt/Pictures is where autofs is mounting a remote share.
- In my home, I have a symbolic link: Pictures -> /mnt/Pictures

The following steps will cause autofs to mount /mnt/Pictures:
- first run 'mount' to check that the mount point is not mounted yet.
- then run 'ls ~' or simply open Nautilus
- run 'mount' again
=> and sure enough, /mnt/Pictures has been mounted.

This whole behavior completely defeats the purpose of autofs. Even worst, if the remote server is not available for one reason or another, then 'ls ~' simply hangs and I cannot open Nautilus anymore (or at least experience huge delays).

This doesn't happen if I don't use a symbolic link. For example, if I mount the share directly in my home directory, Pictures will show up as a directory in my home (I run autofs with --ghosts) but I don't run into the problem described above. This really happen only because of the validation happening on the symbolic links.

Of course I could simply avoid using symbolic links - but then accessing the remote shares is becoming rather painful :(

Thanks a lot for any tips!

---

