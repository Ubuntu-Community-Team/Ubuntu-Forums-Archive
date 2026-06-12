---
title: "wine and ultima online"
date: 2006-11-16
forum: General Help
---

### Post by cyborg on 2006-11-16
**i post this under general since i dont know if it is a wine related bug, or whatever, just read on.**

Well, well, it is not really wine related i think, because it isnt working in no other wine instances either anymore (cedega or cxoffice), but at least maybe somebody could post some hint.

whats the matter:
my ultima online stopped working. i use it to play on several freeshards, and all of them stopped working AT ONCE.
The get some error message when i try to log in.

when did that happen? when i was changing my network ip adress to another (fixed one) via kde control center. after that i thought of course, thats the problem, so i rechanged it to dhcp, but it seemed, that was not the thing.

first i thought i was banned (at once?) and rebooted windows. I used the SAME install there, and it worked.
also i changed network config there, and that worked too.
so it wasnt my ip adress.
maybe my /etc/network/interfaces? or wine?

So, of course, I thought it is wine. purged wine. deleted .wine. reinstalled and recreated .wine.
same effect.
then i thought, maybe wine is saving things somewhere else too. so i created a new user and a new .wine and installed uo completely new on my ext3 partition to avoid problems caused by the fat32 partition.
Nope.

Good. What next? I tried to install it on my laptop which is using breezy (i am using ubuntu edgy eft), and used same network settings as my pc here. it worked! so what the f... i thought (thats the part where i got really messy, because i thought maybe it is of some network-linux issue)

So I thought maybe its the network card. or the kernel. reinstalled the kernel with --reinstall and after that, still nothing, i changed my network card to a completely different one (other driver too, nforce3 onboard), still nothing.

nvidia was next. we know its closed source, so maybe glx or randr or xcompiz has some issue. so i started x11 with blank nv drivers. guess what. nope.

the next thing i began was to reinstall various libraries. since i cant purge everything, i really tried hard to purge-reinstall whatever possible.

i am still reinstalling stuff now. but it doesnt seem to work.

Note: I tried to log in into a local shard created by sphereserver.net on my machine. that works. also i looked up firewall settings, and played around with iptables to capture some network traffic. i know, uo tries to log in.
i know, the servers are responding. however, it seems that the encrypted login code sent by uo is messed up somehow over the net.
also i know, that wine works with the net. games like soldat work. so does connect steam, even if that never really works flawlessy. i dont use any sound driver so i cant imagine sound to be responsible. 

i always relogged on windows, and on my laptop, and there it works. however i cant play on the laptop, too slow, and i dont want to reboot everytime for my fav game.

finding this nasty bug costed me 3 days now (and full days) of trying around. i dont know anything now to try.

so anybody out there, using wine playing ultima online, especially on edgy eft, please tell me if it is only my machine. and anybody with suggestions how exactly i could try to find out, whatever messes up my uo login, is welcome to contact me.

I tried more things, so i have more answers, even. Also, please anybody could state, which libraries i should reinstall and are used for networking via wine.
And any other trick too.

note: technically there is no wine error.

with kind regards, g4b
and, i think i win the nobel price for having the strangest linux problem ever.

---

### Post by daou on 2006-11-16
Is there still a good community in UO? Any good free servers?
I stopped playing in 2000, but never really got over my addiction ;) .

---

### Post by Gargamella on 2006-11-16
it is a beautiful addicting game, the best one probably ever tried

---

### Post by cyborg on 2006-11-17
seems to be libnss3's fault.

deinstalling this library solved everything. could have been some other action, however, i think it was this.

yes, uo is still played, and there are freeshards with a lot of roleplaying, which is even more addictive, but most of which i know are german.

cyborg

---

### Post by greywolf79 on 2006-11-24
Ultima online is an awesome game. The only reason I do not leave windows completely behind in favor of linux. I am looking for a way to run UO in ubuntu 6.10. I am a new user of linux and would appreciate any assistance in getting uo to run in linux.

Also, if you are looking for a good free shard... Demise - it is run by RunUO. Excellent. No other free shard has compared to it so far for me.

---

### Post by Roasted on 2006-11-24
I personally play UOGamers: Hybrid. UOGamers, I believe, also runs the Demise shard. The UOGamers team created RunUO too, just for your information.

Great staff. Great people. You have your typical jerks roaming around but there's a good community there too.

The unique thing about the Hybrid server is the fact that... it's a hybrid server. It combines the best of both worlds, pre-age of shadows and post-age of shadows. Only one facet, Felucca only (the way it should be) along with a few rules of age of shadows. Too much to explain, just a damn good shard.

Sorry I couldn't help, I just dual boot to win2k to get on UO. I didn't even bother trying to get UO to work on wine because I KNEW wine wouldn't support razor. Razor was created by the RunUO team specifically for their servers (Hybrid, etc) and Razor runs off of Microsoft's .net framework and I knew it wouldn't be supported so I didn't bother. Razor is RunUO's version of UOAssist.

---

### Post by greywolf79 on 2006-11-29
I have successfully gotten UO to run on linux using wine. However, I am still unable to access the free shards. Please any help would greatly be appreciated. I am 1 step from ditching the bloated useless code of microsloth... PLEASE !!!! I beg all UO players who use linux to help find the solution.

Note...

Sunuo and uoproxy do not work for some reason. Uoproxy at least installed, but I cannot alter the config file even with super user privaledges (tells me I have not got the needed privaledges).

Thanks ahead of time.

Also, other than the RunUO shards is also a good one you can check out at [www.allureoftheunknown.com](www.allureoftheunknown.com) ... unfortunately they have only Samurai empire support... but lots of extras like pet breeding and new skills and resources (ie different metals and what not).

---

### Post by daou on 2006-12-02
> I have successfully gotten UO to run on linux using wine. However, I am still unable to access the free shards. Please any help would greatly be appreciated. I am 1 step from ditching the bloated useless code of microsloth... PLEASE !!!! I beg all UO players who use linux to help find the solution.

I found this link in UO Stratics a while back. 
[http://uo.stratics.com/content/guides/linux.shtml]("http://uo.stratics.com/content/guides/linux.shtml")

I haven't tried it yet myself, but it tells you how to get UO to run on wine.
Another solution would be to use UO with VMWare.

---

### Post by greywolf79 on 2006-12-04
The problem is I have ultima online working... I cannot access the free servers or as uo calls them, shards. I do not pay for access to the main server, I need to access the free ones. There are many things out there that say they will do it, but none sofar work on linux... I am trying to get to the free shards now that I have uo mondain's legacy working on linux.

---

### Post by sk8dork on 2006-12-04
i have the same problem. i am amazed that this is the best search result i can get when searching for how to play uo on free servers in linux. why oh why do the utilities to get into free shards have to be so complicated that they don't work with wine? i really hate going into windows to play a game that works in linux, just cuz i want to play on a free server.

---

### Post by guest5 on 2006-12-05
how did you get esword to work using wine?

i installed esword, which gives a link on the desktop, but when I click on it I just get an error, 'couldn't display...esword.lnk.

i must be doing something dumb ? or not doing something i'm supposed to be doing, hey?

---

### Post by greywolf79 on 2006-12-06
I agree... I wish it were easier to get these running on linux. I have found help in Wine website for uo, but nothing so far has helped. PLEASE Linux GURUs... HELP!!!

---

### Post by cyborg on 2006-12-10
login.cfg may be a hint.

you need an account (which is not to pay) on a server if you wanna play.

you dont need osi account, unless you want to play the real game with real lots of people.

---

### Post by sk8dork on 2006-12-13
i have it!

ok, it took for freakin ever to figure this out. i can't believe this is nowhere else to be found.

if you have uo working as far as getting to the login screen and you want to join a freeshard, do the following.

get [uo_rice.]("http://stud1.tuwien.ac.at/~e9425109/UO_RICE.htm") (the download is at the very bottom of this very ugly website) this part requires you go into windows first. you run uo_rice in windows, it will auto find UO (it has to be installed in windows obviously) and add a no encryption client exe file, by default named no_crypt_client_2d.exe (if you want to play 3d in linux, think again. think many years from now when that is maybe fixed). you can find the new non encrypted file in your UO directory. you will need to get this file to your ubuntu file system somehow, whether it's accessing the drive in ubuntu if you have that set up, putting it on a usb key, or uploading it to some filesharing site (zshare.net). put it in your UO directory in ubuntu.

get [uo launchpad.]("http://home.cogeco.ca/~xfile/index_files/Page384.htm") (i googled to get this page) this will need no install and just runs from the exe, and wine likes it just fine. you'll need to add an entry for your free shard. for example:
name: Hybrid
ip: login.uogamers.com
port: 2593
account: sk8dork
password: 
client directory: <click browse and point it to the non encrypted file you copied into your UO directory in the ubuntu file system>

the name is not important, you can put your password in the designated field if you want, and if you need to figure out how to get to your hidden wine directory (you should be started in your home directory) type ".wine" with no quotes and hit enter, you'll then be able to navigate to it easily.

click ok and then done and it will add it to the list on the left. click the item in the list and click launch. HOORAY IT WORKS!!!

you will have to re-uo-rice your windows client each time a new patch comes out, if you want to run the latest patch version. as far as i can tell you can play out of date patches on my server. haven't noticed any negative effects to it.

as far as i am aware and as far as i have read there is no other way to play uo on a freeshard in linux. i have tried a bunch of other launchers and they just don't even work cuz wine doesn't like them (they use.NET and stuff like that).

i hope this helps someone out.

---

### Post by greywolf79 on 2006-12-22
Thank you so much for your reply... I will be trying it out tonight after work. Very much appreciated with the help on this link. I have been searching for months now, good to know there are others interested too.

Sk8dork, thank you for this help. I will try tonight and see if it works for me. What shard do you play on? I have an account on Demise, but play Allureoftheunknown right now, allureoftheunknown.com is their website. If you would like to play, I have their ip and port info if you need it. Thanks again. Very helpful.

---

### Post by willskills on 2007-02-14
Presumably there is no linux type macro program like Razor/UO assist? I am sure they were all written for windows.

I would definitely pick up UO again if I could have a 3rd party macro prog :]

---

### Post by ant2ne on 2007-03-08
I got wine and UO to install with little problems. I got a few bugs. I got no sound, and I got a squished view. It is like the normal UO window is stretched horizontaly. I suspect this has something to do with my wider screen laptop monitor.

Any advice?

If UO works in wine, why wouldn't Razor? (a UO macro program) I'm new to Linux and Wine, but not to UO and programing. I'll get you a good macro program that runs in Linux in no time. I doubt it'll be as sweet as Assist or Razor, but it'll keep the corpal tunnel down!! I've already written a few decent programs for this purpose. ;-)

---

### Post by willskills on 2007-04-25
> **will]Downloading UO at the moment, used to play on Defiance myself, after I left Europa.

I am pretty new to linux, but have spoken to a few people, and I'm going to see if I can get razor to work with mono, that would be great  said:**
> http://wiki.winehq.org/MicrosoftDotNet[/url]

Will post back asap, on a side note, UO installed fine with wine, it is now patching :)

[http://www.runuo.com/forums/razor-cutting-edge-uo-assistant/33248-linux-support.html](http://www.runuo.com/forums/razor-cutting-edge-uo-assistant/33248-linux-support.html)

---

### Post by willskills on 2007-04-26
Ok, so it looks like linux is not really viable for playing UO; I mean, the game runs, but if you are serious about your PvP, you need a pretty heavy macro set, and to do that properly, you really need razor or uoassist.

I have a slighty old machine I'm going to install windows on, to play UO - bah. After I saw these posts, I really got the UO itch again, which never really goes away! Now I'm about to install windows /cry

---

### Post by willskills on 2007-04-30
Well, I took the plunge and installed Windows on my old box........ and I have to say, I am absoutely loving UO still! (11 years later)

I am still playing WoW - but raiding Karazhan/Gruul's most nights is just too tiring! Whatever happened to making your own entertainment (a la UO stylee)!

---

### Post by Ripfox on 2007-08-14
Btw UO Rice works under wine, so I don't think you need to use a windows install.

---

### Post by Ripfox on 2007-08-14
Tested this and it works, skipping the step of doing the UORice operation on a windows machine, and just using uorice with wine after you update mondains legacy. I am currently playing on Hybrid with your exact config (except user name of course) :)

---

### Post by ant2ne on 2007-08-29
Easy UO works just fine via Wine. Assist and Razor need .net and advanced API, so no go. 

Is it just me, or will No_Crypt_Client.exe only connect to sphere type shards, and not RunUO type shards?

---

### Post by Mr_J_ on 2007-09-11
I thought I'd post how I got Ultima Online running.

Installed using the official Mondain's Legacy Setup threw Wine.
Update 2d Client. (Since the 3d is no longer supported)
Use UO rice to create the No Crypt Client.
Edit Login.cfg with notepad to change the server address and port to your corresponding shard.

Use your No Crypt Client to play!

(I actually didn't use UO rice, and actually copied an already working Windows install.)
Some already said UO rice works, so it's a small lie. :lolflag:

All I need is an Aplications Menu shorcut to start the client and I'm done.
Sad that I haven't gotten Razor, but you can't get everything. :(

---

### Post by LostMagix on 2007-12-20
but is there anyways to install UOrice without windows?

---

### Post by proxess on 2008-01-12
just run UO rice and then run the no crypt client to play on free shards? thats all?! anyone remember which wine/cedega version 3D client worked on? i think it did work at some time.

---

### Post by Ripfox on 2008-01-22
All credit to everyone who got us on the right track to get free shards going with wine! Awesome work. I have discovered something very important though...DO NOT PATCH AFTER INSTALL. Then you can just run UO Rice from a terminal like this: place it in your home folder and run > wine uo_rice.exe 

Then all you have to do is edit login.cfg to the shard of your choice and BAM your in.

:guitar::guitar::guitar:

---

### Post by Ripfox on 2008-02-07
I forgot to mention that you need to run UO from the No_Crypt_Client_2d.exe file in your .wine/programfiles/eagames folder. Otherwise if you run it from the gnome menu like normal, it will try to use the regular encrypted launcher and begin to update UO.

---

### Post by binarymutant on 2008-03-18
I couldn't install riceuo with wine, the error message said it couldn't find the uo directory, however I found the No_Crypt_Client_2d.exe on the net and would like to share it with everyone still having problems playing this game on a free shard. 

[http://rapidshare.com/files/100559453/No_Crypt_Client_2d.exe.html]("http://rapidshare.com/files/100559453/No_Crypt_Client_2d.exe.html")
which I found at this site:
[http://www.edu.lahti.fi/~iramo/]("http://www.edu.lahti.fi/~iramo/")

So for anyone looking to play on a free shard just download this No_Crypt_Client_2d.exe, put it into your Ultima Online directory, and run it with wine from within that directory.

I've run into no problems playing UO on a free shard :)

---

### Post by Ripfox on 2008-03-26
Funny, UORice works quick and easy here, but thanks for the link fella.

What shard do you play on?

---

### Post by binarymutant on 2008-03-26
I dunno, UO Rice just kept saying it couldn't find the uo installation path and all the info I've read on the net said do it in Windows first which I thought was ridiculous. 
I'm currently looking for a good shard with 100+ people on it and possibly RP on it too, but while I'm searching, uogamers.com and abc-uo are 2 that I like.

---

### Post by Ripfox on 2008-03-27
I'm currently paying on Six Feet Under, very nice.

---

### Post by SirSmegalot on 2008-05-15
I just got this working, did the UORice thing, changed the config file to alterna and simply clicking the decrypted client.exe file

BTW the BEST free UO shard is Alterna-uo

[http://www.alterna-uo.net](http://www.alterna-uo.net)  give it a try

---

### Post by ant2ne on 2008-05-17
Is anyone having problems with compiz and UO? I suspect compiz is crashing my UO.

---

### Post by Macchia on 2008-06-02
anyone tried injection under ubuntu? i still trying to find why it doesn't find the uo window (injection is a uo assist clone)

[http://yoko.netroof.net/eng/injection.htm](http://yoko.netroof.net/eng/injection.htm)

---

### Post by leodido on 2008-06-07
hi guys having prob with UO, i could install it no problem but i'd like to try to play on Hybrid -> [www.uogamers.com](www.uogamers.com) awesome shard btw at least 1000 people on it on the evening and it's renaissance like i think not too sure anyways i could install dot net and razor but razor wont start saying it misses ressources :(

---

### Post by Macchia on 2008-06-08
> **leodido said:**
> hi guys having prob with UO, i could install it no problem but i'd like to try to play on Hybrid -> [www.uogamers.com](www.uogamers.com) awesome shard btw at least 1000 people on it on the evening and it's renaissance like i think not too sure anyways i could install dot net and razor but razor wont start saying it misses ressources :(

sorry to say but razor wont work under linux.

---

### Post by cmileto on 2008-06-13
BS razor works great with wine. Just make sure you are using a current version of wine and then use the winetricks script to install dotnet2. After that install the fontfix with the same winetricks and then razor will install and work perfectly.

I got wine and winetricks from winehq btw :P

---

