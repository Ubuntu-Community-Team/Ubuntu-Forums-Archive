---
title: "What magical incantation do you need to get web browsers to play 5.1 audio?"
date: 2019-12-09
forum: General Help
---

### Post by Mythological on 2019-12-09
I am running Ubuntu 18.04.3 LTS and am trying to figure out how to do one simple thing:  Play this YouTube Dolby test video in a web browser so that sound comes out of the correct speakers, preferably using ALSA only:  [https://www.youtube.com/watch?v=PqVCPE8_ntE](https://www.youtube.com/watch?v=PqVCPE8_ntE)

What I find is that no matter what I do, sound will not come out of the correct speakers.  If I have pulseaudio disabled using pulseaudio -k, which I prefer anyway because if lets Kodi use ALSA, then I get **no sound at all** from Firefox or Chromium, and also no output devices appear in the sound settings.  If I enable pulseaudio, then my HDMI output (which is what I am using to send the sound to my receiver) shows up in the sound settings and I can select it, and the speaker tests all have sound coming out of the correct channels, BUT neither YouTube nor Chromium will play that test video correctly - the rear channels come out of the front speakers, and the low frequencies that should come out of the subwoofer are not heard at all!  If you download that same test video and play it in Kodi as a video, then the sound does come out of the correct speakers using ALSA only.  But it seems like Kodi is the ONLY thing that can deal with that situation, and even it falls down if you try to use their YouTube addon.

If I run **speaker-test --channels 6 --rate 48000 --device hw:0,3** from a command prompt all the sound comes out of the correct channels, and if I have pulseaudio enabled then just **speaker-test --channels 6** works.  But either way those browsers refuse to play 5.1 audio!

What on earth do you need to do to get web browsers to play that video (and, I assume, any video with 5.1 audio) using all six channels correctly?

---

### Post by SeijiSensei on 2019-12-10
YouTube doesn't appear to support 5.1 audio.

[https://askubuntu.com/questions/733359/does-youtube-support-5-1-surround-sound](https://askubuntu.com/questions/733359/does-youtube-support-5-1-surround-sound)

Even its pay-TV service, YouTubeTV, does not yet support 5.1, though it has been hinted for some time now.  

[https://support.google.com/youtube/thread/8776578?hl=en](https://support.google.com/youtube/thread/8776578?hl=en)

---

### Post by stereomac2 on 2019-12-16
[COLOR=#222222][FONT=Verdana]You'll need to have your video encoded using something like Dolby Digital II, which supports discrete output to whatever channel/speaker you want the audio. When you see the Dolby Digital II logo on the DVD or Blueray, and have a receiver that has the Dolby Digital logo on the back of it, then you can get 48khz per channel in 5.1.  I didn’t know this, but NETFLIX streams in Dolby Digital II, and Atmos (7.1capable) if the movie has that feature.  The newer Dolby Digital formats are called Dolby Pure, and Dolby HD, and Dolby Atmos…respectively.[/FONT][/COLOR]


[COLOR=#222222]Dolby Digital isn’t an open-source deal, so having a browser that delivers it to 6 channels will need to have the corresponding software/codec implemented.  If you have a soundcard/DSP (digital signal processor)that is multi-channel capable, you could encode the video using the AAC audio format.  AAC is a Dolby Digital codec workaround for multi-channel capability without Dolby Digital copyrights.  To play Dolby Digital content from a computer you’ll need to have a movie player/software installed that supports Dolby Digital.[/COLOR]


[COLOR=#222222][FONT=Verdana]Idealistically, you want to send a pure Dolby Digital stream to your receiver with you’re receiver set to Doobly Digital or auto (you’ll see the Dolby Digital II logo light up on your amp) to manipulate individually recorded audio streams.[/FONT][/COLOR]


In [COLOR=#222222][FONT=Verdana]any case t[/FONT][/COLOR]o begin with [COLOR=#222222][FONT=Verdana]you will need software to encode whatever discrete multi-channel format.[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]By using a 2ch stereo high definition audio stream with your video, and your receiver set to STEREO 5.1/7.1, your audio stream will be stereo up mixed to 6 channels with better than discrete audio tuning in most instances.  Mind you those channels are not discrete. [/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]I would look into hosting your video somewhere other than YouTube to support the corresponding codecs since YouTube doesn’t support the features at this time.[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Let me know if you figure out a way to do it because you’ve got me very interested.[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]TakeCare.[/FONT][/COLOR]

---

