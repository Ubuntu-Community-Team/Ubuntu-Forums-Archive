---
title: "Can Wine run these programs?"
date: 2008-05-10
forum: General Help
---

### Post by avrilrox on 2008-05-10
Hey, i want to install some applications that do not run under Ubuntu and I'd like to know if Wine can be used.

**I want to run these applications:**

[I]Adobe Photoshop CS3 Extended.
Windows Live Messenger 9
Winscp (Ftp client)
Can i run games, such as Call of Duty 2? :)[/I]


I did use gFTP but it lacks something i really need, thats why i need Winscp.

Thank you very much.

Also, *will applications run slower using Wine*? Will they hang sometimes?

---

### Post by TeoBigusGeekus on 2008-05-10
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Check this link

---

### Post by avrilrox on 2008-05-10
^Thank you for the link!

---

### Post by Victormd on 2008-05-10
Check the Wine site:
[www.winehq.org](www.winehq.org)

Also, you might want to download wine-tools:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

It should be straight forward. If you haven't done so, add wine to the repositories to install the most up-to-date version by copying and pasting the following lines (this is assuming you are using Hardy)

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Then, update the list and install Wine:
```
sudo apt-get update
sudo apt-get install wine
```

If you've already installed it, then:
```
sudo apt-get upgrade
``` to update the installed wine to the most up-to-date version.

Once that's done, let me know the softs you want to install and we'll give it a go...
As for the appz you've listed, I can say that I've installed Photoshop CS2 (check the winehq database to see if CS3 is supported).

For messenger, you might want to try amsn (has all functionalities of msn, including audio/video) or emesene (this is the one I use but lacks video support). As for the other 2 appz, check the winehq database for them.

---

### Post by avrilrox on 2008-05-10
> **Victormd said:**
> Check the Wine site:
[www.winehq.org](www.winehq.org)

Also, you might want to download wine-tools:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

It should be straight forward. If you haven't done so, add wine to the repositories to install the most up-to-date version by copying and pasting the following lines (this is assuming you are using Hardy)

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Then, update the list and install Wine:
```
sudo apt-get update
sudo apt-get install wine
```

If you've already installed it, then:
```
sudo apt-get upgrade
``` to update the installed wine to the most up-to-date version.

Once that's done, let me know the softs you want to install and we'll give it a go...

W.O.W.!!!!!
Thank you!!!!!
I will do that! Thank you!!!!

---

### Post by Gina on 2008-05-10
I use FileZilla for FTP.

---

### Post by avrilrox on 2008-05-10
I couldnt install Filezilla for some reason. Can you help me?

---

### Post by Victormd on 2008-05-10
> **avrilrox said:**
> I couldnt install Filezilla for some reason. Can you help me?

It's in the repos. What happened when you tried to install?

From the terminal, all you have to do is:
```
sudo apt-get update
sudo apt-get install filezilla
```

If this doesn't work, you might want to try selecting other sources for your progz, i.e., SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and mark all four sources under the Ubuntu Software tab, also, change the "Download from:" server to "Main server" (if not selected already). Then go to the "Updates" tab and select all the "Ubuntu updates" options. Once you've done that, run the two code lines posted above and that should do the trick.

---

### Post by avrilrox on 2008-05-10
> **Victormd said:**
> It's in the repos. What happened when you tried to install?

From the terminal, all you have to do is:
```
sudo apt-get update
sudo apt-get install filezilla
```


Thanks! I downloaded filezilla from the internet and i didnt know how to install it.

I'm not at home now, and im using Windows so i can't try to do anything now. I'll be using Ubuntu in 3-4 hours.

Seriously, you guys are amazing. Thank you for your help!

---

### Post by sekinto on 2008-05-10
If they don't work in WINE you could give these programs a try:

> Adobe Photoshop CS3 Extended
Well there is GIMP, although you might not like it compared to Photoshop CS3.
> Windows Live Messenger 9
Kopete, aMSN, Pidgin?
> Winscp (Ftp client)
There are plenty of FTP clients avaible for Linux.

---

### Post by Victormd on 2008-05-10
> **avrilrox said:**
> Thanks! I downloaded filezilla from the internet and i didnt know how to install it.

I'm not at home now, and im using Windows so i can't try to do anything now. I'll be using Ubuntu in 3-4 hours.

As for installing anything using wine, here are a few considerations:
1. Familiarize yourself with the WINE environment/configuration, you'll need it depending on the applications you install;
2. When installing from a CD/DVD-ROM, it's usually better to start the install from the terminal, that way, you'll be able to see what's happening and check for errors (I can help you with this when the time comes);
3. Some programs require you to setup a virtual display (under WINE configuration) at least to install them. You can remove the virtual display settings after all is installed;
4. Don't expect them to work right away. You might have to play around quite a bit to get the programs running;
5. there was something else I wanted to say but it just ran out of my head... probably to go get a beer or something... better go catch it... :)
6. If your program list is extensive, you might consider Virtualbox... but I would suggest using the linux alternatives when possible.

---

### Post by avrilrox on 2008-05-10
> **sekinto said:**
> Well there is GIMP, although you might not like it compared to Photoshop CS3.
Yeah... I prefer PhotoShop, plus i have loads of brushes for Photoshop :/

> **sekinto said:**
> 
Kopete, aMSN, Pidgin?

Do they all run under Ubuntu? I do like Kopete and aMSN. Thanks!

> **sekinto said:**
> 
There are plenty of FTP clients avaible for Linux.
I couldnt find any! They were all for Windows! :lolflag:

---

### Post by avrilrox on 2008-05-10
> **Victormd said:**
> As for installing anything using wine, here are a few considerations:
1. Familiarize yourself with the WINE environment/configuration, you'll need it depending on the applications you install;
Yes, it will be necessary.
> **Victormd said:**
> 
2. When installing from a CD/DVD-ROM, it's usually better to start the install from the terminal, that way, you'll be able to see what's happening and check for errors (I can help you with this when the time comes);
Right.
> **Victormd said:**
> 
3. Some programs require you to setup a virtual display (under WINE configuration) at least to install them. You can remove the virtual display settings after all is installed;
Ok.
> **Victormd said:**
> 
4. Don't expect them to work right away. You might have to play around quite a bit to get the programs running;
Sounds like its not going to be easy to install them...
> **Victormd said:**
> 
5. there was something else I wanted to say but it just ran out of my head... probably to go get a beer or something... better go catch it... :)
:lolflag:
> **Victormd said:**
> 
but I would suggest using the linux alternatives when possible.
Yes, definitely.

---

### Post by itaintover on 2008-05-10
Photoshop CS2 works perfectly with WINE, i hear there can be problems running CS3 cause Wine doesn't support it yet

---

### Post by avrilrox on 2008-05-10
> **itaintover said:**
> i hear there can be problems running CS3 cause Wine doesn't support it yet
:(
Any links please?

---

### Post by liquidfunk on 2008-05-10
I'd recommend Emesene as your MSN client. I know Pidgin is great and all but I think Emesene is a bit more attractive :D

 Oh and COD2 works like a dream, was playing it yesterday ^^

---

### Post by itaintover on 2008-05-10
> **avrilrox said:**
> :(
Any links please?

check this out [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

technically you can run CS3 through wine, but it take some work to do this and it doesn't work too good

---

### Post by OoooMatron on 2008-05-10
instead of winscp nautilus works pretty good.

just type

ssh://username@hostname:port

and away you go.

same works for ftp.

---

### Post by AndyCooll on 2008-05-10
> **avrilrox said:**
> I couldnt find any! They were all for Windows! :lolflag:

Just wondering how you are searching for applications. You shouldn't need to to do any searching on the Internet, they should all be in the repos. 
There are two quick and easy ways to get your hands on apps for Ubuntu: 

You can use Applications > Add/Remove and do a search. I typed in ftp and came up with a long list. You place a tick in the appropriate box for the app you want. click Apply Changes, enter your password ...done, it's installed!

The second method is to use System > Administrations > Synaptic Package Manager. This a slightly more advanced front end to the above procedure. Even this is easy to use though.

:cool:

---

### Post by avrilrox on 2008-05-10
> **AndyCooll said:**
> Just wondering how you are searching for applications. You shouldn't need to to do any searching on the Internet, they should all be in the repos.

Oh! Ok, thanks!

---

### Post by avrilrox on 2008-05-10
Ok, i installed Filezilla using Synaptic! That was really easy!

---

### Post by atomkarinca on 2008-05-10
Emesene should be in the repos, too. That's a very slick WLM client.

---

### Post by minus198 on 2008-05-10
> **avrilrox said:**
> Hey, i want to install some applications that do not run under Ubuntu and I'd like to know if Wine can be used.

**I want to run these applications:**

[I]Adobe Photoshop CS3 Extended.
Windows Live Messenger 9
Winscp (Ftp client)
Can i run games, such as Call of Duty 2? :)[/I]


I did use gFTP but it lacks something i really need, thats why i need Winscp.

Thank you very much.

Also, *will applications run slower using Wine*? Will they hang sometimes?

Emesene for Windows Live Messenger.
FileZilla for Winscp.
And why not buy Quake, Unreal Tournament, Quake Wars: Enemy Territory as they all run nativly in linux. No need for Wine. :)

And also: The Valve Source engine is being ported to linux at the moment. Which means that Half Life 2, CS: Source an other games will work nativly in linux.

edit: Ow.. I missed that the thread was 3 pages long. So I might have repeated what every one else has been saying.

---

### Post by Irony on 2008-05-10
I used to use gftp but found it a bit buggy when shunting more than one file at time.

I now use Nautilus (the file browser) - just open up the folder you want to transfer stuff from and then go File > Connect to Server and drag your stuff over. Edit if something doesn't want to go then hit refresh on the server window and do it again.

---

### Post by Victormd on 2008-05-11
Just thought I'd post a screenshot with some options for you...
You'll see that I'm running firefox on one workspace, virtualbox with Windows XP on workspace 2, MS excel and MS word on workspace 3, and photoshop on workspace 4...

---

### Post by itaintover on 2008-05-12
> **Victormd said:**
> Just thought I'd post a screenshot with some options for you...
You'll see that I'm running firefox on one workspace, virtualbox with Windows XP on workspace 2, MS excel and MS word on workspace 3, and photoshop on workspace 4...

nice alternative, yeah right, try running that on an average persons's laptop

---

### Post by Th3Professor on 2008-05-12
> **Victormd said:**
> Just thought I'd post a screenshot with some options for you...
You'll see that I'm running firefox on one workspace, virtualbox with Windows XP on workspace 2, MS excel and MS word on workspace 3, and photoshop on workspace 4...

Which option do you have enabled (in compiz?) to get that workspace view?

---

### Post by Victormd on 2008-05-13
> **itaintover said:**
> nice alternative, yeah right, try running that on an average persons's laptop

I never said it was running as smoothly as possible (but it was running pretty smooth, and check my specs on my signature)... I was just showing that it could be done... :)

---

### Post by Victormd on 2008-05-13
> **Th3Professor said:**
> Which option do you have enabled (in compiz?) to get that workspace view?

That's the EXPO plugin under DESKTOP...

---

### Post by Th3Professor on 2008-05-15
> **Victormd said:**
> That's the EXPO plugin under DESKTOP...

Ahh... ok, thanks. :) I already had expo... it just had the default "deformation" set to none; it had to be set to "curve".

---

### Post by Dusal on 2008-05-18
Check this link:

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=6584](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=6584)

---

