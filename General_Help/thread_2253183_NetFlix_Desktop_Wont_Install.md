---
title: "NetFlix Desktop Wont Install"
date: 2014-11-17
forum: General Help
---

### Post by mfilacchione on 2014-11-17
Hello All,

I am having problems runing the PPA installer for Netflix.  I have installed serveral diffrent flavors of ubuntu over the past few months (Ubuntu, EduUbuntu, ect.) and not have a problem up till yesterday.  The commands I am using for the PPA are the fallowing: 
[B][I]sudo apt-add-repository ppa:ehoover/compholio
[/I][/B]
[B][I] sudo apt-get update
[/I][/B][B][I]sudo apt-get install netflix-desktop
[/I][/B]
[I]** sudo apt-get install msttcorefonts**
[/I]
I do not notice any erros when runing the commands, it is up till I either complete the msttcorefonts or when trying to select the netflix icon that the issue begains.  I get an error message that is worded slightly diffrent at times but in the end always has this same statement in it: ***"Failure to download extra data files"***.   Even if I reboot the OS and do not attempt to launch netflix after a while I get a box open that sees *"**Update information"***with the fallowing: 

[B][I]Failure to download extra data files
The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.
netflix-desktop
The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.[/I][/B]

Their is a option to ***"run this action now"*** in the box, If I attempt to run it, a terminal window loads with the fallowing command in it: ***netflix-desktop: downloading [http://developer.netflix.com/files/Netflix_API2_57x57.png](http://developer.netflix.com/files/Netflix_API2_57x57.png)***
The window then sits for a bout 45 seconds and dispears with nothing happening.

I have tried the fallowing to resolve the issue:
[I]Ubnstalled - Reinstalled the package
Verfied Ubuntu restricted extras installed
Tried PipeLight software alterntive
Tried Various Source Selections in the Updater and various servers
Uninstalled and reinstalled EduUbuntu, Ubuntu, and Ubuntu Studio
Made sure Silverlight and Pipeline where enabled
Even ran seperate installs of Wine[/I]

I still consider my self a novice or early apprentaince when it comes to Ubuntu, but after looking over other forum threads similar to my post and trying the above I really ohnostly do not beleive this is an issue with the PPA commands, software, or OS on the work station.  I wounder if their is some underlying network issue that I am not aware of.  When on Ubuntu I always a have a sloid internet connection, and for the most part have no other issue's when installing other software (how ever I seen similar message on occasion when changing sources in the updater). Could this mean the server hosting or connecting me to the PPA is not available or having issue's providing additional parts of the package?  Does that make since?  I do not feel like I am fully up to speed on how the software updater and PPA installer works in general for the Ubuntu. 

Any ways I would really love to get Netflix working again it is one of the few peices of software left that keeps me semied tied to windows.  I was really surprised that this started at late since I have installed it so many times in the past with no issue. So any advice would be apprecaited. 

                        Kind Regards - un cordial saludo - cordialement - Herzliche Grüße - &#1057; &#1091;&#1074;&#1072;&#1078;&#1077;&#1085;&#1080;&#1077;&#1084; - [FONT=Droid Sans Fallback][SIZE=2]&#25964;&#20855; [/SIZE][/FONT]- venlig hilsen - [FONT=Lohit Marathi]&#1571;&#1591;&#1610;&#1576; &#1575;&#1604;&#1578;&#1581;&#1610;&#1575;&#1578; [/FONT]- Cheers!

-Michael

---

### Post by QIII on 2014-11-17
If you are having such trouble, are you wedded to the idea of the Netflix desktop or do you just want to be able to use Netflix without fuss?  With no requirement for Wine?

---

### Post by dFlyer on 2014-11-17
Are you using chrome or firefox. Firefox will not work with Netflix.

---

### Post by QIII on 2014-11-17
Firefox will, but it is troublesome to arrange.

---

### Post by yancek on 2014-11-17
I haven't used Netflix Desktop but have used wine-pipelight which worked well.  With wine-pipelight and firefox, you need a User Agent Switcher or User Agent Overrider to identify the browser.  If you are running a recent Ubuntu (14.04/14.10) , it would be a lot simpler to just download and install google-chrome from the Software Center as it works without any changes needed.

---

### Post by mfilacchione on 2014-11-18
No, I am not tied to solely using the desktop, I just found it was generally was the easiest method to run netflix on Ubuntu with only 3 commands. To bhoneset I have not configured to much manually in wine.

---

### Post by monkeybrain20122 on 2014-11-18
Either 1) pipelight  + user-agent-overrider addon  for Firefox or 2) Chrome out of the box. Both work well for me.

---

### Post by mfilacchione on 2014-11-18
For the past Year and half I have successfully installed and ran the Netflix Desktop on Fire Fox over 15 times, on 3 flavors of Ubuntu ,up until the day before yesterday with only these 4 commands for the PPA: 
[I][B]sudo apt-add-repository ppa:ehoover/compholio
  [/B][/I]
[I][B]sudo apt-get update
sudo apt-get install netflix-desktop
[/B][/I]
***sudo apt-get install msttcorefonts***

---

### Post by coffeecat on 2014-11-18
If you want a hassle-free way of viewing Netflix on an Ubuntu desktop, simply download and install the chrome browser. It has to be Chrome and not Chromium. You can download it here:

[https://www.google.com/chrome/browser/](https://www.google.com/chrome/browser/)

Installing from the downloaded deb also adds a source to your apt sources so that it will be kept up to date. Netflix now works out of the box with Chrome with no extra configuration needed. If you don't like the idea of using the proprietary Chrome browser for all your web browsing, simply do as I do, and use your favourite browser for everything else and reserve Chrome only for Netflix viewing.

---

### Post by mfilacchione on 2014-11-18
I have tried to use Wine-Piplight altertive with the desktop as per intstructions from people in these forums with no avail.  I have not ran chrome on Unbuntu for net flix in long in a long time but I will give it a shot to behonest I do not know why I did not think of it.  but to behonest I feel like I am going to wind up with the same issue.Since the error I am receiving appearrs to be more about a download issue with some needed files vs what is happening on the work station: 
***Failure to download extra data files***

[B][I]The following packages requested additional data downloads after  package installation, but the data could not be downloaded or could not  be processed.
netflix-desktop
The download will be attempted again later, or you can try the download  again now.  Running this command requires an active Internet connection.[/I][/B]

---

### Post by mfilacchione on 2014-11-18
Since Chrome has been suggested by many folks in this thread (something I suspose I should a of thought of myself :( ) when I come home tonight I will install and give it shot.  I appreacaite every one's suggestions and insgiht on this.  

It would also still be nice to figure out why suddlenly the methode I have been using with firefox over the past year just stoped working.  Or especailly what that error actaully means in the end.  If anyone can provide me with insight into the error or where I could get more information in regards to it would be great.

Once again every one thanks for the isight and I will post here to let you know how chrome install went in regards tonight.

---

### Post by monkeybrain20122 on 2014-11-18
The netflix-desktop has not been updated since May, probably it is no longer maintained and replaced  by pipelight (same developers) Pipelight works as a Firefox plugin, there is no need to install netflix-desktop

Instructions to install pipelight [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

---

### Post by mfilacchione on 2014-11-18
Thanks for the additioanl tip monkeybrain20122 , When I install the pipline PPA I see the  plugin in FireFox and I have it set to always active but when I try to  acess the movie I get the gerneic Netflix page that explains I need to  be on Mac or windows for netflix movies to play.  Is their anything else I need to set in regards that I am not aware of? In the mean time I am going to also give Chrome a shot.

---

### Post by deadflowr on 2014-11-18
> **mfilacchione said:**
> Thanks for the additioanl tip monkeybrain20122 , When I install the pipline PPA I see the  plugin in FireFox and I have it set to always active but when I try to  acess the movie I get the gerneic Netflix page that explains I need to  be on Mac or windows for netflix movies to play.  Is their anything else I need to set in regards that I am not aware of? In the mean time I am going to also give Chrome a shot.

Did you grab the [user-agent-switcher]("http://pipelight.net/cms/installation-user-agent.html")
?

---

### Post by yancek on 2014-11-18
Simple instructions for wine-pipelight to run in firefox.  Also need User Agent Overrider and to enable the plugin.  If you have a current Ubuntu, the google-chrome from the repositories should work.  Earlier versions did not.

[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

---

### Post by mfilacchione on 2014-11-18
Thanks Deadflowr,

Thanks so much, that worked, I appreciate everyone&#8217;s efforts who answered and especially deadflowr and monkeybrain20122. I do not know how I missed that step deadflowr thanks again.  
I am sort glad I wrote this thread, not only did benefit me getting NetFlix back online but it also has cleared up the fact that their is still efficient way to install and run NetFlix in Ubuntu's choice of of a default web browser.
I try to introduce a lot of standard computer users to the system explaining how simple it is to use and install their favourite programs vs. Linux of old and being able to still demstrait a way to install NetFlix on Ubuntu is great!

I like to ask one additional question, is their a way to find out who the original author was for the NetFlix Desktop APP PPA?  I would like to see if the app was abandoned or if my issue was network related.  I am still a little concerned with the way the software updater acts with my workstation at times. I have had other PPA's fail and have had a few update issue's. I like to see if it is on my end or if it could be possibly be the suppliers of the packages as suggest by monkeybrain20122 earlier.  Should I create a separate thread in regards to that one and have this one closed?

Kind Regards - un cordial saludo - cordialement - Herzliche Grüße - &#1057; &#1091;&#1074;&#1072;&#1078;&#1077;&#1085;&#1080;&#1077;&#1084; - [FONT=Droid Sans Fallback][SIZE=2]&#25964;&#20855; [/SIZE][/FONT]- venlig hilsen - [FONT=Lohit Marathi]&#1571;&#1591;&#1610;&#1576; &#1575;&#1604;&#1578;&#1581;&#1610;&#1575;&#1578; [/FONT]- Cheers!

-Michael

---

### Post by mfilacchione on 2014-11-18
Thanks,

Yancek it is up and working on Fire Fox now as stated per my post above.  Going to see how well it works in Chrome next :) !!!

---

### Post by yancek on 2014-11-18
> I like to ask one additional question, is their a way to find out who the original author was for the NetFlix Desktop APP

Erich Hoover.  His official web site below.

[http://compholio.com/](http://compholio.com/)

> It's also important to note that netflix-desktop is integrated with the pipelight project

The quote above is from the official Hoover web site, link below:

[http://www.compholio.com/netflix-desktop/](http://www.compholio.com/netflix-desktop/)

---

### Post by deadflowr on 2014-11-18
> **mfilacchione said:**
> Thanks,

Yancek it is up and working on Fire Fox now as stated per my post above.  Going to see how well it works in Chrome next :) !!!


Unlike firefox, chrome(meaning Google Chrome, and not chromium) has all you need to run netflix nearly out of the box.
The only thing you need to do is change a setting in your Netflix account to prefer stream HTML5 instead of silverlight.
But you do not need any user agent switchers, nor pipelight(which is moot since pipelight cannot work on chrome now anyway)

---

### Post by monkeybrain20122 on 2014-11-19
> **deadflowr said:**
> Unlike firefox, chrome(meaning Google Chrome, and not chromium) has all you need to run netflix nearly out of the box.
The only thing you need to do is change a setting in your Netflix account to prefer stream HTML5 instead of silverlight.
But you do not need any user agent switchers, nor pipelight(which is moot since pipelight cannot work on chrome now anyway)

Actually I didn't change any setting in Chrome, it just works.

---

### Post by coffeecat on 2014-11-19
> **monkeybrain20122 said:**
> Actually I didn't change any setting in Chrome, it just works.

Deadflowr didn't say that you should change a setting in Chrome, just in your Netflix account: silverlight -> HTML5. In fact I didn't even have to do that when I first used Chrome with Netflix - my Netflix account settings were already set to HTML5, but I don't remember whether that was the default when I first set up my account or whether I changed it then knowing that hell would freeze over before I ever needed silverlight! :wink:

**Edit:** I've just checked my playback settings in my Netflix account in Chrome and I don't see the option to choose between silverlight and HTML5 any more. I'm sure I saw it there the other day. Or perhaps I saw it on one of the other devices I use. Or perhaps Netflix is autodetecting Chrome and making the choice unnecessary.

---

### Post by monkeybrain20122 on 2014-11-19
> **coffeecat said:**
> Deadflowr didn't say that you should change a setting in Chrome, just in your Netflix account: silverlight -> HTML5. In fact I didn't even have to do that when I first used Chrome with Netflix - my Netflix account settings were already set to HTML5, but I don't remember whether that was the default when I first set up my account or whether I changed it then knowing that hell would freeze over before I ever needed silverlight! :wink:

**Edit:** I've just checked my playback settings in my Netflix account in Chrome and I don't see the option to choose between silverlight and HTML5 any more. I'm sure I saw it there the other day. Or perhaps I saw it on one of the other devices I use. Or perhaps Netflix is autodetecting Chrome and making the choice unnecessary.

I meant I didn't change any setting in Netfkix. In fact it plays on both Chrome and Firefox (with pipelight) without me having to switch any netflix seting manually, so it uses both silverlight and html5 depending on which browser I use.

---

### Post by monkeybrain20122 on 2014-11-19
> **coffeecat said:**
> Deadflowr didn't say that you should change a setting in Chrome, just in your Netflix account: silverlight -> HTML5. In fact I didn't even have to do that when I first used Chrome with Netflix - my Netflix account settings were already set to HTML5, but I don't remember whether that was the default when I first set up my account or whether I changed it then knowing that hell would freeze over before I ever needed silverlight! :wink:

**Edit:** I've just checked my playback settings in my Netflix account in Chrome and I don't see the option to choose between silverlight and HTML5 any more. I'm sure I saw it there the other day. Or perhaps I saw it on one of the other devices I use. Or perhaps Netflix is autodetecting Chrome and making the choice unnecessary.

I meant I didn't change any setting in Netfkix. In fact it plays on both Chrome and Firefox (with pipelight) without me switching any netflix seting manually, so it uses both silverlight and html5 depending on which browser I happen to be on.

---

### Post by mfilacchione on 2014-11-19
> **deadflowr said:**
> Unlike Firefox, chrome(meaning Google Chrome, and not chromium) has all you need to run netflix nearly out of the box.
The only thing you need to do is change a setting in your Netflix account to prefer stream HTML5 instead of silverlight.
But you do not need any user agent switchers, nor pipelight(which is moot since pipelight cannot work on chrome now anyway)

Great good to know. I did not get a chance to play with it on chrome yet.  I also did not know that Netflix has a switch between HTML 5 and Silverlight.  I guess it is a good thing since I heard MS abandoned Silver light?  
Thanks once again Deadflowr

---

### Post by mfilacchione on 2014-11-19
> **monkeybrain20122 said:**
> I meant I didn't change any setting in Netfkix. In fact it plays on both Chrome and Firefox (with pipelight) without me switching any netflix seting manually, so it uses both silverlight and html5 depending on which browser I happen to be on.

Interesting MonkeyBrain20122, glad to hear I should be able to see what happens tonight.  I am going to make a quick Edu video of how to install 5 to 6 different type of web browsers tonight on Ubuntu Chrome will be one and see what happens I will post up the results when done.

---

### Post by mfilacchione on 2014-11-19
> **yancek said:**
> Erich Hoover.  His official web site below.

[http://compholio.com/](http://compholio.com/)



The quote above is from the official Hoover web site, link below:

[http://www.compholio.com/netflix-desktop/](http://www.compholio.com/netflix-desktop/)

Ah cool thanks I will have to check out the site in the bit, Especially since it seems my system still has part of the PPA from the where I was trying to install the NetFlix Desktop agent. It is weird I ran the un-installer for the desktop agent, removed the [compholio]("http://compholio.com/") portion,  and every time I re-boot the system it tries to launch to download part of the Desktop Agent that it originally failed to do, then it prompts saying it can not download it.

---

### Post by troy7 on 2014-11-23
mfilacchione - thanks for being persistant in getting the answer.  Adding the switcher to FireFox worked for me also.

---

### Post by mfilacchione on 2014-11-24
> **troy7 said:**
> mfilacchione - thanks for being persistant in getting the answer.  Adding the switcher to FireFox worked for me also.



I hope no one found me aggravating though lol.  I just wanted to clear up all a lot of confusion that I have seen in the community on this topic. I have seen people saying you can not run it in certain browsers to other comments that I figured did not add up.  My persistence was in regards to getting some sort of SOP on how to do this, which appears what we have in the end, well that is ill something else changes in the Ubuntu world.  (like that would ever happen :P lol)  

I still need to post my results with chrome and a few other browsers I am trying to get it to run on. I will try to reply back as soon as possible with the results.

---

### Post by mfilacchione on 2014-11-24
> **mfilacchione said:**
> Ah cool thanks I will have to check out the site in the bit, Especially since it seems my system still has part of the PPA from the where I was trying to install the NetFlix Desktop agent. It is weird I ran the un-installer for the desktop agent, removed the [compholio]("http://compholio.com/") portion,  and every time I re-boot the system it tries to launch to download part of the Desktop Agent that it originally failed to do, then it prompts saying it can not download it.

If you are fallowing the thread and ran the fallowing commands
[SIZE=2]*sudo apt-get update    &&    sudo apt-get install ppa-purge    &&    sudo ppa-purge ppa:ehoover/compholio   &&    sudo apt-get remove netflix-desktop, *[/SIZE]

to remove the desktop package for NetFlix (not the pipelight install) and still are still seeing Netflix install messages poping as me, I notice that PPA's may not been removed 
from your software updater for what ever reason. I found simply by going into the software updater and unchecking the boxes named ehoover and compholio resolved this issue for me. I am 
not for sure if their is a a better command to completely remove them but this seem to resolve the annoying pop issue I was having with it.

---

