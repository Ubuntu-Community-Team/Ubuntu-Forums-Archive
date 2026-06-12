---
title: "Audio/video default applications"
date: 2023-02-14
forum: General Help
---

### Post by habana on 2023-02-14
I have set VLC as my default Video application and Rhythmbox as my default Music application.

When I click on an mp3, it opens in VLC

When I right click on an mp3 it shows VLC as the default application. If I select "Open With...." I can select and play with Rhythmbox and also select "Always use for this file type". The file then plays with Rhythmbox but next time it plays with VLC.

If I go back to Settings and selects Videos instead of VLC it has no effect when I next try to play an mp3. It still shows VLC as the default application.

Short of purging VLC from my system (22.10), how do I sort this out?

---

### Post by monkeybrain20122 on 2023-02-14
I have not experienced such thing, but you can try this. Right click on a mp3 file, go to properties >  open with and right click on vlc in the "Recommended applications" list and choose "Forget association"

---

### Post by habana on 2023-02-15
@monkeybrain20122
Thanks for the suggestion. Unfortunately, on my system, when I right click an mp3 file  there is no "Recommended application" under properties. The applications available are the default or "Open With..." as noted in my post.

---

### Post by tea for one on 2023-02-15
Right click mp3 file > Properties > Select Open With
Do you see more options i.e. Reset, Forget, Add, Set as Default?

---

### Post by habana on 2023-02-15
@tea for one

Under properties I see the folder info,dates, permissions and audio properties. There is no "Select  Open With" under properties. I see that option directly I right click on the file. To be clear, when I right click on any mp3 file I see:
Open with VLC player
Open with....
Cut
Copy
Move to...
Copy to...
Rename
Compress
Email...
Move to the rubbish bin
Properties

I am using the standard Ubuntu files manager

---

### Post by tea for one on 2023-02-15
Left click on [COLOR="#0000FF"]Open With[/COLOR].
Do you see the options in the attachment?

---

### Post by habana on 2023-02-15
I see as attached. Note that I am unable to disable "Always use for this file type"  
[ATTACH=CONFIG]291782[/ATTACH]

---

### Post by tea for one on 2023-02-16
I've just twigged that my version of Files (nautilus) is 42.2 using Ubuntu 22.04.
Your version is probably 43.0 in Ubuntu 22.10.
Apologies for the wild goose chase - I do not know what else to suggest as I use 22.04.
Hopefully, somebody with more familiarity with 22.10 can offer some advice.

---

### Post by habana on 2023-02-16
Thanks for your interest anyway! My version is indeed 43.0 with which I have other issues. Perhaps another thread.

---

### Post by speartip on 2023-02-16
Are you actually using Ubuntu or Lubuntu as per your signature?

---

### Post by habana on 2023-02-16
Ubuntu 22.10. I don't seem to be able to add the current version to my signature.

---

### Post by coffeecat on 2023-02-16
> **habana said:**
> Ubuntu 22.10. I don't seem to be able to add the current version to my signature.

Oops. Sorry about that. A routine bit of housekeeping that was forgotten. You should be able to do so now.

---

### Post by habana on 2023-02-20
Thanks coffeecat, now updated.

A bit more information on my problem. I have a spare computer also running Ubuntu 22.10 (soon to be upgraded to 23.04 for fun). Until today I had no media files on this computer and VLC is not installed. I added an mp3 file and found that, although the default application in Settings is Rhythmbox, it actually opens with Videos. Right clicking on the mp3 file shows the default application as Videos and I can't change it. So, both computers are behaving similarly and the problem is not restricted to VLC.

---

### Post by #&amp;thj^% on 2023-02-20
Can you try this please:
In a terminal navigate to a folder w/MP3 file or just drop any .mp3 in the terminal prefaced with; .

What is the output of the command below?
If 1) is not Rhythmbox then select the desired option number.

```
mimeopen -d <file_name>.mp3
```
My example shows:
```
mimeopen -d '/home/me/Music/ALT-80/6. Alarm - Rain In The Summertime.mp3' 
Please choose a default application for files of type audio/mpeg

	1) Audacious  (audacious)
	2) mpv Media Player  (mpv)
	3) Strawberry  (org.strawberrymusicplayer.strawberry)
	4) SMPlayer  (smplayer)
	5) Enqueue in SMPlayer  (smplayer_enqueue)
	6) Other...


```
and:
```
use application #3
Opening "/home/me/Music/ALT-80/6. Alarm - Rain In The Summertime.mp3" with Strawberry  (audio/mpeg)

```
I check back, work is demanding my presence...LOL

---

### Post by tboerner on 2023-02-21
Hi habana, can you try the following:
- right click on mp3 file
- click on Open with...
- in the list you see choose your favorite application (Rhythmbox in your case I think)
- activate "Always use for this file type" at the bottom
- click Open at the top

Rhythmbox should open with that file.

If you now right click again on a mp3 file you *should* see Rhythmbox as the default under "Open with..." and it actually should work as default. In my case it does and I am using 22.10

You should not be worried that you cannot DE-activate the "Always use..."-switch, you only can activate it on the new association.

Hope that helps

---

### Post by habana on 2023-02-21
@1fallen
Rhythmbox was indeed the no.1 option which I selected and the mp3 file opened in same. When I closed both Rhythmbox and the terminal and then clicked on the same mp3 file, it opened with VLC

@tboerner
OK as far as "Rhythmbox should open with that file." It did.
However, when I right click on that or another mp3 file the default is still VLC.

Thanks both for your suggestions but no luck yet!

---

### Post by #&amp;thj^% on 2023-02-21
> **habana said:**
> @1fallen
Rhythmbox was indeed the no.1 option which I selected and the mp3 file opened in same. When I closed both Rhythmbox and the terminal and then clicked on the same mp3 file, it opened with VLC
Thanks both for your suggestions but no luck yet!

I kind of need to see that output, please:
```
mimeopen -d /path/to /.mp3

```
I knew it would show as #1, but I need to check with what yours shows...
I'm looking for this>>"2) Videos (org.gnome.Totem)"
This as well:
```
xdg-mime query default audio/mp3

```
one more:
```
xdg-mime query default video/mp4
```

---

### Post by habana on 2023-02-21
Here's what I get:

```
bill@computer2:~/mp3/clannad/macalla$ mimeopen -d indoor.mp3
Please choose a default application for files of type audio/mpeg

	1) Rhythmbox  (org.gnome.Rhythmbox3)
	2) EasyTAG  (easytag)
	3) MusicBrainz Picard  (org.musicbrainz.Picard)
	4) VLC media player  (vlc)
	5) Other...

use application #
```

and

```
use application #1
Opening "indoor.mp3" with Rhythmbox  (audio/mpeg)
```

I'm a bit confused about your last para. Where is the org folder and what exactly do I add?

---

### Post by #&amp;thj^% on 2023-02-21
Good your here, please show me this mate:
```
xdg-mime query default audio/mp3
```
and  the location should be in:
```
cat ~/.local/share/applications/mimeapps.list

```

---

### Post by habana on 2023-02-21
Here you go:

```
bill@computer2:~$ xdg-mime query default audio/mp3
vlc.desktop
bill@computer2:~$ xdg-mime query default video/mp4
vlc.desktop
bill@computer2:~$ cat ~/.local/share/applications/mimeapps.list

[Default Applications]
text/html=chromium-browser.desktop
x-scheme-handler/http=chromium-browser.desktop
x-scheme-handler/https=chromium-browser.desktop
x-scheme-handler/about=chromium-browser.desktop
x-scheme-handler/unknown=chromium-browser.desktop

```

---

### Post by MAFoElffen on 2023-02-22
I credit to 1fallen for jogging something in my memory on this...

1fallen asked the OP to do
```

cat ~/.local/share/applications/mimeapps.list

```
That is where "user only" (user specific) changed default applications choices are stored...

If you look at /usr/share/applications/defaults.list, that is where the defaults list is for "system wide" settings... Since there is no settings listed for audio and video in your 'user changed' mime.list, I would suspect that they are listed in the /usr/share/applications/defaults.list file... As when VLC was installed with sudo privileges, that is where it sets those types of settings.

A quick way to check for that would be
```

grep -i 'vlc' /usr/share/applications/defaults.list

```
Or to check what is set for what you are looking for
```

grep -i 'audio\|video' /usr/share/applications/defaults.list

```
There is a way to change that quickly with sed if you can confirm that for us...

---

### Post by habana on 2023-02-22
Thanks MAFoElffen

Response from both those commands below. Null output from the first
```
bill@computer2:~$ grep -i 'vlc' /usr/share/applications/defaults.list
bill@computer2:~$ grep -i 'audio\|video' /usr/share/applications/defaults.list
audio/3gpp=org.gnome.Totem.desktop
audio/ac3=org.gnome.Totem.desktop
audio/AMR=org.gnome.Totem.desktop
audio/AMR-WB=org.gnome.Totem.desktop
audio/basic=org.gnome.Totem.desktop
audio/flac=rhythmbox.desktop
audio/midi=org.gnome.Totem.desktop
audio/mp4=org.gnome.Totem.desktop
audio/mpeg=org.gnome.Totem.desktop
audio/mpegurl=org.gnome.Totem.desktop
audio/ogg=rhythmbox.desktop
audio/prs.sid=org.gnome.Totem.desktop
audio/vnd.rn-realaudio=org.gnome.Totem.desktop
audio/x-ape=org.gnome.Totem.desktop
audio/x-flac=rhythmbox.desktop
audio/x-gsm=org.gnome.Totem.desktop
audio/x-it=org.gnome.Totem.desktop
audio/x-m4a=org.gnome.Totem.desktop
audio/x-matroska=org.gnome.Totem.desktop
audio/x-mod=org.gnome.Totem.desktop
audio/x-mp3=rhythmbox.desktop
audio/x-mpeg=rhythmbox.desktop
audio/x-mpegurl=rhythmbox.desktop
audio/x-ms-asf=org.gnome.Totem.desktop
audio/x-ms-asx=org.gnome.Totem.desktop
audio/x-ms-wax=org.gnome.Totem.desktop
audio/x-ms-wma=org.gnome.Totem.desktop
audio/x-musepack=org.gnome.Totem.desktop
audio/x-pn-aiff=org.gnome.Totem.desktop
audio/x-pn-au=org.gnome.Totem.desktop
audio/x-pn-realaudio=org.gnome.Totem.desktop
audio/x-pn-realaudio-plugin=org.gnome.Totem.desktop
audio/x-pn-wav=org.gnome.Totem.desktop
audio/x-pn-windows-acm=org.gnome.Totem.desktop
audio/x-realaudio=org.gnome.Totem.desktop
audio/x-real-audio=org.gnome.Totem.desktop
audio/x-sbc=org.gnome.Totem.desktop
audio/x-scpls=rhythmbox.desktop
audio/x-speex=org.gnome.Totem.desktop
audio/x-tta=org.gnome.Totem.desktop
audio/x-wav=org.gnome.Totem.desktop
audio/x-wavpack=org.gnome.Totem.desktop
audio/x-vorbis=rhythmbox.desktop
audio/x-vorbis+ogg=rhythmbox.desktop
audio/x-xm=org.gnome.Totem.desktop
video/3gpp=org.gnome.Totem.desktop
video/dv=org.gnome.Totem.desktop
video/fli=org.gnome.Totem.desktop
video/flv=org.gnome.Totem.desktop
video/mp2t=org.gnome.Totem.desktop
video/mp4=org.gnome.Totem.desktop
video/mp4v-es=org.gnome.Totem.desktop
video/mpeg=org.gnome.Totem.desktop
video/msvideo=org.gnome.Totem.desktop
video/ogg=org.gnome.Totem.desktop
video/quicktime=org.gnome.Totem.desktop
video/vivo=org.gnome.Totem.desktop
video/vnd.divx=org.gnome.Totem.desktop
video/vnd.rn-realvideo=org.gnome.Totem.desktop
video/vnd.vivo=org.gnome.Totem.desktop
video/webm=org.gnome.Totem.desktop
video/x-anim=org.gnome.Totem.desktop
video/x-avi=org.gnome.Totem.desktop
video/x-flc=org.gnome.Totem.desktop
video/x-fli=org.gnome.Totem.desktop
video/x-flic=org.gnome.Totem.desktop
video/x-flv=org.gnome.Totem.desktop
video/x-m4v=org.gnome.Totem.desktop
video/x-matroska=org.gnome.Totem.desktop
video/x-mpeg=org.gnome.Totem.desktop
video/x-ms-asf=org.gnome.Totem.desktop
video/x-ms-asx=org.gnome.Totem.desktop
video/x-msvideo=org.gnome.Totem.desktop
video/x-ms-wm=org.gnome.Totem.desktop
video/x-ms-wmv=org.gnome.Totem.desktop
video/x-ms-wmx=org.gnome.Totem.desktop
video/x-ms-wvx=org.gnome.Totem.desktop
video/x-nsv=org.gnome.Totem.desktop
video/x-ogm+ogg=org.gnome.Totem.desktop
video/x-theora+ogg=org.gnome.Totem.desktop
video/x-totem-stream=org.gnome.Totem.desktop
x-content/video-dvd=org.gnome.Totem.desktop
x-content/video-vcd=org.gnome.Totem.desktop
x-content/video-svcd=org.gnome.Totem.desktop
x-content/audio-cdda=rhythmbox-device.desktop
x-content/audio-dvd=banshee-audiocd.desktop
x-content/audio-player=rhythmbox-device.desktop
bill@computer2:~$ 

```

I installed vlc conventionally via synaptic

---

### Post by MAFoElffen on 2023-02-22
Well Dang.

I still think 1fallen is on the right track. If you use mimeopen to open a file type, then it should associate that file type to the application you choose from then on.

---

### Post by habana on 2023-02-22
Didn't I do that in post #18?

The last sentence of that post makes no sense as post #17 was edited afterwards.

---

### Post by MAFoElffen on 2023-02-22
I just spun up a VM of 22.10 to test on, then installed VLC. Not elegant but:
```

mafoelfffen@ubuntu-2210-01:~$ xdg-mime query default audio/mp3
vlc.desktop
mafoelfffen@ubuntu-2210-01:~$ grep 'audio/mp3' /usr/share/applications/defaults.list
mafoelfffen@ubuntu-2210-01:~$ grep 'audio/mpeg' /usr/share/applications/defaults.list
audio/mpeg=org.gnome.Totem.desktop
audio/mpegurl=org.gnome.Totem.desktop
mafoelfffen@ubuntu-2210-01:~$ xdg-mime query default audio/mpeg
org.gnome.Totem.desktop
mafoelfffen@ubuntu-2210-01:~$ xdg-mime default org.gnome.Totem.desktop audio/mp3
mafoelfffen@ubuntu-2210-01:~$ xdg-mime query default audio/mp3
org.gnome.Totem.desktop

```
Then this 'file' is created as ~/.config/mimeapps.list, with this contents:
```

[Default Applications]
audio/mp3=org.gnome.Totem.desktop

```

---

### Post by habana on 2023-02-23
Yes! That worked, obviously substituting Rhythmbox for Totem. Many thanks for your help. I will mark this as solved.

---

### Post by #&amp;thj^% on 2023-02-23
> **MAFoElffen said:**
> I just spun up a VM of 22.10 to test on, then installed VLC. Not elegant but:
```

mafoelfffen@ubuntu-2210-01:~$ xdg-mime query default audio/mp3
vlc.desktop
mafoelfffen@ubuntu-2210-01:~$ grep 'audio/mp3' /usr/share/applications/defaults.list
mafoelfffen@ubuntu-2210-01:~$ grep 'audio/mpeg' /usr/share/applications/defaults.list
audio/mpeg=org.gnome.Totem.desktop
audio/mpegurl=org.gnome.Totem.desktop
mafoelfffen@ubuntu-2210-01:~$ xdg-mime query default audio/mpeg
org.gnome.Totem.desktop
mafoelfffen@ubuntu-2210-01:~$ xdg-mime default org.gnome.Totem.desktop audio/mp3
mafoelfffen@ubuntu-2210-01:~$ xdg-mime query default audio/mp3
org.gnome.Totem.desktop

```
Then this 'file' is created as ~/.config/mimeapps.list, with this contents:
```

[Default Applications]
audio/mp3=org.gnome.Totem.desktop

```
Thanks MAFoElffen for covering my absence, sheese I wish I had more time to spend in forums....

---

### Post by MAFoElffen on 2023-02-23
> **1fallen said:**
> Thanks MAFoElffen for covering my absence, sheese I wish I had more time to spend in forums....
No problem. I know you get busy with work.

@both --
I think I noticed a BUG with 22.10 concerning the contents of /usr/share/applications/default.list, as it relates to Rhythmbox... In that file, it associates audio files to 'rhythmbox.desktop'... But that desktop file has changed it's name to 'org.gnome.Rhythmbox3.desktop'. 

Could you two confirm that for me? If so, then I'll file a bug at LaunchPad so they can get that changed/updated... I just do not know what system to file it against. I probably need to also check Lunar, to see if it is the same in there...

EDIT: Yes, is wrong in Lunar also...

---

### Post by #&amp;thj^% on 2023-02-23
> **MAFoElffen said:**
> No problem. I know you get busy with work.

@both --
I think I noticed a BUG with 22.10 concerning the contents of /usr/share/applications/default.list, as it relates to Rhythmbox... In that file, it associates audio files to 'rhythmbox.desktop'... But that desktop file has changed it's name to 'org.gnome.Rhythmbox3.desktop'. 

Could you two confirm that for me? If so, then I'll file a bug at LaunchPad so they can get that changed/updated... I just do not know what system to file it against. I probably need to also check Lunar, to see if it is the same in there...

EDIT: Yes, is wrong in Lunar also...
Debian unstable: as shown in post #18 "1) Rhythmbox  **_(org.gnome.Rhythmbox3)_**"
If you do file a bug, my best guess here is "exo-open with"

---

### Post by MAFoElffen on 2023-02-23
"exo-open with" was not a valid installed package, so I filed it against nautilus. That way the triage team can figure out where to transfer it too. (LOL)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2008420](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2008420)

---

### Post by #&amp;thj^% on 2023-02-23
What ever am I going to do with you>>>>"exo-utils"
My bad, I need to learn to be more literal in forums, Don't I. :P
It's fixed here:
```
exo-utils/unstable,testing,now 4.18.0-1 amd64 [installed,automatic]
  Utility files for libexo

```
EDIT: WoW, I don't even see it in your bug report "exo-utils" for depends? I think you made a better guess than mine< Nuatilus**

---

### Post by habana on 2023-02-24
@ MAFoElffen

I confirm the wrong entry in my default list. After 15 years of Ubuntu I have found my first bug! But not of course the solution which is down to you guys. Thanks again to both of you!

---

