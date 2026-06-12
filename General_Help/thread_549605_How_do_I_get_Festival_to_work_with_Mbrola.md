---
title: "How do I get Festival to work with Mbrola?"
date: 2007-09-12
forum: General Help
---

### Post by kentl on 2007-09-12
Hi,

I've installed the text to speech application Festival using "apt-get install Festival". However I want it to use Mbrola for the speech synthesizer, as those voices are MUCH more natural.

There is a guide for those who installed it by untaring it. I'm not good at that. I guess it means installed it from source. But as I did not, I don't really know what to do.

The guide is located at: [http://www.cstr.ed.ac.uk/projects/festival/mbrola.html]("http://www.cstr.ed.ac.uk/projects/festival/mbrola.html")

If you haven't used it you should try it! The MBrola voices sounds EXCELLENT, go [here]("http://tcts.fpms.ac.be/synthesis/mbrola.html") and click on one of the flags for an example.

I am really in need of some help here. There are a few threads mentioning Festival on this forum. But they don't hold much information about using Mbrola with it, in fact, none. :(

---

### Post by kentl on 2007-09-12
If you know Spanish I think the solution is in this tutorial. As I don't I'm a bit afraid to try the commands given, when there's no explanation I can understand. Could someone who knows Spanish please help out?
[http://huevon.blogspot.com/2006/01/tts-text-to-speech-usando-festival-y.html](http://huevon.blogspot.com/2006/01/tts-text-to-speech-usando-festival-y.html)

---

### Post by kentl on 2007-09-13
I didn't get the Spanish tutorial to work. But I might have messed something up in it as I don't know Spanish.

I'll try to follow: [http://www.cstr.ed.ac.uk/projects/festival/mbrola.html]("http://www.cstr.ed.ac.uk/projects/festival/mbrola.html")

And if I get it to work I'll post it here and perhaps in the "How To":s, as the voices in Mbrola really are excellent.

---

### Post by kentl on 2007-09-13
Now I actually got it working! :-) It's defenitely not as robotic, this new voice. If anyone's interested in knowing what I did (I combined the Spanish tutorial with the installation web page linked to earlier) answer here, in case I'll post a quick guide to what I did in English. :-)

---

### Post by D.S.E on 2007-11-25
Yes, please. I am interested in your guick guide :)

---

### Post by MonkeeSage on 2008-04-10
Here's what I did to get us1_mbrola, us2_mbrola and us3_mbrola installed.

*[color=green]NOTE:[/color] If you have the space and bandwidth to spare, you can get even better sounding voices for festival by installing the CMU Arctic voices. A guide for doing this on Ubuntu is [thread="677277"]here[/thread].*

*[color=green]NOTE:[/color] I've started a HOWTO with detailed instructions on how to install all of the available English voices for festival: MBROLA, CMU Arctic, and Nitech HTS. [thread="751169"]HOWTO[/thread].*

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

**[size="4"][color="#3b3b3b"]Getting ready:[/color][/size]**

Make sure all of the prerequisite packages are installed:

```

sudo apt-get install festival festlex-cmu festlex-poslex libestools1.2 unzip

```


**[size="4"][color="#3b3b3b"]Step 1:[/color][/size]**

Download the mbrola deb package, voices, and festvox wrappers to a temporary directory (about 20 megs in all):

```

mkdir mbrola_tmp
cd mbrola_tmp/
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/bin/pclinux/mbrola3.0.1h_i386.deb
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/dba/us1/us1-980512.zip
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/dba/us2/us2-980812.zip
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/dba/us3/us3-990208.zip
wget http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_us1.tar.gz
wget http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_us2.tar.gz
wget http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_us3.tar.gz

```


**[size="4"][color="#3b3b3b"]Step 2:[/color][/size]**

Install the deb and unpack the voices and wrappers:

```

sudo dpkg -i mbrola3.0.1h_i386.deb
unzip -x us1-980512.zip
unzip -x us2-980812.zip
unzip -x us3-990208.zip
tar xvf festvox_us1.tar.gz
tar xvf festvox_us2.tar.gz
tar xvf festvox_us3.tar.gz

```


**[size="4"][color="#3b3b3b"]Step 3:[/color][/size]**

Make directories for the voices and move them there:

```

sudo mkdir /usr/share/festival/voices/english/us1_mbrola/
sudo mkdir /usr/share/festival/voices/english/us2_mbrola/
sudo mkdir /usr/share/festival/voices/english/us3_mbrola/
sudo mv us1 /usr/share/festival/voices/english/us1_mbrola/
sudo mv us2 /usr/share/festival/voices/english/us2_mbrola/
sudo mv us3 /usr/share/festival/voices/english/us3_mbrola/

```


**[size="4"][color="#3b3b3b"]Step 4:[/color][/size]**

Install the wrappers:

```

sudo mv festival/lib/voices/english/us1_mbrola/* /usr/share/festival/voices/english/us1_mbrola/
sudo mv festival/lib/voices/english/us2_mbrola/* /usr/share/festival/voices/english/us2_mbrola/
sudo mv festival/lib/voices/english/us3_mbrola/* /usr/share/festival/voices/english/us3_mbrola/

```


**[size="4"][color="#3b3b3b"]Step 5:[/color][/size]**

Test everything is working by starting festival[color=red]***[/color] and typing the following at the prompt:

```

festival> (voice_us1_mbrola)
festival> (SayText "Does it work?")
festival> (quit)

```


[color=red]***[/color] On my machine I call festival through the [font="mono"]aoss[/font] wrapper program from the alsa-oss package, another option is the [font="mono"]esddsp[/font] wrapper from esound-clients &#8212; but *_caveat emptor_* -&#8212; there is a bug ([#214465]("https://bugs.launchpad.net/ubuntu/+source/esound/+bug/214465")) in the [font="mono"]esddsp[/font] script right now (see [post="4682046"]this post[/post] for a workaround); yet another option is to set up festival to use esd or alsa via settings in /etc/festival.scm (see [community docs on TextToSpeech]("https://help.ubuntu.com/community/TextToSpeech")).


**[size="4"][color="#3b3b3b"]Cleanup:[/color][/size]**

Now clean up the tmp stuff:

```

cd ../
rm -rf mbrola_tmp/

```


That's it. :)

---

