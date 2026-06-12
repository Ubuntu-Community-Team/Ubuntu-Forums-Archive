---
title: "Always get 'partial.mp4.ts' download from iplayer"
date: 2016-12-12
forum: General Help
---

### Post by grey1beard on 2016-12-12
Running 12.04 LTS, and over the last few months I've found that any iplayer download (using terminal) always results in a shortfall of about 100MB in length.
At least I'm always warned of the result by the file name -    ######.partial.mp4.ts  .

Running the video, one of the Planet Earth 11, which I'm doing at the moment as a test, seems to be perfectly normal, but the running time indicates a shortening from 59 minutes to 37minutes.

Any help greatly appreciated,
John

---

### Post by ajgreeny on 2016-12-12
What version of get-iplayer are you using (I assume it is get-iplayer)?
Did you use the ppa at [https://launchpad.net/~jon-hedgerows/+archive/ubuntu/get-iplayer?field.series_filter=precise](https://launchpad.net/~jon-hedgerows/+archive/ubuntu/get-iplayer?field.series_filter=precise) to install it?
Finally are you aware that the default download is now HD and its size has for the past couple of months been a great deal larger than it used to be, (about 2.5GB or more per hour I think) and if HD downloads are not needed you can change that by changing the command used, as shown at [https://github.com/get-iplayer/get_iplayer/wiki/modes](https://github.com/get-iplayer/get_iplayer/wiki/modes).

To make life easier I have added several aliases to my system so I can download programs at the quality I want without the need to remember long and relatively complicated commands.
```
alias gip='get_iplayer'
alias gipg='get_iplayer -g --tvmode=tv25fps --file-prefix="<nameshort><-senum><-episodeshort>"'
alias gipgbetter='get_iplayer -g --tvmode=better --file-prefix="<nameshort><-senum><-episodeshort>"'
alias gipghd='get_iplayer -g --file-prefix="<nameshort><-senum><-episodeshort>"'
alias gipi='get_iplayer --info'
alias giplive='get_iplayer --type=livetv --get'
alias gipr='get_iplayer --type radio'
```

---

### Post by grey1beard on 2016-12-13
Hi ajgreeny, and thanks for your help.
Not sure which version, so does the following line give the answer ?

RTMPDump v2.4-n111-gitfa8646d-ppa9p2~precise

As the old grey cells are creaking a bit, I can only say that the Jon Hedgerows is familiar !

Yes, the HD versions did produce a huge jump in size, and I reduced the quality mode that I downloaded. This was successful for my last round of downloads, about three months ago, but now I continually get this 'partial' extension, and I'm not sure of my way forward.
I've also forgotten how I set the mode, so a bit of reading is now going on.
I like the idea of your aliases, and I'll have to adopt that approach.
Regards
John
EDIT  the three month gaps are because I'm yo-yoing between USA and UK every two month for the time being, hence I'm saving downloads here to view when I'm over there !

---

### Post by ajgreeny on 2016-12-13
If you simply run the command ```
get_iplayer
``` it will tell you the version you have at present, which should be **get_iplayer 2.97-ppa26** if you're using the ppa, if not I do not know which version you will have now in 12.04.

I use it a lot in 14.04 and 126.04 with no problems of any sort, so I wonder if your problem is something to do with your use of 12.04.

---

### Post by grey1beard on 2016-12-13
Yes, I have the identical version of get-iplayer.
I confess that I'm very very reluctant to move on from 12.04, having had issues in the past when I've upgraded.
I'm sure that it's always been 'operator error', but I do get confused rather more easily than I used to.
Just don't like change, I suppose. :D
See signature.

Now something really weird.
I've just repeated the download using a lower mode (sorry, didn't take note which one) and got the download about 1GB, but labelled partial.mp4.ts, then type 'message catalogue', and needless to say neither I nor the laptop have a clue as to what to do with it.
Perhaps I should purge the get-iplayer and start again.
Reluctant to do that, as the programme I'm trying to grab is the Planet Earth 2, episode 1, and I've just less than an hour to get it :(

I've just noticed in the terminal window, get-iplayer searches for an 'editorial version', and that the resulting download adds 'editorial.partial' to the file name.
I suspect this is significant. Can I prevent it searching for the 'editorial version ?
John

Just tried via versionslist to grab original, but it says that it doesn't exist, so I opted for the one that was, 'audiodescribed(?) or something like that and it downloaded about 7MB.
have now given up trying for the 1st episode, but will continue trying to solve the issue in time for the second which gives me another 7 days !

---

### Post by ajgreeny on 2016-12-13
Sorry, but none of what you are describing is known to me; get-iplayer has been working faultlessly for a long time recently in 14.04, but now in 16.04, as I have at last upgraded my system by clean installing 16.04 over 14.04. I always clean install so can not comment on upgrades.

Try using the pid number of Planet Earth II Episode 1 using command ```
get_iplayer --pid=p048sflc
```which is the current pid at this moment.

---

### Post by dinkypumpkin on 2016-12-13
Add
```
--ffmpeg=/usr/bin/avconv --tvmode=hls
```
to your get_iplayer command. Add those options permanently to get_iplayer preferences with:
```
get_iplayer --prefs-add --ffmpeg=/usr/bin/avconv --tvmode=hls
```
For the best solution, you should acquire a modern version of ffmpeg to replace the antiquated version installed with libav-tools. See the release notes for get_iplayer 2.96 for an explanation.

---

### Post by grey1beard on 2016-12-13
Thanks both, but in both cases the result was still to download a file containing original.partial.mp4.ts , and my experience has been that this always results in a large chunk of the programme missing at the end.
I'm giving up for this evening, but will consider what next tomorrow.
John

---

### Post by #&amp;thj^% on 2016-12-13
I just got done with:
```
get_iplayer --type=livetv --pid="b00jzwsf"
```
For Episode 1 Complete and Excellent Quality. Also on 16.04.1 with version "get_iplayer 2.97-ppa26"
I'm not trying to rub salt into a wound here.

---

### Post by dinkypumpkin on 2016-12-13
Sounds like you have some peculiar problem killing the downloads, but there is no way to tell with out seeing the --verbose output from get_iplayer. I can tell you that Planet Earth II downloads fine in HD on both 12.04 systems I have within reach, using the options I suggested. Perhaps try using --tvmode=flash and let rtmpdump handle the downloading. Different media streams might net different results.

Also, "[COLOR=#000000]original.partial.mp4.ts" at the end of the file name doesn't necessarily mean the file is truncated. It may just signify that your avconv or ffmpeg is failing. get_iplayer leaves the .ts file behind if it can't be remuxed to MP4. You can use --raw to skip the remuxing and keep the .ts file.[/COLOR]

---

### Post by grey1beard on 2016-12-14
That's ok, I like the taste of salt !
John

---

### Post by grey1beard on 2016-12-14
hi diddypumpkin,
Thanks for your input.
you give me two possibilities in your first paragraph. 
Could you be kind enough to spell out the code, and I'll try each in turn, I guess the first is for your examination.
Will it just be *get-iplayer --verbose*, or do I need to append an actual program ?

My next thought runs along the lines of purging the whole of my get-iplayer(how?) and then re-loading the ppa.
John

---

### Post by grey1beard on 2016-12-14
Just tried get-iplayer --verbose and it looks like its downloaded the Encyclopedia Brittanica ! So I guess that is not what is required.

---

### Post by dinkypumpkin on 2016-12-14
If your ffmpeg or avconv is failing and leaving the .ts file, it should be noted in the output even without the --verbose option (a "conversion failed" message). However, the --verbose option is exactly what is required if you want to diagnose a problem. Yes, it creates a gargantuan spew, but if you can save it in a file and upload it somewhere, I'll take a look. Before you do that, check the .ts file in a media player like VLC to confirm that it is in fact truncated. But really, the best solution is to follow the instructions in the get_iplayer 2.96 release notes to install a working version of ffmpeg.

Try the latest episode of Planet Earth II:

```
get_iplayer --pid=b0861m8b --ffmpeg=/usr/bin/avconv --tvmode=hls --verbose > hls.txt 2>&1
```

The other option I suggested, using RTMP (Flash) media streams:

```
get_iplayer --pid=b0861m8b --ffmpeg=/usr/bin/avconv --tvmode=flash --verbose > flash.txt 2>&1
```

---

### Post by grey1beard on 2016-12-16
Just tried both of the code lines that you supplied, but each one seems to sent terminal to sleep. A brief blinking of the cursor, followed by utter stillness !
I'll now re-read and follow your advice at the beginning of your #14 post and see if that sorts me out.
many thanks
Jhon

---

### Post by grey1beard on 2016-12-16
Just downloaded 'cities' and then tried it on VLC, and success !
The file plays right to the end.
Curiously, the downloaded file was stated to be 1003 MB, but it downloaded 1049MB. 
I should worry, I'm just grateful for the result.
In my home folder, the file type is 'message catalogue', and if I double click on it, my laptop can't open it, unless I tell it to use VLC.
I've included the following from the Terminal window, as it might also give a pointer to what's happening.

> 
INFO: Begin recording file: /home/john/Planet_Earth_II_-_6._Cities_b0861m8b_original.partial.mp4.ts
INFO: Recorded: 1042.03MB in 01:09:26 at  2049kbps to /home/john/Planet_Earth_II_-_6._Cities_b0861m8b_original.partial.mp4.ts
INFO: Begin converting file: /home/john/Planet_Earth_II_-_6._Cities_b0861m8b_original.partial.mp4.ts
Unrecognized option 'stats'
Failed to set value '-i' for option 'stats'
INFO: Command exit code 1 (raw code = 256)
WARNING: Conversion failed - retaining /home/john/Planet_Earth_II_-_6._Cities_b0861m8b_original.partial.mp4.ts

Thanks for your help, thus far.
I'll try more episodes tomorrow, and post the result before I mark the thread as solved.
John

---

### Post by dinkypumpkin on 2016-12-16
> **grey1beard said:**
> Just tried both of the code lines that you supplied, but each one seems to sent terminal to sleep. A brief blinking of the cursor, followed by utter stillness !

That was kind of the point. It seems you may be new to the shell, so if nobody else comes along to explain this, google "how to redirect stdout and stderr".
> **grey1beard said:**
> Just downloaded 'cities' and then tried it on VLC, and success ! The file plays right to the end. Curiously, the downloaded file was stated to be 1003 MB, but it downloaded 1049MB. 

As I suspected, get_iplayer itself is working fine. File sizes are only estimated before download, so not necessarily bang on the final size
> **grey1beard said:**
> 
In my home folder, the file type is 'message catalogue', and if I double click on it, my laptop can't open it, unless I tell it to use VLC.

Those .ts files are MPEG Transport Stream files, a streaming format. You may need to change the default file association to open with VLC.
> **grey1beard said:**
> 
I've included the following from the Terminal window, as it might also give a pointer to what's happening.

It's as I've already said: Follow my advice in #7. Or if you're content with .ts files and some harmless warning messages, there is no need to do anything.

EDIT: And as I said in #10, you can use --raw to keep the .ts file and avoid the warning messages.

---

### Post by grey1beard on 2016-12-17
Hi dinkypumpkin, (sorry for earlier misreading!) 
Thanks for your patience, and advice.
When my brain clears from sleep, I'll go back and read #7, and follow through, but breakfast first.
Regards
John

---

### Post by grey1beard on 2016-12-20
Have now sorted out the ffmpeg problem, and the latest download has converted as it used to, with the 'partial' tag disappearing.

---

