---
title: "New to Linux / Need Help (again)"
date: 2007-04-09
forum: General Help
---

### Post by Bashed on 2007-04-09
Although I posted a few times asking for help, I was never able to get all the details I need. I do appreciate any help given, and I hope this time I get all the possible info and answers here on this thread.  I have tried to switch to linux, was not happy but here I am again trying and won't quit. I hope in light of this you linux gurus can assist a new fellow in town to switch smoothly and without the temptation to go back to Windows. While I'm not a MS hater nor have anything against Vista, I would not mind trying linux to get the free software and better performance if so.

** #1**

Microsoft Intellipoint Wireless 6000 Laser Mouse. Any driver for that? When I'm scrolling in Firefox, the scroll speed is too fast. Back button does not work either. Any modifications need to get the full functionality working including back button, zoom button, wheel button (scrolling and button functions)?
[B]
#2[/B]

Creative Soundblaster Live! 24-bit External (USB). Any drivers for this, with full 5.1 capability, ** with nothing lacking ** ?

** #3**

Best font quality possible, as close to Windows as possible? I remember one method, a popular one but did not seem to work well. Fonts were not sharp and crisp in Linux compared to XP or Vista. I've enabled sub-pixelling (full) and all, RGB, 96 dpi, etc. with default Sans Serif 9pt, was not crisp. Please explain best possible method, settings, tweaks, etc. to replicate as much as I can to Windows. Its critical for me.

Please use my personal site as reference. [www.talkjesus.com]("http://www.talkjesus.com")
I would appreciate if you provide a full screen shot of the home page including shoutbox and let me know exactly what font settings you have (please provide as much detail as possible including font type, settings, etc). I attached a screenshot to show you the nice Windows quality I'm used to on Vista (or XP). It also looks fine on brothers MAC OSX, but sadly not in Linux by default from past experience.

** #4**

For a Linux newbie coming from Windows, now ready to install official Kubuntu (or Ubuntu) 7 when its released on the 19th, what recommended software do you recommend? Also, is Beryl / Compaz part of Kubuntu (or Ubuntu) 7 by default? What software managers should I install to enable the easiest possible quick downloads/install of software without the need to learn command line? I heard of Automatix 2 recent release, which likely explains why their site is down now. 

** #5**

Windows software alternatives you recommend for the below 

- roboform (I need an alternative that can handle complete form fillers with custom fields, password generators, password saver, etc)
- avg anti-virus
- roxio digital media studio deluxe (including burning audio, dvd, iso, mp3, data, etc)
- ms expression web (critical for me as I use this often, anyone tried with WINE?)
- secure crt (very important, I use this very often and its feature rich)

[B]#6

[/B]I've used Windows all my life, since the days of 3.x, currently Vista (nice interface). What in your opinions is the hottest theme out there with the most richest quality? Ubuntu's default interface is ok in my opinion, not horrible but I do have to admit I like some eye candy and real crisp to the quality of the theme.

** My Specs Below**. [COLOR=Red]Please let me know if any necessary or recommended tweaks needed be done, including special drivers[/COLOR].

Sony Vaio Laptop
Core 2 Duo 1.83GHz
2GB Memory
Main Partition: Vista Ultimate
Creative Soundblaster Live! 24-bit External USB
Intel 945GM / 950 Chipset
15.4" Widescreen (1280x800)
Intellipoint Wireless Laser 6000 Mouse

---

### Post by happymellon on 2007-04-09
Wow, quite a few specific questions, I'll try and answer what I can.

2. They mention the Live! External [in this thread]("http://ubuntuforums.org/showthread.php?t=204840"). By the sounds of things it should work, just need to add the extra settings for the other channels.

4. Compiz is included as default, and although is not activated it is simply pressing a button to turn it on. Beryl requires a little more work, but since they seem to be merging the two projects in to Compiz, hopefully this won't be necessary for much longer. Software managers, the Add/Remove app works fine for most programs and if you want something else Synaptic covers everything else. Both are installed by default, Add/Remove just contains a most used subset.
Neither require the command line, and adding extra repositories doesn't require the command line, it's all GUI if you want. Automatix is normally a run once program, but it does place itself in the System folder and I recommend it to virtually everyone, it isn't quite the same thing as Synaptic so it won't replace it.

5. You could try here [ Link ]("http://ubuntuforums.org/showthread.php?p=2240781") but unfortunatly there isn't much quite like Roboform. By the sounds of things you could try Oprah?
Antivirus isn't need on Linux, but if you want to scan files before passing it to a Windows machine you can try [Clam AV]("http://www.clamav.net/")
CD/DVD Burning software should be covered, I use Gnome Baker, but there are a few others you can try.
MS Expression, sorry never used it
SecureCRT is an SSH application? You can use the command line tool SSH to connect to another system. Perhaps If I knew which features you were looking for I could help further.


6. Try [gnome-look.org]("http://www.gnome-look.org") or if your running Kubuntu [http://kde-look.org]("http://kde-look.org")

---

### Post by Bashed on 2007-04-09
More questions :D

**#7 **

What is the MAC OSC widget / style found commonly in these themes listed at this site, such as this? How do I enable this cool widget?
[http://www.kde-look.org/content/show.php/Green+Leaf?content=54875](http://www.kde-look.org/content/show.php/Green+Leaf?content=54875)

[B]#8

[/B]Any possible alternative file manager, something easy to use like windows explorer? I admit, I get easily frustrated in the linux file system area.

---

### Post by FluffyElmo on 2007-04-10
I'll chip away at a couple of questions...

**4.** Compiz will have a utility to install commercial graphics drivers and enable desktop effects, but the effects won't be turned on by default.  Try [http://ubuntuguide.org]("http://ubuntuguide.org") for information on installing most common software. They have links for Automatix and EasyUbuntu, I've used both in the past and both are easy.

**5.** 
roboform: Seahorse will encrypt and manage desktop passwords while for the web functionality this Firefox extension is similar ([https://addons.mozilla.org/en-US/firefox/addon/3863]("https://addons.mozilla.org/en-US/firefox/addon/3863"))

Roxio: use K3B. Very feature rich and very easy to use. 

Instead of SecureCRT just try the terminal found under *Applications->Accessories->Terminal* as it supports tabs and various emulations. To start an ssh session just type *ssh username@serveraddress*. Also, note that you can type an address directly into the file manager to connect to a remote site graphically, for instance *sftp://username@serveraddress* will start a secure ftp connection with the server specified.

For web design (MS Expression?) I use Inkscape and the GIMP to produce graphics. NVU is a WYSIWYG HTML editor, while BlueFish, Skreem or Aptana are nice code based development tools. All these except Aptana should be available via *Applications->Add/Remove* or via Synaptic.

**6.** 
For Gnome I use Murrine ([http://cimi.netsons.org/pages/murrine.php]("http://cimi.netsons.org/pages/murrine.php"))  and like the look, though I customize the icons and colors to suit my taste using the theme manager. 

Compiz provides 3D desktop effects similar to Vista or OSX and will be easy to enable in the next release. You can choose your theme and then decide whether you want the 3D effects ot not, they are essentially separate.

You'll find Ubuntu to be very configurable in terms of themes, this can be confusing to start but gives you far more options than Windows in the long run. Themes will be completely different depending on whether you use Gnome or KDE. 

**7.** There are a variety of OSX style dock applets but I haven't used them so can't comment. There is one included with Compiz which is probably your best bet since it sounds like you'll be enabling it anyways.

**8.** If you're using gnome the file manager is quite configurable. Click on *Places->Home* and in the resulting window you can choose *View->Side Pane* for a more explorer style tree view. In *Edit->Preferences* you can configure additional options which may suit you better than the defaults. The KDE file manager is much closer to Windows and you may be happier with KDE overall though as a GNome fan I hate to say it :)

---

### Post by solar george on 2007-04-10
> #8

Any possible alternative file manager, something easy to use like windows explorer? I admit, I get easily frustrated in the linux file system area.

What is it about windows explorer that you particularly like?

If it is the file system layout there is not much that you can do aside from learning the linux file system layout.

---

### Post by airtonix on 2007-04-13
#5 please explain in great detail on the use of SecureCRT : 
  + how you use it?
  + what are you aiming to achieve?


There is a GUI way of SSH and  Terminal way of SSH.

Example, i can double clikc on a icon on my desktop, it opens a folder view of files that are on a remote server. this connection is made using the SSH protocol.

The terminal way involves using command line options.....useful if you need to run bluefish on the remote servers cpu but display it on your computer...

re : expressions... lol lol lol lol lol... when i saw this prog come out....i thought : hey maybe microsoft are actually getting th point.....it claims to output w3c compliant code....but i think we will see for ourselves. (garbage in = garbage out...ergo if you dont know why that P tag is bumping your LI list down a few EM's in IE only then you shouldnt be making websites or expecting pixel perfect results. 

and no dont go crying to macromedia flash ..... all you do there is exclude blind and handicapped people or those who waant to print your stuff out. 

repeat after me : flash is evil as a replacement for HTML/CSS.

---

### Post by Bashed on 2007-04-13
SecureCRT enables me to save a list of servers to log in into and their login passwords including wheel group usernames, root, custom ports, customer interface/ssh settings per server info saved in the list. Its feature rich.

---

### Post by airtonix on 2007-04-18
well the ssh support intergrated into the gnome desktop enviroment does all this.

ssh is native to linux, not windows.

---

### Post by Bashed on 2007-04-18
What is the proper way to uninstall Ubuntu 7 should I not like it? I will create a 10GB partition inside Vista's partition manager, but I need to know the proper method of removing that partition and correcting the MBR that Ubuntu will modify upon installation. 

The one thing that has kept me from fully using any linux flavor is the fonts and overall, interface. I love the Windows Vista font quality and design. Its extremely high quality, slick and clean. Linux may perform faster and be free, which is awesome but in the end for a business person and one who runs a ministry forum online around the clock 7 days a week, I need to be at peace in every aspect: design, quality, performance and a load of free software ;)

I just want to know one thing that I hope I will get mature, professional responses on. These are simple, sincere questions so let's hope we don't get linux fanatics mocking me or making hateful comments towards Microsoft. I don't care for those childish responses at all.

Why is the interface not of high quality like Windows or MAC OSX? 
Why are there no standard quality, crisp sharp fonts by default? 
(Windows has their own, MAC has their own, surprised Linux does not).

In regards to font quality, let's be honest. Many complain about this (I've observed many linux forums for a almost a year now). The interface, I know there are themes available but I have yet to find any that is still on par with quality like Vista or MAC OSX.  Yes, I know Linux is free (awesome) and that is why I'm here to try it out. I have many to buy MAC and Vista (which I use now), but in my personal quest I'd like to give linux a shot for good.

Thanks.

---

### Post by crispy_420 on 2007-04-18
#1 Mouse

Look here you just have modify the key maps: [http://ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx518](http://ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx518)
Made for logitech but is just mapping keys to macros, so it should work.

#5

No need for antivirus unless you are worried about shared files and windows.

I think you should have made seperate posts. Too much to ask for one post.

---

### Post by Bashed on 2007-04-19
Can someone please explain the proper method of uninstalling Ubuntu safely without ruining Vista?

---

### Post by rich.bradshaw on 2007-04-19
boot of Windows repair disk

fdisk /mbr

restart delete partition.

---

### Post by Bashed on 2007-04-19
Are you sure this can be done off Vista cd?

---

