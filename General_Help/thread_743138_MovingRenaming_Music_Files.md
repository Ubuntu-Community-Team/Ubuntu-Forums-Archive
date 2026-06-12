---
title: "Moving/Renaming Music Files"
date: 2008-04-02
forum: General Help
---

### Post by AustinMatherne on 2008-04-02
Hi, I'm new to Kubuntu, I copied over my music collection in iTunes to an external hard drive and after installing Kubuntu I moved the iTunes collection into a folder named Music under /home. Problem is iTunes sorts the music by directory "My Documents/My Music/iTunes/Artist/Album/song files" and now under Kubuntu its "/home/Music/Artist/Album/song files" and I would now like to make it "/home/Music/song files". 

I'm sure there's a pretty simple terminal commend to do this, there's just one problem, I have songs with the same name under different albums, so I would need to attach the Artist's name and Album to the beginning of the music file names.

I have just under 200 GB's in music so if someone could help me out here, that would be great.

Thank you,
Austin

P.S. I'm using Kubuntu 7.10, 64 bit if that matters at all.

---

### Post by warp99 on 2008-04-02
Sure very simple:

```
mv /home/Music/Artist/Album/song\ files /home/Music
```

then remove the Artist directory:

```
rm -r /home/Music/Artist
```

make sure the directory is **empty** first. You may want to rename the directory "song files" to "song_files" so you don't have to use the backslash when changing directories.

```
mv /home/Music/Artist/Album/song\ files /home/Music/song_files
```

You can also do this in Dolphin file manager with the cut and paste function or in Konqueror file manager with the move files option. Both use the "right click" convention

Please see my signature for move helpful tips.

---

### Post by warp99 on 2008-04-02
> **AustinMatherne said:**
> 

I'm sure there's a pretty simple terminal commend to do this, there's just one problem, I have songs with the same name under different albums, so I would need to attach the Artist's name and Album to the beginning of the music file names.

I didn't read this part. You can retag the files using MusicBrainz tagger Picard so the name of the artist can be put in-front of the song:

[http://musicbrainz.org/doc/PicardDownload](http://musicbrainz.org/doc/PicardDownload)

Better yet you already have a powerful media player installed called Amarok that will read the directories and sort it's database to the location of your music so you don't need to change a thing, then you can export or import files from you iPod or mp3 player very easy from Amarok:

[http://amarok.kde.org/](http://amarok.kde.org/)

Edit:

I use Amarok exclusively since it's the best music media player and manager that I've seen and that list includes Windows Media Player and iTunes.

---

### Post by AustinMatherne on 2008-04-02
Sorry, I didn't clarify on the folder structure.

There are multiple "Artist" folders under "/home/Music" one for each artist in my music library. There are also more then one "Album" folders in each "/home/Music/Artist" folder.

Here is an example, the folder "/home/Music/The Beatles/Abbey Road/" contains the song files **"Come Together.mp3"**, "Something.mp3", "Maxwell's Silver Hammer.mp3", "Oh! Darling.mp3", "Octopus's Garden.mp3", etc, etc, etc.

and for another example, the folder "/home/Music/The Beatles/The Beatles 1/" contains the song files **"Come Together.mp3"**, "Love Me Do.mp3", "From Me To You.mp3", "She Loves You.mp3", "I Want To Hold Your Hand.mp3", etc, etc, etc.

Notice how both the "Album" folders "Abbey Road" and "The Beatles 1" contain "Come Together.mp3". So if I were to copy all of the song files by hand (which would take forever) I would end up overwriting one of the "Come Together.mp3" with the other one.

Therefor, I need to rename them to "The Beatles - Abbey Road - Come Together.mp3" and "The Beatles - The Beatles 1 - Come Together.mp3".

(or preferably "the_beatles_-_abbey_road_-_come_together.mp3" and "the_beatles_-_the_beatles_1_-_come_together.mp3")

and then copy them to the "/home/Music/" directory.

I hope that's not to confusing,
Austin



Edit:

Actually, that's sort of what I plan to do. I'm trying to use Picard to put the correct ID3 tags on my music collection. The problem is Picard doesn't seem to be able to read sub directory's and seeing as how I have over 2000 Album directory's I don't want to have to do them individually.

iTunes also adds a bunch of junk files to the album directory's that I would like to be able to delete, but again, I don't want to have to go through each one individually, as it would take months to finish.

---

### Post by warp99 on 2008-04-02
If you did it manually it would take you a **very** long time with 200 GB unless you had a script to automate this. My scripting capabilities are limited, so someone else may be able to help you in that department.

Now if you use Amarok it will automatically catalog all of your music according to the location if that's what you want to do, no need to change anything. So you can leave at the files were they are and Amarok will catalog them in its database the same way as iTunes did. 

So it depends on what are the advantages of placing the files in /home/Music verses the directory structure that iTunes had. My guess is that it would be more work then it's worth, but you can do it with the correct script. Hope this helps.

---

### Post by AustinMatherne on 2008-04-02
Wow, I feel stupid.

Picard does support reading from sub directory's, I just didn't realize it.

Thanks for your help,
Austin

P.S. Does Amarok move the files into it's own folder structure, or does it leave them as they are?

---

### Post by pointone on 2008-04-02
I wanted to do this exact same thing a while ago, and wrote my own Python script to accomplish it. Picard is nice, but I already had everything tagged correctly--Picard just tended to screw things up. All I wanted was to rename files. See my post [here]("http://ubuntuforums.org/showpost.php?p=4186915&postcount=9") for a link to my script.

It doesn't support stepping into subdirectories yet. I haven't worked on it for a while now, but I'm still planning on updating it. In fact, my music collection is starting to get a bit messy again, so I may be finishing it up soon.

What I did was simply move all my files into the same directory "/share/music", making sure no files were overwritten. Then I ran my script, renaming all the files. Some duplicate files with the same name (different albums) weren't moved, so I was able to now move them since the other file (from the other album) had been renamed. A second run of my script fixed everything up all nice-like. For a couple files that were triples or quadruples, I ran my script manually on them.

---

### Post by warp99 on 2008-04-02
> **AustinMatherne said:**
> 

P.S. Does Amarok move the files into it's own folder structure, or does it leave them as they are?

Amarok leaves them as they are, it only updates its database to reflect the location of the files. The catalog structure in Amarok is the same as the file structure in iTunes (Artist/Album/Song).

Edit:

Any songs you import through Amarok can be stored in any fashion you like in any directory you choose. Amarok will update its database and list them as Artist-Album-Song. In other words Amarok will sort out the mess that iTunes did. So you can leave it as a jumbled hodge-podge of files, then change the structure at your leisure.

---

### Post by warp99 on 2008-04-02
Another thing you could have done was to catalog all of the music on the original drive with Amarok, then set up a "Generic Audio Device" with a mount point to your new location /home/Music. 

Amarok would have copied the Music from the original drive to the new location with the file structure you wanted by settings the parameters in the "Generic Audio Device" configuration. When the music was transferred you would change the old music directory in Amarok to the new directory in /home/Music. Amarok would then update its catalog to reflect this. 

See everything in a *nix system is seen as a "file" or "directory" so you can make the mount point anywhere you want. It's a neat little trick on transferring files. But since you already copied the music I would suggest if you want to change the directory structure to use the python script that another poster suggested.

---

