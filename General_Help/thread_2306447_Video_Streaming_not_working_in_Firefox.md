---
title: "Video Streaming not working in Firefox"
date: 2015-12-15
forum: General Help
---

### Post by Sam_Harrington on 2015-12-15
Hello. I'm new to Ubuntu OS. I really like it, but I wanted to know if you guys could help me with something I found today.

I was using Firefox like I normally do, and I tried to play a streaming video on Facebook:

[https://www.facebook.com/MrStevieRiks/posts/10153369896362057](https://www.facebook.com/MrStevieRiks/posts/10153369896362057)

The video's audio sounds terrible. Then I noticed that the video playback on all the other Facebook videos are the same.

I wanted to make sure it was the Firefox browser that was the problem so I tested this in Chrome Browser and the problem disappears. 

Can someone else confirm that this problem exists in Firefox with me? What must I do to fix my Firefox browser because I don't trust Chrome browser with my personal information. Hopefully that makes sense. 

What is wrong with Flash in Firefox? Are their any ways to fix Firefox so video playback on Facebook works? 

Thank you,

Ubuntu OS Newbie

---

### Post by Yawanathan_Israel on 2015-12-16
Hello,

Have you tried to use HTML5? if that is available?
What ver of Firefox are you using? Have you tried the nightlies?

I am using ver46 of firefox and the I also use HTML5 HD video and the sound is fine.

Thanks
Yawanathan

---

### Post by Sam_Harrington on 2015-12-16
Hello [**[COLOR=#000000]Yawanathan[/COLOR]**]("http://ubuntuforums.org/member.php?u=1974662"), 

I just installed the nightly Firefox PPA to upgrade my firefox browser. After this upgrade I am now running ver43, not ver 46 though. Are you running Ubuntu 12.04 LTS or a more recent version of Ubuntu OS?? because the best I can do is ver43 firefox from the nightly PPA??? I'm confused to why I would be running a more later version of Firefox browser considering the fact that you are running ver46. Where can i download and install the nightly ver46 verision of Firefox for Ubuntu 12.04?

I'm glad the audio is working for you with the above link, but still it sounds terrible for me even with the latest upgrades as suggested.

Hm..

How do I make the HTML5 work with the default installation of Ubuntu OS? 

I'm happy to reinstall the whole operating system again since it only took around 20 minutes to do it on my computer, but I want to know what is going to make it so I can play video correctly with Facebook and the above link I posted. 

What version of Ubuntu are you using to view the above link? 

How did you install your flash plugin for Firefox to make it work for the above link? 

Thank you,

Sam Harrington

---

### Post by Sam_Harrington on 2015-12-16
Updates so far. I have purged Firefox browser from the command line like this:

[https://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed](https://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed)

Then I purged all my plugins and even VLC and Mplayer. 

I autoremoved everything and autocleaned everything. Restarted. Then I reinstalled a fresh copy of Firefox ver43 from the security repos on Ubuntu 12.04.

Now the only thing that is different with my plugins is that I am now running (the default?) ones: 

OpenH264 Video Codec provided by Cisco Systems, Inc. 1.5.1
and
Shockwave Flash 20.0.0.248

All my other plugins and extensions are reinstalled too. 

I'm still getting the audio high pitched squealing like an old fashioned 56k modem noises when playing videos on Facebook.  The video plays and I can see what is playing but I can't hear anything except noise. All the other web sites I have tested so far, like youtube.com and etc work perfectly. I'm at a loss to fix my facebook video playback sound issue. Any suggestions would be wonderful. Thank you.

PS

If anyone would like to test my facebook video link above and let me know if you had success or not, please post your Firefox verson and Ubuntu OS version you have installed on your computer. I'm thinking I may need to upgrade to 14.04 LTS just to solve this one issue, but I don't want to unless I have to do it because everything else works good so far. 

Sam Harrington
Ubuntu 12.04 LTS

---

### Post by Sam_Harrington on 2015-12-16
Okay. I fixed my own problem. As suggested I needed to upgrade to the latest nightly version of Firefox as a first step to fix this audio problem.  I used this to install the nightly latest test version of Firefox:

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-trunk

Then you need to create a launcher icon for it called:

Application
Firefox Web Browser
firefox-trunk %u

because if not it will continue to run your older version with the command 'firefox %u'

If you want to install plugins, but it won't let you with an error that says "this browser is unsupported" (i.e Password Explorer, etc etc) then you will need to install the Firefox Nightly Testor Tools add-on extesion from here:

[https://addons.mozilla.org/en-US/firefox/addon/nightly-tester-tools/](https://addons.mozilla.org/en-US/firefox/addon/nightly-tester-tools/)

Firefox Menu >> Tools >> Nightly Testor Tools >> Force Add-on Compatibility

Now you will be able to install any add-on for Firefox you need even if untested or unsupported for your latest version of Firefox browser.

Lastly, you will need to install the latest Adobe Flash player like this:

sudo apt-get install adobe-flashplugin

After it is done restart your browser or your system. 

Okay, the audio in the Facebook video works just like it does on Chrome browser now. No more noises. Whew! This was a pain to solve but if you only want Firefox for all your online needs in Ubuntu this will help you when you need to have greater compatibility with all available web content.

Don't forget to purge any previous changes to your system you made after the problem developed on your Firefox browser before attempting this solution, otherwise it probably will create false-flag type problems when upgrading to the latest untested version of Firefox.

I've had other problems in the past with default Firefox browser being out-of-date in Ubuntu 12.04 LTS, but this seems to be a better browser and the older browser was almost 2+ years out of date being version 43. They need to update the default repos for ubuntu with a more recent version imho, but I am not sure if they have a reason for why the version of Firefox in ubuntu repos is so out of date either... since nobody here knows yet. Thanks! :)

---

