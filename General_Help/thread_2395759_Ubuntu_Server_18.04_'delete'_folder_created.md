---
title: "Ubuntu Server 18.04 'delete' folder created"
date: 2018-07-06
forum: General Help
---

### Post by Jnetty99 on 2018-07-06
Quick question if someone could help me. 

Fully switched to Ubuntu Server as my Plex server at home about a month ago. 

my home folder at /home/username/ has a plex/ folder with all the Plex files. 

Today I notice the home folder also has a delete/ folder and inside it has the folder structure of the plex folder and child folders, but no files inside. 

not sure what this delete folder is? 

I use rsync on the server to make a copy of all the files to another drive, but also use the --delete option to remove files or folders deleted on the original plex folder to keep exact copies. 

```
rsync -avh source/ dest/ --delete
```

So again any ideas and I assume safe to remove the delete folder.

---

