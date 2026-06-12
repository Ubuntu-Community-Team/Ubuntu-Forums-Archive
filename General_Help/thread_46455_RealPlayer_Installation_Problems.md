---
title: "RealPlayer Installation Problems"
date: 2005-07-04
forum: General Help
---

### Post by wadesmart on 2005-07-04
07042005 1837 GMT-5

Since I have not been able to watch video with MPlayer, Xine or Totem, my company went out of their way to change formats to RealPlayer so I could get back to work. Unfortunatly after trying to install realplayer, things have really become messy. 

I followed the directions from the ubuntuguide for installing real but it hung and wouldnt install further than 16%. After four times, I tried something different. The Synaptic Package Manger did install RealPlayer10, put a link in the Applications/Sound & Video but, when you click on it nothing happens. I reinstalled it - same thing. 

I went to RealPlayer itself and read the install instructions and that was even worse. 

If someone has real installed I would really enjoy your input on what the problem is. 

Wade

---

### Post by arnieboy on 2005-07-04
i watch DVD's on totem, xine, mplayer and vlc, can watch all video formats in one or more of these players. I also have realplayer installed with the firefox mplayer and realplayer plugin installed. everything works perfect for me video wise. 

dont give up.. try to identify what went wrong.. thats the whole essence of using linux.
what problems did u face with xine and totem? which formats cud u not watch?

identify what executable is needed to run realplayer and run it from the terminal.
that way u will get to know is going wrong

in all possibility u have to run "realplay" from terminal. do it and let me know what errors u get.
 if it says it cant find "realplay" do a "sudo updatedb" from terminal and then type "slocate realplay" that will tell u where the realplayer executable is. go to that folder in terminal and run the realplay executable and let me know what errors u get.

from now whenever something doesnt work, run it from terminal. that will tell u whats going wrong in most cases. the more u learn to identify problems on ur own and become a better troubleshooter, u will love linux even more.

---

### Post by wadesmart on 2005-07-04
07042005 1925 GMT-5

Its just frustrating when something that seems so simple (one Windows) is so difficult on linux. Yea, Im new and grasping it all is very big thing. But, I view videos for a company for a living and I havent worked in two weeks because I cant view videos. 

Ok. Today a client emailed me a movie (giant email) and after saving it I found that I could watch it in Xine. But there is no sound. Only a burb every five seconds.

MPlayer absolutly will not play anything. It crashes almost immediatly. It starts up with the control on the right of the screen and a large blue screen on the left and then a giant "Error!" box comes up with nothing in it. Does it every time. I finally just uninstalled it. 

Totem....I dont know if it plays anything at the moment because it didnt recognize any of the formats.

I have the codecs from mplayer site in the win32 directory but xine I found doesnt see them. I found this error log in xine, and these are the message:

video_out: thowing away image with pts 79354 because its too old (diff : 3013).
...lots of those and Im not copying them all
xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: demuxer failed to start
xine: found demuxer plugin: RealMedia file demux plugin
>>>Check if another program already uses PCM<<<

snd_pcm_open() failed: -16: Device or resource busy

Ok. Ran it a few times, similar messages every time. So, it is seeing the files but something isnt starting. How do I know what demuxer is and how can I fix that? 


As for realplayer, when I click on the app to run, nothing comes on screen but I can see in System Manager that it is running, but asleep. (???) 

I just installed it before seeing your message so Im going to install it again and Ill post what I see per your instructions. 

Wade

---

### Post by wadesmart on 2005-07-04
07042005 1947 GMT-5

Ok. I installed RealPlayer from the Synaptic Package Manger. I followed your instructions. I am right now in the /usr/lib/realplay$ location and I typed realplay but nothing is happening. All I get is a odd skinny square prompt. 

There doenst seem to be any error, or anything for that matter. Also, its not running in the Process Manager either. 

Wade

---

### Post by wadesmart on 2005-07-04
07042005 1954 GMT-5

Ok. My mistake. I wrote the wrong line. 
Im in /usr/lib/realplay-10.0.4 and then I typed realplay but nothing still happens. However, I do see that it is in System Monitor. 

Its under gnome-terminal/bash/sh/realplay.bin. 

Something I dont get though. It says realplay.bin Sleeping 54mb and then has two more listings of realplay.bin Sleeping 21.1 mb each. 

No error come up, nothing at all happens. Still that odd prompt on the command line. 

Wade

---

### Post by wadesmart on 2005-07-04
07042005 2020 GMT-5

I finally got an error message. It took a long time. 

I typed in:
wadesmart@wadesmart: /user/lib/realplay-10.0.4$ realplay

Returned was:
/user/bin/realplay: line 81: 11685 Terminated               $REALPLAYBIN "$@"

Does that tell you something? 

Wade

---

### Post by arnieboy on 2005-07-04
when u say "i put the codecs in the win32 directory" i will not assume that u have put it in the correct diectory. I like newbies mentioning everything (and that includes full path names). In this case the correct path is /usr/lib/win32
Did u go to the /us/lib/win32 directory to find out whether u have all the codes listed? and when u say codecs, i also need to be sure u downloaded the correct codecs. let me know which link u used.

Firstly do u have "backports" added to your repositories? ( [http://ubuntuguide.org](http://ubuntuguide.org) )
If not, dont bother abt the rest of the post and let me know

Alright now i will go step by step.
Please follow my steps one by one.
Firstly Mplayer!
from terminal do this:
1) sudo apt-get remove mplayer*

2) sudo apt-get install mplayer-386 mplayer-fonts

3) make sure u have the windows codecs in the /usr/lib/win32 directory, Refer to the section on how to install the codecs in this howto that I written a few months back:
[http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061)

Now run mplayer from start menu--> sound and video --> mplayer
it will work fine.

next: install xine and totem-xine

1) sudo apt-get install totem-xine 

this will automatically install xine.

if the files are correctly installed already it will tell u so.

Now for realplayer:

Go to synaptic. search for "realplayer"
remove the package
then install it once again.
restart your machine.
things should work fine after that.

---

### Post by wadesmart on 2005-07-04
---07042005 2121 GMT-5

Yes, I went to /usr/lib/win32 and there are 126 items in there, received from url [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html). 

Yes, I have backports open. Did that whole thing when I first learned about that guide. 

I installed MPlayer and when I opened a file, (I had xine configured to open all files) and sure enough I had audio with video. YEA!!!!

Ok. MPlayer still wont do anything. It just opens a large error! box with nothing in it. 

RealPlayer, Im clueless on this one. No application starts. On the cmd line, it just blinks on and on. 

Right now Im in /usr/bin and I typed realplay and it just hangs. 

There are supposed to be error messages or some messages right?


Wade

---

### Post by wadesmart on 2005-07-04
07042005 2140 GMT-5

I just got an error message: 

/usr/bin/realplay: line 81:  8459 Terminated     $REALPLAYBIN "$@"

Wade

---

### Post by arnieboy on 2005-07-04
Your situation looks pretty bad to me though its difficult to answer why. I have not faced any such problems with stable packages.
I think its a problem of broken libraries which did not get installed properly when u installed ubuntu or upgraded something.
The last thing i would suggest is to go to synaptic and look under the "broken" packages section to see if there are any such packages and reinistall them.
if not, my advice for you would be to reinistall ubuntu.
what are ur machine specs?
i mean processor, archictecture etc.
I am sorry I could not be of more help but I really cant simulate the problems u are facing because in mycase everything got installed without a glitch (without my having to do any serious tweaking) and after that they worked out of the box.
I hope u have more luck when u reinstall the OS.
Good Luck.

---

### Post by wadesmart on 2005-07-04
07042005 2151 GMT-5

I just tried one of the videos to work on and there is now no sound. 
I dont know what happened. 
I had it before installing Real ... so Ill uninstall that first and see what happens. 

Wade

---

### Post by wadesmart on 2005-07-05
07052005 1046 GMT-5

A follow up from yesterday. I uninstalled RealPlayer. 
I tried Mplayer -> still nothing.
I tried Xine -> no sound. 

I uninstalled MPlayer per the instructions in this thread, then reinstalled it. 
I tried MPlayer -> still nothing. 

I installed xine. It said it was already installed.
I opened one of my downloaded videos and it played sound! YES!!!
I opened a second one, no sound. Ten more and no sound. 

I dont know what the actual problem is but after playing one video the sound is somehow lost. Something to do with codecs or something. 

Wade

---

