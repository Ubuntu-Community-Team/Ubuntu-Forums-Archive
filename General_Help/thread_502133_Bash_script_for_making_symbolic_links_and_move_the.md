---
title: "Bash script for making symbolic links and move the file"
date: 2007-07-16
forum: General Help
---

### Post by Kuraudo on 2007-07-16
Hello people,

I have just started to get my torrents to go again and I've started to use rtorrent since it seems to be the best one out there. Ah well, my problem now. When I download a torrent it'll be saved to a default directory. What I then want to do is to move all the files in the directory it created to my own choice of directory but at the same time make a symlink of the files in the directory rtorrent downloaded them to to the new directory I've moved them to.

Example of the process:

I download artist - album.torrent and saves it in my torrent directory.

rtorrent starts to download the torrent and it is saved in the default directory, ~/download/artist - album/

Now I move the files in ~/download/artist - album/ to /music/artist/album/ and after that I create a symlink from /music/artist/album/ to ~/download/artist - album/ so it still can be seeded.

I want to create a bash script that does this so all I have to do is type bash_script ~/download/artist\ -\ album/ /music/artist/album/

I also have a question, which do you think is better? To move the files and create a symlink for the torrent or to just create a symlink for my structure in /music/ and have the real files unorganised. I don't really know if it will make a difference as long as I have the symlinks but it's probably better to move the real files?

Thanks for your help!

---

### Post by Kuraudo on 2007-07-16
*bump*

---

