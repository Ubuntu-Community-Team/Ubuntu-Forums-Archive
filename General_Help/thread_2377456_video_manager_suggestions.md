---
title: "video manager suggestions"
date: 2017-11-13
forum: General Help
---

### Post by smokeyone2 on 2017-11-13
Hello

[FONT=arial]I am looking for ideas for a video manager - [COLOR=#24292E] - how do you keep a simple record of the video contents - I tried making the file name cover the contents but it's too long - for example a short clip of a moving car - how would you store the location/make of car/car model and engine type - am I missing something here - best idea I could think of was to make a thumbnail of the video and then treat the thumbnail as an image in digikam to set the details but there should be a better way

Thanks

PS  How do you make a new thumbnail of a video - my existing videos depict a thumbnail but I would need a copy somehow ...[/COLOR][/FONT]

---

### Post by Yellow Pasque on 2017-11-13
So you want to add tags/metadata? [https://wiki.multimedia.cx/index.php?title=FFmpeg_Metadata](https://wiki.multimedia.cx/index.php?title=FFmpeg_Metadata)
> how would you store the location/make of car/car model and engine type
You could put that info in the 'Description' or 'Comment' tags. Or, if you're using Matroska, you can create custom tag fields (another cool thing about Matroska).

---

### Post by smokeyone2 on 2017-11-14
Thank you for the advice - how difficult is it going to be to install Fmpeg

---

### Post by HermanAB on 2017-11-14
FFMPEG is probably already installed.  

Otherwise, do:
$ sudo apt install ffmpeg

which will give you most of it.  

The problem is getting the good, the bad and the ugly plugins...

---

### Post by smokeyone2 on 2017-11-14
Thank you for the     [COLOR=#000000]sudo apt install ffmpeg       how to I find/use it on my system - [/COLOR][COLOR=#000000]sudo apt install ffmpeg   installed via terminal -
Thanks
[/COLOR]

---

### Post by mastablasta on 2017-11-14
not sure how well video is supported, but have you looked at digikam. piwigo is maybe also an option as it has a plugin that will store videos (only some formats) in the database.

---

### Post by smokeyone2 on 2017-11-14
I already use Digikam but it doesn't find all my videos, only some and then does not display them - Piwigo might be good idea -
Have looked at Wwidd but unless someone can explain in detail how to install it I am stuck -

---

### Post by mastablasta on 2017-11-15
wwidd look slike an abandoned project to me. 

perhaps you can find something here: [https://alternativeto.net/software/wwidd/](https://alternativeto.net/software/wwidd/)

---

### Post by smokeyone2 on 2017-11-15
I did wonder if there was a problem with wwidd - went to [http://wwidd.com/](http://wwidd.com/)
downloaded the file and extracted it -
installed **nodejs**[COLOR=#FFFFFF][FONT=arial], [/FONT][/COLOR]**ffmpeg**[COLOR=#FFFFFF][FONT=arial], [/FONT][/COLOR]**sqlite3**[COLOR=#FFFFFF][FONT=arial], and [/FONT][/COLOR][B]vlc from terminal

[/B]But after that I cannot get it to do anything

---

### Post by coldraven on 2017-11-15
> [FONT=arial][COLOR=#24292E]PS  How do you make a new thumbnail of a video - my existing videos depict a thumbnail but I would need a copy somehow ...[/COLOR][/FONT]
You can use VLC to take snapshots at any point during playback. They can be in png or jpeg format, look in Tools>Preferences>Video
If you give the jpeg the same name as the video you could store descriptions it's EXIF data. To edit the EXIF data install pyExifToolGUI
See here: [https://hvdwolf.github.io/pyExifToolGUI/](https://hvdwolf.github.io/pyExifToolGUI/)

To view the description, right click on the jpeg, select Properties>Image
There is almost certainly a way for the command line exiftool to search entire folders for keywords but I cannot find an example at the moment.

Edit: My apologies, it seems that pyExifToolGUI can only add descriptions to files that already have some EXIF data. I just tried it with a VLC snapshot and it did not work :(
More Edit: It does work! I had stupidly tried to add EXIF data to a png file. When I realised I went back and checked the jpeg, it had the internal description that I had just created.
This happened because I had two versions of the snapshot, VLC will now only create jpeg snapshots.

---

### Post by smokeyone2 on 2017-11-15
That's the answer - thanks very much - I already have exiftool for my photos - can you help with installing [COLOR=#000000]pyExifToolGUI - I downloaded then
found the Debian folder - install - copy and paste to terminal - [/COLOR]manual /usr/share/pyexiftoolgui
scripts /usr/share/pyexiftoolgui
bin /usr

Command not found

---

### Post by Yellow Pasque on 2017-11-15
First off, could you specify what format of files you are trying to work with? I was under the impression that you were trying to work with video files, like mp4 and mkv.
> 
found the Debian folder - install - copy and paste to terminal - manual /usr/share/pyexiftoolgui
scripts /usr/share/pyexiftoolgui
bin /usr

Command not found 

That doesn't really make sense. Copy and paste from the terminal instead of trying to describe what you did.

---

### Post by Yellow Pasque on 2017-11-15
```
sudo apt-get install python-pyside libimage-exiftool-perl          #if you don't already have them
cd ~/Downloads          #for example, use whatever directory you want
wget https://github.com/hvdwolf/pyExifToolGUI/archive/0.5.tar.gz
tar xzf 0.5.tar.gz
cd pyExifToolGUI-0.5/
sudo ./install_remove.py install
pyexiftoolgui
```

---

### Post by smokeyone2 on 2017-11-16
Hello
Thank you for your help with my video files -

Downloaded okay
sudo apt-get install python-pyside libimage-exiftool-perl 
  
okay
cd ~/Downloads 

okay
wget [https://github.com/hvdwolf/pyExifToolGUI/archive/0.5.tar.gz](https://github.com/hvdwolf/pyExifToolGUI/archive/0.5.tar.gz)

All entered in terminal however I am stuck on


tar xzf 0.5.tar.gz
cd pyExifToolGUI-0.5/
sudo ./install_remove.py install
pyexiftoolgui

---

### Post by Yellow Pasque on 2017-11-16
Once again, Copy and paste from the terminal instead of trying to describe what you did. Help us help you. Saying you are "stuck" without giving us the output from the command you are stuck on is unhelpful.

---

### Post by smokeyone2 on 2017-11-16
When I mentioned stuck I meant in the context that nothing actually happened in terminal.
However third attempt and I have [COLOR=#000000]pyExifToolGUI installed and it is listed under graphics - single click and it opens -
I have loaded a thumbnail but how do I add comments to the thumbnail image.
Thanks[/COLOR]

---

### Post by Yellow Pasque on 2017-11-16
Some commands only give output if they fail. It doesn't mean you are stuck.
I've never used the program. I just gave a recipe for installing it.
Good luck.

---

### Post by coldraven on 2017-11-16
> [COLOR=#000000]I have loaded a thumbnail but how do I add comments to the thumbnail image.[/COLOR]
The first tab in pyExiftoolGUI is GPS, choose the second tab "EXIF".
Write something in the description field.
Then select how ever many jpegs you want that description to be added to.
At the bottom click "Add to selected images".

---

### Post by smokeyone2 on 2017-11-16
Thank you to everyone for the help

---

