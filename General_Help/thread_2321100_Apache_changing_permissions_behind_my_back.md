---
title: "Apache changing permissions behind my back?"
date: 2016-04-20
forum: General Help
---

### Post by bob173 on 2016-04-20
First, the scenario. We are trying to run Tickets computer assisted dispatch. It uses Apache, MySQL, and PHP. One of the tasks within Tickets is downloading Open Street Map tiles for off-line use. The format for the files is /zoom/x/y.png. Zoom is the zoom level, x is the column, and y is the tile.

Now, the problem. When all the tiles for the selected area are downloaded, the attributes for the zoom and x directories are changed, clearing the "x" bit and causing difficulty accessing the tiles. When I asked the software developers about it I was told it was a function of the server; that the program does not set or change the attribute bits (the program in their words is OS-agnostic).

It doesn't matter if I let the application create the necessary directory (e.g., 15 for zoom level 15) or I create it using mkdir before starting Tickets. The attributes still are changed when the download is completed.

I assume there is a setting somewhere in Apache's configuration that will inhibit the changing of the attributes, but I can't figure it out. Help, please!

---

### Post by SeijiSensei on 2016-04-20
Open a page that references the tiles in a browser and view its source (e.g., use right-click in Firefox).  Post an example of the HTML code that references a tile inside [noparse]```

```[/noparse] tags.  There may be simple ways to fix this, but we need to see a URL first.  Also please give us the corresponding full path to the tile image in the Linux filesystem like /path/to/images/zoom/x/y.png.

---

### Post by bob173 on 2016-04-21
Quick answer to your second request: /var/www/html/tickets/_osm_tiles/[zoom]/[x]/y.png

In spite of the developer's assertion, I found in the source code governing the fetching of OSM tiles calls to the php function chmod(). The problem would appear to be in the program, not the server. I'm still trying to figure out the exact action the program is taking. It appears that it is not always correctly recognizing a file name as a directory name. 
Sherlock Holmes back to work.

Thanks for your help.

---

### Post by SeijiSensei on 2016-04-21
That sounds like a kludge to me to fix ownerships if something goes awry.

If the program downloads the tiles to directories the www-data user can write to, which I presume it can, it should have no problem reading the files that it writes.  Try commenting out the chown lines in the PHP code with a hash mark ("#") at the beginning of each line, then run the scripts again and see if they work.

I'd set the ownership of  /var/www/html/tickets/_osm_tiles/[zoom]/[x]/ and its parents to user:group www-data, with 750 privileges if you're concerned about security.  Perhaps these directories have to be created on-the-fiy when new zoom or x coordinates are referenced?  If /_osm_tiles/ has owner www-data with write privileges it should be able to create those directories without a problem.  If it still has issues, you can use the SUID and SGID bits on /_osm_tiles/ to have any files and directories created below it inherit the ownership and permissions of the directory itself.  If the above suggestions don't work, try this:
```

cd /var/www/html/tickets
sudo chown www-data:www-data _osm_tiles -R
sudo chmod 4750 _osm_tiles -R

```
and see if that works any better.  (The "-R" switch "recurses" down the directory tree from the specified origin and changes the ownership or permissions of every file and directory it finds.)

---

### Post by bob173 on 2016-04-25
During the download process, the program creates the necessary directories with the correct permissions (0750) and the tile files with permissions 0644. When the download is complete, it calls chmod_r().

The function chmod_r() recursively descends the directories under ../_osm/tiles, setting the permissions of directories to 0750 and those of the tiles to 0644. If I comment it out as suggested, the permissions remain correct.

chmod_r() calls is_dir() to determine if the entity being called is a file or a directory. It appears that the return from that call is always FALSE; hence changes the permissions to 0640. My programming skills are rusty (I haven't been an active programmer for about ten years) but I cannot see anything "wrong" with the function. Probably moot at this point since commenting out the call to chmod_r() eliminates the problem.

The ten-line function is as follows:

function chmod_r($Path) {
    $dp = opendir($Path);
    while($File = readdir($dp)) {
        if($File != "." AND $File != "..") {
            if(is_dir($File)){
                chmod($File, 0750);
                chmod_r($Path."/".$File);
                } else {
                chmod($Path."/".$File, 0644);
                }
            }
        }
    closedir($dp);
    }

---

