---
title: "BBC video and Linux"
date: 2007-05-13
forum: General Help
---

### Post by pbbear on 2007-05-13
When the BBC put a bit of video on any website, it becomes clear that they expect it to be opened by only one of two players:

RealPlayer or

Windows Media Player.

When I try to open such a video, Linux tries to open it with Mplayer (totem movie player), but always shows an error, and the video will not play.  I have the latest version of Mplayer installed.

I have also installed RealPlayer (Linux version).  I may not have done so correctly, but I used the .bin program and followed instructions carefully.  Also, I can call up RealPlayer and run a  video file from that, so I tink it is properly installed.

Unfortunately, the BBC download cannot find RealPlayer on my system.  Any suggestions?

pbbear

---

### Post by ss87 on 2007-05-13
From my own experience, mplayer is the best at this. Make sure you have the plugin installed, I think this can be obtained from automatix -codecs- mplayer& ff plugin. If it stalls then try and click the play in stand alone player function. It should then load the video with the mplayer plugin in the same window.

---

### Post by firebadger on 2007-05-13
I can watch all the BBC stuff fine.  I use mplayer and the mozilla-mplayer plugin.  I've also installed the additional codecs from medibuntu (win32codecs).

---

### Post by pbbear on 2007-05-13
Thank you SS87 and Firebadger.

I'm not very good at installing from source code, and I love Gdebi as a result.  I can work a .bin file, but as soon as the dependencies list grows, I get a bit disheartened.

I tried the various downloads, and at one point I thought I was on to a winner because I had the necessary codecs there in front of me.

However, the Install Readme told me to copy them into directories such as /usr/lib/codecs and when I tried to do so (using copy/paste) I was told that I did not have permission.  How do you get round such things?

Thank you for your help.

---

### Post by pbbear on 2007-05-13
I looked in GDebi and found an mplayer plug-in file, which I then installed.

The BBC videos open now in mplayer, but only give sound, not vision, so I am not much better off.  

However, I find I am learning all the time, and some day I'll be able to play videos properly in Linux Feisty.

---

### Post by firebadger on 2007-05-14
You can do all this without touching tarballs or debs yourself using Synaptic or the command line apt tools.  It's generally a much better way of doing things.  Have a look at the following...

[https://help.ubuntu.com/community/SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by itsjustarumour on 2007-05-14
> **pbbear said:**
> However, the Install Readme told me to copy them into directories such as /usr/lib/codecs and when I tried to do so (using copy/paste) I was told that I did not have permission.  How do you get round such things?

Thank you for your help.

pbbear - maybe you got this error message because you were trying to do admin tasks without being logged in with Superuser privileges. Try (in Gnome Terminal):

> sudo nautilus

enter your password, and then try cutting and pasting from there...

---

### Post by whitefort on 2007-05-14
This question keeps on coming up over and over in Linux forums.

I would strongly urge that people who are affected by this issue make a point of emailing the BBC, asking for more support for open source software.  The more of us who do this, the more likely they are to take it seriously.

---

### Post by pbbear on 2007-05-14
To all concerned:

Thank you for your help.  I have successfully downloaded Medibuntu, I understand and have used sudo nautilus.

However, I still cannot get the BBC video to play (I get the sound of it, but not the picture).  But I am not unhappy, because I am learning a lot!

Best Wishes

---

### Post by pbbear on 2007-05-14
Perhaps the following comment will help people to find a solution to my problem:

when I attempt to play the BBC video, Mplayer is called up.  One option is the "Launch this in  standalone player"

When I do this, the Mplayer plugin is called up, and gives sound but not vision.

Now I definitely have RealPlayer installed. on the Desktop.  Is there no way that I can be given a choice and "Launch this in"....RealPlayer?

If I could even save the clip somewhere, I could play it again using RealPlayer.  Any thoughts?

---

### Post by firebadger on 2007-05-14
Did you try adding the medibuntu repositories and installing w32codecs and mozilla-mplayer?  As I said before, I have no problems watching the BBC content.  For example, you could do it this way..

```
sudo apt-get install mozilla-mplayer
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O - | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install w32codecs
```

---

### Post by ss87 on 2007-05-14
This is not the most intuitive of suggestions, even though the real player codec works fine for me and many others, I also find that under preferences choosing windows media format can sometimes work.

---

### Post by pbbear on 2007-05-16
I followed the instructions carefully:

sudo apt-get install mozilla-mplayer
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O - | sudo apt-key add -
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install w32codecs
  

It seemed to install the codecs correctly (though it took a good few minutes).

I restarted the computer (always a useful thing to do, I find).

And IT WORKED!     BBC are now able to send me their videos in technicolor!

Thank you to everyone  :)   :) 

pbbear (Anthony -- in Liverpool, England)   All the best.

---

### Post by fragos on 2007-05-16
I got it to work after allowing popups from "bbc.co.uk" with the mplayer Firefox plugin.  They had given me an error message but it said I needed to enable javascript which wasn't true.  Clearly the BBC site isn't Linux friendly.

---

### Post by xadder on 2007-05-17
I'm having problems too, despite having all codecs, mplayer, realplayer, etc. I tried enabling pop-ups as recommened above, but it didn't help. I've read in another thread that about 50% of fiesty users are having problems, and nobody seems to have found a universal solution. Something strange here. And I also had the BBC working fine with edgy :confused:

---

### Post by itsjustarumour on 2007-05-17
> **xadder said:**
> I'm having problems too, despite having all codecs, mplayer, realplayer, etc. I tried enabling pop-ups as recommened above, but it didn't help. I've read in another thread that about 50% of fiesty users are having problems, and nobody seems to have found a universal solution. Something strange here. And I also had the BBC working fine with edgy :confused:

I've tried every fix on the forum to cure this BBC/RealPlayer problem and its still not working. The best I managed was getting RealPlayer to work in Opera, although it was jerky and unwatchable - something akin to an old-school slide show - and broke again after some update or other.

I've posted many times here and elsewhere.  Most responses have tried to be helpful, although some have sadly just been along the lines of "you should be ashamed of yourself for using RealPlayer, its DIRTY, you should be using an OSS media player" - not very helpful at all.

I HAVE to use RealPlayer btw, as I have to be able to fast forward and back through streams.  The other media players simply do not provide this functionality.
  

Anyway rather than listening to me moaning on and on, I suggest applying a little pressure on the BBC with regards to their site not working properly with Linux/RealPlayer! ;-)

[http://www.bbc.co.uk/complaints/make_complaint_step1.shtml](http://www.bbc.co.uk/complaints/make_complaint_step1.shtml)

Easy process, will only take you a couple of minutes...  :-D  (And yes, before you ask, I DID also file a complaint about this... ;-)  )

---

### Post by whitefort on 2007-05-18
> **itsjustarumour said:**
> 
Anyway rather than listening to me moaning on and on, I suggest applying a little pressure on the BBC with regards to their site not working properly with Linux/RealPlayer! ;-) )

I totally agree.  There seems to be a rapidly increasing number of Linux users in the world, but too many websites and software/hardware people are just going to keep on thinking it's a Windows world (with a few Mac users) unless we start politely bugging them and letting them know we exist.

It only takes a minute or two to write an email - I think we should all, in our own small way be GNU/Lunux/OSS activists.

---

### Post by itsjustarumour on 2007-05-23
> **whitefort said:**
> I totally agree.  There seems to be a rapidly increasing number of Linux users in the world, but too many websites and software/hardware people are just going to keep on thinking it's a Windows world (with a few Mac users) unless we start politely bugging them and letting them know we exist.

It only takes a minute or two to write an email - I think we should all, in our own small way be GNU/Lunux/OSS activists.

Whitefort - thanks for your comment, which was perhaps phrased more eloquently than my own!  You're absolutely right - everyone should in their own small way try and do their bit to "further the cause" of GNU/Linux/OSS...

By way of an update re my own experiences, I started another thread on this last week and have just received a reply from the BBC.  Check out [http://ubuntuforums.org/showthread.php?p=2708349#post2708349](http://ubuntuforums.org/showthread.php?p=2708349#post2708349) :D

---

### Post by hiruzzolo on 2007-06-03
I had a similar problem and I solved the problem installing the AUD-DVD codecs from the automatix for my amd64..

---

### Post by marym on 2007-10-17
The BBC is being taken to task for restricting its new video player to Microsoft users.  One of the reasons they say they are not developing a Linux/MAC platform is because they don't know how many licence players use Linux.  Does anyone have any ideas about how we could tell them?  We are not a secret society and I am sure they would be surprised if they knew how many of licence payers actually use non-Microsoft products.  

For BBC website news go to [http://news.bbc.co.uk/1/hi/technology/7047381.stm](http://news.bbc.co.uk/1/hi/technology/7047381.stm)

Mary

---

### Post by whitefort on 2007-10-17
> **marym said:**
> Does anyone have any ideas about how we could tell them?  We are not a secret society and I am sure they would be surprised if they knew how many of licence payers actually use non-Microsoft products.  

Just use the 'contact us'  link on their website, and write to let them know you're not happy about Linux users being excluded.  When i did this, I got a fairly dismissive reply, but if enough people make a fuss about it, they might start to realise that there are more than 3 or 4 of us out here!

---

### Post by FredB on 2007-10-17
> **pbbear said:**
> When the BBC put a bit of video on any website, it becomes clear that they expect it to be opened by only one of two players:

RealPlayer or

Windows Media Player.

When I try to open such a video, Linux tries to open it with Mplayer (totem movie player), but always shows an error, and the video will not play.  I have the latest version of Mplayer installed.

I have also installed RealPlayer (Linux version).  I may not have done so correctly, but I used the .bin program and followed instructions carefully.  Also, I can call up RealPlayer and run a  video file from that, so I tink it is properly installed.

Unfortunately, the BBC download cannot find RealPlayer on my system.  Any suggestions?

pbbear

You need dirac codec as a gstreamer plugin.

Look at add-remove panel. You'll find easily these codecs.

---

### Post by rockprincess on 2007-10-17
i've made the experience that VLC and kaffeine play almost anything....and are very easy to use ;)

that said, you need to have the right codecs to play them.
have a look [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs")

i realise that this post might be redundant ;)

---

### Post by expatCM on 2007-10-18
[http://yro.slashdot.org/article.pl?sid=07/10/16/1958217](http://yro.slashdot.org/article.pl?sid=07/10/16/1958217)

---

