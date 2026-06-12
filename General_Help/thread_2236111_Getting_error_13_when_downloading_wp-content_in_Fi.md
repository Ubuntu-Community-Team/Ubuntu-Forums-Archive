---
title: "Getting error 13 when downloading wp-content in Filezilla"
date: 2014-07-24
forum: General Help
---

### Post by cuddlefishkitty on 2014-07-24
Hi, I don't know if this has something to do with my OS Ubuntu, but I am just curious and maybe it does. I had tried disabling my machine's firewall but its still getting error.

When I am downloading the wp-content in filezilla, I on keep getting an error saying: [B]Directory '/wp-content' couldn't be created (error 13: Permission denied) 

[/B]and it also shows

*Status:    Starting download of /site/wp-content/cache/config/master.php**Error:    Failed to open "/wp-content/cache/config/master.php" for writing*
*Error:    File transfer failed*
*Status:    Starting download of /site/wp-content/cache/config/master.php*
*Error:    Failed to open "/wp-content/cache/config/master.php" for writing*
*Error:    File transfer failed*
*Status:    Disconnected from server*
*Status:    Disconnected from server*
*Error:    Could not read from socket: ECONNRESET - Connection reset by peer*
[I]Error:    Disconnected from server

[/I]
Is there someone who know what's causing this? Cos my hosting support said it's working fine in their end. And they said that it could be with my machine. I don't know much about Ubuntu since I am using it for months now, and I hope to find a solution for this.

---

### Post by TheFu on 2014-07-24
error 13 is permission denied. The userid downloading the files does not have rights to write into the target directory.  All errors like this are in the error.h file under /usr/src/include/ .... somewhere.

It has NOThing to do with the firewall.

BTW, I know ZERO about wordpress, but the save-to locations look wrong to me too.

---

