---
title: "how do i open external subtitles from a zip file"
date: 2014-02-10
forum: General Help
---

### Post by deaton25 on 2014-02-10
hi 

would someone please give me explicit step by step instructions how to install an external subtitle onto a foreign video that 
i will play on SMPlayer. i know how to download the zip file from google and once the text version of the file is in my Download file i know how to drag and drop the text onto the video. I just don't know the intervening steps very well.
Somewhere along the line i seem to recall using a text editor...The hardest part was getting the text into my Download file
Please dont tell me to open it up like any other zip file because i have no idea how to do that
thanks

---

### Post by benjismith on 2014-02-11
to unzip the file first go to your terminal (ctrl+alt+T) and type 
sudo apt-get install unzip
then, assuming the file is in your downloads folder, type 
cd downloads
and then...
unzip (here you add the file name).zip -d downloads

then you should see both the zipped and the unzipped files on the downloads folder...

---

### Post by Impavidus on 2014-02-12
Find the zip file in your file manager, right click and choose "unpack here" or "unpack to" or something like that. Or double click and it should open in the archive manager, which has an option to unpack.

---

### Post by mattdlyons00 on 2014-02-12
As impavidus said simply extract the file first. Also if you plan to watch the movie more than once than you can simply place it in the folder with the movie and rename the .srt or .txt to the same file name as the movie.It should look something like Batman.avi and Batman.srt or txt in the same folder. 

Sorry just reread your post and noticed you don't know how to unzip a file. You should have an archive manager on your system right click the .zip file and choose open with archive manager. You should then be shown the contents of the .zip folder which should be your subtitles file just drag and drop it to your downloads folder.

---

