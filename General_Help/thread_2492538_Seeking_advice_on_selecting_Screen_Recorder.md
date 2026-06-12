---
title: "Seeking advice on selecting Screen Recorder"
date: 2023-11-14
forum: General Help
---

### Post by satimis on 2023-11-14
Hi all,

Seeking advice on selecting Screen Recorder

What I'm going to acheive is as follow;

I have old Sony V8 analogue tape ripped by profession shop to digital video .mp4 format.  Certain sections need to be restored with different filters.

I run VLC media player playing the .mp4 video

**[COLOR="#FF0000"]Restoring Steps:[/COLOR]**
Tools -> Effect and Filter -> Video Effects
Essential
[check] imgage adjust
adjust Hue and Brightness simultaneously

[check] Sharpen
adjust Sigma

etc.

It works able to enhance the digital video.  However I can't save the settings because it saves them to VLC media player not on the digital video.

I'm prepared to use a screen recorder to help me recording that section..

Please recommend me a screen recorder.  Thanks in advance

Regards

---

### Post by dragonfly41 on 2023-11-14
I am not a digital video editor, but it reads to me that you need to automate your editing workflow and save settings. Or perhaps draw from a list of pre-prepared settings.
I often advocate a very simple but versatile tool named Actiona (English/French developers) which you can install from repo.
Now with this installed simply launch the GUI and create a workflow where you first launch VLC media player and then create scripts which "drive" the VLC media player app. You can do this by targetting either images or x.y positions in the open app GUI. You can also leverage hot keys. So you could create profiles to reflect your session settings if you are running through a batch. Since the Actiona code editor is fiddly I prefer writing code in Sublime Text then import variables in either a json file or ini file and in a Code box use the notation ..

include("full/path/to/js/file/videoconf.js");

This is just one UI automation idea that comes to mind.

P.S. for screenrecorder you could open FlameShot session and grab images. Again that can be automated through Actiona if you have many such actions to run.


Just to expand the possibilities Actiona can "drive" any similar complex app such as Blender, WolframAlpha .. in fact any application which can be seen on desktop. It acts as an orchestrator but the onus is on you to work out the targets to hit (buttons, menus, hotkeys etc.) and write these in an external script (js or as) to be included.  You can also addin Python scripting.

---

### Post by satimis on 2023-11-14
> **dragonfly41 said:**
> I am not a digital video editor, but it reads to me that you need to automate your editing workflow and save settings. Or perhaps draw from a list of pre-prepared settings.
I often advocate a very simple but versatile tool named Actiona (English/French developers) which you can install from repo.
Now with this installed simply launch the GUI and create a workflow where you first launch VLC media player and then create scripts which "drive" the VLC media player app. You can do this by targetting either images or x.y positions in the open app GUI. You can also leverage hot keys. So you could create profiles to reflect your session settings if you are running through a batch. Since the Actiona code editor is fiddly I prefer writing code in Sublime Text then import variables in either a json file or ini file and in a Code box use the notation ..

include("full/path/to/js/file/videoconf.js");

This is just one UI automation idea that comes to mind.

P.S. for screenrecorder you could open FlameShot session and grab images. Again that can be automated through Actiona if you have many such actions to run.


Just to expand the possibilities Actiona can "drive" any similar complex app such as Blender, WolframAlpha .. in fact any application which can be seen on desktop. It acts as an orchestrator but the onus is on you to work out the targets to hit (buttons, menus, hotkeys etc.) and write these in an external script (js or as) to be included.  You can also addin Python scripting.
Thanks for your advice.

I have invested sometimes on restoring old video.  I have been searching on AI video editors on Internet.  Up-to-now all AI video editors, one filter is applied to the whole video.  Then I have to trim the old video into setions, apply different filter to each section separately and export all edited sections.  Afterwards re-combine all edited sections as a complete video.  I can do it either on GUI or on command lines in trimming the video to sections and recombine them afterwards.  But it is time-consuming.

Later I found VLC media player which can play video in different settings (filters). If I can find a screen recorder which can start and stop recording. I just record that section which is displayed correctly.  Then play the video on VLC again with another set of settings (filter) and record another section etc.

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Ubuntu 22.04 Screenshot can do the job, recording the video but without audio

---

### Post by dragonfly41 on 2023-11-14
> [COLOR=#000000]But it is time-consuming.[/COLOR][COLOR=#000000]

That is why I thought that a UI emulator might help. 

If you can write down, step by step, your actions (An editing session) they can be automated. And I see that VLC media player allows export of settings. Even the physical positions of the "panel knobs" can be grabbed after you have tweaked.  Flameshot which I suggested is a red herring since it is difficult to transfer settings from a static image. into the GUI

P.S. I see that I have installed at some stage "recordmydesktop"

[/COLOR]https://askubuntu.com/questions/4428/how-can-i-record-my-screen

That could be driven as separate process from Actiona.

and it records audio.
[https://en.wikipedia.org/wiki/RecordMyDesktop](https://en.wikipedia.org/wiki/RecordMyDesktop)

---

### Post by satimis on 2023-11-14
> **dragonfly41 said:**
> [COLOR=#000000]

That is why I thought that a UI emulator might help. 

If you can write down, step by step, your actions (An editing session) they can be automated. And I see that VLC media player allows export of settings. Even the physical positions of the "panel knobs" can be grabbed after you have tweaked.  Flameshot which I suggested is a red herring since it is difficult to transfer settings from a static image. into the GUI

P.S. I see that I have installed at some stage "recordmydesktop"

[/COLOR]https://askubuntu.com/questions/4428/how-can-i-record-my-screen

That could be driven as separate process from Actiona.

and it records audio.
[https://en.wikipedia.org/wiki/RecordMyDesktop](https://en.wikipedia.org/wiki/RecordMyDesktop)

I have tried following steps on below YouTube video uploaded by me

**Teramo, Italy**
[https://www.youtube.com/watch?v=gRvjDhTHBV4](https://www.youtube.com/watch?v=gRvjDhTHBV4)

To remove the yellowish color on dinner gathering at about end of the video

**[COLOR="#FF0000"]Steps performed on VLC media player[/COLOR]**
Tools -> Effects and Filters
-> Video Effects
Essential
[select] Image adjust
adjusting Hue
and
adjusting Brightness

Colors
[select] Color threshold
adjusting Saturation
and
adjusting Similarity

continue playing the video.  Yellowish color removed, very simple.

You can't save the settings-> [Save]

It saves them to VLC.  You can't use this VLC play other video.

Where is the export feature on VLC?

Regards

---

### Post by dragonfly41 on 2023-11-14
> Where is export feature ...

I'm reading this for first time  ... Toolbar > Help > Help
[https://wiki.videolan.org/Documentation:User_Guide/](https://wiki.videolan.org/Documentation:User_Guide/)
Shortcuts .. exploring since this is one route from Actiona into VLC Media Player
[https://wiki.videolan.org/QtHotkeys/](https://wiki.videolan.org/QtHotkeys/)
Ctrl + Shift + W
Also ..
[https://wiki.videolan.org/index.php?search=conf&title=Special%3ASearch&go=Go](https://wiki.videolan.org/index.php?search=conf&title=Special%3ASearch&go=Go)
Search &#8220;conf&#8221;

---

### Post by satimis on 2023-11-15
> **dragonfly41 said:**
> I'm reading this for first time  ... Toolbar > Help > Help
[https://wiki.videolan.org/Documentation:User_Guide/](https://wiki.videolan.org/Documentation:User_Guide/)
Shortcuts .. exploring since this is one route from Actiona into VLC Media Player
[https://wiki.videolan.org/QtHotkeys/](https://wiki.videolan.org/QtHotkeys/)
Ctrl + Shift + W
Also ..
[https://wiki.videolan.org/index.php?search=conf&title=Special%3ASearch&go=Go](https://wiki.videolan.org/index.php?search=conf&title=Special%3ASearch&go=Go)
Search &#8220;conf&#8221;
Hi,

Thanks for your links. Now I found how to save the change to the video file, to be edited, not saving the change to VLC.

**[COLOR="#FF0000"]Steps[/COLOR]**
Start Menu -> Media -> Convert / Save -> Click Add button and browse to the file to convert -> Click Convert / Save button.

It will make changes to entire video.

Afterwards I have to combine all edited sections as a complete video.

Now I'm moving in 2 routes

**[COLOR="#FF0000"]Route-1[/COLOR]**
Make changes to all trimmed sections and consolidate them as a complete video

I'm not optimistic that there will be a good resultant video.

**[B][COLOR="#FF0000"]Why there are some sections in the .mp4 digital video ripped by the profession shop in good quality?[/COLOR]**[/B]
**[COLOR="#0000CD"]Why there are some sections in the .mp4 digital video ripped by the profession shop in extreme poor quality?[/COLOR]**
It was because the profession shop ripping the old Sony V8 analogue tape with one set of settings.  The video in the cassette were captured in different time, in differnet places and in different environment.  It won't have a good result with one set of settings ripping throughout the whole cassette.

**[COLOR="#FF0000"]Route-2[/COLOR]**
Now I resume shopping on EBay for a good second-hand V8/Hi8 camcorder.  I'm prepared to rip the old Sony V8 analogue tapes myself.  

I have been shopping on EBay for second-hand camcorder before.  My difficulty is how to get a good second-hand V8/Hi8 camcorder.  The key component is the magnet heads.  It would be difficulty for me to assess the magnet heads in shopping.  In my past shopping all sellers claimed that their second-hand camcorders were in good condition, capable capturing video on V8 tape and playing the tape back.

**[COLOR="#FF0000"]How good is the quality of the video ?[/COLOR]**

I have to taking a chance.  I have knowledge ripping analogue V8 tape to computer as digital video.  I have done ripping long time ago before my Sony V8 camcorder broken down.

Regards

---

### Post by dragonfly41 on 2023-11-15
This field of knowledge is outside my usual domain.

However I follow basic principles in any such challenge by breaking down the task into multiple processes/tasks/actions.

That is why I like using simple automation tools.  Even within Actiona you can have multiple procedures. And you can create multiple Actiona scripts each with added capability of embedding Python or other scripts as embedded resorces. Another tool I am exploring/experimenting with is Pipedream. A pipeline of tasks.

But regarding the engineering challenge of ripping (your domain of knowledge)  I have recently been exploring Wolfram Mathematica which has many advanced features in different domains (yours included).

Here for example is one discussion thread I found  ..

[https://mathematica.stackexchange.com/questions/224327/exporting-a-manipulate-animate-with-sound-to-create-a-video](https://mathematica.stackexchange.com/questions/224327/exporting-a-manipulate-animate-with-sound-to-create-a-video).

I searched "using Wolfram Mathematica engine to rip analogue V8 tape to digital video".


[https://reference.wolfram.com/language/tutorial/ImportingAndExportingVideo.html](https://reference.wolfram.com/language/tutorial/ImportingAndExportingVideo.html)


Now this is just a flare of an idea but Wolfram is one domain I feel that I must  learn across many sectors.

Returning to the earlier automation idea I would try these ideas in parallel. In fact they are complementary since Mathematica commands can be automated. That is what Jupyter Notebooks can do.

Perhaps I have thrown too much "chad" towards you.

---

### Post by HermanAB on 2023-11-15
Hmm, I always end up using the Kdenlive video editor.

---

### Post by dragonfly41 on 2023-11-15
I see that I have that editor installed too for some old experiment I can't remember. That too is I imagine is capable of being UI automated for batch work. Seems to fits well with Krusader (KDE dual pane editor) which is my prime editor which can run UserActions (scripts) on selected files. Nice toolchains can be built starting with seecting file then running UserActions (which can drive Actiona scripts) in a chain..

---

### Post by satimis on 2023-11-15
Hi all,

I doubt whether I can restore the video ripped by the profession shop?  They applied one filter throughout the complete video.

---

### Post by dragonfly41 on 2023-11-15
Perhaps you need the equivalent of the [Wayback Machine]("http://web.archive.org/").

Click on hamburger button and search Video.

---

### Post by TheFu on 2023-11-15
Wayland or X11?  Most screen recorders only work with one or the other.
How important is audio quality?  The simple X11 recorders have simplistic stereo audio recording too.  Ease of use vs complexity of features.  There's always a choice.  BTW, any screen recorder will capture anything happening in the rectangle and going through the audio card during playback, so you'll need to disable the screen saver and prevent all those little alarms/notifications common on desktops these days.  

I use simple screen recorder with X11. For important things, I'll create a new userid so prevent those pesky notifications that my normal userid has.

The good thing about professional video rips is they add that cheesy music and if these are home videos of the kids on a playground, they might speed up the running around for excellent laughs.  My older brother was pushing his sisters down the slides before they were ready to go.  50 yrs later, it is still funny.  Since I wasn't born at the time, I missed the actual events.  OTOH, seeing one of my sisters running after my brother with a baseball bat trying to beat him over the head a few years later is just a funny. ;)  

I use SSR once a week during football season to capture play-by-play data and mux that into the TV video and radio audio play-by-play.  The TV announcers suck.  SSR doesn't work with Wayland and never will.

---

