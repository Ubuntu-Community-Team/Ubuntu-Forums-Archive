---
title: "Impossible"
date: 2008-05-01
forum: General Help
---

### Post by Antdemo on 2008-05-01
this Ubuntu is so hard for me, i don't understand all these commands and all this blah d blah crap, i read alot on google but people just say /kjhd/dssasd/adad you know, im like ok wtf,i understand you type this in but what a way to run a os

it must be good because you guys enjoy using it, and i'd love to be the same but im confused, lost, and my head is really fooked up, ok i need help big time.

Just installed linux ubuntu, 1st time on it, now all i want to do is this:, copy a plug to firefox pplugins but i can't, the root has the permission and i need to do some code line to enable me to use this permissions for me to paste into the the folder but its locked up with permissions which does my head in but its for safety so i gusse it helps others.

ANyway thats just 1

second do i need to download all my drivers for this linux? how do i update?

thnx alot guys i really do respect those to take time and to help me, i enjoy helping others on other forums just like you, so give me some good feedback

thnx guys have a wonderful day

also, can i play gta san andreas on this linux? i have gta sa on a disk and 1st i bought it but will it let me install on linux? don't have time to check it out as i gtg fast so cya

---

### Post by chrisccoulson on 2008-05-01
First of all, what plugin are you trying to copy across to your Firefox plugins folder? The reason I ask is because the common plugins are available through the software repositories (Add / Remove or Synaptic), so you shouldn't have to do this.

As for the drivers, most of your hardware is probably supported by drivers in the form of kernel modules which are already on your system, so you shouldn't need to install much else:) Do you notice any particular bit of hardware which isn't working? The only extra drivers you might need to install would be for wireless cards or graphics cards. Could you tell us what graphics / wireless card you have? 

As for GTA San Andreas - this is a Windows only game, but it might work under Wine (installable from Synaptic), or [**_Cedega_**]("http://www.transgaming.com/") (but this isn't free).

Hope that helps:)

---

### Post by TeoBigusGeekus on 2008-05-01
Welcome to Ubuntu!
First of all, relax...
Nobody started using linux knowing everything about it, it all comes up with experience. I started a few months ago as a total noobie and now I can find my way through most of the situations.

If the terminal scares you, don't use it... Or, better, use it only when it's necessary: most of the common operations in Ubuntu can be done through gui, so... relax!

A good starter's guide for the terminal can be found here
[http://www.unixguide.net/linux/linuxshortcuts.shtml]("http://www.unixguide.net/linux/linuxshortcuts.shtml") 
although a search on these forums or even google will give you a lot more.

About your first question... To copy a file from one directory to another you use the command cp
```
cp /path/to/file/nameoffile.extension /new/path/of/file
```
In order to do this having root priviledges, you need to precede your command with the word sudo.
```
sudo cp /path/to/file/nameoffile.extension /new/path/of/file
```
Ubuntu will ask you for your password, just type it and you are done.

About your second question...If everything works ok, then you don't need to download anything. Ubuntu has installed everything for you. To update your system, go to menu System->Administration->Update Manager
Press Check (you will be prompted for password) and Ubuntu will check for available updates.

Third and final question... There is a piece of software in Linux called Wine (available through the Add/Remove dialog box) that will let you run *some* window$ programs in Linux. Wine has a database which you can check for compatibility of your game.
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

I'm gonna repeat my advice to you: RELAX!!!

Take it easy and you are gonna enjoy one of the best os's out there - in a few weeks you will be surprised with yourself...

And again...

WELCOME!!! :)

---

### Post by Antdemo on 2008-05-01
Thank you very much guys, I'll give it ago, Im dead busy at the moment, I don't have much access to the pc alot, I work so much all this frustrates me and any time I want to do something , their is either a phone call or work to atend to, like paper work, to stressfull and I can't try what you guys said as I'm busy, I'd rather have this time to post this comment because I respect those that help and take their time.

Thanks alot again.

I'm not a releaxed person, when you get in my job line its frustrating and to much sometimes, bascially i do paper work adding up blah blah, lol.

anyway cya and thanks ill give it ago when I getback, i gtg out again to see some clients.

Thanks again.

Forgot to mention, I was on youtube and it asked me for the flash player, thats the one im trying to copy and paste as I googled how to install it but I can't find much, just things that say copy the .so file in firefox plugins



*Edit8

I got time here

Ok I clicked terminal but i type that in and it says unknown dictinary, well, of course, but like I said, Im new and I would'nt know what to put in file path and all that

maybe usr/firefox/flash.so?

i have no idea but i want to copy something from the desktop to the firefox plugs folder.

o god i feel odd about this hehe

---

### Post by TeoBigusGeekus on 2008-05-01
I don't use firefox, but I think the path to its plugins is

```
/usr/lib/firefox/plugins
```

So the command should be

```
sudo cp /home/yourusername/Desktop/flash.so /usr/lib/firefox/plugins
```

But before you do that... What are you trying to do? Do you want to install flash? You should do this through Synaptic Package Manager...

---

### Post by bollix47 on 2008-05-01
You might also consider opening Synaptic Package Manager and installing ubuntu-restricted-extras.  It includes the flash plugin among other goodies.

---

### Post by spudratic on 2008-05-01
the flash is in the repo.Then name to search for is 'flash non free'.Now I'm not sure it  will show up at first,SO do this,go to the top panel open system, administration, software sources and make sure the boxes for ubuntu software are checked all mine are the go to the next tab third party software and make sure that conical is checked also before you close uncheck the cd options at the bottom of the ubuntu software choices tab this alone will have you going nuts putting the cd in and out.Close the software sources.Next go to system again , administration, synoptic package manager.Hit reload in the upper left conner then search and put in flash.you want flash-nonfree from the search results.It seems to work pretty well on fire fox 3.5 but does crash on utube from time to time.If it crashes to muck you can down grade fire fox try to install flash from the adobe site or wait for ubuntuzilla to get updated to work with firefox3.5.Oh just to be certain make sure that no other flash package is installed like gnash.If there are they will show up in the search with green boxes they are installed right click and select completely remove,this is just for flash.also you might want to get java6.



Wait!!there are some good posts on everything needed on fresh installs.here this is a good guide to follow I used it [http://ubuntuforums.org/showthread.php?t=766683&highlight=xorg+hardy](http://ubuntuforums.org/showthread.php?t=766683&highlight=xorg+hardy) this should give you all you need for video including flash.

---

### Post by Antdemo on 2008-05-03
thanx alot guys, I have done this and it works well.

and those links you posted I am learning those right now, and another thing, i followed what that guy said about updating and thats great I took your advice and I'm all good now.

Ok, guys I respect this alot so thanks, I added a thanks next to, if I can help you guys in anything for you, such as rep? do you have one? I'll post that, anyway on another forums I use someone was asking about how to install unbuntu and vista, well I gave him all your credit and wrote and told him the links you gave him.

I also provided link to this page so that hopefully he can thank you.

Anyway, thanks alot.

Anthony

---

