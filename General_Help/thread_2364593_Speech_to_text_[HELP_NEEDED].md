---
title: "Speech to text [HELP NEEDED]"
date: 2017-06-25
forum: General Help
---

### Post by 1jarwolf on 2017-06-25
Hello, to start off, I wish to appologize upfront if this is a duplicate and or in the wrong place to post.

     Alright, so I am wanting to get Speech to text for LibreOffice Writer so I don't have to type. I have googled, and googled, and googled and can't find any software, that is until I came across this link. [http://www.brighthub.com/computing/linux/articles/55794.aspx](http://www.brighthub.com/computing/linux/articles/55794.aspx)

Alright, so I downloaded what they wanted me to download, the problem is... I am too new and I do NOT know how to actually install these. 

     The first picture below is the directory of the sphinxbase-5prealpha. I have no clue on how to install this or any of the commands to do so.

     The second picture below is festival, in which I also do NOT know how to install, nor do I know the commands to do so as well.

One last image, which is the strangest out of them all, is perlbox-voice. I didn't even install the right one apprently and I can't seem to find the right version. I am running Ubuntu 16.04 LTS.

---

### Post by howefield on 2017-06-25
First off, please be considerate to those on lower bandwidth connections and desist with the oversized images.

There is a readme file in your first and second screenshot, they usually contain installation instructions. Have you read them ? Also an install.sh file which would normally initiate the install process but peruse the readme file first.

As an aside, I'd caution you to be careful with tutorials as old as this one is.

---

### Post by 1jarwolf on 2017-06-25
> **howefield said:**
> First off, please be considerate to those on lower bandwidth connections and desist with the oversized images.

There is a readme file in your first and second screenshot, they usually contain installation instructions. Have you read them ? Also an install.sh file which would normally initiate the install process but peruse the readme file first.

As an aside, I'd caution you to be careful with tutorials as old as this one is.

I understand! I post the images how you fixed them. I appologize. Well, honestly, I am unsure how to install the files however, I will certainly read the readme files. May I ask if you know of any better ways as of software that does speech to text?

---

### Post by cariboo on 2017-06-25
You can install festival from the repositories, use you favourite method of installing it, synaptic,The Software Centre, or the command line

---

### Post by Impavidus on 2017-06-26
Just checking in synaptic, it seems festival is mostly about text to speech, but of course some components could help doing the reverse. Sphinx is in the repositories too. On 17.04 I find the package pocketsphinx, described as> CMU Sphinx is a large vocabulary, speaker-independent continuous speech recognition engine.

This package contains end-user speech recognition tools.Not to be confused with python-sphinx, which is about producing documentation for Python projects.

I never used any of those, so I can't comment on their use or their usefulness.

---

### Post by 1jarwolf on 2017-06-26
> **Impavidus said:**
> Just checking in synaptic, it seems festival is mostly about text to speech, but of course some components could help doing the reverse. Sphinx is in the repositories too. On 17.04 I find the package pockedsphinx, described asNot to be confused with python-sphinx, which is about producing documentation for Python projects.

I never used any of those, so I can't comment on their use or their usefulness.

Hmm. I understand. I am using 16.04 LTS. I will install synaptic and see if I can find it. Okay, I believe I have everything installed however, I can't seem to actually find the program and run it.

---

### Post by howefield on 2017-06-27
They are both in 16.04 but but perhaps a typo above.. it is pocketsphinx not pockedsphinx as far as I can see.

```
apt-cache policy festival
festival:
  Installed: (none)
  Candidate: 1:2.4~release-2
  Version table:
     1:2.4~release-2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```
```
apt-cache policy pocketsphinx
pocketsphinx:
  Installed: (none)
  Candidate: 0.8.0+real5prealpha-1ubuntu2
  Version table:
     0.8.0+real5prealpha-1ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

---

### Post by Impavidus on 2017-06-27
> **howefield said:**
> ... but perhaps a typo above..You're right. Fixed it.

---

