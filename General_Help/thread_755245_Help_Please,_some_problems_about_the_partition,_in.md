---
title: "Help Please, some problems about the partition, internet, sound etc. pleasee"
date: 2008-04-14
forum: General Help
---

### Post by the_analyzer on 2008-04-14
be patient, and please read my post. (and sorry if I have a bad english)

I love ubuntu, and for that I also distribute it, but now Im becoming a little angry with that. I have several problem and PLEASE, try to help me, for some issues I am struggling for months and no result. anyway. lets start with the simpliest and for me, very important. 

1. I have internet, (I am in a college) with ubuntu, but a guy connected my ubuntu (he was som kind of a geek, :) ) anyway, I want to do it myself but I cannot, and the guy there is no more. Now, you can help me only if you know how I connect it with XP I guess, So here is the link: 
[HTML]http://www.aubg.bg/template5.aspx?page=4819&menu=006001003001[/HTML]
that shows the way that I connect it on Windows. (also I want to learn how to connect the internet with ubuntu because as I said,  I distribute ubuntu in my college and nobody wants that without internet. or without those f## windows codecs. 

Now I want to know how to connect with internet because the 2nd issue:

2. I want to reinstall the ubuntu (I use 7,10) because it freezes a lot, many many times. I discussed in #ubuntu chatroom with a guy for this issue and he asked me if I had swap memory, and I think I dont have installed ubuntu with that option, I dont remember the command that he gave me for seeing this, anyway, if anyone from you does, he can say it. And I dont know if I can create a swap memory without formatting,  and before the formattin I have the other issue:

3. I have installed ubuntu two times in a separated 40 GB partition, so in one 13 GB and in the other 27 GB. Now how can I join them before I format it because I want one partition for Ubuntu. ANyway, in the ubuntu that Ive installed (I think with swap memory) I think it works better and does not freeze (like the other one in the begining does not stuck) but it froze one day with gimp. anyway. maybe it happens sometimes. 

the other common iSSUe that Ive read on the internet

4. I dont have sound on firefox with flash movies, so no youtube or stuff like that, and no music. Its horrible, I dont know if the fix is found yet. PS: I Had sound in flash some months ago.

and the most painful issue that I have months that Im trying to fix.

5. I use acer extensa 5210, I think with sound card high definition ...bla bla. 
Ive tried also OSS but no, I dont have SOUND. Actually, I have sound with speakers, but when I plug the headphones nothing happens. 

6. I also cannot access the files of the new ubuntu that Ive installed in one of the partitions with the old one (the one that has not swap memory activated) it says, restricted, or something like that because I dont remember very well. I can connect with the vista drive and vice versa, but I cannot ubuntu with ubuntu, that its strange. 


I WOULD REALLY REALLY REALLY appreciate anyone for helping me for these ******* problems that I hope will be resolved. 

REGARDS, and sorry for the long post.

---

### Post by FAJALOU on 2008-04-14
1) for the internet,,, are you on wireless?  You could possibly use 'ndiswrapper's to do it, and if not, I personally like wicd, which works well 

4) have you installed flashplugin-nonfree?  try installing 'sudo apt-get install flashplugin-nonfree' in terminal, minus the quotes.  

Sorry for not being able to help with more, but that's what I've been able to garner so far.

---

### Post by the_analyzer on 2008-04-14
thnx about the response.
regarding issue 1, Its not wireless, but I really need somebody to read the link that I gave and to understand what is the procedure, I know that its simple but I cannot figure it out.
It requires aunthetification by using e windows certificate. 
But I dont know what is the procedure with linux. 

and about issue 4, I think, I have already done that, but anyway Im doing it again now, I will notify if I have sound.

Thnx again for your response.

---

### Post by the_analyzer on 2008-04-14
I tried that, (note; I had firefox open while installing, maybe was a mistake, I dont know) but sound from flash wont work.

---

### Post by FAJALOU on 2008-04-14
do you have sound in other applications or in things other than youtube?  b/c you might possibly have the sound turned off in youtube on accident.  You could try, in Firefox, going into Edit>Preferences Then in the content tab, making sure that JavaScript is enabled.  I personally don't have Java enabled and my youtube sound works.  It sounds like overall sound problems.

---

### Post by the_analyzer on 2008-04-15
yes yes, Im sure that everything is fine with the firefox, javascript is enabled, but not only from youtube, I cannot listen from any flash movie, imeem etc etc, it sucks man.
anyone?
help me.

---

### Post by FAJALOU on 2008-04-15
Alright try this:

```
sudo apt-get install alsa-oss
```

Then restart Firefox.

If that doesn't work try:

```
sudo apt-get install libflash-mozplugin
```

And do you have Automatix installed?  Because automatix can update some of the scripts for you, like the proprietary flash ones ;).  


Hopefully these things work.  Make sure to restart your browser after you do these so they get installed.  Report back with the results.

---

### Post by mips on 2008-04-15
I think you would be better off asking how to setup your network for workgroups & security certificates in the networking section.

Just make sure the title of your thread is specific and clear as to what you want.

---

### Post by chrisccoulson on 2008-04-15
I think that setting up the network should be pretty easy. Most of the steps on that webpage you linked to involved finding details about your computer and filling in an application form. As for setting the computer name and workgroup, you can do this manually by going to Adminstration -> Network.

If you're using a wired connection over a LAN (which I'm pretty sure you are), then assuming you haven't played with any settings - it should be nearly ready to go (as Network Manager will obtain your IP address via DHCP by default). You just need to set up PEAP though, and I've no idea how to do this on Gutsy. Network Manager in Hardy provides an easy way of doing this, although I haven't got experience with setting it up.

If you're using Hardy (and I'm not sure you will be yet, as it's still beta), then you can set up PEAP by left clicking on the network manager icon, and selecting 'Connect to a 802.1X protected wired network). From here, you can specify the certificate file you downloaded, and also your allocated user name and password.

For Gutsy or earlier, please have a look at [http://ubuntuforums.org/showthread.php?t=684540]("http://ubuntuforums.org/showthread.php?t=684540")

---

### Post by the_analyzer on 2008-04-17
> **FAJALOU said:**
> Alright try this:

```
sudo apt-get install alsa-oss
```

Then restart Firefox.

If that doesn't work try:

```
sudo apt-get install libflash-mozplugin
```

And do you have Automatix installed?  Because automatix can update some of the scripts for you, like the proprietary flash ones ;).  


Hopefully these things work.  Make sure to restart your browser after you do these so they get installed.  Report back with the results.

No man, none of them worked.
Hey does anyone what is timidy, coz sometimes when I install stuff from the terminal, I see some kind of an error that says, timidy failed to start or stuff like that. I think that maybe is an application that Ive installed, maybe it was installed wrong

---

### Post by FAJALOU on 2008-04-17
I'm not sure about timidy, but *timidity* is a software sound renderer.  You might want to try installing it with ```
sudo apt-get install timidity
```

You may also want to register this as a bug with Ubuntu, and try posting something about this in the "sound" section.  Hopefully, you can get even more ideas than you are getting now.   
Hopefully timidity works.  Report back.

---

