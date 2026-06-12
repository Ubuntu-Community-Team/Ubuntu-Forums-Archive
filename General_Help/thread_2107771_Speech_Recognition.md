---
title: "Speech Recognition"
date: 2013-01-22
forum: General Help
---

### Post by NathanMartins on 2013-01-22
Hello, I would like to know if there really is a viable speech recognition software for Linux, and before you guys start telling me, I know there is Julius, and Simon, and also Sphinx, but i have never been able to get any of them actually installed and working.
Is there any tutorial online ? Is it even possible at all ? How ? 

Remembering Im on 12.10  :p

---

### Post by tgalati4 on 2013-01-22
No.

---

### Post by NathanMartins on 2013-01-24
Well thats was blunt.....
Anyone else have any ideas

---

### Post by tgalati4 on 2013-01-24
I'm waiting for google to open up its api for its web-based voice recognition service.  It works well on Android phones and in dictating email.  There seems to be some momentum to extend it to word processing in google docs.  

Some folks have gotten older versions of Dragon Naturally Speaking working through wine.  I always found using DNS a pain because even with training, it still required a lot of editing.

The current options that you have mentioned provide some basic functionality, but require a lot of tweaking to get working properly.

So my answer stands.

---

### Post by monkeybrain2012 on 2013-01-24
I found this, costs you $ though (on my Canadian location it says Cad $11.12 ($0.12???))

[https://play.google.com/store/apps/details?id=com.nds.ubuntuspeechinput&hl=en](https://play.google.com/store/apps/details?id=com.nds.ubuntuspeechinput&hl=en)

---

### Post by NathanMartins on 2013-01-27
> **tgalati4 said:**
> I'm waiting for google to open up its api for its web-based voice recognition service.  It works well on Android phones and in dictating email.  There seems to be some momentum to extend it to word processing in google docs.  

Some folks have gotten older versions of Dragon Naturally Speaking working through wine.  I always found using DNS a pain because even with training, it still required a lot of editing.

The current options that you have mentioned provide some basic functionality, but require a lot of tweaking to get working properly.

So my answer stands.
Great, thanks, sounds  just like what I need. Well pretty soon I will  post some updates, I too have been having a look around Google's API´s  and I happened to stumble upon a speech engine, thats relatively nice,  I´ve also been in contact with Chad Barraford,  the creator of the Apple based DLA (Digital Life Assistant) that  literally speaks for itself (pun intended ), so far we've have had some  success, when executing some simple commands like you said it require  some fair amount of tweaking, but hay it was worth it. Now I´m starting  some work with Python and if all goes well I will post the links here so  y'all can see,  Thanks tgalati4 :)

---

### Post by tgalati4 on 2013-01-27
Like I said, I stand by my answer.  Unless you prove me wrong.  Good luck in your coding!

---

### Post by NathanMartins on 2013-01-27
Thanks, I´ll try my best. :)

---

### Post by theantibob on 2013-11-30
*Thread closed*

Nawww... Just kidding. But seriously? Anyone else distraught over having to pick through so many closed threads on this subject? Why (mods) close a thread just for the sake duplicating the exact same thread with the exact same questions and the exact same lack of answers/information? One of the reasons I look for answers everywhere EXCEPT the ubuntuforums first.

Here's what I came up with:

```
pocketsphinx_continuous -hmm /usr/share/pocketsphinx/model/hmm/en_US/hub4wsj_sc_8k -lm /usr/share/pocketsphinx/model/lm/en_US/hub4.5000.DMP -dict /usr/share/pocketsphinx/model/lm/en_US/cmu07a.dic
```[SUP]^[/SUP]C to exit.

will sort of work (or at least try to) as long as you at least have:

pocketsphinx-utils pocketsphinx-hmm-en-hub4wsj pocketsphinx-lm-en-hub4 gstreamer0.10-pocketsphinx

i'm not sure if gstreamer0.10-pocketsphinx is required, it's late and i'm not applying the scientific process appropriately. **EDIT:**It's not required for typical sphinx usage

as long as APT::Install-Recommends is true, you can sudo ```
apt-get install gstreamer0.10-pocketsphinx
``` to get all the dependencies for the aforementioned command to run pocketsphinx in continuous mode.

**EDIT:**To avoid installing the unnecessary gstreamer plugin, sudo:```
apt-get install pocketsphinx-utils pocketsphinx-hmm-en-hub4wsj pocketsphinx-lm-en-hub4
```

it's hilarious the the things it thinks i'm saying. **EDIT:**Probably what is happening is the audio stream from my microphone is not being transported to pocketsphinx as 16khz 16/8bit mono, causing some issues, I.E. the quality of audio I'm inputting is too high and needs preprocessing before being sent to pocketsphinx. **EDIT:**pocketsphinx_continuous accepts the argument --samprate for this. The default is 16k and i get better results using 16000 than 8000, even though the acoustic model i'm using is downsampled to 8k.


i'll be working on this from time to time, and will post more comprehensive info at a later date (pending actual success) as long as this thread isn't locked out for not being a sparkly new duplicate of the Speech Recognition necrothreads.

**EDIT:**Some useful information for multiple speech-recognition systems can be located on [the VoxForge forums]("http://www.voxforge.org/home/forums") - Recommended
also: [Sphinx wiki]("http://cmusphinx.sourceforge.net/wiki/start") and [VoxForge acoustic models tutorials]("http://www.voxforge.org/home/dev/acousticmodels/linux")<-- Info for both shinx and julius

rant2[SUB][SIZE=1]what if i was waiting to be notified of someone posting to the thread? imagine if people could type "speech recognition" into the search field and be directed to one thread, go to the last page and see what the status currently is without being confused by a hundred closed posts that all contain no info.[/SIZE][/SUB]

**EDIT: Day2 -** The output of psc (pocketsphinx_continuous) is horribly diluted by messages from stderr(2) and stdout(1), basically making this binary useful for playing around with, but not much more. There are two command line arguments (--hyp and --hypseg) that are supposed to allow the result of a transcribed statement (the HYPothesis) to be written to a file. This is passed from the hyp variable in the psc code. Unfortunately, I haven't been able to get them to work. At all.
Ideally, for my personal use, I would like psc to output the speech input cleanly to stdout. Unfortunately the output from stdout(1) looks like this:```
READY....
Listening...
Stopped listening, please wait...
000000000: that test
READY....
Listening...
Stopped listening, please wait...
000000001: testing testing testing
READY....
Listening...
Stopped listening, please wait...
000000002: testing was in to worry
READY....
Listening...
Stopped listening, please wait...
000000003: testing want to bring
READY....
Listening...
Stopped listening, please wait...
000000004: testing one two three
READY....
```There is also a *very* large amount of statistical information being output to stderr(2) even though --verbose is set to no. (i'm redirecting the stderr(2) messages to /dev/null by appending 2>/dev/null to the end the command i'm using to execute psc, like this:```
pocketsphinx_continuous -agc noise -hmm /usr/share/pocketsphinx/model/hmm/en_US/hub4wsj_sc_8k -lm /usr/share/pocketsphinx/model/lm/en_US/hub4.5000.DMP -dict /usr/share/pocketsphinx/model/lm/en_US/cmu07a.dic -fwd3g -fwdflatlw 2>/dev/null
```
What I would like to have for output is this:```
that test
testing testing testing
testing was in to worry
testing want to bring
testing one two three
```
I've been attempting to achieve this by pipeing the output of stdout(1) to tee and grep in order to redirect different types of messages. Example and results (this is the transcribed audio of my 1.5yo daughter talking):
```
pocketsphinx_continuous -agc noise -hmm /usr/share/pocketsphinx/model/hmm/en_US/hub4wsj_sc_8k -lm /usr/share/pocketsphinx/model/lm/en_US/hub4.5000.DMP -dict /usr/share/pocketsphinx/model/lm/en_US/cmu07a.dic -fwd3g -fwdflatlw 2>/dev/null |tee >(grep ... > pss) |grep :
000000000: 
000000001: hey
000000002: oh
000000003: so who most high
000000004: this yeah hi
000000005: her
000000006: i do you c.
```
the "2>/dev/null" function suppresses the output stderr(2) to the terminal as already mentioned (for the sake of ease of viewing. these messages are not part of stdout(1) unless you use 2>&1, but why would you do that here?)
the "|tee >(grep ... > pss)" function is to pass all stdout(1) messages containing "..." to a file called pss in the working directory/folder. My weak kung-fu is blatantly obvious here, as this command does not function as I had intended. All stdout(1) messages are passed to pss instead of only the state related messages (READY..., Listening..., Stopped listening, please wait...) However, this file (pss) does not contain any data until the command is terminated. I had this working properly at one point, but cannot figure out what subtle difference there is between the method that worked and this method.
the "|grep : function" filters all stdout(1) messages for lines containing the ":" character and displays only those lines to stdout(1).
I have been attempting to append the function "cut -c 12-" or "sed 's/[0-9]*\: //'" to the end of this command to remove the numeric information, the : and the space from the beginning of each line of transcribed speech. This also does not work. My weak kung-fu is to blame here. Both of these commands cause stdout to never be passed to the terminal output, even though sed works with streams.

**EDIT:** My kung-fu has improved! Kung-fu now level 0! The problem I have is that the tee command does not autoflush it's stdout buffer. stdbuff may help with this, or not.

The proper solution to this problem is to modify the code of continous.c in the pocketsphinx-utils source or write a seperate program to do what I want it to (TRANSCRIBE SPEECH TO TEXT AND OUTPUT IT TO STDOUT!) but i'm trying to make it easy for anyone using debian/*buntu to have this same result without too much effort. After all, s2t is the whole point of a speech recognition console command, right?
I think the way to make a simple command to do this is with two parts by piping stdout(1) to a file and using another command to filter the output into something usable.

I do have other things going on, so hopefully the final one-line soulution to using repository-available software to transcribe speech to text will be posted here by tomorrow at the latest. I must say, i'm very suprised that the only speech recognition solution that seems to be around for *buntu is simon, which doesnt' at all do what I want to do.

---

### Post by theantibob on 2013-12-02
Turns out the tee command modifies the stdout buffer and cannot be used for such purposes.

the oneliner to run pocketsphinx_continuous and recieve usable out is:```
pocketsphinx_continuous -hmm /usr/share/pocketsphinx/model/hmm/en_US/hub4wsj_sc_8k -lm /usr/share/pocketsphinx/model/lm/en_US/hub4.5000.DMP -dict /usr/share/pocketsphinx/model/lm/en_US/cmu07a.dic 2>/dev/null |grep --line-buffered : |stdbuf -oL cut -c 12-
```you can then pipe(|) this to another program for processing, or send it to spd_say, espeak, say, etc. for a good time.

You can expirament with these flags to see if you can get better results:

-agc - Automatic gain control for c0 ('max', 'emax', 'noise', or 'none')
-fwd3g - Use trigrams in first pass search
-fwdflat - Run forward flat-lexicon search over word lattice (2nd pass)
-fwdflatbeam - Beam width applied to every frame in second-pass flat search
-fwdflatefwid - Minimum number of end frames for a word to be searched in fwdflat search
-fwdflatlw - Language model probability weight for flat lexicon (2nd pass) decoding
-fwdflatsfwin - Window of frames in lattice to search for successor words in fwdflat search
-fwdflatwbeam - Beam width applied to word exits in second-pass flat search
-fwdtree - Run forward lexicon-tree search (1st pass)

and others listend in the pocketsphinx_* manpages

**Pay no attention to the previous post, obviously made by someone unbalanced.**

---

