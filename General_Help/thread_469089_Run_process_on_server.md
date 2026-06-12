---
title: "Run process on server"
date: 2007-06-09
forum: General Help
---

### Post by Heinrisch on 2007-06-09
I am using the latest version of the ubuntu server and I am controlling it through putty on a seperate windows computer. What I want to do is start rtorrent, start a download and then close putty and still have the rtorrent running. The later on start up putty again an access rtorrent again. How can I do that?

Thanks in advance!

---

### Post by MattJ100 on 2007-06-09
There are 2 ways, a built-in way and there is a program you can use that also allows you to do this.

1. Type the command, followed by an ampersand: &
Like: rtorrent&

When you want to switch to it type: %1
When you want to send it back to the background, it usually works by pressing Ctrl+z
To see a list of background tasks and their id, type: jobs

Method 2:
Install screen: sudo aptitude install screen
Type: screen <command>
To get back to the command prompt you can press Ctrl+a, then press d
To switch to the program again type: screen -r
(if you have more than one screen running it will give you a list of their id's. Type screen -r <id> then)

Hope this helps :)

---

