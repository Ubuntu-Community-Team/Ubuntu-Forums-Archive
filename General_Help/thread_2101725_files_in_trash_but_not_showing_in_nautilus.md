---
title: "files in trash but not showing in nautilus"
date: 2013-01-05
forum: General Help
---

### Post by sdowney717 on 2013-01-05
I been deleting a few files when I had root nautilus open. Following online guide said change owner to user of trash then you will see. Any way couple files in trash only show in terminal view.

```
scott@scott-P5QC:~/ram$ sudo chown -R scott /root/.local/share/Trash/[sudo] password for scott: 
chown: cannot access `/root/.local/share/Trash/': No such file or directory
scott@scott-P5QC:~/ram$ sudo su
root@scott-P5QC:/home/scott/ram# cd /root/.local/share
root@scott-P5QC:~/.local/share# ls
recently-used.xbel  zeitgeist
root@scott-P5QC:~/.local/share# rm -i -r trash/
rm: cannot remove `trash/': No such file or directory
root@scott-P5QC:~/.local/share# sudo rm -rf ~/.local/share/Trash/*
root@scott-P5QC:~/.local/share# sudo rm -rf ~/.local/share/Trash/*
root@scott-P5QC:~/.local/share# sudo rm -rf ~/.local/share/Trash/*
root@scott-P5QC:~/.local/share# sudo rm -rf ~/.local/share/Trash/*
root@scott-P5QC:~/.local/share# sudo rm -rf ~/.local/share/Trash/*
root@scott-P5QC:~/.local/share# cd /root/.local/share
root@scott-P5QC:~/.local/share# ls
recently-used.xbel  Trash  zeitgeist
root@scott-P5QC:~/.local/share# cd Trash
root@scott-P5QC:~/.local/share/Trash# ls
files  info
root@scott-P5QC:~/.local/share/Trash# 

```

I am always wondering where stuff goes when deleted and it piles up somewhere invisibly.

---

