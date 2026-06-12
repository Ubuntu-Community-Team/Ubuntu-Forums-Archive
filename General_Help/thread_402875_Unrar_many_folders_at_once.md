---
title: "Unrar many folders at once"
date: 2007-04-06
forum: General Help
---

### Post by grizzly666 on 2007-04-06
Does anyone now how to unrar many folders at once?
Like you do on winrar in win.
Say that i have 10 folders with movies or games that i want to unpack in one go.
Like it is now i can only unpack 1 folder or 1 archive at a time.
Can it be done on linux at all?

I have tryed to install winrar in wine.
But all i get is a window that say that wine needs to download active x.

"this application is requesting an activex browser object but the mozilla activex control is curently not installed.
Do you whis to download and install it?"

And i can answer yes or no.
If i answer yes a download window comes up but never starts to download i have left it open for several days.
But nothing happens.
Untill i force the shutdown.
If a answer no wine just shut down.
And in both cases no mapp or files is copied into wine/drive_c/program_files

Anyone got any ide what do to?

---

### Post by Maestro23 on 2007-04-06
Install rar and unrar from the repositories.  No need to go thru wine.

> sudo aptitude install rar unrar


If they can't be found, add extra repositories:  [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by raja on 2007-04-06
You can enable multiverse repositories and then install rar. Then you should be able to use it from the command line or with a frontend like ark or 7-zip.

---

### Post by Jose Catre-Vandis on 2007-04-06
Three options:

Place this script in your nautilus scripts folder.
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
  for arg
  do
      gnome-terminal -x /usr/bin/unrar e -y "$arg"
  done
```
In Nautilus select all the rars you want, right click and chose the script
unrar will handle each one in turn, asking for passwords if needed.
Note: no spaces in filenames!

or



```
unrar e -y "*.rar"
```

(e -> extracts to current directory, -y -> suppresses confirmations etc)

Go to this post and read through, which you would have found with a search :-)

[http://ubuntuforums.org/showthread.php?t=161687](http://ubuntuforums.org/showthread.php?t=161687)

---

### Post by qpieus on 2007-04-06
Post #2 in this thread has some code to extract multiple rars, but I'm not sure it will put the extracted files into their own directories. Give it a try.

[http://ubuntuforums.org/showthread.php?p=1481995]("http://ubuntuforums.org/showthread.php?p=1481995")

---

### Post by grizzly666 on 2007-04-06
To Maestro23 and raja.
I have unrar and can unrar.
But i was asking about how to unrar several folders or several files (not split files) in 1 go.

And thanks to Jose Catre-Vandis and qpieus for answerd.
But i did read those post already.

I should have said some more things in my first post.
that i rarely or never extract to the same folder that the rar files is in.

And when i have selected more than 1 files or folders.
I want to have a window asking where to extract.
The reason i want this is i have folders named movies and then in movies genre folders like comedy,fantasy,etc.
And the same with games,tv,ebooks,manuals and so on and on.
What i did now when i was waiting for answer was i did some shell script.
And i have 5 diffrent shell scripts now each pointing to a unpack folder on 5 diffrent hd.
And then i have to move them into the rigth folders.

And if i wanted to add a shell script for every folder i want to extract to then it would be to many of them.
And it would take time to find the right script for the time being.

So i do not want any shell script at all or maybe 1 that brings up some browse window to choose where to extract.
And then it should work for the diffrent folders or files that i have selected.

Hope you guys understands what i want:lolflag: 
At least i do:mrgreen: :mrgreen: :mrgreen: 

Or i want to get winrar to work.
But cant get it to install.
Have tryed 5 diffrent verisions now and its the same with them all.
Anyone nows what or why wine is asking for mozilla active x control.
Or where to get it?

Before i did this thread.
I was extracting a couple of complete tvshows that was rared and episodes was in Separately folders.
Totally around 280 diffrent episodes each unrared 1 and 1.
Untill i got feed up](*,) ](*,) ](*,)  and ftp to a win box and unpacked then ftp back again.
It took about 1 min longer per ep to doo that but i didnt have to sitt and watch all the time and start the next ep after 1-2 min.

---

### Post by bashologist on 2007-04-06
Here are some simple things I've made for myself to unrar files. 
```
# Unrar archives directly into current folder
unrar x *.rar

# Unrar all archives making a seperate folder for each unrared file
for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
```

---

### Post by grizzly666 on 2007-04-06
Thanks but not really what i was looking for.
I have 6 hd in this computer.
And 1 is download and system disk and the rest share,backup disks.
And when i unrar it is very,very unlikley that i unrar to the same folder or separate folder for each file.

Example:
1 tvshow ex the simspons wich have 18 seasons and counting.
I have the first 17 seasons in folders like this
simpsons/season1/episode1
simpsons/season1/episode2
simpsons/season2/ep1
simpsons/season2/ep2
and so on.
I want to click or rclick on the folder simpsons.
And then choose where to save all the unrared files (not on the same hd or folder).
As i have 5 disks to choose from then maybe the disk i have all tvshows on is full or dont take all the ep of simspons (too many GB).

All disk is like this.
/movie/action
/movie/comedy
Tv/action
Tv/comedy
Games/action
Games/comedy
Prg/media
Ebook/comedy
And so on.

My download disk is the same.
In the download folder.
/movie/action
/movie/comedy
Tv/action
Tv/comedy
Games/action
Games/comedy
Prg/media
Ebook/comedy
And so on.

I use to unrar when a folder is getting to be big (around 20GB or so)
And therfore it can take a long time to unrar to and from the same place.

---

### Post by qpieus on 2007-04-06
> **bashologist said:**
> Here are some simple things I've made for myself to unrar files. 
```
# Unrar archives directly into current folder
unrar x *.rar

# Unrar all archives making a seperate folder for each unrared file
for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
```

Nice job bashologist. I can see why your nic is bashologist. Your code worked for me to unrar multiple rar to there own subdirs. I've been looking for that for a while Can a similar code work for multiple zip files? I assume the answer is Yes :), I'm just not sure how to modify the code. I think putting "unzip" where "rar" is will work. I will need to substitute the appropriate unzip argument for "unrar x" I guess.

Back to grizzly's question though...

If you are using KDE, there is a konqueror servicemenu (right-click menu) that does what you want - right click on a rar and an "extract to" dialog box will pop up asking where you want the extracts to go, and you can direct it to anywhere you want. Look here:
[http://www.kde-apps.org/content/show.php/KUnRAR?content=33751](http://www.kde-apps.org/content/show.php/KUnRAR?content=33751)

---

### Post by grizzly666 on 2007-04-08
Thanks but i run gnome :(

---

