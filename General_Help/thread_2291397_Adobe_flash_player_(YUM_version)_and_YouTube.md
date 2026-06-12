---
title: "Adobe flash player (YUM version) and YouTube"
date: 2015-08-19
forum: General Help
---

### Post by Mistermisanthrope on 2015-08-19
I don't know how to install this version. I am no longer able to watch videos on YouTube. Someone posted that they had success with the YUM version. I down loaded it from the web site. I saved the file in Archive Manager and I have no idea what to do now. I have no computer tech skills, so when I open the file nothing makes sense to me and there are no prompts. My OS is Ubuntu 12.04. Any simple advice would be appreciated. I am wary of experimenting so I have resisted copying the code (if it is code) and trying to use it as a command. Totally lost. Thanks---Mr.Mis.

---

### Post by QIII on 2015-08-19
yum is a package/update management utility for rpm-based (Red Hat Package Manager) distributions such as Red Hat and Fedora.  

Ubuntu is Debian-based and so uses aptitude, apt, synaptic, etc, to manage packages and updates in the form of deb files.

If you are not comfortable usin the terminal,  you will probably not want to use the alien utility to convert the rpm to a useable deb.

What, exactly, is the problem causing you to try this?

---

### Post by efflandt on 2015-08-19
Do you keep your system up to date when notified of updates. There was a period of time recently when Firefox blocked certain flash versions due to a known flash vulnerability.

What specific videos are you having trouble with? I have 64-bit 12.04 on another drive and while just testing YouTube in Firefox, it worked fine. Then I looked at my flash version and realized that I last updated it 6/23/2012 when I was apparently manually updating it with a tar.gz file when Linux 64-bit flash was still beta and the Ubuntu repos used 32-bit flash with a wrapper. So I removed all that, installed **flashplugin-installer** which installed the current 64-bit flash version and that also works fine for YouTube. Normally flashplugin-installer is automatically installed if you install **ubuntu-restricted-extras** which also installs TrueType fonts and other audio/video codecs you might need, although, something additional needs to be done to play certain DVDs.

The only flash videos I am aware of that may have stopped working recently are on Hulu due to them switching to a flash method of protected content (maybe due to optional ShowTime). But if that is an issue you could likely get around that in 12.04 by installing **hal**. Although, hal is no longer used or in standard repositories for newer Ubuntu versions, so I had to use a 3rd party ppa to install hal in 14.04.

The easiest way I found to locate programs (especially if looking for a specific driver version or by its specific package name) is the old **synaptic** package manager (which can be installed from Ubuntu Software Center). But if you use synaptic you need to remember to hit the little curly icon to update package lists before searching for or installing things. At first I was not used to the Software Center because it could not find the specific package ubuntu-restricted-extras by that name, although, it could find the Restricted Extras for Ubuntu, etc. if just searching for **restricted** or **restricted extras** without the hyphens.

---

### Post by monkeybrain20122 on 2015-08-19
Since FF40 all youtube videos default to play in HTML5 (if you disable flash or set it to ask to activate videos will still play automatically, --which is somewhat annoying IMO)
As far as youtube is concerned flash is irrelevant.

I suspect your system is not up to date (and I would avoid installing the .rpm. It is the same outdated flash that you can install from the Software Centre/synaptic. There is no advantage and alien may or may not work)

---

### Post by Mistermisanthrope on 2015-09-02
My apologies to all. I thought that I would be notified via e-mail were I to get a response to this post. Those were the days! I was reading commentaries about my current version of AFP and found that others were having the same problem with YouTube. One commentator said that she had solved the problem by installing the YUM version. Since then Hulu and the BBC have told me that I need the YUM version. I reckon I need the YUM version.

I have no technical knowledge or skills as far as computers go. I don't understand most of the answers that people are kind enough to post. I tried the synaptic package manager. Nothing there. I tried canonical repository. It does not exist. I am working with the Ubuntu 12.04 32 bit OS. I guess I will try to update the SPM and see what happens. Thank you all. I really do appreciate any help I can get. You are all captains and I....I am a mere oarsman. Mr.Mis.

---

### Post by Mistermisanthrope on 2015-09-02
I wasn't aware of the curly icon. I tried SPM but there was nothing whatsoever about Adobe Flash. I will do what you suggested. Thanks a lot.

---

### Post by btindie on 2015-09-02
If you just want to watch videos on youtube then you don't actually need flash, you can instead use HTML5, you certainly don't need the RPM from the YUM repository.

I'm not familiar with FF, but for chromium it's fairly straight forward.

The below is all done from the terminal, which once you get used to it is much quicker and easier than any GUI tool.

Make sure you update your local list of packages before installing anything
```
sudo apt-get update
```

Close chromium before installing the below.

For youtube to work with chromium you just need to install the chromium-codecs-ffmpeg-extra package.
```
sudo apt-get install chromium-codecs-ffmpeg-extra
```
That'll then use HTML5 for playing the videos.

If you must have flash, for iPlayer, then you can get that working by installing the pepflashplugin-installer package
```
sudo apt-get install pepflashplugin-installer
```

The pepflashplugin-installer package that comes with Ubuntu 12.04 doesn't enable itself when installed. To do so you need to edit it's config file.
Edit it with
```
gksu gnome-text-editor /etc/chromium-browser/default
```
and add the below line to the bottom of it, that loads flash when chromium is started. Save and close it.
```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```
Note the '.' at the beginning of the line, that's required to source the shell script.

---

### Post by Yellow Pasque on 2015-09-02
> Since then Hulu and the BBC have told me that I need the YUM version. I reckon I need the YUM version.

I'm not sure who gave you that advice, but I suspect they couldn't install a package on any Linux distro if their life depended on it.

---

### Post by Bucky Ball on 2015-09-02
Go [here]("http://youtube.com/html5") and enable html5 in Youtube.

---

### Post by monkeybrain20122 on 2015-09-02
> **Bucky Ball said:**
> Go [here]("http://youtube.com/html5") and enable html5 in Youtube.

No need to opt in now. HTML5 has been the default in Chrome/Chromuim for a while and since FF 40 Youtube will play in html5 even if flash is activated. So now you need something to stop it from autoplay kind of like flash block but for html5. :)

Edited :For some graphic drivers there is a problem for Firefox to play Youtube in 1080p or above using html5 though. The option is disabled by default so Youtube video's settings only show 720p max (need to go to about:config and set media.mediasources.enabled=T media.mediasources.webm.enabled =T) After this the 1080p and higher options appear but FF crashes as soon as I choose them. This is an intel machine upgrading to mesa 11 fixed this but caused other problems so I rolled back to the stock driver. Same with another Nvidia machine I tried using the proprietary driver. So this is probably not usable yet for some users, hence disabled by default.

---

### Post by Bucky Ball on 2015-09-02
> **monkeybrain20122 said:**
> No need to opt in now. HTML5 has been the default in Chrome/Chromuim for a while and since FF 40 Youtube will play in html5 even if flash is activated. So now you need something to stop it from autoplay kind of like flash block but for html5. :)

Tnx for that. Good to know. :)

---

### Post by Mistermisanthrope on 2015-09-03
Thanks for that, but I don't have any idea what  it means. I have no knowledge of computer technology and it is hard to learn because I can never understand the advice I get. I will try to enable html5, but so far  I have had no luck trying to do anything to fix the problem. I downloaded the Chromium browser but that didn't help. I can't watch videos on that either. I can watch video on PBS using Fire Fox (my default browser) I don't know why that is. My computer is old. I need to get a better graphics card, so I don't really need 1080p capabilities I think I am generally at 360p. You Tube has made some changes recently and that is when the trouble began. I no longer have any options as far as pixalation(?) is concerned. ...Any way.. thanks

---

### Post by Mistermisanthrope on 2015-09-03
I clicked on "here." The You Tube page says that I can"request" html5, but it doesn't say where or how. It's maddening. Thank you--Mr.Mis.

---

### Post by Mistermisanthrope on 2015-09-04
You were right about HTML5. I removed my current version of Adobe Flash Player  and that had no affect on YouTube video. Unfortunately there was no improvement. The buffering is very slow; the audio is choppy; and the video is more like a slide show and completely out of sync. This problem is intermittent and the quality varies. It may be my computer or Time Warner Cable. I will have to run a speed test.

As far as other sites go, I am unable to live stream BBC radio;  nor watch video on Hulu or  PBS. Hulu says I need to use the YUM version. BBC says I need to upgrade flash player. PBS says "No playable source found."

I reinstalled the available player from Software Center, but it simply does not work. I tried using the synaptic package manager (I did hit the update icon) but there is no version of AFP there. I tried following the instructions for installing YUM in a tutorial I found but I have hit a wall there  because I apparently need some sort of software that I don't have and I don't really understand what I'm doing or need to do. 

I appreciate everyone's help, but I am ready to give up. I just don't think I have enough technical abilities to deal with this kind of problem.  From the comments I read under the Adobe Flash Installer in the Software Center, I gather that others are having similar problems. The only one who said they had solved the problem was a woman who installed the YUM version, but i just can't figure out how to do that. Thanks again--Mr.Mis

---

### Post by monkeybrain20122 on 2015-09-04
Hulu's stream is DRMed. You need flash 11.2 and hal [https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal) (or Pipelight, see below) It won't work on Chrome. I tend to agree that they don't know what they are talking about if they told you the rpm would work. It is the same flash as you get from the Software Centre, just packaged for RedHat based distros, there is no special juice in it.

But pipelight flash would solve all your problems about drmed flash contents. It is Windows' flash in a wine wrapper (but performance may not be so great) [http://ubuntuforums.org/showthread.php?t=2274467&p=13346475#post13346475](http://ubuntuforums.org/showthread.php?t=2274467&p=13346475#post13346475) (don't need to remove flashplugin-installer like in the post)

As for Youtube, its html5 player appears to be very resource demanding on Firefox because of absence of hardware acceleration (Chrome works a lot better). I would use the mpv addon and perhaps a html5 blocker to prevent Youtube from autoplay (google that, there are a few FF addon to block html5) The performance is a lot better than both flash and html5. For mpv addon see post #8 [http://ubuntuforums.org/showthread.php?t=2284266](http://ubuntuforums.org/showthread.php?t=2284266) It also works on many other sites than Youtube (youtube-dl claims to work on PBS, if true then mpv addon will work, can't test it since I am outside the U.S and mpv-addon doesn't work over a vpn)

There is also a standalone Youtube app you can use. Install smtube from [https://launchpad.net/~rvm/+archive/ubuntu/ppa](https://launchpad.net/~rvm/+archive/ubuntu/ppa) (the repo version doesn't work, too old to keep up with Google's changes)

---

### Post by Bucky Ball on 2015-09-05
flashplugin-installer is what you are looking for in Synpatics. Yes, it is there.

You do not need the YUM version. That is not even for Ubuntu. Don't believe a word of it. :D

---

