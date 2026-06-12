---
title: "Good filesharing program?"
date: 2004-10-14
forum: General Help
---

### Post by ming0 on 2004-10-14
I'm looking for a filesharing program with a good GUI. I would prefer something that is easy to set up/use...

Any suggestions of Ubuntu packages? 

Thanks,

Dean

---

### Post by eNiNjA on 2004-10-15
mebbe gtk-gnutella?

sudo apt-get install gtk-gnutella

---

### Post by WimVriend on 2004-10-15
[quote=ming0]I'm looking for a filesharing program with a good GUI. I would prefer something that is easy to set up/use...

Any suggestions of Ubuntu packages? 

Thanks,

Dean[/quote]

Hello,
Try Gift. You find OpenFT and Gnutella in the Ubuntu collection. FastTrack (kazaa) has to be downloaded and compiled by you. You find it at berlios.de
Greetz
Wim

---

### Post by flygmaskin on 2004-10-15
If you only want music, I can recommend nicotine (apt-get install nicotine).

> Description: graphical client for the SoulSeek peer-to-peer system
 Nicotine is a client for SoulSeek, a light and efficient file sharing
 system, written in Python and using the GTK2 toolkit, based on the
 PySoulSeek project.

 It features uploading, downloading, searching and chatting, with
 strict bandwidth control, and tries to look like PySoulSeek.

---

### Post by HungSquirrel on 2004-10-15
I used DCGUI-QT the last time I fileshared in Linux.  DC hubs require you to have a large amount of stuff shared just to get in, though.  Linux ISOs work nicely for creating a nice, large, *legal* share to get into DC hubs.   :twisted:

---

### Post by ming0 on 2004-10-15
Thanks for all the suggestions--I'll post some reviews on the packages that I tried. I was looking for something relatively easy to set up, that worked well (got lots of search hits and downloaded things fast) and that had an intuitive and easy to use GUI. I forwarded all necessary ports for each program. Now for the reviews: 

**DCGUI-QT**: This is somewhat difficult to set up, and I couldn't find a way to bookmark hubs as favorites. I really like Direct Connect, and my main complaint with this program is its unbelievably cluttered GUI. It is good for getting large files (like videos or isos), but as was mentioned above, you need to share lots of stuff to get onto the hubs. This client will dock into the tray, freeing up space on your taskbar.

**Nicotine**: This is probably the easiest to set up and most intuitive to use--just make up any username and password and log in. I didn't get as many hits on music I was looking for, but once you find a song you want, you can download the folder that the user held the file in. Also, it's primarily for music, but you can get other sorts of files.

**Gift**: I downloaded Gift and OpenFT, but they were hard to get working--and I wasn't looking to compile anything, so I didn't even try to get the FastTrack plugin working. If you're into Kazaa, this might be worth all the trouble.

**Gtk-Gnutella**: This program was moderately difficult to set up, and doesn't have a very intuitive GUI. I got quite a few hits once I got it running, but I was never able to figure out why some hubs were blacklisting me (had something to do w/ zlib??). I was able to get a decent number of downloads going.

**Xmule**: Not terribly easy to set up, and I wasn't able to get a lot of downloads going--I seemed to get a few started, but wasn't able to get much fully downloaded (other than a brittney spears song--which is sort of my litmus test). This client will dock into the tray, freeing up space on your taskbar.

If anyone has any suggestions, or thinks I'm mis-using or mis-representing their favorite client, let me know :)

I'll post more reviews if I find any more programs to try.

--Dean

---

### Post by oddabe19 on 2004-10-15
[quote=HungSquirrel]I used DCGUI-QT the last time I fileshared in Linux.  DC hubs require you to have a large amount of stuff shared just to get in, though.  Linux ISOs work nicely for creating a nice, large, *legal* share to get into DC hubs.   :twisted:[/quote]

That's what I used... so I have a whole partition just of Linux ISO's... so the RIAA doesn't bust me.

---

### Post by eNiNjA on 2004-10-15
After reading this, I installed Nicotine. So far, so good.

Thanks flygmaskin =)

---

### Post by -baHam- on 2004-10-15
Limewire is the best.

---

### Post by bpmckie on 2004-10-15
I'll second on Limewire. Has worked on whatever machine I am using Windows or Linux.

B.

---

### Post by ubuntu-geek on 2004-10-15
[quote=-baHam-]Limewire is the best.[/quote]

agreed limewire is good

---

### Post by ming0 on 2004-10-16
I'd like to try Limewire, but I can't get Java working :( 

How did you get java going? (you could post to the thread below)

[http://ubuntuforums.org/viewtopic.php?t=628&amp;highlight=java](http://ubuntuforums.org/viewtopic.php?t=628&amp;highlight=java)

---

### Post by -baHam- on 2004-10-16
I answered ;)

---

### Post by philippe on 2004-10-24
[QUOTE=ming0]**DCGUI-QT**: This is somewhat difficult to set up [...]
**Nicotine**: This is probably the easiest to set up and most intuitive to use [...]
**Gift**: I downloaded Gift and OpenFT, but they were hard to get working [...]
**Gtk-Gnutella**: This program was moderately difficult to set up [...]
**Xmule**: Not terribly easy to set up, and I wasn't able to get a lot of downloads [...] 
I'll post more reviews if I find any more programs to try.
--Dean[/QUOTE]

thank you for sharing your reviews, Dean
filesharing is the most important popular feature missing on ubuntu next to music/video playback.

i read xmule has been abandoned by it's authors ?
did you have a look at amule (fork from emule; both edonkey2000/ed2k clients) ?
also i like **mldonkey** a lot, but on my ubuntu it does not connect ...
[http://mldonkey.org/](http://mldonkey.org/)
It is a multi p2p network client, supporting the following networks:
    * eDonkey (uses eMule extensions, recognizes MLdonkey, eDonkey, eMule, lMule and Shareaza)
    * Overnet
    * BitTorrent
    * Gnutella/Gnutella2
    * FastTrack (Kazaa)

---

### Post by Julius on 2004-10-24
> **philippe]thank you for sharing your reviews, Dean
filesharing is the most important popular feature missing on ubuntu next to music/video playback.

i read xmule has been abandoned by it's authors ?
did you have a look at amule (fork from emule said:**
> http://mldonkey.org/[/url]
It is a multi p2p network client, supporting the following networks:
    * eDonkey (uses eMule extensions, recognizes MLdonkey, eDonkey, eMule, lMule and Shareaza)
    * Overnet
    * BitTorrent
    * Gnutella/Gnutella2
    * FastTrack (Kazaa)
 I have tried MLdonkey:

apt-get install mldonkey-server mldonkey-gui

apt-get couldn't found kmldonkey, so I'm using the web UI.

---
This is what I've done
apt-get install mldonkey-server mldonkey-gui

You will be asked wether to start mldonkey at start or not.

mkdir /home/username/mldonkey
cd /home/username/mldonkey
mlnet &

Then go to: [http://127.0.0.1:4080/](http://127.0.0.1:4080/)
It will automatically connect to 3-4 servers. I downloaded a file successfully, but it downloaded it 4 times! (Everytime it finished, it started again). But I think it was just an error.

No idea on how to "turn-off" the server :P

---

### Post by jgeorgeson on 2004-10-24
I use gift and the apollon UI, giftoxic is nice too but it doesn't have a systray icon. Although the KDE pacakges available in ubuntu don't seem to have a compatible systray so the systray icon for apollon just floats in it's own window. Anyhow, you don't need to do any source compilation for the FastTrack (kazaa) plugin, just add this apt source

deb [ftp://ftp.berlios.de/pub/gift-fasttrack/](ftp://ftp.berlios.de/pub/gift-fasttrack/) unstable main

---

### Post by im_ka on 2004-10-24
imho, there's no really good movie sharing app. i'm probably just too impatient to wait  for days. i much rather go and rent a dvd for 0,50-1 € per day, it's right around the corner.

for music, nicotine beats everything. i like the "personal" feel of it. i always have it running, and let people download.

---

### Post by irifan on 2004-11-10
there is an amule package for ubuntu available at [http://download.berlios.de/amule/amule_2.0.0rc7-ubuntu1_i386.deb](http://download.berlios.de/amule/amule_2.0.0rc7-ubuntu1_i386.deb)

it has not been compiled against gtk2 so it doesnt look as cool as with mandrake, but it works ;) 


full info at the amule forum
[http://forum.amule.org/thread.php?sid=44db1bcbd0dbc96cb67dc1a673bb9b8b&postid=21131#post21131](http://forum.amule.org/thread.php?sid=44db1bcbd0dbc96cb67dc1a673bb9b8b&postid=21131#post21131)

---

### Post by shoelessmike on 2004-11-15
Bittorrent coupled with suprnova.org or lokitorrent is great for movies and TV shows, just apt-get bittorrent (if i remember correctly). Unfortunately, you're stuck with the old bittorrent client instead of Azeurus which is quite nice, but then again it's automatically integrated so I'm happy.

---

### Post by mattyh on 2004-11-15
Azureus is as easy as installing Java, and then untarring Azureus to wherever you like.  As for integration, that was discussed on another topic.  (I believe the bittorrent one).  It amounts to a few clicks that set it as the default handler of .torrent.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=shoelessmike]Bittorrent coupled with suprnova.org or lokitorrent is great for movies and TV shows, just apt-get bittorrent (if i remember correctly). Unfortunately, you're stuck with the old bittorrent client instead of Azeurus which is quite nice, but then again it's automatically integrated so I'm happy.[/QUOTE]
 I use Azureus. Its just a matter of installing java and extracting azureus to where you want it, making a shortcut to the menu/panel and downloading :)

---

### Post by norwyn on 2004-12-05
When I used windowsXP, Azureus took VERY much cpu-power. How does it work in Ubuntu?

---

### Post by BWF89 on 2004-12-05
I'm still useing Windows but since I try not to install non free software I usually use Limewire and Shareaza...

Speaking of which, does anyone know where I can download "The Free Software Song"?, I tried Limewire, Shareza, and even the proprietary WinMX :shock: ...

---

### Post by talkingwires on 2004-12-11
[QUOTE=BWF89]I'm still useing Windows but since I try not to install non free software I usually use Limewire and Shareaza...

Speaking of which, does anyone know where I can download "The Free Software Song"?, I tried Limewire, Shareza, and even the proprietary WinMX :shock: ...[/QUOTE]I remember that song appeared on Slashdot a long time ago. I tried a quick search, but couldn't find it. Then again, Slashdot uses what may be the worst search engine ever created for a website...

---

### Post by mojorising on 2004-12-14
aMule is the best I have seen. I am not sure if it is the apt-get repositories but it's worth a look. 

It is very good and easy to use. 

Mike

---

### Post by adbak on 2004-12-15
[QUOTE=talkingwires]I remember that song appeared on Slashdot a long time ago. I tried a quick search, but couldn't find it. Then again, Slashdot uses what may be the worst search engine ever created for a website...[/QUOTE]
 To search just one site, go to [http://www.google.com](http://www.google.com) and in the search bar type "site://slashdot.org <search criteria>".

Subsitute slashdot.org for any other website.

---

### Post by ubuntu_demon on 2004-12-29
What is the best emule client for linux ? Amule , xmule or another ?

having a friendslist that don't have to wait in queue for long is a pro

---

### Post by piedamaro on 2004-12-30
Stay away from xmule, a little research on amule's forum or on goggle will show you why ;)
Amule can use friend slot. Slotted friends are granted to start uplading once a slot is freed (could be even an hour), that's all, no bandwidth granted.

---

### Post by Perfect Storm on 2004-12-30
amule
Azureus
Limewire

All great! Check out the unofficial starter guide for ubuntu on how to install: [click here](http://ubuntuguide.org/index.html)

---

### Post by Quest-Master on 2004-12-30
It hasn't broken out in popularity yet, but I must recommend the BitTorrent users to try out a new GUI client on the scene. It's extremely similar to Azureus, and functions in the same way.

Why use it? It was coded much better in a more robust language; Python. It eats very little CPU power and is easy to use as well. Many people I know use it since it doesn't crap their resources down quickly like Azureus. It is known as G3Torrent.

Be sure to give it a shot at [http://g3torrent.sf.net/](http://g3torrent.sf.net/).

---

### Post by ubuntu_demon on 2004-12-31
Can you give me a link about this ?

I found some text on the xmule website saying amule has more features but xmule will be more extendible.

---

### Post by Uuranor on 2004-12-31
[QUOTE=demon666_nl]Can you give me a link about this ?

I found some text on the xmule website saying amule has more features but xmule will be more extendible.[/QUOTE]
 I use Amule with Gtk2 :D
It is great!

---

### Post by clparker on 2005-01-18
Anybody know an easy way to install nicotine 1.0.8 to Warty?

---

### Post by Error1312 on 2005-01-18
'sudo apt-get install nicotine ' did the job for me.

But I still prefer LimeWire. Very good for music.

---

### Post by clparker on 2005-01-19
> clparker@SHODAN:~ $ sudo apt-get install nicotine
Reading Package Lists... Done
Building Dependency Tree... Done
nicotine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
 
 
 See, I allready have 1.0.7 Installed, Again I ask, Does Anybody know to install 1.0.8x to Warty?

---

### Post by Ste on 2005-01-19
[QUOTE=clparker]See, I allready have 1.0.7 Installed, Again I ask, Does Anybody know to install 1.0.8x to Warty?[/QUOTE]
 Download it from the site, unpack the tarball then it should run straight out of that.

[http://nicotine.thegraveyard.org/](http://nicotine.thegraveyard.org/)

---

### Post by theh0g on 2005-01-22
[QUOTE=Uuranor]I use Amule with Gtk2 :D
It is great![/QUOTE]

How did you make it use Gtk2?! The default using Gtk1 is SO ugly!

---

### Post by animalstyle on 2005-02-18
where can you get limewire?  Its not in any repositories, and the site only lists an rpm package

---

### Post by pumpkinpatch on 2005-02-18
I installed nicotine but I doesn't want to let me log on.  I set up my profile but it just keeps saying invalidpas.

---

### Post by ow50 on 2005-02-18
[QUOTE=pumpkinpatch]I installed nicotine but I doesn't want to let me log on.  I set up my profile but it just keeps saying invalidpas.[/QUOTE]

Maybe you are trying to connect with a username that's already taken. Select something very bizarre as your username.

---

### Post by ceti on 2005-02-19
[QUOTE=animalstyle]where can you get limewire?  Its not in any repositories, and the site only lists an rpm package[/QUOTE]

1 - Go to:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

2 - Find ADD-ON APPLICATIONS and click on:
9 -How to install P2P Gnutella Client (LimeWire)?

3 - On 3 - Download LimeWireLinux.bin: Here or Here, click on the first Here to download LimeWireLinux.bin

To install, follow the remaining instructions and you're done.

---

### Post by piedamaro on 2005-02-19
[QUOTE=theh0g]How did you make it use Gtk2?! The default using Gtk1 is SO ugly![/QUOTE]
You need gtk2 compiled wxwidgets and you need to recomple aMule against them.

---

### Post by paretooptimum on 2005-03-09
I've put a page on the wiki on filesharing. Can you all please contibute to it and make it better.

[http://www.ubuntulinux.org/wiki/FileSharingP2PPeerToPeer](http://www.ubuntulinux.org/wiki/FileSharingP2PPeerToPeer)

---

### Post by Bogart on 2005-03-30
[QUOTE=-baHam-]Limewire is the best.[/QUOTE]

Limewire works good. I use it together with eDonkey2000, and i must say eDonkey is the best for me. It has a much larger number of files and downloads go fast in general.

However, the best of eDonkey is that it's the easiest I've found for Ubuntu. You just go to [eDonkey2000](http://www.edonkey2000.com/) and download the linux GUI version. Untar the file, and double-click the file runDonkey.sh. And that's it, the program will open and start working. Absolutely no installation needed !    :D

---

### Post by philippe on 2005-03-30
hello Bogart

> However, the best of eDonkey is that it's the easiest I've found for Ubuntu.
do you use the paid version or the one with advertising ?
did you try MLDonkey or aMule too, which are using the same network (ed2k) ?

kind regards     philippe

---

### Post by ubuntu_demon on 2005-03-31
amule 2.0.0.0.rc7 included in hoary works like a charm :)
I also use bittorrent for my (legal) anime and sometimes a linux cd-image.

---

### Post by Bogart on 2005-03-31
[QUOTE=philippe]hello Bogart

> However, the best of eDonkey is that it's the easiest I've found for Ubuntu.
do you use the paid version or the one with advertising ?
did you try MLDonkey or aMule too, which are using the same network (ed2k) ?

kind regards     philippe[/QUOTE]

I use the free version. Advertising? I didn't see it around. It looks like the Linux version has no ads at all (the Windows free version has).

I tried MlDonkey, but as reported by other users, it didn't connect to the networks correctly for me either.

I didn't try aMule in Ubuntu, but I did in another distro and in Windows and it's not quite the same as eDonkey. The network they connect to must be different, since eDonkey has much more files available for download (and much more sources to d/l those files).

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=Bogart]I use the free version. Advertising? I didn't see it around. It looks like the Linux version has no ads at all (the Windows free version has).

I tried MlDonkey, but as reported by other users, it didn't connect to the networks correctly for me either.

I didn't try aMule in Ubuntu, but I did in another distro and in Windows and it's not quite the same as eDonkey. The network they connect to must be different, since eDonkey has much more files available for download (and much more sources to d/l those files).[/QUOTE]
 regarding amule :

amule connects to the same network.as xmule,emule,mldonkey and edonkey. Amule uses the emule protocol which is better than the original edonkey protocol because you are rewarded when you upload more by getting through the queues faster and things like that.

xmule and amule in warty suck. amule in hoary rocks. But ofcourse you have to upload at least 10 kbyte/s to get it working a bit and you have to connect to a good server like razorback2. And its best if the pc running amule is permant online or at least a big part of the day.

But you can find good movies on the ed2k network. And your downloads don't take your ping down like bittorrent does if you don't cap it.

---

### Post by Bogart on 2005-04-02
[QUOTE=demon666_nl]regarding amule :

amule connects to the same network.as xmule,emule,mldonkey and edonkey. Amule uses the emule protocol which is better than the original edonkey protocol because you are rewarded when you upload more by getting through the queues faster and things like that.
[/QUOTE]

eDonkey does connect to the eMule/aMule network it you enable it, but as default it connects to the Overnet network. That is why I say there are much more files available for download and more sources to download from and it goes faster. Well, at least for me it does. Besides, it works fine in Warty and no installations needed.

But I gues each one should try different options and see which one is best for them.

---

### Post by Kimm on 2005-04-03
if you have wine installed you can run Ares Lite, it connects to, as far as I know, the Warez network and has plenty of users. If you have Crossover Office the standard version of Ares will work, this wount work just in wine however :razz:

---

### Post by Vertical on 2005-04-11
Where I can get amule package compiled for GTK2 for Ubuntu? I have wxgtk2.5.3 and wxWidgets2.5.3 installed

---

### Post by boysha on 2005-10-12
To all of you!

I am an old guy who loves computers and lately I fell in love with UBUNTU.
I was trying to find an answer to the question of good filesharing program and you guys helped even more then I could've imagine.

Thank you all!

Best of luck!

Neb

---

### Post by FaceLeg on 2007-03-29
I personally like PySoulSeek...

I tried to use SoulSeek in wine - Far, far too slow.

Then I tried Nicotine...  The software is great, but it couldn't seem to find any of the artists I wanted.  Which is the reason I use a separate download program for music (I like some rather obscure stuff).

PySoulSeek found the files I wanted, and found them FAST!

I use Azureus for all my other downloading.  Yes it does rape my CPU, but I am used to it and it works well.  Nice range of plugins available as well.

---

