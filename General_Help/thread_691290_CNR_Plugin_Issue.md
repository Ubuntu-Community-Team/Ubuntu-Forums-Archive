---
title: "CNR Plugin Issue"
date: 2008-02-08
forum: General Help
---

### Post by Jojochinoise on 2008-02-08
I installed the CNR plugin, but it fails to initialize. Can anyone help?

---

### Post by S3Indiana on 2008-02-08
> **Jojochinoise said:**
> I installed the CNR plugin, but it fails to initialize. Can anyone help?Pls. run cnr from the command prompt and reply with any error messaging...

---

### Post by Jojochinoise on 2008-02-09
> **S3Indiana said:**
> Pls. run cnr from the command prompt and reply with any error messaging...

timer: 1440[Debug] rows in installed package model  0 
[Warning]" " 
[Debug]Creating InstallComplete
[Debug]distSnapVersion: 0
[Debug]Doing full parse
[Debug]Downlaoding:  to /tmp//qt_temp.TJ6016
[Debug]No server set to connect to while attempting to download the Distribution Index

---

### Post by S3Indiana on 2008-02-09
> **Jojochinoise said:**
> timer: 1440[Debug] rows in installed package model  0 
[Warning]" " 
[Debug]Creating InstallComplete
[Debug]distSnapVersion: 0
[Debug]Doing full parse
[Debug]Downlaoding:  to /tmp//qt_temp.TJ6016
[Debug]No server set to connect to while attempting to download the Distribution IndexInquiring with the CNR Client developers...

---

### Post by S3Indiana on 2008-02-11
> **Jojochinoise said:**
> timer: 1440[Debug] rows in installed package model  0 
[Warning]" " 
[Debug]Creating InstallComplete
[Debug]distSnapVersion: 0
[Debug]Doing full parse
[Debug]Downlaoding:  to /tmp//qt_temp.TJ6016
[Debug]No server set to connect to while attempting to download the Distribution IndexCNR Client access issue is [resolved]("http://community.cnr.com/thread/1102"). Pls. try again...

---

### Post by Jojochinoise on 2008-02-12
> **S3Indiana said:**
> CNR Client access issue is [resolved]("http://community.cnr.com/thread/1102"). Pls. try again...

Still not working for me....

---

### Post by S3Indiana on 2008-02-12
> **Jojochinoise said:**
> Still not working for me....Pls. try (starting with the second step) [                                     Resolving CNR Client Issues]("http://community.cnr.com/docs/DOC-1126")...                 
             
 > Open File Manager  [LIST=1]
[*]Browse to /var/lib/cnr/client and delete the file named: packages
[*]Browse to /var/cache/cnr/client/lists and delete the file named: _var_cache_cnr_client_dists_linspire_arch_binary-i386_Packages[/LIST]

---

### Post by Jojochinoise on 2008-02-12
> **S3Indiana said:**
> Pls. try (starting with the second step) [                                     Resolving CNR Client Issues]("http://community.cnr.com/docs/DOC-1126")...

Doesn't work. I tried going to:
/var/lib/cnr/client and delete the file named: packages
/var/cache/cnr/client/lists and delete the file named: _var_cache_cnr_client_dists_linspire_arch_binary-i386_Packages

I deleted the first file, but I don't have the 2nd one. Within the "lists" folder, there's a "partial" folder which is empty.

---

### Post by S3Indiana on 2008-02-12
> **Jojochinoise said:**
> Doesn't work. I tried going to:
/var/lib/cnr/client and delete the file named: packages
/var/cache/cnr/client/lists and delete the file named: _var_cache_cnr_client_dists_linspire_arch_binary-i386_Packages

I deleted the first file, but I don't have the 2nd one. Within the "lists" folder, there's a "partial" folder which is empty.Understand. So after removing the packages file, then restarting the CNR Client that didn't reinitialize the [FONT=Helvetica, Arial, sans-serif]Distribution Index[/FONT]???

---

### Post by Jojochinoise on 2008-02-19
> **S3Indiana said:**
> Understand. So after removing the packages file, then restarting the CNR Client that didn't reinitialize the [FONT=Helvetica, Arial, sans-serif]Distribution Index[/FONT]???

No, it didn't work. Still doesn't....

---

### Post by S3Indiana on 2008-02-19
> **Jojochinoise said:**
> No, it didn't work. Still doesn't....Pls. try [downloading]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") and installing the client again (FYI an updated version of the CNR Client is in final QA)...

---

### Post by S3Indiana on 2008-03-13
An [updated]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") version of the CNR Client has been released that quite possibly could resolve your issues...

---

### Post by ajmorris on 2008-03-28
hi there,
i was just wondering what the attraction of CNR is? What is wrong with Ubuntu's own repositories? Ubuntu's own built in software management system is awesome, why replace that with CNR?

---

### Post by S3Indiana on 2008-03-28
> **ajmorris said:**
> i was just wondering what the attraction of CNR is? What is wrong with Ubuntu's own repositories? Ubuntu's own built in software management system is awesome, why replace that with CNR?It's an option (same as Synaptic), and it provides access to applications not found in the default ubuntu repositories...

---

### Post by ajmorris on 2008-03-28
what extra applications does it provide access to?

---

### Post by S3Indiana on 2008-03-28
> **ajmorris said:**
> what extra applications does it provide access to?[Skype]("http://cnr.com/product/productOverview.seam?productId=17937") ([latest]("http://cnr.com/product/productSpecifications.seam?productId=17937") w/video capability), [My Money]("http://www.cnr.com/product/productOverview.seam?productId=41725"), [Lotus Symphony]("http://www.cnr.com/product/productOverview.seam?productId=41475"),  [Google Earth]("http://cnr.com/product/productOverview.seam?productId=16206") ([4.2]("http://cnr.com/product/productSpecifications.seam?productId=16206")), [Adobe Acrobat Reader]("http://www.cnr.com/product/productOverview.seam?productId=18106"), [StarOffice]("http://www.cnr.com/product/productOverview.seam?productId=17838") (alternative to OpenOffice), [Crossover Linux]("http://www.cnr.com/product/productOverview.seam?productId=22431") (and [Pro]("http://www.cnr.com/product/productOverview.seam?productId=38136")), and more (hope I didn't list any that are in the default ubuntu repositories)...

---

### Post by ajmorris on 2008-03-28
IBM Lotus symphony, is that the IBM licensed trial version, or the full?
That proprietary software, crossover provides working debs for those.
GoogleEarth is accessible via the medibuntu repositories, this repository is easier to add than installing CNR.
Adobe Acrobat Reader is also available via medibuntu.
Skype version 2.0.0.63 with video capability is avaliable via medibuntu.
MTH My Money is almost a virtual clone of Homebank, Homebank is in the ubuntu repositories and in gnome-app-install.
The StarOffice installer is as easy to use as the Deb installers.
And what about for 64bit users? If im a 64bit user, does any of this help me?

The reality of this is, is that CNR is just like AutomatiX.

---

### Post by S3Indiana on 2008-03-28
> **ajmorris said:**
> The reality of this is, is that CNR is just like [AutomatiX]("http://www.getautomatix.com/").> **03/26/2008:** Automatix development has ceased (There will be no Automatix for Ubuntu 8.04). Read more [          [COLOR=#C85A17]           **here**          [/COLOR]         ]("http://www.getautomatix.com/forum/index.php?showtopic=2424")Faults noted, doesn't change the value in the one-stop user experience at [CNR.com]("http://www.cnr.com/")...

---

### Post by xArv3nx on 2008-03-28
> **ajmorris said:**
> IBM Lotus symphony, is that the IBM licensed trial version, or the full?
That proprietary software, crossover provides working debs for those.
GoogleEarth is accessible via the medibuntu repositories, this repository is easier to add than installing CNR.
MTH My Money is almost a virtual clone of Homebank, Homebank is in the ubuntu repositories and in gnome-app-install.
The StarOffice installer is as easy to use as the Deb installers.
And what about for 64bit users? If im a 64bit user, does any of this help me?

The reality of this is, is that CNR is just like AutomatiX.
Hi, no. That's wrong.

CNR is more than Automatix is (and ever will be), CNR.com offers CNR Aisles (Google it), a legal DVD player (one of the only ones in Linux), purchasble legal codecs, Parallels Workstation, and a LOT of others.

If you want to use CNR on a 64-bit computer, can't you just use those 32-bit libs or w/e? It's not like everything needs to use 64-bit processors (especially if it doesn't help speed-wise). 

Also, CNR is more for beginners. So, if you aren't a beginner then you can probably just use dpkg -i to install package, or just compile from source or whatever you feel like. It doesn't really matter, it's all about choice.

One last thing, I'm not sure if Ubuntu supports CNR (Linspire, the company behind CNR, and Ubuntu do have a partnership thing, though), so this might be in the wrong section. Either way, I'd suggest posting at CNR.com. lol

Feel free to ask anymore questions,
Jo

---

### Post by compiledkernel on 2008-03-28
First why use 64-bit if you are going to install a billion of 32-bit libs it defeats the purpose. 

Running 64bit versus 32bit does actually happen to give a rather significant speed boost in performance in general and huge speed performance when doing heavy stuff (compiling, movie editing, sound/music editing, image editing etc.), especially on new 64-bit computers. Any developer, musician, or video editor will tell you that, and to assume it doesnt is rather naive. 

I also think that CNR will hose your system if you try CNR on 64-bit as the libs are set to /usr/lib as an example, if you want to install 32-bit libs on 64-bit, they need to go to /usr/lib32 or your system becomes severely unhappy. Another thing is there's diffrences on w32codecs and w64codecs they aren't compatible.

So 64bit users are themselves out of luck where CNR is concerned, unless the status of a 64bit Client has changed. Thus far Im aware it hasnt. 

Parallels Workstation is actually offered over in the Partner Repo that is sponsored by Canoncial. So im not really sure why thats such a big deal either. 

The codec issue goes back to whats legal in your country. The mediubuntu respository (very simple to add in Synatpic , and something that even a beginner should understand and know how to do  in my opinion) contains GoogleEarth(current release), Skype(current release), Acroread(current release), all the codecs, including the DVD codec for Encrypted DVD's, xmms-wma (windows media audio for XMMS), w32codecs (as well as w64codecs for us 64bit users), and the current release of FFMpeg. 

So , thus far your statements make a moot point. If all CNR provides is user experience, then it seems pretty useless to me, and only causes the user to avoid "learning" to do anything with the operating system they have in front of them. Ease of use is no replacement for proper education and direction of the user. As S3Indiana says, faults aside, nothing beats one stop user experience. Yes, something does. Educating the user and fostering knowledge in the user. Not leaving them to fear how to do things with what they have.

---

### Post by S3Indiana on 2008-03-28
> **compiledkernel said:**
> As S3Indiana says, faults aside, nothing beats one stop user experience.Is taking [content]("http://ubuntuforums.org/showthread.php?p=4602088#post4602088") out-of-context standard practice???

---

### Post by xArv3nx on 2008-03-28
> **compiledkernel said:**
> First why use 64-bit if you are going to install a billion of 32-bit libs it defeats the purpose. 

Running 64bit versus 32bit does actually happen to give a rather significant speed boost in performance in general and huge speed performance when doing heavy stuff (compiling, movie editing, sound/music editing, image editing etc.), especially on new 64-bit computers. Any developer, musician, or video editor will tell you that, and to assume it doesnt is rather naive. 

I also think that CNR will hose your system if you try CNR on 64-bit as the libs are set to /usr/lib as an example, if you want to install 32-bit libs on 64-bit, they need to go to /usr/lib32 or your system becomes severely unhappy. Another thing is there's diffrences on w32codecs and w64codecs they aren't compatible.

So 64bit users are themselves out of luck where CNR is concerned, unless the status of a 64bit Client has changed. Thus far Im aware it hasnt. 

Parallels Workstation is actually offered over in the Partner Repo that is sponsored by Canoncial. So im not really sure why thats such a big deal either. 

The codec issue goes back to whats legal in your country. The mediubuntu respository (very simple to add in Synatpic , and something that even a beginner should understand and know how to do  in my opinion) contains GoogleEarth(current release), Skype(current release), Acroread(current release), all the codecs, including the DVD codec for Encrypted DVD's, xmms-wma (windows media audio for XMMS), w32codecs (as well as w64codecs for us 64bit users), and the current release of FFMpeg. 

So , thus far your statements make a moot point. If all CNR provides is user experience, then it seems pretty useless to me, and only causes the user to avoid "learning" to do anything with the operating system they have in front of them. Ease of use is no replacement for proper education and direction of the user. As S3Indiana says, faults aside, nothing beats one stop user experience. Yes, something does. Educating the user and fostering knowledge in the user. Not leaving them to fear how to do things with what they have.
Remember, computers are supposed to make life easier, not harder.

---

### Post by ajmorris on 2008-03-28
> **xArv3nx said:**
> Remember, computers are supposed to make life easier, not harder.

you give no evidence to contradict CompiledKernel's claim....

---

### Post by xArv3nx on 2008-03-29
> **ajmorris said:**
> you give no evidence to contradict CompiledKernel's claim....
I'd reply if I wanted to:

A) Start a flame war
B) Get attacked constantly (pls. see the SkyOS thread I just made)
C) Argue about something pointless
D) Keep reviving a dead topic

---

### Post by compiledkernel on 2008-03-29
There is a technical discussion here xArv3nx, and I dont really see much more than that going on. Ive yet to see any indication from the other side either meriting or discrediting the technical aspects of the thread. 

In your noted thread about SkyOS, I see  it being a bit unhappy, however I have made attempt to enter the thread and give better insight.

---

### Post by SOULRiDER on 2008-03-29
> **S3Indiana said:**
> It's an option (same as Synaptic), and it provides access to applications not found in the default ubuntu repositories...

It seems youre missing the point of Free software.
[http://www.debian.org/doc/debian-policy/ch-archive.html#s-dfsg](http://www.debian.org/doc/debian-policy/ch-archive.html#s-dfsg) and [http://www.ubuntu.com/community/ubuntustory/licensing](http://www.ubuntu.com/community/ubuntustory/licensing) it seems you need to read the basics.

> First why use 64-bit if you are going to install a billion of 32-bit libs it defeats the purpose.

Running 64bit versus 32bit does actually happen to give a rather significant speed boost in performance in general and huge speed performance when doing heavy stuff (compiling, movie editing, sound/music editing, image editing etc.), especially on new 64-bit computers. Any developer, musician, or video editor will tell you that, and to assume it doesnt is rather naive.

I also think that CNR will hose your system if you try CNR on 64-bit as the libs are set to /usr/lib as an example, if you want to install 32-bit libs on 64-bit, they need to go to /usr/lib32 or your system becomes severely unhappy. Another thing is there's diffrences on w32codecs and w64codecs they aren't compatible.

So 64bit users are themselves out of luck where CNR is concerned, unless the status of a 64bit Client has changed. Thus far Im aware it hasnt.

+1

> Remember, computers are supposed to make life easier, not harder.

Is having a borked and bloated system making life easier? If it is, then i'd rather not have it easy.

---

### Post by Joeb454 on 2008-03-29
Having looked into CNR a bit after read this thread, and being a 64 bit user myself, I can't see the point of using it unless you have a 32 bit system.

Even then, I'm still not sure why you would want to use it, it does seem similar to automatix

---

### Post by SOULRiDER on 2008-03-29
It actually seems to me like a glorified clone of sites like download.com

---

### Post by JoshuaRL on 2008-03-29
I agree that this may not be the best place to find support for CNR.  It doesn't fit in well with either the best installation methods or the ethos of Ubuntu.  Is it a good application?  I really don't think so, but you have to answer that for yourself.  But if the Linspire Project Manager (S3Indiana) can't help you get something installed correctly, then is it a good application?

---

### Post by S3Indiana on 2008-03-29
> **JoshuaRL said:**
> I agree that this may not be the best place to find support for CNR.  It doesn't fit in well with either the best installation methods or the ethos of Ubuntu.  Is it a good application?  I really don't think so, but you have to answer that for yourself.  But if the Linspire Project Manager (S3Indiana) can't help you get something installed correctly, then is it a good application?For clarification I'm not a developer, but have been successful using the CNR Client on ubuntu 7.04, kubuntu 7.10 in a few configurations. The [CNR.com]("http://www.cnr.com/index.html") repository is an exact mirror of the default ubuntu repositories, so if there's an issue possibly it's a package issue. Don't quite understand the unfounded fear that some have in using CNR...

---

### Post by ajmorris on 2008-03-29
> **S3Indiana said:**
> For clarification I'm not a developer, but have been successful using the CNR Client on ubuntu 7.04, kubuntu 7.10 in a few configurations. The [CNR.com]("http://www.cnr.com/index.html") repository is an exact mirror of the default ubuntu repositories, so if there's an issue possibly it's a package issue. Don't quite understand the unfounded fear that some have in using CNR...


It's not really a fear... Its just that the default ubuntu system of installing packages is perfect for ubuntu, there is no point using CNR. And, the arguments being presented for CNR, are the same that were presented for AutomatiX :/

---

### Post by JoshuaRL on 2008-03-29
> **S3Indiana said:**
> For clarification I'm not a developer, but have been successful using the CNR Client on ubuntu 7.04, kubuntu 7.10 in a few configurations. The [CNR.com]("http://www.cnr.com/index.html") repository is an exact mirror of the default ubuntu repositories, so if there's an issue possibly it's a package issue. Don't quite understand the unfounded fear that some have in using CNR...

I'm sorry, but I need some clarification.  Are you saying the issue is with how well your repo copies the ubuntu repos?  Because if so, that really doesn't make the point any different.  If not, then you are obviously pointing to the ubuntu repos as the problem.  If this was the problem, a lot more people than just the CNR users would have issues.

CNR is unnecessary, badly implemented, and from a company that has a focus completely off-kilter from Ubuntu.

And while you might not be a developer, you are in charge of them.  Or at very least within almost immediate contact with them.  So why do you spend so much time here posting as a normal user?  Couldn't you be of more use on your own support forums?

---

### Post by SOULRiDER on 2008-03-29
> **JoshuaRL said:**
> I'm sorry, but I need some clarification.  Are you saying the issue is with how well your repo copies the ubuntu repos?  Because if so, that really doesn't make the point any different.  If not, then you are obviously pointing to the ubuntu repos as the problem.  If this was the problem, a lot more people than just the CNR users would have issues.

CNR is unnecessary, badly implemented, and from a company that has a focus completely off-kilter from Ubuntu.

And while you might not be a developer, you are in charge of them.  Or at very least within almost immediate contact with them.  So why do you spend so much time here posting as a normal user?  Couldn't you be of more use on your own support forums?

Not a bad idea seeing how much the people running it are having problems with its packages:
[http://forum.freespire.org/forumdisplay.php?f=23](http://forum.freespire.org/forumdisplay.php?f=23)

---

### Post by S3Indiana on 2008-03-29
> **JoshuaRL said:**
> I'm sorry, but I need some clarification.  Are you saying the issue is with how well your repo copies the ubuntu repos?  Because if so, that really doesn't make the point any different.  If not, then you are obviously pointing to the ubuntu repos as the problem.  If this was the problem, a lot more people than just the CNR users would have issues.For simplicity sake, what I posted is that the package is the same as in the default ubuntu repository using the same basic tool - apt, so pls. explain how CNR has issues not found in the native system (your hypothesis is truly not logical)...

> **JoshuaRL said:**
> CNR is unnecessary, **badly implemented**There appears to be a significant population that disagrees with you, and request you provide irrevocable evidence of your allegation...

> **JoshuaRL said:**
> So why do you spend so much time here posting as a normal user?  Couldn't you be of more use on your own support forums?Don't many active community member frequent multiple forums (use Google to understand the extent of S3's activities :)...

---

### Post by S3Indiana on 2008-03-29
> **SOULRiDER said:**
> Not a bad idea seeing how much the people running it are having problems with its packages:
[http://forum.freespire.org/forumdisplay.php?f=23](http://forum.freespire.org/forumdisplay.php?f=23)Forums exist for those with [difficulties,]("http://ubuntuforums.org/forumdisplay.php?f=131") not the the majority that are satisfied (as this Support tool provides)...

---

### Post by Alan_M on 2008-03-30
CNR is NOT supported, WILL NEVER be supported, all further discussions of CNR will possibly be locked, deleted...im guessing on those two, but they WILL DEFINATELY be frowned upon.  Move on, save your breath for something thats actually IMPORTANT to the ubuntu community, like Aptitude, or Synaptic...stuff we actually support guys. Thanks, have a great day!

---

### Post by JoshuaRL on 2008-03-30
> **compiledkernel said:**
> First why use 64-bit if you are going to install a billion of 32-bit libs it defeats the purpose. 

Running 64bit versus 32bit does actually happen to give a rather significant speed boost in performance in general and huge speed performance when doing heavy stuff (compiling, movie editing, sound/music editing, image editing etc.), especially on new 64-bit computers. Any developer, musician, or video editor will tell you that, and to assume it doesnt is rather naive. 

I also think that CNR will hose your system if you try CNR on 64-bit as the libs are set to /usr/lib as an example, if you want to install 32-bit libs on 64-bit, they need to go to /usr/lib32 or your system becomes severely unhappy. Another thing is there's diffrences on w32codecs and w64codecs they aren't compatible.

So 64bit users are themselves out of luck where CNR is concerned, unless the status of a 64bit Client has changed. Thus far Im aware it hasnt. 

Parallels Workstation is actually offered over in the Partner Repo that is sponsored by Canoncial. So im not really sure why thats such a big deal either. 

The codec issue goes back to whats legal in your country. The mediubuntu respository (very simple to add in Synatpic , and something that even a beginner should understand and know how to do  in my opinion) contains GoogleEarth(current release), Skype(current release), Acroread(current release), all the codecs, including the DVD codec for Encrypted DVD's, xmms-wma (windows media audio for XMMS), w32codecs (as well as w64codecs for us 64bit users), and the current release of FFMpeg. 

So , thus far your statements make a moot point. If all CNR provides is user experience, then it seems pretty useless to me, and only causes the user to avoid "learning" to do anything with the operating system they have in front of them. Ease of use is no replacement for proper education and direction of the user. As S3Indiana says, faults aside, nothing beats one stop user experience. Yes, something does. Educating the user and fostering knowledge in the user. Not leaving them to fear how to do things with what they have.

I'm still waiting on a response to this.  An honest, technical answer refuting it.  Please don't avoid this or talk around it, but give a plain and simple answer.  

And please don't point to the Ubuntu repos as the only technical issue, that obviously can't be the real problem with just installing the base CNR application in the first place.

---

### Post by S3Indiana on 2008-03-30
> **JoshuaRL said:**
> I'm still waiting on a response to this.  An honest, technical answer refuting it.  Please don't avoid this or talk around it, but give a plain and simple answer.  

And please don't point to the Ubuntu repos as the only technical issue, that obviously can't be the real problem with just installing the base CNR application in the first place.The simple answer is the CNR Client has not **yet** been built against a 64-bit system (developers are working on it). Unsure on timeframe for release...

---

### Post by compiledkernel on 2008-03-30
Then there is no problem in making the statement -- I also think that CNR will hose your system if you try CNR on 64-bit as the libs are set to /usr/lib as an example, if you want to install 32-bit libs on 64-bit, they need to go to /usr/lib32 or your system becomes severely unhappy. Another thing is there's diffrences on w32codecs and w64codecs they aren't compatible.

Because indeed if you are a 64bit user, CNR will most definitely break, hose, bork, and generally make your system unhappy. 

Worthless to a 64bit user, sadly which you might not think of which, there are 1000s.

---

### Post by S3Indiana on 2008-03-30
> **Alan_M said:**
> CNR is NOT supported, WILL NEVER be supported, all further discussions of CNR will possibly be locked, deleted..(im guessing on those two)Is there an official response (link pls.); otherwise, more FUD...

---

### Post by S3Indiana on 2008-03-30
> **compiledkernel said:**
> Worthless to a 64bit user, sadly which you might not think of which, there are 1000s.Agree there are many (that's why the developers are working on a 64-bit build), but the percentage is still low even in the ubuntu community...

---

### Post by JoshuaRL on 2008-03-30
And so what's the answer about the repos?  They obviously can't be the issue the OP had, he couldn't even get to them.

---

### Post by SOULRiDER on 2008-03-30
> **S3Indiana said:**
> Forums exist for those with [difficulties,]("http://ubuntuforums.org/forumdisplay.php?f=131") not the the majority that are satisfied (as this Support tool provides)...

We're talking about pkg management here not general support.

---

### Post by SOULRiDER on 2008-03-30
> **S3Indiana said:**
> Is there an official response (link pls.); otherwise, more FUD...

Scroll up (and maybe a page back) and check out the links I posted about Debian's and Ubuntu's policies on propietary software.

---

### Post by S3Indiana on 2008-03-31
> **SOULRiDER said:**
> Scroll up (and maybe a page back) and check out the links I posted about Debian's and Ubuntu's policies on propietary software.Fully understand the Debian policy on software, but doesn't [this]("https://shop.canonical.com/index.php?cPath=19&osCsid=0f77d5d52749304a17340b8280cc59a5") provide commercial proprietary software???

---

### Post by S3Indiana on 2008-03-31
> **SOULRiDER said:**
> We're talking about pkg management here not general support.Incorrect, the OP was having issues initializing the CNR Client (IOW basically a CNR Client installation issue - which was most likely resolved in the most [recent]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") CNR Client build)...

---

### Post by xArv3nx on 2008-03-31
Since you guys are STILL going on about some crap, I guess I'll go ahead and reply.

> First why use 64-bit if you are going to install a billion of 32-bit libs it defeats the purpose. 

Running 64bit versus 32bit does actually happen to give a rather significant speed boost in performance in general and huge speed performance when doing heavy stuff (compiling, movie editing, sound/music editing, image editing etc.), especially on new 64-bit computers. Any developer, musician, or video editor will tell you that, and to assume it doesnt is rather naive. 

[B]To assume that a musician or video editor is using Ubuntu is rather dumb. Also, Ubuntu isn't for developers, it is for end-users. Most end-users don't do these things.

People using 64-bit != People that need to be using CNR[/B]

I also think that CNR will hose your system if you try CNR on 64-bit as the libs are set to /usr/lib as an example, if you want to install 32-bit libs on 64-bit, they need to go to /usr/lib32 or your system becomes severely unhappy. Another thing is there's diffrences on w32codecs and w64codecs they aren't compatible.

**That's probably true, I don't really care, though.**

So 64bit users are themselves out of luck where CNR is concerned, unless the status of a 64bit Client has changed. Thus far Im aware it hasnt. 

**It has, I guess.**

Parallels Workstation is actually offered over in the Partner Repo that is sponsored by Canoncial. So im not really sure why thats such a big deal either. 

**It's not.**

The codec issue goes back to whats legal in your country. The mediubuntu respository (very simple to add in Synatpic , and something that even a beginner should understand and know how to do in my opinion) contains GoogleEarth(current release), Skype(current release), Acroread(current release), all the codecs, including the DVD codec for Encrypted DVD's, xmms-wma (windows media audio for XMMS), w32codecs (as well as w64codecs for us 64bit users), and the current release of FFMpeg. 

**And, then again, many Linux (especially Freespire) users live IN America.**

So , thus far your statements make a moot point. If all CNR provides is user experience, then it seems pretty useless to me, and only causes the user to avoid "learning" to do anything with the operating system they have in front of them. 

**I don't like your way of thinking, the computer is made to make things EASIER, you shouldn't have to "learn" useless things about how your system works, especially if you don't want a career in computers. Besides, the only reason you need to know how your system works is if your system screws up (pretty badly). And that shouldn't happen (Ever tried Upgrading to a new release?).**

Ease of use is no replacement for proper education and direction of the user. 

**60-year olds do NOT care how the inner system of their OS works. They just want it to work. That is who this is aimed at.**

As S3Indiana says, faults aside, nothing beats one stop user experience. Yes, something does. Educating the user and fostering knowledge in the user. Not leaving them to fear how to do things with what they have.

**Remember, they fear the OS for a reason. :lolflag:**


---

### Post by squizzi on 2008-03-31
I remember seeing on these forums a little quote in someones signature "Don't just use your computer, learn to use it"

Sure, ease of use is of utmost importance, because thats the friendly environment that the user first wants to access.  But, 60 years old or not, in our day and age its important, and relatively required to learn the backbone.  Not to mention, in future generations backbone will be more important then ease of use, seeing as how the future generations are indeed coming into the tech age.

Also, I'd like to add that almost all computers are diving into the 64bit hardware now.  But, hardware producers still continue to put 32 bit OS's on that hardware because of the lack of 64 bit applications, why not start the change?  Why not start that change, instead of spitting statistics everywhere.  To tell you the truth, if you want ease of use from the box, you want a 64bit environment that runs on that persons hardware straight from the box, with all the apps, etc.  

My 3 cents.

---

### Post by S3Indiana on 2008-03-31
> **squizzi said:**
> I remember seeing on these forums a little quote in someones signature "Don't just use your computer, learn to use it"

Sure, ease of use is of utmost importance, because thats the friendly environment that the user first wants to access.  But, 60 years old or not, in our day and age its important, and relatively required to learn the backbone.  Not to mention, in future generations backbone will be more important then ease of use, seeing as how the future generations are indeed coming into the tech age.That's like saying that because you drive a car you need to have first hand knowledge of the process required for a tune-up or changing the oil. If a tool exists that meets the need of providing browse, search, research, collaborate, download and install of software for the tens of thousands that would never visit a forum, shouldn't that be the goal???

> **squizzi said:**
>  Also, I'd like to add that almost all computers are diving into the 64bit hardware now.  But, hardware producers still continue to put 32 bit OS's on that hardware because of the lack of 64 bit applications, why not start the change?  Why not start that change, instead of spitting statistics everywhere.  To tell you the truth, if you want ease of use from the box, you want a 64bit environment that runs on that persons hardware straight from the box, with all the apps, etc. Developers are actively working on a 64-bit version of the CNR Client (it will happen - all in time)...

---

### Post by paultag on 2008-03-31
> **S3Indiana said:**
> That's like saying that because you drive a car you need to have first hand knowledge of the process required for a tune-up or changing the oil. If a tool exists that meets the need of providing browse, search, research, collaborate, download and install of software for the tens of thousands that would never visit a forum, shouldn't that be the goal???

People will always have problems with their computers. We just aren't that good. Hell this thread is because CNR does not work right. You may not need to know how to "change your oil" but one day when you get stranded, it is good to know how to get your software working again without having to consult some company. This is the spirit behind the F & OS movement, and the basic Freedom a user should have. CNR Crushes this by charging users for Free software, and trying to turn a quick buck on other's software.

Free software, as well has become a catalyst of new, original and intuitive software. CNR is making a profit from this movement, riding in its shadow. Software will always have problems, if you think you can do it better, go make the change to some F&OSS, and give BACK to the community. Disney did it with Photoshop, Sun did it with OO.Org, IBM did it with the GNU / Linux OS, and Linspire should take the hint.

Oh, and xArv3nx:
> 
60-year olds do NOT care how the inner system of their OS works. They just want it to work. That is who this is aimed at.


So CNR is for 60 Year Olds?

---

### Post by bodhi.zazen on 2008-03-31
I am closing this thread now as it seems to have degenerated.

FYI: There is an official forums policy re: "installation scripts" which CNR seems to be (I think there was a request of clarification of forums policy earlier in this thread):

[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)

See the second post :twisted:

It seems CNR has it's own forums and I would refer anyone wanting to learn about or use CNR there :

[http://forum.freespire.org/forumdisplay.php?s=&daysprune=&f=55](http://forum.freespire.org/forumdisplay.php?s=&daysprune=&f=55)

---

