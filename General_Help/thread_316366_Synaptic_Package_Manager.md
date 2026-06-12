---
title: "Synaptic Package Manager"
date: 2006-12-10
forum: General Help
---

### Post by raveneffct on 2006-12-10
HELP!

Out of nowhere when I try to open Synaptic Package Manager I get the following error

```
E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

```

Please help.

[IMG]http://ourworld.cs.com/raveneffct/Screenshot.png[/IMG]

---

### Post by loell on 2006-12-10
post you sources.list by doing this in the console

```
cat /etc/apt/sources/list
```

highlight it , copy and paste it here

---

### Post by riven0 on 2006-12-10
> **raveneffct said:**
> HELP!

Out of nowhere when I try to open Synaptic Package Manager I get the following error

```
E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

```

Please help.

Perhaps there is something wrong with the sources.list? Go to the terminal and copy and paste:

>  sudo gedit /etc/apt/sources.list

Then paste the contents of that file here.

---

### Post by raveneffct on 2006-12-10
> **riven0 said:**
> Perhaps there is something wrong with the sources.list? Go to the terminal and copy and paste:



Then paste the contents of that file here.

```
# 
# 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted #Added by software-properties


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main


deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse #Added by software-properties

deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe #Added by software-properties
#AUTOMATIX REPOS END


```

---

### Post by temcat on 2006-12-10
Try deleting this line (which is the sixth one):

> deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

It doesn't add anything and doesn't list specific repositories (like main or restricted).

---

### Post by raveneffct on 2006-12-10
> **temcat said:**
> Try deleting this line (which is the sixth one):



It doesn't add anything and doesn't list specific repositories (like main or restricted).

Did the changes...get this:

"You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

---

### Post by temcat on 2006-12-10
> **raveneffct said:**
> Did the changes...get this:

"You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

To edit the file, you need administrator privileges.

Launch terminal, then enter:

```
sudo gedit /etc/apt/sources.list
```

Enter your password, then the text editor will be launched where you will be able to make the changes and save the file.

---

### Post by raveneffct on 2006-12-10
> **temcat said:**
> To edit the file, you need administrator privileges.

Launch terminal, then enter:

```
sudo gedit /etc/apt/sources.list
```

Enter your password, then the text editor will be launched where you will be able to make the changes and save the file.

It worked, taking out line 6 made it work..Ok so, what was line 6 and how did it get there?

---

### Post by raveneffct on 2006-12-10
This is what my repositories used to look like

[IMG]http://ourworld.cs.com/raveneffct/Screenshot-1.png[/IMG]

Now that we got rid of that line 6, CDROM/DVD only lists One.

Also why does my repositories look like the above, when every tutorial I see shows it looking like this:

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=RepositoriesUbuntu04.png[/IMG]

---

### Post by temcat on 2006-12-10
> **raveneffct said:**
> It worked, taking out line 6 made it work..Ok so, what was line 6 and how did it get there?

I'm not sure how it got there - maybe changing some preferences in Synaptic or System->Administration->Software Sources triggered that. Looks like a bug if you didn't mess with /etc/apt/sources.list yourself (and apparently you didn't, since you asked that question about saving the file). Anyway, what this line *tried* to do was to specify Edgy CD-ROM as one of the sources for your software, but a) it was already specified as such on line 2; and b) this 6th line was missing a parameter.

---

### Post by raveneffct on 2006-12-10
> **temcat said:**
> I'm not sure how it got there - maybe changing some preferences in Synaptic or System->Administration->Software Sources triggered that. Looks like a bug if you didn't mess with /etc/apt/sources.list yourself (and apparently you didn't, since you asked that question about saving the file). Anyway, what this line *tried* to do was to specify Edgy CD-ROM as one of the sources for your software, but a) it was already specified as such on line 2; and b) this 6th line was missing a parameter.

Ok, well I appreciate the help. Thanks man.

But can you tell me why my preferences>repositories looks different from what it should (As listed in my above post with images) Thanks.

---

### Post by temcat on 2006-12-10
> **raveneffct said:**
> Ok, well I appreciate the help. Thanks man.

But can you tell me why my preferences>repositories looks different from what it should (As listed in my above post with images) Thanks.

This picture is in fact not about how repository window **should** look like, but rather how it **could** look like. It assumes that you haven't added your CD-ROM as a source.

---

### Post by raveneffct on 2006-12-10
> **temcat said:**
> This picture is in fact not about how repository window **should** look like, but rather how it **could** look like. It assumes that you haven't added your CD-ROM as a source.

Well, I can't get dvd playback I want to fix that. I have no idea how to check if multiuniverse and universe are enabled or how to add repositories. (Because when they explain how, my repositories menu is different)


Apparently this is a way to get DVD playback working, but it doesn't work for me
```
This requires that all the relevant repositories are enabled. So before you do the sudo aptitude install (...), go to System -- Administration -- Synaptic Package Manager -- Settings -- Repositories and then click Add. It's not sufficient to just click all the tickboxes next to all these channels listed on that screen: You have to actually click the Add button, and check the Community maintained (Universe) and Non-free (Multiverse) boxes.

Codec support

gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs

For DVD playing

gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```

---

### Post by Azakus on 2006-12-10
For dvd playback, add these lines to your sources.list file
```
## PLF
## Please report any bug on https://launchpad.net/products/plf/+bugs
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
```
Then do this ```
sudo aptitude install libdvdcss2 libdvdread3
```
Now any movie player you have will decode DVD's.

---

### Post by raveneffct on 2006-12-10
> **Azakus said:**
> For dvd playback, add these lines to your sources.list file
```
## PLF
## Please report any bug on https://launchpad.net/products/plf/+bugs
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
```
Then do this ```
sudo aptitude install libdvdcss2 libdvdread3
```
Now any movie player you have will decode DVD's.

Ok that worked, now to test it.

---

### Post by raveneffct on 2006-12-10
Actually it didn't work

```

matthew@ubuntu:~$ sudo aptitude install libdvdcss2 libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
[B]No candidate version found for libdvdcss2
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.[/B]
Writing extended state information... Done

```

That's what I hate about the terminal...can't undo changes :(

---

### Post by Azakus on 2006-12-10
Oops. I assumed you would update first. Try this
```
sudo aptitude update && sudo aptitude install libdvdcss2 libdvdread3
```

---

### Post by raveneffct on 2006-12-10
> **Azakus said:**
> Oops. I assumed you would update first. Try this
```
sudo aptitude update && sudo aptitude install libdvdcss2 libdvdread3
```

"Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do."

Should I do it.

---

### Post by Azakus on 2006-12-10
Yes. I've done it and it works perfectly.
Also run this code to remove that stupid message (it adds the repo's trust authentication).
```
wget http://plf.zarb.org/plf.asc && apt-key add plf.asc && rm plf.asc
```

---

### Post by raveneffct on 2006-12-10
> **Azakus said:**
> Yes. I've done it and it works perfectly.

Ok, I did it..and now the dvd plays..but I get no sound???

EDIT: Nevermind, thanks man.

But...How come sometimes throughout the videos I see horizontal scan lines on the videos?

---

### Post by riven0 on 2006-12-10
> **raveneffct said:**
> Ok, I did it..and now the dvd plays..but I get no sound???

Hmm... try this:

> sudo apt-get update && sudo apt-get install alsa-oss

Tell us if it works.

---

### Post by raveneffct on 2006-12-10
> **riven0 said:**
> Hmm... try this:



Tell us if it works.

I was wrong, the sound does work..sorry about that.

But im not totally happy with the video quality. Is there something I can do about this? (My video card is installed properly)

---

### Post by riven0 on 2006-12-10
> **raveneffct said:**
> I was wrong, the sound does work..sorry about that.

But im not totally happy with the video quality. Is there something I can do about this? (My video card is installed properly)

Can you tell us what exactly is wrong with the video quality?

---

### Post by raveneffct on 2006-12-10
> **riven0 said:**
> Can you tell us what exactly is wrong with the video quality?

It's hard to describe, and it only occurs sometimes..but at points in the video, during movement I will see horizontal lines in the video.

---

### Post by Azakus on 2006-12-10
If you have an nVidia card, the free driver that comes with is really bad for video. Try the non-free with ```
sudo aptitude install nvidia-glx && sudo nvidia-xconfig
``` Then restart your computer.

---

### Post by raveneffct on 2006-12-10
> **Azakus said:**
> If you have an nVidia card, the free driver that comes with is really bad for video. Try the non-free with ```
sudo aptitude install nvidia-glx && sudo nvidia-xconfig
``` Then restart your computer.

I have ATI
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

---

### Post by riven0 on 2006-12-10
> **raveneffct said:**
> I have ATI
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

Alright, hope for the best on this one, because I never had success installing ati's official drivers... *stupid ati*  ](*,) 

Anyway, try [this howto]("http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+x300") and see where it gets you.

---

