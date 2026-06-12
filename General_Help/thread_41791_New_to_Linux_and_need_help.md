---
title: "New to Linux and need help"
date: 2005-06-14
forum: General Help
---

### Post by Xaruan on 2005-06-14
I currently still use Windows XP (dual boot), but I'm trying to slowly phase it out.  I chose Ubuntu because it seemed to be the most user friendly of the free linux distros.

I already know Ubuntu doesn't come with plugins for mp3, java, mpeg, avi, and others.  
I have tried installing realplayer and lots of other stuff, and the most I could get was a very choppy sound from my mp3s.  And despite my best efforts I can't get java to work with firefox.  For an engineer, I'm not the greatest at dealing with computers and I detest programming.  If anyone could give me detailed instructions on (the easiest) way to install these plug-ins, I would be forever grateful.

I think if Linux ever wants to eventually replace Windows for more and more users, getting and installing programs needs to be mindlessly easy (like Windows).  Most people, like myself, do not get pleasure out of using a terminal to install things.  The power of Linux with the ease of Windows (minus the blue screen of death) is what everyone wants.

---

### Post by desdinova on 2005-06-14
Unfortunately for software such as Java where the license is against free redistribution, thats the way things are ... did you check out Ubuntuguide.org - you can add the backports to your synaptic lists and install java and its plugins via that - graphically - without the console.

The one thing about the terminal is that the more you use it, the more you will realise its one of the most powerful features of linux. Its the Ferrari to the Trabant that is the Dos Command Prompt

[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by astronerd on 2005-06-14
Xauran, check out this site.... 
  [http://ubuntuguide.org](http://ubuntuguide.org)
They have the answer to most newbie questions and they can tell you how to set up most things.  Synaptic is the easiest way to install programs and all you have to do is add certain repositories to your list and look for packages in the synaptic list.  There are alot of different media players out there, XMMS is a good one(which I use) and it is in synaptic and this website will show you how to allow mp3;s to be played..  Hope this helped a little, I was in your postion a few months ago too..  Just remember you can always find more help here. 
Charles

---

### Post by Xaruan on 2005-06-14
Thanks.  I tried the terminal entry from UbuntuGuide to get j2re installed.

[B]
sudo apt-get install sun-j2rel.5[/B]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5

I never said learning how to use the terminal was bad.  I simply implied that 90%+ of all computer users don't want to have to deal with it if at all possible.  It's a fact that everyone creating programs for linux has to face.  Linux users generally want other people to switch to Linux for 2 reasons : Microsoft sucks and if more people use Linux then more program/gaming support will be for linux.

I must say, the speed at which I got a reply to my first post was great.  And my boss at work said the Gentoo linux forum community was the best.  It took a day before I got any response back from my post on those forums.  (I had to install Gentoo at work, and that's quite an undertaking.)

---

### Post by astronerd on 2005-06-14
[QUOTE=Xaruan]Thanks.  I tried the terminal entry from UbuntuGuide to get j2re installed.

[B]
sudo apt-get install sun-j2rel.5[/B]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5

I never said learning how to use the terminal was bad.  I simply implied that 90%+ of all computer users don't want to have to deal with it if at all possible.  It's a fact that everyone creating programs for linux has to face.  Linux users generally want other people to switch to Linux for 2 reasons : Microsoft sucks and if more people use Linux then more program/gaming support will be for linux.

I must say, the speed at which I got a reply to my first post was great.  And my boss at work said the Gentoo linux forum community was the best.  It took a day before I got any response back from my post on those forums.  (I had to install Gentoo at work, and that's quite an undertaking.)[/QUOTE]
 If you add the extra repos in your synaptic list then all the dependencies will be downloaded for you and you dont have to worry about anything else.  Should fix that missing package.  And using the gui for synaptic might be easier than apt get  IMO.  
Charles

---

### Post by Xaruan on 2005-06-14
Thanks.
It's partly working now.  The applet will load for such things as yahoo games.  

One page that has a dropdown menu gave me an error

[JavaScript Application]
This feature is not supported by your browser.

---

### Post by angkor on 2005-06-15
[QUOTE=Xaruan]Linux users generally want other people to switch to Linux for 2 reasons : Microsoft sucks and if more people use Linux then more program/gaming support will be for linux.
[/QUOTE]

I really couldn't care less if more people switch to Linux or not, it's all a matter of choice. I definately don't need more program support for GNU/Linux cause it already provides me with everything I need....games maybe, but I don't play games that much.

But hey, welcome to the wonderful world of Linux anyhow :) Synaptic should keep you away from the command line when installing programs.

---

### Post by psychicdragon on 2005-06-15
I don't think that error you posted is related to the jre. It says javascript not java. My guess is the site you're visiting detects whether you're using IE and if not spits out an error. Can you link to the site?

Pretty much everything you could ever need is in the [ubuntuguide](http://www.ubuntuguide.org/), which astronerd already linked too. Anything else can probably be resolved with a little help from us folks on the forums.

Welcome to Ubuntu

To angkor: Do you really find synaptic useful? If you know the package you want it's easier to install from the command line and if you don't it's impossible to find in synaptic anyway  ](*,)

---

### Post by Xaruan on 2005-06-15
You can use the search command in synaptic to apply an extra filter.

Thanks everyone for the help.  Things seem to working well now.

Again, much better responses than I ever got from the Gentoo forums.
(Gentoo is a pain.  It takes SO long to install.  Sure it's "powerful", but one wrong configuration and the system can go "kablooey")

---

### Post by angkor on 2005-06-15
[QUOTE=psychicdragon]To angkor: Do you really find synaptic useful? If you know the package you want it's easier to install from the command line and if you don't it's impossible to find in synaptic anyway  ](*,)[/QUOTE]

Actually I have never used it  :grin:  When a friend of mine first taught me the ways of Linux and installed a debian system for me, he never told me there was a graphical front-end to apt. By the time I found out, I was used to installing from the command line and since then I've never been tempted to use a frontend. I merely suggested using synaptic to Xaruan cause he seems to dislike the command line.

---

### Post by Xaruan on 2005-06-15
If the instructions are clear, I don't mind the command line.  It's just copy-paste-enter.
For programs that are downloaded off websites for linux, I think it would be more inviting to have  something simlar to Windows' Install Shield.  

For a long time I kept putting off installing linux simply because of the lack of gaming support for it.  Of course I want more and more people to use Linux.  If the number of Linux users increases, the amount of support we get will increase, thus causing more people to swtch to Linux.  If that ideal trend continues, Microsoft will have to improve Windows and its other programs in order to compete.  This all ends with benefits for both Linux and Windows users.  Personally, I don't think Linux should stay as an OS meant solely for the computer literate.  The increasing popularity of Linux is, in my opinion, vital to the longterm improvement of everyone's PC experience.  There's my little bit of ranting.

Cedega FTW

I doubt there needs to be any further replies to this thread unless any of you feel it's necessary.

---

